<script setup>
import { useRouter } from "vue-router";
import { onMounted } from "vue";
import { register } from "@teamhanko/hanko-elements";

const hankoApi = import.meta.env.VITE_HANKO_API_URL;

const router = useRouter();

const redirectAfterLogin = () => {
  // successfully logged in, redirect to a page in your application
  router.push("/profile");
};

onMounted(() => {
  register(hankoApi)
    .catch(() => {
      // handle error
    });
});
</script>

<template>
  <hanko-auth @onAuthFlowCompleted="redirectAfterLogin" />
</template>
