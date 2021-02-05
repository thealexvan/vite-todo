<template>
  <section class="space-y-4" v-if="todos.length > 0">
    <h3
      class="text-3xl font-bold"
      :class="color === 'red' ? 'text-blue-800' : 'text-red-800'"
    >
      {{ title }}: {{ todos.length }}
    </h3>
    <ul class="space-y-4">
      <li
        v-for="todo in todos"
        :key="todo.id"
        class="bg-white square-xl text-2xl py-2 px-4 font-light text-center hover:text-white cursor-pointer transition-colors"
        :class="
          color === 'green'
            ? 'text-black-800 hover:bg-red-800'
            : 'text-black-800 hover:bg-blue-800 '
        "
        @click="changeStatus(todo.id)"
      >
        {{ todo.text }}
      </li>
    </ul>
  </section>
</template>

<script setup>
import { defineProps } from 'vue'
import { changeStatus } from '../helpers/useTodos'

defineProps({
  color: {
    type: String,
    default: 'green',
  },
  title: {
    type: String,
    default: 'Todo List',
  },
  todos: {
    type: Array,
    default: [],
  },
})
</script>
