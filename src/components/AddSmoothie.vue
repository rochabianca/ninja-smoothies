<template>
  <div class="add-smoothie container">
    <h2 class="center-align indigo-text">Add Smoothie</h2>
    <form @submit.prevent="AddSmoothie">
      <div class="field title">
        <label for="title">Smoothie Title</label>
        <input type="text" name="title" v-model="title">
      </div>

      <div v-for="(ingredient, index) in ingredients" :key="index">
        <label for="ingredient">Ingredient</label>
        <input type="text" name="ingredient" v-model="ingredients[index]">
      </div>

      <div class="field add-ingredient">
        <label for="add-ingredient">Add an Ingredient</label>
        <input
          type="text"
          name="add-ingredient"
          @keydown.tab.prevent="addIngredient"
          v-model="another"
        >
      </div>

      <div class="field center-align">
        <p v-if="feedback" class="red-text">{{feedback}}</p>
        <button class="btn pink">Add Smoothie</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "AddSmoothie",
  data() {
    return {
      title: null,
      another: null,
      ingredients: [],
      feedback: null
    };
  },
  methods: {
    AddSmoothie() {
      console.log(this.title, this.ingredients);
    },
    addIngredient() {
      if (this.another) {
        this.ingredients.push(this.another);
        console.log(this.ingredients);
        this.another = null;
        this.feedback = null;
      } else {
        this.feedback = "You must enter a value to add a ingredient";
      }
    }
  }
};
</script>

<style lang='scss'>
.add-smoothie {
  margin-top: 60px;
  padding: 20px;
  max-width: 500px;

  h2 {
    font-size: 2em;
    margin: 20px auto;
  }
  .field {
    margin: 20px auto;
  }
}
</style>
