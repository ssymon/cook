<script setup lang="ts">
import { useIndexedDB } from '~/composables/db'
import { appName } from '~/constants'
import { installPrompt } from './utils/pwa'

// https://nuxt.com/docs/api/composables/use-head
useHead({
  title: appName,
  meta: [
    {
      name: 'description',
      content: '哇哦，孙同学又来学做饭了！',
    },
  ],
})

const indexedDB = useIndexedDB()

onMounted(() => {
  installPrompt()
  indexedDB.init()
})
</script>

<template>
  <VitePwaManifest />
  <NuxtLayout>
    <NuxtLoadingIndicator />
    <NuxtPage />
  </NuxtLayout>
</template>
