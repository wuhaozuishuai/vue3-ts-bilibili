<template>
  <van-swipe class="my-swipe" :autoplay="3000" indicator-color="white">
    <van-swipe-item v-for="item in list" :key="item.imgSrc">
      <img :src="item.imgSrc" />
    </van-swipe-item>
  </van-swipe>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import axios from 'axios'

interface ISwiper {
  imgSrc: string
  link: string
}
// ref 函数用于定义模板中使用的响应式数据，相当于 Vue2 的 data
const list = ref<ISwiper[]>([])

axios({
  url: '/swiperList',
  method: 'get'
}).then(res => {
  console.log('轮播图数据', res.data.result)
  list.value = res.data.result
})
</script>

<style lang="less" scoped>
.my-swipe {
  img {
    width: 100%;
  }
}</style>
