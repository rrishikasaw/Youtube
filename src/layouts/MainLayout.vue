<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="header">
      <q-toolbar class="flex justify-between">
        <div class="flex">
          <q-btn
            flat
            dense
            round
            icon="menu"
            aria-label="Menu"
            @click="toggleLeftDrawer"
          />

          <q-toolbar-title class="flex">
            <img src="../assets/image/home/youtube.jpg" width="130" alt="" />
          </q-toolbar-title>
        </div>

        <div class="flex hide-sm">
         

          <q-input
  outlined
  v-model="searchText"
  placeholder="Search..."
  clearable
  dense
  rounded
  style="width: 500px"
 
>
  <template v-slot:prepend>
    <q-icon name="search" class="cursor-pointer" />
  </template>
  <template v-slot:append>
    <q-icon name="event" class="cursor-pointer" />
  </template>
</q-input>
          

           <q-icon
          slot="append"
          name="mic"
          class="cursor-pointer q-mx-md  q-mt-sm"
          @click="startVoiceSearch"
          size="28px"
        />
        </div>
       

       <div class="flex hide-sm">
         <q-icon
          slot="append"
          name="more_vert"
          class="cursor-pointer q-mr-sm q-mt-sm"
          @click="openMenu"
          size="24px"
        />
        
    <q-btn outline rounded color="primary" label="Profile"  icon="person" />
    <q-icon
  slot="append"
  name="water_drop"
  class="cursor-pointer q-mx-md q-mt-sm"
  @click="openMenu"
  size="24px"
/>
       </div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> Essential Links </q-item-label>

        <EssentialLink
          v-for="link in linksList"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

defineOptions({
  name: "MainLayout",
});

const linksList = [
  {
    title: "Home",
       // caption: "github.com/quasarframework",
    icon: "home",
    link: "https://quasar.dev",
  },
  {
    title: "Shorts",
    // caption: "github.com/quasarframework",
    icon: "code",
    link: "https://github.com/quasarframework",
  },
  {
    title: "video",
    // caption: "chat.quasar.dev",
    icon: "chat",
    link: "https://chat.quasar.dev",
  },
 
  {
    title: "Save",
    // caption: "@quasarframework",
    icon: "rss_feed",
    link: "https://twitter.quasar.dev",
  },
  {
    title: "Download",
    // caption: "@QuasarFramework",
    icon: "public",
    link: "https://facebook.quasar.dev",
  },
 
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>

<style scoped>



    @media (max-width: 800px) {
      .hide-sm {
        display: none;
      }
    }
.header {
  background-color: white;
  color: black;
}
</style>
