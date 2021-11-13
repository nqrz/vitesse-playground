<script setup lang="ts">
import { isDark, toggleDark } from '~/composables'

const { t, availableLocales, locale } = useI18n()

const toggleLocales = () => {
  // change to some real logic
  const locales = availableLocales
  locale.value = locales[(locales.indexOf(locale.value) + 1) % locales.length]
}
</script>

<template>
  <div class="flex justify-between items-center py-2 px-1 sticky top-0">
    <div class="flex">
      <router-link class="icon-btn mx-2 flex items-center" to="/" :title="t('button.home')">
        <carbon-home />
        <p class="ml-1 font-semibold hidden sm:block">
          {{ t('button.home') }}
        </p>
      </router-link>

      <router-link class="icon-btn mx-2 flex items-center" to="/about" :title="t('button.about')">
        <carbon-dicom-overlay />
        <p class="ml-1 font-semibold hidden sm:block">
          {{ t('button.about') }}
        </p>
      </router-link>
    </div>

    <div>
      <button class="icon-btn mx-2 !outline-none" :title="t('button.toggle_dark')" @click="toggleDark()">
        <carbon-moon v-if="isDark" />
        <carbon-sun v-else />
      </button>

      <a class="icon-btn mx-2" :title="t('button.toggle_langs')" @click="toggleLocales">
        <carbon-language />
      </a>
    </div>
  </div>
</template>
