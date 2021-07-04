<template>
<v-row>
  <v-col class="text-center">
    <v-text-field
      label="Multitab Text Field"
      v-model="textField"
    ></v-text-field>
  </v-col>
</v-row>
</template>

<script>
export default {
  mounted() {
    if (!process.server) {
      this.activateStorage();
    };
  },
  data: () => ({
    textField: null
  }),
  watch: {
    textField(val) {
      localStorage.setItem('forInput', val);
    }
  },
  methods: {
    activateStorage() {
      window.addEventListener('storage', (e) => {
        this.textField = localStorage.getItem('forInput');
      });
    }
  }
}
</script>
