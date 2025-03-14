<template>
  <section class="flex flex-col mt-5">

  <button 
  
  :disabled="nonEligere"
  v-for=" {nomen, id} in optiones" 
  :key="id" 
  @click="$emit('electusOptio', id)"
  :class="['capitalize disabled:shadow-none disabled:bg-gray-100', {
    recte: id === recteResponsio && nonEligere,
    'non-recte': id !== recteResponsio && nonEligere,
  }]"
  >
    {{ nomen }}
    </button>

  </section>
</template>

<script setup lang="ts">
import type { Pokemon } from '../interfaces';

interface Props {
  optiones: Pokemon[];
  nonEligere: boolean;
  recteResponsio: number;
}

defineProps<Props>();

defineEmits<{
  electusOptio: [id:number]
}>()
</script>

<style scoped>
@import 'tailwindcss';
button {
  @apply bg-white shadow-md rounded-lg cursor-pointer p-3 my-2 w-40 text-center hover:bg-gray-100 transition-all;
}

.recte{
  @apply bg-blue-500 text-white
}
.non-recte{
  @apply bg-red-100 opacity-70
}
</style>
