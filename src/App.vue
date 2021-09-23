<template>
  <div id="app">
   
  </div>
</template>

<script>
import * as toxicity from '@tensorflow-models/toxicity';

export default {
  name: 'App',
  components: {
  },
  mounted(){
    // The minimum prediction confidence.
    const threshold = 0.8;
    const labelsToLoad = ["insult", "toxicity"]
    // Load the model. Users optionally pass in a threshold and an array of
    // labels to include.
    toxicity.load(threshold, labelsToLoad).then(model => {
      const sentences = ["this is not good of you. I expected better. you acted wrong"];
    
      model.classify(sentences).then(predictions => {
        console.log(predictions);
      });
    }).catch(err => {
      console.log("an arror occured")
      console.log(err)
    })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
