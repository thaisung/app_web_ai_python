<template>
  <div class="flex w-[100%] grow min-h-screen bg-gray-200">
    <div class="flex flex-col bg-gray-100 mx-auto max-w-7xl grow px-3 py-4">
      <div
        class="shadow-md rounded-md w-full grow-0 h-[100px] bg-cover bg-center bg-[url('https://helpx.adobe.com/content/dam/help/en/photoshop/using/convert-color-image-black-white/jcr_content/main-pars/before_and_after/image-before/Landscape-Color.jpg')]"
      ></div>
      <p class="py-4 font-bold text-[20px]">Thương hiệu</p>
      <div class="grid grid-cols-10 gap-2 w-full grow-0">
        <router-link
          v-for="(i, index) in counter.thuong_hieu_danh_sach"
          :to="'/loc/thuong-hieu/' + i.Name"
          v-on:click="this.counter.F_loc_san_pham('', '', i.Name)"
          :key="index"
          class="flex justify-center items-center cursor-pointer border-[1px] rounded-md border-gray-[#e5e7eb] h-[34px] px-1 py-1 bg-white"
        >
          <img :src="i.Avatar" />
        </router-link>
      </div>
      <p class="py-4 font-bold text-[20px]">Xuất xứ</p>
      <div class="grid grid-cols-9 gap-2 w-full grow-0">
        <router-link
          v-for="(i, index) in counter.quoc_gia_danh_sach"
          :to="'/loc/quoc-gia/' + i.Name"
          :key="index"
          :style="{ backgroundImage: `url('${i.Avatar}')` }"
          v-on:click="this.counter.F_loc_san_pham('', i.Name, '')"
          class="shadow-md relative cursor-pointer rounded-md h-[135px] bg-cover bg-center"
          @mouseover="hoveredIndex = index"
          @mouseleave="hoveredIndex = null"
        >
          <p
            v-show="hoveredIndex === index"
            class="absolute bottom-[140px] left-0 px-1 py-1 bg-white border-[1px] rounded-md border-gray-700 text-[14px] font-normal"
          >
            {{ i.Name }}
          </p>
        </router-link>
      </div>
      <p class="py-4 font-bold text-[20px]">Sản phẩm đang bán</p>
      <div class="grid grid-cols-5 gap-4 w-full grow-0">
        <router-link
          :to="`/chi-tiet/${i.id}`"
          v-for="(i, index) in counter.san_pham_danh_sach.data"
          :key="index"
          v-on:click="counter.F_chi_tiet_san_pham(i.id)"
          class="shadow-md flex flex-col items-center rounded-md py-2 px-2 hover:scale-105 cursor-pointer bg-white"
        >
          <div class="px-2">
            <img :src="i.Avatar" />
          </div>
          <p class="font-bold text-[20px] text-slate-600 w-full">
            {{ i.Name }}
          </p>
          <div class="flex gap-2 w-full">
            <p class="text-[18px] text-red-500 font-semibold">
              {{ i.Price_has_decreased }}₫
            </p>
            <div class="w-full flex items-center justify-start font-semibold">
              <div class="relative">
                <p class="">{{ i.Price }}₫</p>
                <div
                  class="h-[0px] w-full border-[1px] border-slate-700 absolute top-[10px]"
                ></div>
              </div>
            </div>
          </div>
          <div class="flex items-center justify-between w-full">
            <div class="flex gap-1 items-center">
              <svg
                v-for="(i, index) in 5"
                :key="index"
                xmlns="http://www.w3.org/2000/svg"
                height="16"
                width="18"
                viewBox="0 0 576 512"
              >
                <path
                  fill="orange"
                  d="M316.9 18C311.6 7 300.4 0 288.1 0s-23.4 7-28.8 18L195 150.3 51.4 171.5c-12 1.8-22 10.2-25.7 21.7s-.7 24.2 7.9 32.7L137.8 329 113.2 474.7c-2 12 3 24.2 12.9 31.3s23 8 33.8 2.3l128.3-68.5 128.3 68.5c10.8 5.7 23.9 4.9 33.8-2.3s14.9-19.3 12.9-31.3L438.5 329 542.7 225.9c8.6-8.5 11.7-21.2 7.9-32.7s-13.7-19.9-25.7-21.7L381.2 150.3 316.9 18z"
                />
              </svg>
            </div>
            <div class="flex gap-1 items-center">
              <p>Yêu thích</p>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                height="16"
                width="16"
                viewBox="0 0 512 512"
              >
                <path
                  fill="red"
                  d="M225.8 468.2l-2.5-2.3L48.1 303.2C17.4 274.7 0 234.7 0 192.8v-3.3c0-70.4 50-130.8 119.2-144C158.6 37.9 198.9 47 231 69.6c9 6.4 17.4 13.8 25 22.3c4.2-4.8 8.7-9.2 13.5-13.3c3.7-3.2 7.5-6.2 11.5-9c0 0 0 0 0 0C313.1 47 353.4 37.9 392.8 45.4C462 58.6 512 119.1 512 189.5v3.3c0 41.9-17.4 81.9-48.1 110.4L288.7 465.9l-2.5 2.3c-8.2 7.6-19 11.9-30.2 11.9s-22-4.2-30.2-11.9zM239.1 145c-.4-.3-.7-.7-1-1.1l-17.8-20c0 0-.1-.1-.1-.1c0 0 0 0 0 0c-23.1-25.9-58-37.7-92-31.2C81.6 101.5 48 142.1 48 189.5v3.3c0 28.5 11.9 55.8 32.8 75.2L256 430.7 431.2 268c20.9-19.4 32.8-46.7 32.8-75.2v-3.3c0-47.3-33.6-88-80.1-96.9c-34-6.5-69 5.4-92 31.2c0 0 0 0-.1 .1s0 0-.1 .1l-17.8 20c-.3 .4-.7 .7-1 1.1c-4.5 4.5-10.6 7-16.9 7s-12.4-2.5-16.9-7z"
                />
              </svg>
            </div>
          </div>
        </router-link>
      </div>
      <div class="flex justify-center gap-2 mt-4 w-full">
        <a
          v-show="counter.san_pham_danh_sach.previous"
          v-on:click="counter.product_page(counter.san_pham_danh_sach.previous)"
          class="flex justify-center items-center bg-white hover:bg-gray-100 px-3 py-2 rounded-md shadow-md cursor-pointer"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="20"
            viewBox="0 0 320 512"
          >
            <path
              d="M41.4 233.4c-12.5 12.5-12.5 32.8 0 45.3l160 160c12.5 12.5 32.8 12.5 45.3 0s12.5-32.8 0-45.3L109.3 256 246.6 118.6c12.5-12.5 12.5-32.8 0-45.3s-32.8-12.5-45.3 0l-160 160z"
            />
          </svg>
        </a>
        <div
          class="flex justify-center items-center bg-white px-3 py-2 rounded-md shadow-md text-[18px] font-bold"
        >
          {{ counter.san_pham_danh_sach.current_page }}
        </div>
        <a
          v-show="counter.san_pham_danh_sach.next"
          v-on:click="counter.product_page(counter.san_pham_danh_sach.next)"
          class="flex justify-center items-center bg-white px-3 py-2 hover:bg-gray-100 rounded-md shadow-md cursor-pointer"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="20"
            viewBox="0 0 320 512"
          >
            <path
              d="M278.6 233.4c12.5 12.5 12.5 32.8 0 45.3l-160 160c-12.5 12.5-32.8 12.5-45.3 0s-12.5-32.8 0-45.3L210.7 256 73.4 118.6c-12.5-12.5-12.5-32.8 0-45.3s32.8-12.5 45.3 0l160 160z"
            />
          </svg>
        </a>
      </div>
      <p class="py-4 font-bold text-[20px]">Sản phẩm gợi ý</p>
      <div class="grid grid-cols-5 gap-4 w-full grow-0">
        <router-link
          :to="`/chi-tiet/${i.id}`"
          v-for="(i, index) in counter.danh_sach_san_pham_ai"
          :key="index"
          v-on:click="counter.F_chi_tiet_san_pham(i.id)"
          class="shadow-md flex flex-col items-center rounded-md py-2 px-2 hover:scale-105 cursor-pointer bg-white"
        >
          <div class="px-2">
            <img :src="counter.Domain_Backend + i.Avatar" />
          </div>
          <p class="font-bold text-[20px] text-slate-600 w-full">
            {{ i.Name }}
          </p>
          <div class="flex gap-2 w-full">
            <p class="text-[18px] text-red-500 font-semibold">
              {{ i.Price_has_decreased }}₫
            </p>
            <div class="w-full flex items-center justify-start font-semibold">
              <div class="relative">
                <p class="">{{ i.Price }}₫</p>
                <div
                  class="h-[0px] w-full border-[1px] border-slate-700 absolute top-[10px]"
                ></div>
              </div>
            </div>
          </div>
          <div class="flex items-center justify-between w-full">
            <div class="flex gap-1 items-center">
              <svg
                v-for="(i, index) in 5"
                :key="index"
                xmlns="http://www.w3.org/2000/svg"
                height="16"
                width="18"
                viewBox="0 0 576 512"
              >
                <path
                  fill="orange"
                  d="M316.9 18C311.6 7 300.4 0 288.1 0s-23.4 7-28.8 18L195 150.3 51.4 171.5c-12 1.8-22 10.2-25.7 21.7s-.7 24.2 7.9 32.7L137.8 329 113.2 474.7c-2 12 3 24.2 12.9 31.3s23 8 33.8 2.3l128.3-68.5 128.3 68.5c10.8 5.7 23.9 4.9 33.8-2.3s14.9-19.3 12.9-31.3L438.5 329 542.7 225.9c8.6-8.5 11.7-21.2 7.9-32.7s-13.7-19.9-25.7-21.7L381.2 150.3 316.9 18z"
                />
              </svg>
            </div>
            <div class="flex gap-1 items-center">
              <p>Yêu thích</p>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                height="16"
                width="16"
                viewBox="0 0 512 512"
              >
                <path
                  fill="red"
                  d="M225.8 468.2l-2.5-2.3L48.1 303.2C17.4 274.7 0 234.7 0 192.8v-3.3c0-70.4 50-130.8 119.2-144C158.6 37.9 198.9 47 231 69.6c9 6.4 17.4 13.8 25 22.3c4.2-4.8 8.7-9.2 13.5-13.3c3.7-3.2 7.5-6.2 11.5-9c0 0 0 0 0 0C313.1 47 353.4 37.9 392.8 45.4C462 58.6 512 119.1 512 189.5v3.3c0 41.9-17.4 81.9-48.1 110.4L288.7 465.9l-2.5 2.3c-8.2 7.6-19 11.9-30.2 11.9s-22-4.2-30.2-11.9zM239.1 145c-.4-.3-.7-.7-1-1.1l-17.8-20c0 0-.1-.1-.1-.1c0 0 0 0 0 0c-23.1-25.9-58-37.7-92-31.2C81.6 101.5 48 142.1 48 189.5v3.3c0 28.5 11.9 55.8 32.8 75.2L256 430.7 431.2 268c20.9-19.4 32.8-46.7 32.8-75.2v-3.3c0-47.3-33.6-88-80.1-96.9c-34-6.5-69 5.4-92 31.2c0 0 0 0-.1 .1s0 0-.1 .1l-17.8 20c-.3 .4-.7 .7-1 1.1c-4.5 4.5-10.6 7-16.9 7s-12.4-2.5-16.9-7z"
                />
              </svg>
            </div>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>
<script>
import { useCounterStore } from "@/stores/counter";
import axios from "axios";
import VueCookies from "vue-cookies";

export default {
  data() {
    return {
      url_image: [],
      url_image_inset: [{ id: 4, Image_post: "", post: 4 }],
      url_image_inset_one: "",
      hoveredIndex: null,
    };
  },
  setup() {
    const counter = useCounterStore();
    return { counter };
  },
  mounted: function () {
    this.counter.F_san_pham_danh_sach();
    this.counter.F_thuong_hieu_danh_sach();
    this.counter.F_quoc_gia_danh_sach();
  },
  computed: {},
  methods: {},
  components: {},
};
</script>

<style>
#cjss::-webkit-scrollbar {
  width: 5px;
  height: 8px; /* Chiều rộng vùng chứa scrollbar */
}
#cjss::-webkit-scrollbar-track {
  background: #1f2937; /* Màu nền ngoài của thanh scrollbar */
}
#cjss::-webkit-scrollbar-thumb {
  background-color: #7dd3fc; /* Màu của thanh cuộn (scroll thumb) */
  border-radius: 1px; /* Bo góc scroll thumb */
  /* border: 2px solid #ccc;  Không hỗ trợ padding, margin, transition nên dùng viền cùng màu nên để padding scroll thumb */
}
#cjss::-webkit-scrollbar-thumb:hover {
  background-color: #e0f2fe; /* Hiệu ứng di chuột đổi màu*/
}

#cjss1::-webkit-scrollbar {
  width: 5px;
  height: 8px; /* Chiều rộng vùng chứa scrollbar */
}
#cjss1::-webkit-scrollbar-track {
  background: #393636; /* Màu nền ngoài của thanh scrollbar */
}
#cjss1::-webkit-scrollbar-thumb {
  background-color: #595857; /* Màu của thanh cuộn (scroll thumb) */
  border-radius: 1px; /* Bo góc scroll thumb */
  /* border: 2px solid #ccc;  Không hỗ trợ padding, margin, transition nên dùng viền cùng màu nên để padding scroll thumb */
}
#cjss1::-webkit-scrollbar-thumb:hover {
  background-color: #655f58; /* Hiệu ứng di chuột đổi màu*/
}

#video {
  transform: rotateY(180deg);
  -webkit-transform: rotateY(180deg); /* Safari and Chrome */
  -moz-transform: rotateY(180deg); /* Firefox */
}
</style>
