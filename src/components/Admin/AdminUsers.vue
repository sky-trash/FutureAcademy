<script setup>
import AdminNavbar from "../Admin/AdminNavbar.vue"
import axios from "axios"
import { ref } from "vue"
const teachers = ref(
  (await axios.get(`http://26.232.67.81:3308/api/users`)).data
)
</script>

<template>
  <main class="main">
    <div class="admin">
      <div class="container">
        <h2>ПОЛЬЗОВАТЕЛИ</h2>
        <AdminNavbar />
        <table>
          <thead>
            <tr>
              <th>ID</th>
              <th>ИМЯ</th>
              <th>ФАМИЛИЯ</th>
              <th>НОМЕР</th>

            </tr>
          </thead>

          <tbody>
            <tr v-for="value in teachers" :key="value.id">
              <td>{{ value.id }}</td>
              <td>{{ value.name }}</td>
              <td>{{ value.last_name }}</td>
              <td>{{ value.number }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </main>
</template>

<style scoped>
@import "Admin.scss";
</style>
