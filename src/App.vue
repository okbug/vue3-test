<template>
  <div id="app">
    <h1>Hello World</h1>
    <span>{{ count }}</span>
    <span>double: {{ double }} </span>
    <br />
    <button @click="setCount">Click</button>

    <h2>{{ text }}</h2>
    <input type="text" v-model="text" />
    <button @click="reverseText">Reverse</button>
    <button @click="resetText">Reset</button>
  </div>
</template>

<script>
import { ref, onMounted, watchEffect, computed } from 'vue';
export default {
  name: 'App',
  components: {},
  setup() {
    const count = ref(1);
    const setCount = () => {
      count.value++;
    };

    const double = computed(() => count.value * 2);

    watchEffect(() => {
      console.log(count.value, 'watch');
    });

    const text = ref('Hello World');
    const reverseText = () => {
      text.value = text.value.split('').reverse().join('');
    };
    const resetText = () => {
      text.value = 'Hello World';
    };
    onMounted(() => {
      console.log(1);
      console.log(32);
    });

    return {
      count,
      setCount,
      text,
      reverseText,
      resetText,
      double,
    };
  },
};
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
</style>
