<template lang="pug">
.home
  div (v-for="task in tasks" :key="task.id")
    h4
      router-link(:to="`/task/${task.id}`") {{ task.name }}
  div (v-if="tasks.length===0") Задач не найдено
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { mapGetters } from 'vuex';
import { Task } from '@/types/storeType';

export default defineComponent({
  name: 'HomeView',
  data: () => {
    return {
      tasks:[] as Task [],
    }
  },
  components: {
  },
  methods:{
    ...mapGetters(['getAllTasks']),
  },
  mounted(){
    this.tasks=this.getAllTasks();
  }
});
</script>
