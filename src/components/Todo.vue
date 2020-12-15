<template>
  <div class="todo">
    <h1>VUEDO LIST</h1>
    <div class="goals-box">
      <h2>My goals</h2>
      <label>
        <input type="text" v-model="enteredGoalValue">
      </label>
      <button @click="addGoal" @keyup.enter="addGoal">Add Goal</button>

      <div class="goals-container">
        <div v-if="goals.length !== 0" class="single-goal">
          <h3 v-for="(goal, index) in goals" :key="goal">
            {{ index + 1 }}. {{ goal }}
            <span @click="deleteGoal(index)">x</span>
          </h3>
        </div>
        <p v-else>No task added yet</p>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: "Todo",
  data() {
    return {
      enteredGoalValue: '',
      goals: []
    }
  },
  methods: {
    addGoal() {
      this.goals.push(this.enteredGoalValue)
      this.enteredGoalValue = ''
    },
    deleteGoal(index) {
      this.goals.splice(index, 1)
    }
  }
}
</script>

<style scoped>
.goals-box {
  width: 600px;
  margin: 0 auto;
  border: 1px solid #2c3e50;
  border-radius: 10px;
}

input {
  padding: 5px;
  border: 1px solid #42b983;
}

button {
  padding: 5px 15px;
  background-color: #42b983;
  border: 1px solid #42b983;
  color: white;
}

.goals-container {
  margin: 10px 0;
}

h3 {
  background-color: #deeee6;
  margin: 2px 0;
  padding: 5px;
  position: relative;
}

span {
  position: absolute;
  right: 5px;
  top: 5px;
  font-size: 10px;
  color: crimson;
  cursor: pointer;
}
</style>
