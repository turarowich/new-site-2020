<template>
  <div>
    <Slider :items="sliderItem1" />
    <div class="container">
      <ProductTopWidget />
      <ProductWidget title="Наше специальное предложение" />
    </div>
    <Slider :items="sliderItem2" />
    <div class="container">
      <ProductSliderWidget title="Наше специальное предложение" />
      <NewsWidget title="Новости нашего магазина" />
      <div class="about">
        <div class="about__title">О магазине</div>
        <div class="row">
          <div class="col-12 col-md">
            <div class="about__text">
              <p>
                Студия «О-ДИЗАЙН» занимается продажей эксклюзивных обоев
                отличного качества. У нас представлена продукция, изготовленная
                английскими и шведскими производителями.
              </p>
              <p>
                Качественные элитные обои — это выбор тех, кто обладает хорошим
                вкусом и стремится создать запоминающийся и уютный интерьер. Мы
                предлагаем лучшие образцы известных европейских фабрик,
                регулярно пополняя свой ассортимент новыми коллекциями на любой
                вкус.
              </p>
            </div>
          </div>
          <div class="col-12 col-md-auto">
            <div class="aboutBlock">
              <div class="row no-gutters">
                <div class="col-6">
                  <div class="aboutBlock__item aboutBlock__item--1">
                    <div
                      class="aboutBlock__itemImg aboutBlock__itemImg--1"
                    ></div>
                    <div class="aboutBlock__itemTitle">
                      450 000 довольных клиентов
                    </div>
                  </div>
                </div>
                <div class="col-6">
                  <div class="aboutBlock__item aboutBlock__item--2">
                    <div
                      class="aboutBlock__itemImg aboutBlock__itemImg--2"
                    ></div>
                    <div class="aboutBlock__itemTitle">
                      Эксклюзивный поставщик обоев из Англии и Швеции
                    </div>
                  </div>
                </div>
                <div class="col-6">
                  <div class="aboutBlock__item aboutBlock__item--3">
                    <div
                      class="aboutBlock__itemImg aboutBlock__itemImg--3"
                    ></div>
                    <div class="aboutBlock__itemTitle">
                      Быстрая доставка по России
                    </div>
                  </div>
                </div>
                <div class="col-6">
                  <div class="aboutBlock__item aboutBlock__item--4">
                    <div
                      class="aboutBlock__itemImg aboutBlock__itemImg--4"
                    ></div>
                    <div class="aboutBlock__itemTitle aboutBlock__itemTitle--4">
                      Возможность заказать фотообои под индивидуальный размер
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Slider from '@/components/Slider'
import ProductWidget from '@/components/product/product-widget/ProductWidget'
import ProductTopWidget from '@/components/product/product-top-widget/ProductTopWidget'
import ProductSliderWidget from '@/components/product/product-slider-widget/ProductSliderWidget'
import NewsWidget from '@/components/news/news-widget/NewsWidget'

export default {
  components: {
    Slider,
    ProductTopWidget,
    ProductWidget,
    NewsWidget,
    ProductSliderWidget,
  },
  async asyncData({ $axios }) {
    let response = await $axios.$get(`${process.env.API_URL}/slider/1`);
    const sliderItem1 = response.slides
      ? response.slides.map(item => {
        return { ...item, image: `${process.env.IMAGE_BASE_URL}/${item.image}`
        }
      }) : []

    response = await $axios.$get(`${process.env.API_URL}/slider/2`);
    const sliderItem2 = response.slides
      ? response.slides.map(item => {
        return { ...item, image: `${process.env.IMAGE_BASE_URL}/${item.image}`
        }
      }) : []

    return { sliderItem1, sliderItem2 }
  }
}
</script>

<style lang="scss">
.about {
  margin-bottom: 80px;
  &__title {
    font-size: 32px;
    font-weight: 700;
    margin-bottom: 30px;
  }
  &__text {
    max-width: 500px;
  }
}
.aboutBlock {
  max-width: 580px;
  &__item {
    &--1 {
      border-bottom: 1px solid #ddd;
    }
    &--2 {
      border-bottom: 1px solid #ddd;
      border-left: 1px solid #ddd;
      padding-left: 32px;
    }
    &--3 {
      padding-top: 30px;
    }
    &--4 {
      border-left: 1px solid #ddd;
      padding-left: 32px;
      padding-top: 30px;
    }
  }
  &__itemImg {
    height: 47px;
    width: 50px;
    background-repeat: no-repeat;
    margin-bottom: 20px;
    &--1 {
      background-image: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNTAiIGhlaWdodD0iMzgiIHZpZXdCb3g9IjAgMCA1MCAzOCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggZD0iTTI2LjgxMjUgMEMyMi4zNTU1IDAgMTkuMDk3NyAxLjc2MTcyIDE3LjM3NSA0LjM3NUMxNy4wMTk1IDQuOTEwMTYgMTYuNzUzOSA1LjQ3MjY2IDE2LjUzMTIgNi4wNjI1TDE2LjI4MTIgNS41NjI1QzE2LjExNzIgNS4yMjY1NiAxNS43ODEyIDUuMDA3ODEgMTUuNDA2MiA1QzExLjk0NTMgNSA5LjM1OTM3IDYuNDA2MjUgOCA4LjVDNi43NTc4MSAxMC40MTAyIDYuNjgzNTkgMTIuODEyNSA3LjQ2ODc1IDE1LjA2MjVDNy40MDYyNSAxNS4xNjQxIDcuMjczNDQgMTUuMjE4OCA3LjIxODc1IDE1LjM0MzhDNy4wMzEyNSAxNS43NjE3IDYuOTI5NjkgMTYuMjg5MSA3IDE2LjkwNjJDNyAxNi45MTggNyAxNi45MjU4IDcgMTYuOTM3NUM3LjExMzI4IDE3Ljg0NzcgNy4zNDM3NSAxOC41IDcuNzE4NzUgMTlDNy44Nzg5IDE5LjIxMDkgOC4xMzI4MSAxOS4yMTA5IDguMzQzNzUgMTkuMzQzOEM4LjQ5MjE5IDIwLjA4NTkgOC43MDMxMiAyMC44MjQyIDkgMjEuNDM3NUM5LjE3NTc4IDIxLjgwNDcgOS4zNjMyOCAyMi4xMjExIDkuNTYyNSAyMi40MDYyQzkuNjI4OTEgMjIuNTAzOSA5Ljc0MjE5IDIyLjU3MDMgOS44MTI1IDIyLjY1NjJDOS44MTI1IDIzLjQyMTkgOS43ODUxNiAyNC4xMDk0IDkuNzE4NzUgMjVDOS41MzkwNiAyNS40NTcgOS4xMDE1NiAyNS44NTk0IDguMjgxMjUgMjYuMjgxMkM3LjQ0MTQxIDI2LjcxMDkgNi4zMTY0MSAyNy4xMDk0IDUuMTU2MjUgMjcuNjI1QzMuOTk2MDkgMjguMTQwNiAyLjc1NzgxIDI4Ljc2NTYgMS43ODEyNSAyOS43ODEyQzAuODA0Njg3IDMwLjc5NjkgMC4xMTMyOCAzMi4yMTg4IC05LjExMDY2ZS0wNyAzNC4wMzEyQy0wLjAxNTYyNTkgMzQuMzA4NiAwLjA4MjAzMDQgMzQuNTc4MSAwLjI2OTUzIDM0Ljc3NzNDMC40NjA5MzcgMzQuOTgwNSAwLjcyMjY1NSAzNS4wOTM4IDAuOTk5OTk5IDM1LjA5MzhINy4yMTg3NUM3LjA2NjQgMzUuNjY0MSA2Ljk0NTMxIDM2LjI3NzMgNi45MDYyNSAzNi45Mzc1QzYuODkwNjIgMzcuMjE0OCA2Ljk4ODI4IDM3LjQ4NDQgNy4xNzU3OCAzNy42ODM2QzcuMzY3MTkgMzcuODg2NyA3LjYyODkxIDM4IDcuOTA2MjUgMzhINDIuMDkzOEM0Mi4zNzExIDM4IDQyLjYzMjggMzcuODg2NyA0Mi44MjQyIDM3LjY4MzZDNDMuMDExNyAzNy40ODQ0IDQzLjEwOTQgMzcuMjE0OCA0My4wOTM4IDM2LjkzNzVDNDMuMDUwOCAzNi4yMzgzIDQyLjkxOCAzNS42MDE2IDQyLjc1IDM1SDQ5QzQ5LjI3NzMgMzUgNDkuNTM5MSAzNC44ODY3IDQ5LjczMDUgMzQuNjgzNkM0OS45MTggMzQuNDg0NCA1MC4wMTU2IDM0LjIxNDggNTAgMzMuOTM3NUM0OS44ODY3IDMyLjEyODkgNDkuMTg3NSAzMC43MDMxIDQ4LjIxODggMjkuNjg3NUM0Ny4yNSAyOC42NzE5IDQ2LjA1NDcgMjguMDQ2OSA0NC45MDYyIDI3LjUzMTJDNDMuNzU3OCAyNy4wMTU2IDQyLjY0NDUgMjYuNjE3MiA0MS44MTI1IDI2LjE4NzVDNDEuMDE5NSAyNS43NzczIDQwLjU5NzcgMjUuMzU1NSA0MC40MDYyIDI0LjkwNjJDNDAuMzM5OCAyNC4wOTc3IDQwLjMxMjUgMjMuMzc4OSA0MC4zMTI1IDIyLjU2MjVDNDAuMzc4OSAyMi40NzY2IDQwLjQ5NjEgMjIuNDA2MiA0MC41NjI1IDIyLjMxMjVDNDAuNzYxNyAyMi4wMzEyIDQwLjkyMTkgMjEuNzA3IDQxLjA5MzggMjEuMzQzOEM0MS4zNzExIDIwLjc1MzkgNDEuNTc0MiAyMC4wNTA4IDQxLjY4NzUgMTkuMzQzOEM0MS44OTA2IDE5LjIxNDggNDIuMTI4OSAxOS4yMDMxIDQyLjI4MTIgMTlDNDIuNjU2MiAxOC41IDQyLjg4NjcgMTcuODQ3NyA0MyAxNi45Mzc1QzQzLjA3MDMgMTYuMzg2NyA0My4wMDc4IDE1Ljg3MTEgNDIuODQzOCAxNS40Mzc1QzQyLjc5NjkgMTUuMzE2NCA0Mi42MjUgMTUuMjQyMiA0Mi41NjI1IDE1LjEyNUM0Mi43ODEyIDE0LjYxMzMgNDMuMDMxMiAxNC4xMjg5IDQzLjA5MzggMTMuNUM0My4xODM2IDEyLjU2NjQgNDMuMTA5NCAxMS41MTk1IDQyLjg0MzggMTAuNUM0Mi41NzgxIDkuNDgwNDcgNDIuMTE3MiA4LjQ2ODc1IDQxLjMxMjUgNy42ODc1QzQwLjY2NDEgNy4wNTQ2OSAzOS43NSA2LjY4MzU5IDM4LjcxODggNi41MzEyNUwzOC4zMTI1IDUuNTkzNzVDMzguMTUyMyA1LjIzNDM4IDM3Ljc5NjkgNS4wMDM5MSAzNy40MDYyIDVDMzYuMDIzNCA1IDM0LjU1MDggNS4xMzY3MiAzMy4xODc1IDUuNTYyNUMzMi44MzIgNC43NzM0NCAzMi4zNjMzIDQuMDIzNDQgMzEuNzE4OCAzLjQwNjI1QzMwLjg2MzMgMi41ODIwMyAyOS42NjAyIDIuMDg5ODQgMjguMjgxMiAxLjkzNzVMMjcuNzE4OCAwLjU5Mzc1QzI3LjU1ODYgMC4yMzQzNzUgMjcuMjAzMSAwLjAwMzkwNiAyNi44MTI1IDBaTTI2LjE1NjIgMi4wNjI1TDI2LjY4NzUgMy4yMTg3NUMyNi44NDc3IDMuNTc4MTIgMjcuMjAzMSAzLjgwODU5IDI3LjU5MzggMy44MTI1QzI4LjgzNTkgMy44MTI1IDI5LjY3OTcgNC4yMDcwMyAzMC4zNDM4IDQuODQzNzVDMzEuMDA3OCA1LjQ4MDQ3IDMxLjQ4MDUgNi4zODY3MiAzMS43NSA3LjQwNjI1QzMyLjAxOTUgOC40MjU3OCAzMi4wOTM4IDkuNTM5MDYgMzIgMTAuNDY4OEMzMS45MDYyIDExLjM5ODQgMzEuNTg5OCAxMi4xNDg0IDMxLjQwNjIgMTIuMzc1QzMxLjIxNDggMTIuNjE3MiAzMS4xNDg0IDEyLjkzMzYgMzEuMjE4OCAxMy4yMzA1QzMxLjI5MyAxMy41MzEyIDMxLjUgMTMuNzgxMiAzMS43ODEyIDEzLjkwNjJDMzEuNzY1NiAxMy44OTg0IDMxLjc4MTIgMTMuODk4NCAzMS44MTI1IDEzLjk2ODhDMzEuODY3MiAxNC4wOTc3IDMxLjkyNTggMTQuMzg2NyAzMS45MDYyIDE0Ljc1QzMxLjkwMjMgMTQuNzgxMiAzMS45MTAyIDE0Ljc4MTIgMzEuOTA2MiAxNC44MTI1QzMxLjc2OTUgMTUuNjQwNiAzMS41MzUyIDE2LjEzMjggMzEuMzc1IDE2LjM0MzhDMzEuMjkzIDE2LjQ1MzEgMzEuMjM0NCAxNi40ODgzIDMxLjIxODggMTYuNUMzMC43NDYxIDE2LjUzOTEgMzAuMzcxMSAxNi45MDYyIDMwLjMxMjUgMTcuMzc1QzMwLjIzMDUgMTguMTIxMSAyOS45NDE0IDE5LjA5MzggMjkuNTkzOCAxOS44NDM4QzI5LjQyMTkgMjAuMjE4OCAyOS4yMTQ4IDIwLjUzNTIgMjkuMDYyNSAyMC43NUMyOC45NDUzIDIwLjkxMDIgMjguODI4MSAyMSAyOC44NDM4IDIxQzI4LjUwNzggMjEuMTc1OCAyOC4zMDQ3IDIxLjUyNzMgMjguMzEyNSAyMS45MDYyQzI4LjMxMjUgMjMuMjA3IDI4LjMwNDcgMjQuMjUgMjguNDA2MiAyNS43ODEyQzI4LjQxNDEgMjUuODc4OSAyOC40MzM2IDI1Ljk3MjcgMjguNDY4OCAyNi4wNjI1QzI5LjAwMzkgMjcuNDY4OCAzMC4yMTA5IDI4LjMxNjQgMzEuNTMxMiAyOC45Njg4QzMyLjg1MTYgMjkuNjIxMSAzNC4zNDM4IDMwLjEwOTQgMzUuNzUgMzAuNzE4OEMzNy4xNTYyIDMxLjMyODEgMzguNDY0OCAzMi4wNjI1IDM5LjQwNjIgMzMuMDMxMkM0MC4xMzY3IDMzLjc4MTIgNDAuNTgyIDM0Ljc3MzQgNDAuODQzOCAzNkg5LjE1NjI1QzkuNDE3OTcgMzQuNzczNCA5Ljg2MzI4IDMzLjc4MTIgMTAuNTkzNyAzMy4wMzEyQzExLjUzNTIgMzIuMDYyNSAxMi44NDM3IDMxLjMyODEgMTQuMjUgMzAuNzE4OEMxNS42NTYyIDMwLjEwOTQgMTcuMTQ4NCAyOS42MjExIDE4LjQ2ODggMjguOTY4OEMxOS43ODkxIDI4LjMxNjQgMjAuOTk2MSAyNy40Njg4IDIxLjUzMTIgMjYuMDYyNUMyMS41NjY0IDI1Ljk3MjcgMjEuNTg1OSAyNS44Nzg5IDIxLjU5MzggMjUuNzgxMkMyMS42OTUzIDI0LjM0MzggMjEuNjg3NSAyMy4yMDcgMjEuNjg3NSAyMS45MDYyQzIxLjY5NTMgMjEuNTI3MyAyMS40OTIyIDIxLjE3NTggMjEuMTU2MiAyMUMyMS4xNTYyIDIxIDIxLjE0ODQgMjAuOTg4MyAyMS4xMjUgMjAuOTY4OEMyMS4xMTcyIDIwLjk2NDggMjEuMTA1NSAyMC45NzI3IDIxLjA5MzggMjAuOTY4OEMyMS4wNDY5IDIwLjkyOTcgMjAuOTgwNSAyMC44NDc3IDIwLjkwNjIgMjAuNzVDMjAuNzQ2MSAyMC41MzkxIDIwLjUyNzMgMjAuMjEwOSAyMC4zNDM4IDE5Ljg0MzhDMTkuOTc2NiAxOS4xMTMzIDE5LjY3NTggMTguMTg3NSAxOS41OTM4IDE3LjQwNjJDMTkuNTQ2OSAxNi45Njg4IDE5LjIxNDggMTYuNjEzMyAxOC43ODEyIDE2LjUzMTJDMTguNjgzNiAxNi41MTE3IDE4LjE3MTkgMTYuNTM1MiAxOCAxNC44MTI1QzE3LjkyOTcgMTQuMDQzIDE4LjI5MyAxMy44MTY0IDE4LjI1IDEzLjg0MzhDMTguNjY4IDEzLjU3ODEgMTguODI4MSAxMy4wNDY5IDE4LjYyNSAxMi41OTM4QzE3Ljk4NDQgMTEuMTIxMSAxNy43ODEyIDkuNjAxNTYgMTggOC4xODc1QzE4LjIyNjYgNy45MzM1OSAxOC4zMTI1IDcuNTc4MTIgMTguMjE4OCA3LjI1QzE4LjQwNjIgNi42Mjg5MSAxOC42NzE5IDYuMDQ2ODggMTkuMDMxMiA1LjVDMjAuMjc3MyAzLjYxMzI4IDIyLjYyMTEgMi4yMzA0NyAyNi4xNTYyIDIuMDYyNVpNMzYuNzgxMiA3LjA5Mzc1TDM3LjA5MzggNy43ODEyNUMzNy4yNDIyIDguMTUyMzQgMzcuNjAxNiA4LjM5ODQ0IDM4IDguNDA2MjVDMzguODkwNiA4LjQwNjI1IDM5LjQ0NTMgOC42NzU3OCAzOS45MDYyIDkuMTI1QzQwLjM2NzIgOS41NzQyMiA0MC43MDcgMTAuMjQyMiA0MC45MDYyIDExQzQxLjEwNTUgMTEuNzU3OCA0MS4xNjAyIDEyLjU4MiA0MS4wOTM4IDEzLjI4MTJDNDEuMDI3MyAxMy45ODA1IDQwLjc4OTEgMTQuNTUwOCA0MC42ODc1IDE0LjY4NzVDNDAuNTExNyAxNC45MTQxIDQwLjQ0NTMgMTUuMjAzMSA0MC41IDE1LjQ4NDRDNDAuNTUwOCAxNS43NjU2IDQwLjcyMjcgMTYuMDExNyA0MC45Njg4IDE2LjE1NjJDNDEuMDAzOSAxNi4yNDYxIDQxLjAzMTIgMTYuNDQxNCA0MSAxNi42ODc1QzQwLjkxNDEgMTcuMzc1IDQwLjc2MTcgMTcuNzEwOSA0MC42ODc1IDE3LjgxMjVDNDAuMjE4OCAxNy44NzExIDM5Ljg1MTYgMTguMjQ2MSAzOS44MTI1IDE4LjcxODhDMzkuNzc3MyAxOS4yMzQ0IDM5LjUzOTEgMTkuOTUzMSAzOS4yODEyIDIwLjVDMzkuMTUyMyAyMC43NzM0IDM5LjAxOTUgMjAuOTkyMiAzOC45MDYyIDIxLjE1NjJDMzguODIwMyAyMS4yNzczIDM4Ljc0MjIgMjEuMzcxMSAzOC43NSAyMS4zNzVDMzguNDgwNSAyMS41NTg2IDM4LjMxNjQgMjEuODYzMyAzOC4zMTI1IDIyLjE4NzVDMzguMzEyNSAyMy4yODkxIDM4LjMwMDggMjQuMTM2NyAzOC40MDYyIDI1LjI4MTJDMzguNDE4IDI1LjM2NzIgMzguNDM3NSAyNS40NDkyIDM4LjQ2ODggMjUuNTMxMkMzOC44OTQ1IDI2LjcwNyAzOS44NTU1IDI3LjQ0MTQgNDAuODc1IDI3Ljk2ODhDNDEuODk0NSAyOC40OTYxIDQzLjA0MyAyOC44NzExIDQ0LjA5MzggMjkuMzQzOEM0NS4xNDQ1IDI5LjgxNjQgNDYuMDk3NyAzMC4zNzUgNDYuNzgxMiAzMS4wOTM4QzQ3LjI1NzggMzEuNTkzOCA0Ny41NzQyIDMyLjIyNjYgNDcuNzgxMiAzM0g0MkM0MS45Njg4IDMzIDQxLjkzNzUgMzMgNDEuOTA2MiAzM0M0MS41OTM4IDMyLjQ4ODMgNDEuMjQyMiAzMi4wMzUyIDQwLjg0MzggMzEuNjI1QzM5LjYwOTQgMzAuMzU1NSAzOC4wNzAzIDI5LjU1ODYgMzYuNTYyNSAyOC45MDYyQzM1LjA1NDcgMjguMjUzOSAzMy41NzAzIDI3Ljc1IDMyLjQzNzUgMjcuMTg3NUMzMS4zNDM4IDI2LjY0NDUgMzAuNjkxNCAyNi4wNjY0IDMwLjQwNjIgMjUuNDA2MkMzMC4zMzIgMjQuMjA3IDMwLjMxMjUgMjMuMzA4NiAzMC4zMTI1IDIyLjI1QzMwLjQxOCAyMi4xMjg5IDMwLjU4OTggMjIuMDM5MSAzMC42ODc1IDIxLjkwNjJDMzAuOTQxNCAyMS41NTA4IDMxLjE5MTQgMjEuMTUyMyAzMS40MDYyIDIwLjY4NzVDMzEuNzgxMiAxOS44NzUgMzIuMDAzOSAxOC45Mjk3IDMyLjE1NjIgMThDMzIuNDI5NyAxNy44MzU5IDMyLjc1NzggMTcuODQzOCAzMi45Njg4IDE3LjU2MjVDMzMuNDA2MiAxNi45ODA1IDMzLjcwNyAxNi4xNzU4IDMzLjg3NSAxNS4wNjI1QzMzLjg4NjcgMTUuMDQzIDMzLjg5ODQgMTUuMDE5NSAzMy45MDYyIDE1QzMzLjk2ODggMTQuMzEyNSAzMy44NzExIDEzLjY5OTIgMzMuNjU2MiAxMy4xODc1QzMzLjYwMTYgMTMuMDU4NiAzMy40MTggMTMuMDI3MyAzMy4zNDM4IDEyLjkwNjJDMzMuNjY4IDEyLjI1IDMzLjg4MjggMTEuNTExNyAzMy45Njg4IDEwLjY1NjJDMzQuMDcwMyA5LjY1NjI1IDM0LjAzNTIgOC41NjY0MSAzMy44MTI1IDcuNDY4NzVDMzQuNzEwOSA3LjIyMjY2IDM1Ljc2NTYgNy4xMzI4MSAzNi43ODEyIDcuMDkzNzVaTTE0Ljg0MzcgNy4xMjVMMTUuMjE4NyA3Ljg0Mzc1QzE1LjM1OTQgOC4xNDQ1MyAxNS42NDA2IDguMzU1NDcgMTUuOTY4NyA4LjQwNjI1QzE1LjgzNTkgOS44NTkzOCAxNi4wNjI1IDExLjM2NzIgMTYuNTkzOCAxMi44MTI1QzE2LjIxNDggMTMuMzMyIDE1LjkxMDIgMTQuMDI3MyAxNiAxNUMxNi4xNzU4IDE2Ljc0NjEgMTYuOTU3IDE3LjU3NDIgMTcuNzE4OCAxOC4wMzEyQzE3Ljg3ODkgMTguOTg4MyAxOC4xNjggMTkuOTU3IDE4LjU2MjUgMjAuNzVDMTguNzkzIDIxLjIxMDkgMTkuMDQ2OSAyMS42MjExIDE5LjMxMjUgMjEuOTY4OEMxOS40MTAyIDIyLjA5NzcgMTkuNTgyIDIyLjE2OCAxOS42ODc1IDIyLjI4MTJDMTkuNjg3NSAyMy4zMzk4IDE5LjY2OCAyNC4yODkxIDE5LjU5MzggMjUuNDA2MkMxOS4zMDg2IDI2LjA2NjQgMTguNjU2MiAyNi42NDQ1IDE3LjU2MjUgMjcuMTg3NUMxNi40Mjk3IDI3Ljc1IDE0Ljk0NTMgMjguMjUzOSAxMy40Mzc1IDI4LjkwNjJDMTEuOTI5NyAyOS41NTg2IDEwLjM5MDYgMzAuMzU1NSA5LjE1NjI1IDMxLjYyNUM4LjczNDM3IDMyLjA1ODYgOC4zNTU0NyAzMi41NDMgOC4wMzEyNSAzMy4wOTM4QzguMDE5NTMgMzMuMDkzOCA4LjAxMTcyIDMzLjA5MzggOCAzMy4wOTM4SDIuMjVDMi40NjA5NCAzMi4zMjAzIDIuNzY5NTMgMzEuNjg3NSAzLjI1IDMxLjE4NzVDMy45NDE0MSAzMC40Njg4IDQuOTA2MjUgMjkuOTEwMiA1Ljk2ODc1IDI5LjQzNzVDNy4wMzEyNSAyOC45NjQ4IDguMTYwMTYgMjguNTg5OCA5LjE4NzUgMjguMDYyNUMxMC4yMTQ4IDI3LjUzNTIgMTEuMTk1MyAyNi44MzU5IDExLjYyNSAyNS42NTYyQzExLjY2MDIgMjUuNTY2NCAxMS42Nzk3IDI1LjQ3MjcgMTEuNjg3NSAyNS4zNzVDMTEuNzg5MSAyNC4xMzY3IDExLjgxMjUgMjMuMzEyNSAxMS44MTI1IDIyLjMxMjVDMTEuODIwMyAyMS45NTcgMTEuNjQ0NSAyMS42MjUgMTEuMzQzNyAyMS40Mzc1QzExLjMxMjUgMjEuNDAyMyAxMS4yNDYxIDIxLjMzMiAxMS4xODc1IDIxLjI1QzExLjA3MDMgMjEuMDgyIDEwLjkxOCAyMC44NDc3IDEwLjc4MTIgMjAuNTYyNUMxMC41MDc4IDE5Ljk5NjEgMTAuMjY5NSAxOS4yNjE3IDEwLjE4NzUgMTguNjU2MkMxMC4xMjExIDE4LjIxMDkgOS43NjE3MiAxNy44NjMzIDkuMzEyNSAxNy44MTI1QzkuMjM4MjggMTcuNzEwOSA5LjA4NTk0IDE3LjM3NSA5IDE2LjY4NzVDOC45Njg3NSAxNi40MDIzIDkuMDIzNDQgMTYuMjM4MyA5LjA2MjUgMTYuMTU2MkM5LjQ2ODc1IDE1Ljg3ODkgOS42MTMyOCAxNS4zNTE2IDkuNDA2MjUgMTQuOTA2MkM4LjU3ODEyIDEzLjAzMTIgOC43MjI2NiAxMS4wNzgxIDkuNjg3NSA5LjU5Mzc1QzEwLjU3NDIgOC4yMjY1NiAxMi4yOTY5IDcuMjgxMjUgMTQuODQzNyA3LjEyNVoiIGZpbGw9IiNBQjMyMjYiLz4KPC9zdmc+Cg==);
    }
    &--2 {
      background-image: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNDgiIGhlaWdodD0iNDgiIHZpZXdCb3g9IjAgMCA0OCA0OCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggZD0iTTIwLjM0MzggMEMxNi40Mzc1IDAgMTMuOTA2MiAxLjA2NjQxIDEyLjI4MTIgMi42ODc1QzEwLjY1NjIgNC4zMDg1OSA5Ljk3MjY2IDYuMzM1OTQgOS4zNzUgOC4xMjVDOC4zMzIwMyAxMS4yNDYxIDAuODEyNSAzMy4zNDM4IDAuODEyNSAzMy4zNDM4QzAuNzc3MzQ0IDMzLjQzMzYgMC43NTc4MTMgMzMuNTI3MyAwLjc1IDMzLjYyNUMwLjc1IDMzLjYzNjcgMC43NSAzMy42NDQ1IDAuNzUgMzMuNjU2MkMwLjI3NzM0NCAzNC43MDcgMCAzNS45NDE0IDAgMzcuMzc1QzAgMzkuNzE4OCAwLjg2MzI4MSA0Mi4xMjg5IDIuNjg3NSA0My45Njg4QzQuNTExNzIgNDUuODA4NiA3LjI5Mjk3IDQ3LjAzMTIgMTAuOTY4OCA0Ny4wMzEyQzEzLjk1MzEgNDcuMDMxMiAxNi4yMjY2IDQ2LjE5NTMgMTcuNzUgNDQuODc1QzE5LjI3MzQgNDMuNTU0NyAyMCA0MS43NSAyMCA0MEMyMCAzNy44MDA4IDE4Ljc4NTIgMzUuOTkyMiAxNy4wOTM4IDM0LjgxMjVDMTUuNDAyMyAzMy42MzI4IDEzLjIyNjYgMzMgMTEgMzNDOS41MjczNCAzMyA4LjEwNTQ3IDMzLjMxMjUgNi45Njg3NSAzNC4wMzEyQzUuODMyMDMgMzQuNzUgNSAzNS45NzI3IDUgMzcuNDY4OEM1IDM4LjQxOCA1LjI4NTE2IDM5LjI4OTEgNS44MTI1IDM5LjkzNzVDNi4zMzk4NCA0MC41ODU5IDcuMDc0MjIgNDEuMDE5NSA3Ljg0Mzc1IDQxLjMxMjVDOS4zODI4MSA0MS45MDIzIDExLjIwNyA0MiAxMyA0MkMxMy4zNTk0IDQyLjAwMzkgMTMuNjk1MyA0MS44MTY0IDEzLjg3ODkgNDEuNTAzOUMxNC4wNTg2IDQxLjE5MTQgMTQuMDU4NiA0MC44MDg2IDEzLjg3ODkgNDAuNDk2MUMxMy42OTUzIDQwLjE4MzYgMTMuMzU5NCAzOS45OTYxIDEzIDQwQzExLjMwNDcgNDAgOS42NTIzNCAzOS44NTU1IDguNTYyNSAzOS40Mzc1QzguMDE5NTMgMzkuMjMwNSA3LjYxNzE5IDM4Ljk1MzEgNy4zNzUgMzguNjU2MkM3LjEzMjgxIDM4LjM1OTQgNyAzOC4wMjczIDcgMzcuNDY4OEM3IDM2LjY0NDUgNy4zMzIwMyAzNi4xNjAyIDguMDMxMjUgMzUuNzE4OEM4LjczMDQ3IDM1LjI3NzMgOS44MjAzMSAzNSAxMSAzNUMxMi44NDc3IDM1IDE0LjY3OTcgMzUuNTM5MSAxNS45Njg4IDM2LjQzNzVDMTcuMjU3OCAzNy4zMzU5IDE4IDM4LjUxMTcgMTggNDBDMTggNDEuMTk5MiAxNy41MzEyIDQyLjM5NDUgMTYuNDM3NSA0My4zNDM4QzE1LjM0MzggNDQuMjkzIDEzLjU4NTkgNDUuMDMxMiAxMC45Njg4IDQ1LjAzMTJDNy43MjI2NiA0NS4wMzEyIDUuNTE1NjIgNDMuOTk2MSA0LjA5Mzc1IDQyLjU2MjVDMi42NzE4OCA0MS4xMjg5IDIgMzkuMjM4MyAyIDM3LjM3NUMyIDMzLjU3NDIgNC4wOTc2NiAzMS45MTggNi4zNzUgMzAuOTY4OEM4LjQzMzU5IDMwLjEwOTQgMTAuNDU3IDMwLjAxMTcgMTAuODQzOCAzMEMxMC44OTQ1IDMwLjAwMzkgMTAuOTQ5MiAzMC4wMDM5IDExIDMwQzExLjAzMTIgMzAgMTEuMDYyNSAzMCAxMS4wOTM4IDMwQzE1Ljc3NzMgMzAuMDE1NiAxOC4yMDMxIDMxLjAyMzQgMTkuNzE4OCAzMi40MDYyQzIxLjI0MjIgMzMuNzk2OSAyMS45Mzc1IDM1LjcxNDggMjIuODQzOCAzNy44NzVDMjMuNzUgNDAuMDM1MiAyNC45MTggNDIuNDA2MiAyNy40Njg4IDQ0LjE1NjJDMzAuMDE5NSA0NS45MDYyIDMzLjgzNTkgNDcgNDAgNDdDNDAuNDg4MyA0Ny4wMDc4IDQwLjkxMDIgNDYuNjY0MSA0MSA0Ni4xODc1TDQ3LjA5MzggMTEuODQzOEM0Ny4xNDA2IDExLjU1ODYgNDcuMDU4NiAxMS4yNjU2IDQ2Ljg3MTEgMTEuMDQ2OUM0Ni42ODc1IDEwLjgyNDIgNDYuNDE0MSAxMC42OTE0IDQ2LjEyNSAxMC42ODc1QzQxLjM1OTQgMTAuNjg3NSAzOC4zMzIgMTAuMDE5NSAzNi4yNSA5LjA5Mzc1QzM0LjE2OCA4LjE2Nzk3IDMyLjk4ODMgNi45ODQzOCAzMS44NzUgNS42ODc1QzMwLjc2MTcgNC4zOTA2MiAyOS43MjY2IDIuOTYwOTQgMjggMS44NDM3NUMyNi4yNzM0IDAuNzI2NTYzIDIzLjkyMTkgMCAyMC4zNDM4IDBaTTIwLjM0MzggMkMyMy42NjQxIDIgMjUuNTQzIDIuNjE3MTkgMjYuOTA2MiAzLjVDMjguMjY5NSA0LjM4MjgxIDI5LjE5NTMgNS42Mjg5MSAzMC4zNzUgN0MzMS41NTQ3IDguMzcxMDkgMzMuMDE5NSA5LjgzMjAzIDM1LjQzNzUgMTAuOTA2MkMzNy42Mjg5IDExLjg3ODkgNDAuNzIyNyAxMi40ODA1IDQ0LjkzNzUgMTIuNTkzOEwzOS4xNTYyIDQ0LjkwNjJDMzMuODU1NSA0NC43OTMgMzAuNTY2NCA0My44ODI4IDI4LjU5MzggNDIuNTMxMkMyNi40OTYxIDQxLjA5MzggMjUuNTYyNSAzOS4yMTQ4IDI0LjY4NzUgMzcuMTI1QzIzLjgxMjUgMzUuMDM1MiAyMy4wMzEyIDMyLjcwMzEgMjEuMDYyNSAzMC45MDYyQzE5LjExNzIgMjkuMTMyOCAxNi4xMDk0IDI4LjAyNzMgMTEuMTg3NSAyOEMxMS4xNzU4IDI4IDExLjE2OCAyOCAxMS4xNTYyIDI4QzExLjEyNSAyOCAxMS4wOTM4IDI4IDExLjA2MjUgMjhDMTEuMDQzIDI4IDExLjAxOTUgMjggMTEgMjhDMTAuOTU3IDI3Ljk5NjEgMTAuOTE4IDI3Ljk5NjEgMTAuODc1IDI4QzEwLjg0NzcgMjggMTAuNzgxMiAyOC4wMzEyIDEwLjcxODggMjguMDMxMkMxMC4wODk4IDI4LjA1MDggNy45MzM1OSAyOC4xNjAyIDUuNjI1IDI5LjEyNUM1LjExNzE5IDI5LjMzNTkgNC41OTc2NiAyOS42MjExIDQuMDkzNzUgMjkuOTM3NUM1LjgxMjUgMjQuODk4NCAxMC4zOTA2IDExLjQ0OTIgMTEuMjgxMiA4Ljc4MTI1QzExLjg3NSA3IDEyLjQ3MjcgNS4zMDg1OSAxMy42ODc1IDQuMDkzNzVDMTQuOTAyMyAyLjg3ODkxIDE2Ljc4NTIgMiAyMC4zNDM4IDJaIiBmaWxsPSIjQUIzMjI2Ii8+Cjwvc3ZnPgo=);
    }
    &--3 {
      background-image: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNTAiIGhlaWdodD0iMzciIHZpZXdCb3g9IjAgMCA1MCAzNyIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggZD0iTTIuODAwNzggMEMxLjI2NTYyIDAgMCAxLjI2NTYzIDAgMi44MDA3OFYyOUMwIDMwLjY0NDUgMS4zNTU0NyAzMiAzIDMySDcuMDkzNzVDNy41NzAzMSAzNC44MjgxIDEwLjAzOTEgMzcgMTMgMzdDMTUuOTYwOSAzNyAxOC40Mjk3IDM0LjgyODEgMTguOTA2MiAzMkgzNC4wOTM4QzM0LjU3MDMgMzQuODI4MSAzNy4wMzkxIDM3IDQwIDM3QzQyLjk2MDkgMzcgNDUuNDI5NyAzNC44MjgxIDQ1LjkwNjIgMzJINDdDNDcuODMyIDMyIDQ4LjU1MDggMzEuNjEzMyA0OS4wODIgMzEuMDgyQzQ5LjYxMzMgMzAuNTUwOCA1MCAyOS44MzIgNTAgMjlWMTkuNDAyM0M1MCAxOC4yNzczIDQ5LjU4MiAxNy4yNTM5IDQ5LjE5OTIgMTYuNDY4OEM0OC44MTI1IDE1LjY4NzUgNDguNDIxOSAxNS4xMjUgNDguNDIxOSAxNS4xMjVMNDguNDEwMiAxNS4xMTMzTDQ0LjI5MyA5LjU4OTg0TDQ0LjI4MTIgOS41NzgxMkM0My4zOTQ1IDguNDY4NzUgNDEuOTcyNyA3IDQwIDdIMzJDMzEuNjQwNiA3IDMxLjMwODYgNy4wODIwMyAzMSA3LjIwNzAzVjIuOTAyMzRDMzEgMS4zMDA3OCAyOS42OTkyIDAgMjguMDk3NyAwSDIuODAwNzhaTTIuODAwNzggMkgyOC4wOTc3QzI4LjUgMiAyOSAyLjUgMjkgMi45MDIzNFYzMEgxOC45MDYyQzE4LjQyOTcgMjcuMTcxOSAxNS45NjA5IDI1IDEzIDI1QzEwLjAzOTEgMjUgNy41NzAzMSAyNy4xNzE5IDcuMDkzNzUgMzBIM0MyLjQ0NTMxIDMwIDIgMjkuNTU0NyAyIDI5VjIuODAwNzhDMiAyLjMzNTk0IDIuMzM1OTQgMiAyLjgwMDc4IDJaTTE1IDRDOS41IDQgNSA4LjUgNSAxNEM1IDE5LjUgOS41IDI0IDE1IDI0QzIwLjUgMjQgMjUgMTkuNSAyNSAxNEMyNSA4LjUgMjAuNSA0IDE1IDRaTTE1IDZDMTkuMzk4NCA2IDIzIDkuNjAxNTYgMjMgMTRDMjMgMTguMzk4NCAxOS4zOTg0IDIyIDE1IDIyQzEwLjYwMTYgMjIgNyAxOC4zOTg0IDcgMTRDNyA5LjYwMTU2IDEwLjYwMTYgNiAxNSA2Wk0xNCA4VjEzLjVMMTAuNDAyMyAxNi4xOTkyTDExLjU5NzcgMTcuODAwOEwxNiAxNC41VjhIMTRaTTMyIDlIMzZWMThDMzYgMTguODMyIDM2LjM4NjcgMTkuNTUwOCAzNi45MTggMjAuMDgyQzM3LjQ0OTIgMjAuNjEzMyAzOC4xNjggMjEgMzkgMjFINDhWMjlDNDggMjkuMTY4IDQ3Ljg4NjcgMjkuNDQ5MiA0Ny42NjggMjkuNjY4QzQ3LjQ0OTIgMjkuODg2NyA0Ny4xNjggMzAgNDcgMzBINDUuOTA2MkM0NS40Mjk3IDI3LjE3MTkgNDIuOTYwOSAyNSA0MCAyNUMzNy4wMzkxIDI1IDM0LjU3MDMgMjcuMTcxOSAzNC4wOTM4IDMwSDMxVjEwQzMxIDkuODMyMDMgMzEuMTEzMyA5LjU1MDc4IDMxLjMzMiA5LjMzMjAzQzMxLjU1MDggOS4xMTMyOCAzMS44MzIgOSAzMiA5Wk0zOCA5SDQwQzQwLjgyODEgOSA0Mi4wMDM5IDkuOTMzNTkgNDIuNzE4OCAxMC44MjQyTDQ2Ljc4MTIgMTYuMjczNEM0Ni43ODEyIDE2LjI3MzQgNDcuMDg1OSAxNi43MTA5IDQ3LjQwMjMgMTcuMzU1NUM0Ny42NTYyIDE3Ljg3MTEgNDcuODAwOCAxOC40NzI3IDQ3Ljg4MjggMTlIMzlDMzguODMyIDE5IDM4LjU1MDggMTguODg2NyAzOC4zMzIgMTguNjY4QzM4LjExMzMgMTguNDQ5MiAzOCAxOC4xNjggMzggMThWOVpNMTMgMjdDMTUuMjIyNyAyNyAxNyAyOC43NzczIDE3IDMxQzE3IDMzLjIyMjcgMTUuMjIyNyAzNSAxMyAzNUMxMC43NzczIDM1IDkgMzMuMjIyNyA5IDMxQzkgMjguNzc3MyAxMC43NzczIDI3IDEzIDI3Wk00MCAyN0M0Mi4yMjI3IDI3IDQ0IDI4Ljc3NzMgNDQgMzFDNDQgMzMuMjIyNyA0Mi4yMjI3IDM1IDQwIDM1QzM3Ljc3NzMgMzUgMzYgMzMuMjIyNyAzNiAzMUMzNiAyOC43NzczIDM3Ljc3NzMgMjcgNDAgMjdaIiBmaWxsPSIjQUIzMjI2Ii8+Cjwvc3ZnPgo=);
    }
    &--4 {
      background-image: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjgiIGhlaWdodD0iNDIiIHZpZXdCb3g9IjAgMCAyOCA0MiIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggZD0iTTAuODEyNTA4IDBDMC4zMzU5NDYgMC4wODk4NDQgLTAuMDA3ODAzNTggMC41MTE3MTkgOC40MjMxMWUtMDYgMVY0MUM4LjQyMzExZS0wNiA0MS41NTA4IDAuNDQ5MjI3IDQyIDEuMDAwMDEgNDJIMjdDMjcuNTUwOCA0MiAyOCA0MS41NTA4IDI4IDQxVjFDMjggMC40NDkyMTkgMjcuNTUwOCAwIDI3IDBIMS4wMDAwMUMwLjk2ODc1OCAwIDAuOTM3NTA4IDAgMC45MDYyNTggMEMwLjg3NTAwOCAwIDAuODQzNzU4IDAgMC44MTI1MDggMFpNMi4wMDAwMSAySDI2VjQwSDIuMDAwMDFWMlpNMjEuMTg3NSA1TDE2LjI4MTMgOS41MzEyNUwxNy43NSAxMC4xODc1TDguNDA2MjYgMzAuOTY4OEw2LjkzNzUxIDMwLjMxMjVMNi44MTI1MSAzN0wxMS43MTg4IDMyLjQ2ODhMMTAuMjUgMzEuODEyNUwxOS41OTM4IDExLjAzMTJMMjEuMDYyNSAxMS42ODc1TDIxLjE4NzUgNVoiIGZpbGw9IiNBQjMyMjYiLz4KPC9zdmc+Cg==);
    }
  }
  &__itemTitle {
    font-size: 15px;
    font-weight: 600;
    max-width: 210px;
    margin-bottom: 20px;
    &--4 {
      max-width: 270px;
    }
  }
}

@media (max-width: 768px) {
  .about {
    &__title {
      font-size: 26px;
      margin-bottom: 20px;
    }
  }
  .aboutBlock {
    margin-top: 20px;
    &__item {
      height: 200px;
    }
  }
}
</style>
