<template>
  <div id="app">

    <h1>Would You Rather?</h1>

    <would-you-rather-question v-for="question in questions"
    v-bind:question="question"
    v-bind:key="question.id"
    v-on:answer-changed="answerChanged"></would-you-rather-question>

    <h1>You Would Rather..</h1>
    <p v-if="answers.length===0">...? Try making a selection above</p>
    <ul>
      <li v-for="answer in answers">{{ answer }}</li>
    </ul>
    
  </div>
</template>

<script>
import WouldYouRatherQuestion from './components/WouldYouRatherQuestion.vue'

export default {
  name: 'App',
  components: {
    WouldYouRatherQuestion
  }, 
  data (){
    return {
      questions: [
        {
          id: 0,
          question: 'Would you rather have all traffic lights you approach be green or never have to stand in line again?',
          answer1: 'Have all traffic lights I approach be green', 
          answer2: 'Never have to stand in line again',      
        }, 
        {
          id: 1,
          question: 'Would you rather be a famous inventor or a famous writer?',
          answer1: 'Be a famous inventor', 
          answer2: 'Be a famous writer',
        }, 
        {
          id: 2,
          question: 'Would you rather be incredibly funny or incredibly smart?',
          answer1: 'Be incredibly funny', 
          answer2: 'Be incredibly smart',
        }
      ], 
      answers: []
    }
  }, 
  methods: {
    // child component will pass back what answer was choses and the id of the question
    // question id used to arrange answers in the same order as the questions
    answerChanged(choice, id){
      this.answers[id] = `${choice}`
    }
  }
}
</script>

<style>

body {
  background: lightsteelblue
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: lightyellow
}

li {
  list-style-type: none;
  font-size: large;
}

h1 {
  font-family:Cambria, Cochin, Georgia, Times, 'Times New Roman', serif
}
</style>
