<template>
  <div class="home">
    <h1>Dating App</h1>
    <ul v-if="users.length > 0">
      <li v-for="user in users" :key="user.id">{{ user.userName }}</li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import axios from 'axios'

export default defineComponent({
  name: 'HelloWorld',
  data() {
    return {
      users: []
    }
  },
  async created() {
    await this.getUsers()
  },
  methods: {
    async getUsers() {
      const users = await axios.get('https://localhost:5001/api/users')
      this.users = users.data
    }
  }
})
</script>

<style scoped lang="scss"></style>
