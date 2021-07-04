<template>
  <div class="bg-dark h-screen">
    <div class="flex" style="height: 88vh">
      <!-- side nav -->
      <div class="w-56 bg-black h-full flex-none">
        <div class="p-6">
          <img src="./assets/logos/Spotify_Logo_RGB_White.png" class="h-10" />
        </div>
        <div class="mx-2 mb-5">
          <button
            v-for="page in pages"
            v-bind:key="page.id"
            @click="setID = page.id"
            :class="`w-full rounded text-sm font-semibold px-3 py-2 flex items-center justify-start ${
              setID === page.id ? 'bg-light text-white' : 'text-lightest'
            }`"
          >
            <i class="material-icons mr-3">{{ page.icon }}</i>
            <p>{{ page.name }}</p>
          </button>
        </div>
        <!-- playlists -->
        <div class="mx-5">
          <h1 class="mb-3 text-xs tracking-widest text-lightest uppercase">
            playlists
          </h1>
          <button
            class="
              flex
              items-center
              justify-start
              opacity-75
              hover:opacity-100
              px-3
              py-2
            "
          >
            <i class="material-icons bg-lightest mr-3">playlist_add</i>
            <p class="text-sm text-white font-semibold">Create Playlist</p>
          </button>
          <button
            class="
              flex
              items-center
              justify-start
              opacity-75
              hover:opacity-100
              px-3
              py-2
            "
          >
            <i class="material-icons bg-lightest mr-3">favorite</i>
            <p class="text-sm text-white font-semibold">Liked Songs</p>
          </button>
          <div class="h-px w-full bg-light my-3"></div>
          <div class="mx-5">
            <div class="w-full overflow-y-scroll h-24">
              <p
                v-for="album in albums"
                v-bind:key="album.name"
                class="text-lightest hover:text-white text-sm py-1"
              >
                {{ album.name }}
              </p>
            </div>
          </div>
        </div>
      </div>
      <!-- main content -->
      <div class="w-full h-full relative overflow-y-scroll">
        <!-- header -->
        <div
          class="
            sticky
            top-0
            w-full
            px-4
            py-6
            flex
            items-center
            justify-between
          "
        >
          <div class="flex items-center">
            <button class="rounded-full bg-black w-5 h-5 text-white mr-5">
              <i class="material-icons text-sm font-semibold">arrow_back_ios</i>
            </button>
            <button class="rounded-full bg-black w-5 h-5 text-white">
              <i class="material-icons text-sm font-semibold"
                >arrow_forward_ios</i
              >
            </button>
          </div>
          <div class="realative">
            <button
              @click="showDropDown = !showDropDown"
              class="flex items-center bg-light rounded-full py-1 px-2"
            >
              <i class="material-icons h-5 w-5 mr-3 text-white">
                account_circle
              </i>
              <p class="text-white font-semibold text-sm mr-3">My Account</p>
              <i v-if="!showDropDown" class="material-icons text-white">
                arrow_drop_down
              </i>
              <i v-if="showDropDown" class="material-icons text-white">
                arrow_drop_up
              </i>
            </button>
            <div class="absolute bg-light rounded mt-1">
              <button
                v-if="showDropDown"
                @click="showDropDown = !showDropDown"
                class="flex items-center py-2 border-b border-lightest"
              >
                <p class="text-lightest hover:text-white text-sm px-14">
                  Account
                </p>
              </button>
              <button
                v-if="showDropDown"
                @click="showDropDown = !showDropDown"
                class="py-2 border-b border-light flex items-center"
              >
                <p class="text-lightest hover:text-white text-sm px-14">
                  Logout
                </p>
              </button>
            </div>
          </div>
        </div>
        <!-- cards -->
        <div>
          <div class="px-6 py-3 flex items-center justify-between">
            <h1
              class="
                text-2xl
                pl-2
                font-semibold
                text-white
                tracking-wider
                hover:underline
              "
            >
              Recently Played
            </h1>
            <h2
              class="
                text-xs
                pr-8
                mb-3
                tracking-wider
                uppercase
                hover:underline
                text-lightest
              "
            >
              See All
            </h2>
          </div>
          <div class="w-full flex flex-wrap">
            <div class="p-2 w-48">
              <div class="bg-light w-full h-auto p-5">
                <img src="" class="h-auto w-full shadow mb-2" />
                <h1 class="text-sm font-semibold text-white tracking-wide"></h1>
                <h2 class="text-xs text-lightest tracking-wide"></h2>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- playbar -->
    <div class="w-full bg-light" style="height: 12vh"></div>
  </div>
</template>

<script>
import "./assets/css/main.css";
export default {
  name: "App",
  data: function () {
    return {
      pages: [
        { id: "home", name: "Home", icon: "home" },
        { id: "search", name: "Search", icon: "search" },
        { id: "library", name: "Your Library", icon: "bar_chart" },
      ],
      setID: "home",
      albums: [
        { name: "Tollywood" },
        { name: "Radar India" },
        { name: "Bollywood" },
        { name: "Soul Soothers" },
        { name: "Cherrypick 46" },
        { name: "Selected Chillout" },
      ],
      showDropDown: false,
    };
  },
  methods: {},
};
</script>

<style lang="stylus" scoped></style>
