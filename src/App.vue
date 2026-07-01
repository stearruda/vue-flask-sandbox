<template>
  <div style="text-align: center; margin-top: 50px; font-family: sans-serif;">
    <h1>Vue 3 + Flask Sandbox</h1>
    <p>Server Response: <strong style="color: #42b883;">{{ backendMessage }}</strong></p>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const backendMessage = ref('Loading...')

onMounted(async () => {
  try {
    const response = await fetch('http://localhost:8000/api/message')
    const data = await response.json()
    backendMessage.value = data.message
  } catch (error) {
    backendMessage.value = 'Failed to connect to Flask backend.'
  }
})
</script>
