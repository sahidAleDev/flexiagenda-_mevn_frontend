<script setup>
import { onMounted } from 'vue';
  import { useRoute } from 'vue-router'
  import { useAppointmentsStore } from '@/stores/appoinments ';

  const route = useRoute()
  const appoinments = useAppointmentsStore()

  onMounted(() => {
    appoinments.clearAppointmentData()
  })
</script>

<template>
  
  <nav class="my-5 flex flex-col sm:flex-row gap-3">
    <RouterLink
      :to="{ name: 'new-appointment' }"
      class="flex-1 text-center p-3 uppercase font-extrabold hover:bg-blue-700 hover:text-white" 
      :class="route.name === 'new-appointment' ? 'bg-blue-700 text-white' : 'bg-white text-blue-500'"
    >
      <!-- flex-1 Toma todo el espacio que haya disponible, como hay flex en el padre -->
      Servicios
    </RouterLink>

    <RouterLink
      :to="{ name: 'appointment-details' }"
      class="flex-1 text-center p-3 uppercase font-extrabold hover:bg-blue-700 hover:text-white" 
      :class="route.name === 'appointment-details' ? 'bg-blue-700 text-white' : 'bg-white text-blue-500'"
    >
      <!-- flex-1 Toma todo el espacio que haya disponible, como hay flex en el padre -->
      Cita y Resumen
    </RouterLink>
  </nav>

  <div class="space-y-5">
    <RouterView />
  </div>
</template>
