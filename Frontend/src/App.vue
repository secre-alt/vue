<script lang="ts" setup>
import { ref } from 'vue';

const message = ref('Task');
const newTask = ref('');
const tasks = ref<string[]>([]); // Store the list of tasks

function formSubmitted() {
  if (newTask.value.trim() !== '') {
    tasks.value.push(newTask.value.trim());
    newTask.value = ''; // Clear input
  }
}
</script>

<template>
  <main>
    <h1>{{ message }}</h1>

    <!-- Task Form -->
    <form @submit.prevent="formSubmitted">
      <label>
        New Task
        <input v-model="newTask" name="newTask" placeholder="Enter task" />
      </label>
      <div class="button-container">
        <button type="submit">Add</button>
      </div>
    </form>

    <!-- Task List -->
    <ul class="task-list">
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
      </li>
    </ul>
  </main>
</template>

<style scoped>
main {
  max-width: 400px;
  margin: 2rem auto;
  padding: 1.5rem;
  background-color: #ffffff; /* White card background */
  border-radius: 10px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.2);
  color: #222; /* Darker text color */
  
}

h1 {
  font-size: 1.8rem;
  margin-bottom: 1rem;
  color: #222;
}

label {
  display: block;
  margin-bottom: 0.5rem;
  color: #333;
}

input {
  padding: 0.5rem;
  width: 100%;
  margin-top: 0.25rem;
  border: 1px solid #ccc;
  border-radius: 6px;
  background-color: #f5f5f5;
  color: #000; /* Ensure input text is visible */
}

.button-container {
  display: flex;
  justify-content: flex-end;
  margin-top: 0.5rem;
}

button {
  padding: 0.5rem 1.5rem;
  background-color: #3b82f6;
  color: white;
  font-weight: bold;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

button:hover {
  background-color: #2563eb;
}

.task-list {
  list-style-type: disc;
  margin-top: 1.5rem;
  padding-left: 1.5rem;
}

.task-list li {
  margin-bottom: 0.5rem;
  color: #222; /* Darker task text */
}
</style>
