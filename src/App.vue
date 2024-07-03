<script setup>
import  { onMounted, inject } from 'vue';
import BSTooltip from '@/components/BSTooltip.vue';
import BSNavbar from '@/components/BSNavbar.vue';

// Inject Bootstrap with the same key as defined in main.js
const bootstrap = inject('bootstrap');

onMounted(() => {
  try {
    // Expanding the navbar.
    const collapse = new bootstrap.Collapse('#navbarSupportedContent');
    collapse.show();

    // Tooltips are opt-in and must be initialized manually!
    const tooltipTriggerList = document.querySelectorAll('[data-bs-toggle="tooltip"]')
    const tooltipList = [...tooltipTriggerList].map(tooltipTriggerEl => new bootstrap.Tooltip(tooltipTriggerEl))
  } catch (e) {
    console.log('Bootstrap error: ', e);
  }
});
</script>

<template>
  <div id="wrapper">
    <BSNavbar />
    <BSTooltip />
  </div>
</template>

<style scoped>
#wrapper {
  max-width: 600px;
  margin: 0 auto;
}
</style>
