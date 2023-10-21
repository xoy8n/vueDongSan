<template>
  <div class="menu">
    <a v-for="navBar in menus" :key="navBar">{{ navBar }}</a>
  </div>

  <div class="modal" v-if="modalOpen == true">
    <div class="modal-inner">
      <h4>MODAL</h4>
      <P>Hi. This is modal.</P>
    </div>
  </div>

  <div v-for="(a, i) in 3" :key="a">
    <img :src="require(`./assets/room${i}.jpg`)" alt="" class="room-img" />
    <h4 @click="modalOpen = true">{{ products[i] }} 원룸</h4>
    <p>{{ prices[i] }}만원</p>
    <button @click="increase(i)">REPORT</button>
    <span>count : {{ counts[i] }}</span>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      modalOpen: false,
      counts: [0, 0, 0],
      menus: ["Home", "Products", "About"],
      products: ["성산동", "중동", "을지로동"],
      prices: ["60", "20", "40"],
    };
  },

  methods: {
    increase(i) {
      this.counts[i]++;
    },
  },

  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.menu {
  display: flex;
  justify-content: space-around;
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: #fff;
  padding: 10px;
  text-decoration: none;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}

.modal {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  top: 0;
  padding: 20px;
}
.modal-inner {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
