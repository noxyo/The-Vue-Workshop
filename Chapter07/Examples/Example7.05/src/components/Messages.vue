<template>
  <div>
    <h2>This is messages animation on page initial render</h2>
    <transition-group
      :appear="true"
      appear-class="fade-enter"
      appear-active-class="fade-enter-active"
      tag="div"
    >
      <p v-for="message in messages" :key="message">{{message}}</p>
    </transition-group>
    <button v-on:click="show = !show">
      {{ show ? "Hide list": "Show list"}}
    </button>
    <transition-group
      name="fade"
      tag="div"
    >
      <p v-for="message in messages" :key="message" v-show="show" class="msg-in-animate">{{message}}</p>
    </transition-group>
  </div>
</template>
<script>
export default {
  data() {
    return {
      messages: [
        'Hello, how are you?',
        'The weather is nice',
        'This is message feed',
        'And I am the fourth message'
      ],
      show: false
    }
  }
}
</script>
<style>
.fade-enter-active, .fade-leave-active {
  transition: all 5s;
}
.fade-enter, .fade-leave-active {
  opacity: 0;
  transform: translateX(30px);
}

.fade-move {
  transition: transform 2s ease-in;
}
</style>