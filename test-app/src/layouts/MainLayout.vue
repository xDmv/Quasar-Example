<template>
  <q-layout view="lHh Lpr lFf">
      <q-header>
        <q-toolbar>
            <q-btn flat @click="rigthDrawerOpen = !rigthDrawerOpen">
              <div>
                <img src="~assets/exit.png">
              </div>
            </q-btn>

          <q-toolbar-title>Header</q-toolbar-title>
          <q-btn flat @click="rigthDrawerOpen = !rigthDrawerOpen" round dense icon="menu" />
        </q-toolbar>
      </q-header>

    <q-drawer
        v-model="rigthDrawerOpen"
        :width="320"
        :breakpoint="500"
        overlay
        bordered
        content-class="bg-grey-3"
      >
        <q-scroll-area class="fit">
          <q-list v-for="(menuItem, index) in menuList" :key="index">

            <q-item color="accent" v-ripple>
              <q-item-section avatar>
                <q-icon :name="menuItem.icon" />
              </q-item-section>
              <q-item-section>
                {{ menuItem.label }}
              </q-item-section>
            </q-item>

           <q-separator v-if="menuItem.separator" />

          </q-list>
        </q-scroll-area>
      </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

const menuList = [
  {
    icon: 'inbox',
    label: 'Inbox',
    separator: true
  },
  {
    icon: 'send',
    label: 'Outbox',
    separator: false
  },
  {
    icon: 'delete',
    label: 'Trash',
    separator: false
  },
  {
    icon: 'error',
    label: 'Spam',
    separator: true
  },
  {
    icon: 'settings',
    label: 'Settings',
    separator: false
  },
  {
    icon: 'feedback',
    label: 'Send Feedback',
    separator: false
  },
  {
    icon: 'help',
    iconColor: 'primary',
    label: 'Help',
    separator: false
  }
]

export default {
  name: 'MainLayout',
  data () {
    return {
      rigthDrawerOpen: false,
      menuList
    }
  }
}
</script>
