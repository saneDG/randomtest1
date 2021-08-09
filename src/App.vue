<template>
  <div id="app">
    <p
      v-for="index in 10"
      :key="index"
      class="bar"
      :style="`height: ${amount[index - 1] / 100}px`"
    >
      {{ amount[index - 1] / 100 }}
    </p>
  </div>
</template>

<script>
import Vue from "vue";

export default {
  name: "App",
  components: {},
  data() {
    return {
      amount: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      max: 10,
    };
  },
  mounted() {
    function getRandomInt() {
      return Math.floor(Math.random() * 10);
    }
    const iterations = 10;
    for (let index = 1; index < iterations; index++) {
      setTimeout(() => {
        const num = getRandomInt();
        this.amount[num]++;
        Vue.set(this.amount, num, this.amount[num]);
      }, 5);
    }
  },
};
</script>

<style>
#app {
  display: flex;
  width: 600px;
  height: 100vh;
  align-items: flex-end;
  justify-content: space-between;
  margin: 0 auto;
  color: white;
}

.bar {
  width: 50px;
  background-color: rgb(39, 39, 39);
  text-align: center;
}
</style>
