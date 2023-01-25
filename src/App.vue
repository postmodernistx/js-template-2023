<script setup lang="ts">
import { RouterView, useRoute } from 'vue-router';
// import { getAuth, onAuthStateChanged, signInWithPopup, GoogleAuthProvider } from 'firebase/auth';
import { ref } from 'vue';

// <<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>>
// ----------------8<-------------[ GOOGLE AUTHENTICATION ]--------------------
// <<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>>
const isLoggedIn = ref(false);
// const provider = new GoogleAuthProvider();

const error = ref('');

// const auth = getAuth();
// onAuthStateChanged(auth, user => {
//   if (user !== null) {
//     if (user.uid === 'LPXEjRZbMIbk6GsB1kJi3vwrLcq1' || user.uid == 'q9QQ9eE23HXdflgtTNEVNOVx8iv2') {
//       isLoggedIn.value = true;
//       return;
//     } else {
//       console.warn('User UID not permitted.');
//     }
//   }
//   isLoggedIn.value = false;
// });
//
// function authenticate() {
//   signInWithPopup(auth, provider)
//     .then(() => {
//       console.log('Login successful');
//     })
//     .catch(error => {
//       error.value = 'Error logging in: ' + error;
//     });
// }

// <<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>>
// ----------------8<-------------[ ROUTE TRANSITIONS ]------------------------
// <<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>><<>>
const route = useRoute();
const duration = 0.5;

function onBeforeEnter(el: HTMLElement) {
}

function onEnter(el: HTMLElement, done: gsap.Callback) {
}

function onAfterEnter(el: HTMLElement) {
}

function onEnterCancelled(el: HTMLElement) {
}

function onBeforeLeave(el: HTMLElement) {}

function onLeave(el: HTMLElement, done: gsap.Callback) {
}

function onAfterLeave(el: HTMLElement) {}

function onLeaveCancelled(el: HTMLElement) {
}
</script>

<template>
  <div v-if="!isLoggedIn" class="my-4 mx-4">
    <h1>Please login</h1>
    <div class="text-center">
      <button class="inline-flex gap-1 items-center" @click="authenticate">
        <span>Login</span> <span class="material-symbols-outlined">login</span>
      </button>
      <p class="text-red-500">{{ error }}</p>
    </div>
  </div>
  <div v-else>
    <header>
      You're logged in!
    </header>

    <router-view v-slot="{ Component }">
      <keep-alive>
        <transition
          mode="out-in"
          :css="false"
          @before-enter="onBeforeEnter"
          @enter="onEnter"
          @after-enter="onAfterEnter"
          @enter-cancelled="onEnterCancelled"
          @before-leave="onBeforeLeave"
          @leave="onLeave"
          @after-leave="onAfterLeave"
          @leave-cancelled="onLeaveCancelled"
        >
          <component :is="Component" />
        </transition>
      </keep-alive>
    </router-view>
  </div>
</template>

<style lang="scss">
</style>
