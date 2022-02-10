<script>
  export let name;
  import { Controller } from "swiper";
  import { Swiper, SwiperSlide } from "swiper/svelte";
  import "swiper/css";
  import "./style.css";

  // store swiper instances
  let swipers = [];
</script>

<main>
  <div id="slides">
    <Swiper
      grabCursor={true}
      slidesPerView={3}
      loop={true}
      modules={[Controller]}
      on:swiper={(e) => {
        const swiper = e.detail;
        setTimeout(() => {
          swipers[1] = swiper;
        });
      }}
      controller={{ control: swipers[2] }}
    >
      <SwiperSlide>A</SwiperSlide>
      <SwiperSlide>B</SwiperSlide>
      <SwiperSlide>C</SwiperSlide>
    </Swiper>

    <Swiper
      grabCursor={true}
      slidesPerView={3}
      loop={true}
      modules={[Controller]}
      on:swiper={(e) => {
        const swiper = e.detail;
        setTimeout(() => {
          swipers[2] = swiper;
        });
      }}
      controller={{ control: swipers[1] }}
    >
      <SwiperSlide>D</SwiperSlide>
      <SwiperSlide>E</SwiperSlide>
      <SwiperSlide>F</SwiperSlide>
    </Swiper>

    <Swiper
      grabCursor={true}
      slidesPerView={3}
      loop={true}
      modules={[Controller]}
      on:swiper={(e) => {
        const swiper = e.detail;
        setTimeout(() => {
          swipers[3] = swiper;
        });
      }}
      controller={{ control: [swipers[1], swipers[2]] }}
    >
      <SwiperSlide>G</SwiperSlide>
      <SwiperSlide>H</SwiperSlide>
      <SwiperSlide>I</SwiperSlide>
    </Swiper>
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
