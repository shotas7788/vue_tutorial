<template>
  <div class="cardsFolder">
    <h1 id="page-title">{{ pageTitle }}</h1>
    <div
      class="card"
      v-for="card in cards"
      :key="card.displayOrder"
    >

    <div class="card__title">{{ card.title }}</div>
    <div class="card__body" v-html="card.body"></div>
    <div class="card__expand-fake-button"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardsFolder',
  props: [ 'cardsFolder' ],
  computed: {
    routeName(){
      return this.$route.name
    },
    pageTitle(){
      if (!this.cardsFolder){
        return null
      }

      switch (this.routeName) {
        case 'AboutMe':
        return this.cardsFolder.personal.cardsData
        case 'Quitting':
        return this.cardsFolder.quitting.cardsData
        case 'Desire':
        return this.cardsFolder.desire.cardsData
      }
    }
  }
}
</script>
