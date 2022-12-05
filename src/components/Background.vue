<script setup>
import { ref } from 'vue'

import imgList from '../assets/imageList.json'

const images = imgList


let current = ref(0);

async function changeBackground() {
    if (this.current < this.images.length - 1) {
        this.current = this.current + 1;
    } else {
        this.current = 0;
    }
}

</script>

<template>
    <Transition name="fade">
        <img class="bgimg" @click="changeBackground()" :src="'images/'+images[current]" :key="current" />
    </Transition>
</template>

<style scoped>
.bgimg {
    z-index: -1;
    position: absolute;
    top: 0px;
    right: 0;
    width: 100%;
    height: 100%;
    background-size: auto;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.75s ease-in-out;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>