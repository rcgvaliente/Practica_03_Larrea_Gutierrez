<template>
    <div class="q-pa-md flex flex-center container">
      <q-card square bordered class="q-pa-lg shadow-1" style="width: 500px">
        <q-card-section> </q-card-section>
  
        <q-card-section>
          <q-form class="q-gutter-md">
            <q-input
              square
              filled
              clearable
              v-model="email"
              type="email"
              label="email"
            />
            <q-input
              square
              filled
              clearable
              v-model="password"
              type="password"
              label="password"
            />
          </q-form>
        </q-card-section>
        <q-card-actions class="q-px-md">
          <q-btn
            color="primary"
            size="lg"
            class="full-width"
            label="Login"
            @click="IniciarSesion()"
          />
          <q-btn
            color="primary"
            size="lg"
            class="full-width"
            label="Crear usuario"
          />
        </q-card-actions>
      </q-card>
    </div>
  </template>
  <style>
  body {
    background-color: #eee;
  }
  </style>
  <script>
  // import { login } from "src/boot/keycloak";
  import axios from "axios";
  export default {
    data() {
      return {
        email: "",
        password: "",
      };
    },
    methods: {
      IniciarSesion() {
        try {
          var data = {
            Email: this.email,
            Password: this.password,
          };
  
  
          axios
            .request(config)
            .then((response) => {
              location.href = "/Usuario/Inicio";
            })
            .catch((error) => {
              this.$q.notify({
                type: "negative",
                message: error.response.data.message,
              });
            });
        } catch (error) {
          console.error("Error al obtener datos:", error);
        }
      },
    },
  };
  </script>
  
  <style>
  .container {
    height: 100vh; /* Hace que el contenedor ocupe todo el alto de la ventana */
  }
  
  .my-card {
    width: 300px; /* O el ancho que prefieras */
    max-width: 90%; /* Para asegurar que se vea bien en pantallas pequeñas */
  }
  </style>