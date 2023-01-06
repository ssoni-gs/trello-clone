<template>
  <div class="board">
    <div class="flex flex-row items-start">
      <div class="column" v-for="(column, index) of board.columns" :key="index">
        <div class="flex flex-center font-bold mb-2">
          {{ column.name }}
        </div>
        <div class="task" v-for="(task, taskIndex) of column.tasks" :key="taskIndex">
          <span class="w-full font-bold">
            {{ task.name }}
          </span>
          <p class="text-sm mt-1">{{ task.description }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex';
export default {

  computed: {
    ...mapState(['board'])
  }
}
</script>

<style lang="css">
.task {
  @apply flex items-center flex-wrap shadow mb-2 py-2 px-2 rounded bg-white text-grey-darkest no-underline;
}

.column {
  @apply bg-grey-light p-2 mr-4 text-left shadow rounded;
  min-width: 350px;
}

.board {
  @apply p-4 bg-blue-dark h-full overflow-auto;
}

.task-bg {
  @apply pin absolute;
  background: rgba(0, 0, 0, 0.5);
}
</style>