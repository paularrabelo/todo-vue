<script setup>
    const props = defineProps(['tarefas'])
</script>

<template>
    <ul v-if="props.tarefas.filter(tarefa => !tarefa.pendentes).length >= 1" class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefas">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada }" class="ms-2" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
    <p class="d-flex justify-content-center mt-4 mb-4" v-else>Você não possui tarefas pendentes</p>
</template>

<style scoped>
    .done {
        text-decoration: line-through;
    }
</style>