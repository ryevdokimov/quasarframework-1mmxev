<template>
  <q-page class="column flex-center">
    <div class="q-mt-xl">
      <q-btn color="primary" dense round label="-" @click="count--" />

      <span class="q-mx-md text-bold">{{ count }}</span>

      <q-btn color="primary" dense round label="+" @click="count++" />
    </div>

    <div class="q-pa-md">
      <q-table title="TableTest" dense :rows="state.rows" row-key="name" />
    </div>
  </q-page>
</template>

<script setup>
import { ref, reactive, onMounted } from 'vue';

let count = ref(0);

let state = reactive({ rows: [] });

onMounted(() => {
  getData();
});

async function getData() {
  const response = await fetch(
    'https://c47d7a57-e2fe-42f1-b9bc-e3dc4e2c6d58.mock.pstmn.io/test'
  );
  const data = await response.json();

  state.rows = data;
}
</script>
