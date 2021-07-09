<template>
  <router-link to="/home">Home</router-link>
  <router-link to="/datail">Detail</router-link>
  <transition :name="transitionName">
    <router-view></router-view>
  </transition>
</template>

<script lang="ts">
import { defineComponent, toRefs,reactive } from "vue";
import {useRouter} from 'vue-router'
export default defineComponent({
  name: "App",
  components: {},
  setup() {
    const state = reactive({
      transitionName: "slide-left",
    });
    const router = useRouter()
    router.beforeEach((to, from, next) => {
      console.log(to,from);
      next()
    })
    return {
      ...toRefs(state),
    };
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
a {
  padding: 10px;
}
</style>
