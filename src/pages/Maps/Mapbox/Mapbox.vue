<template>
    <div>
        <h1 class="mapTitle page-title">
            Isdako <span class="fw-semi-bold">Geofencing Maps</span>
        </h1>
        <div class="mapContainer">
            <MglMap :accessToken="accessToken" @load="onMapLoad" :mapStyle="mapStyle"/>
        </div>
    </div>
</template>

<script>
  import Mapbox from "mapbox-gl";
  export default {
    name: 'MapboxMap',
    data() {
      return {
        accessToken: 'pk.eyJ1IjoiZGVtcyIsImEiOiJjanMzMG5ucTAwOWhjNDRyMGV0aGphZDJuIn0.rAQHFl0OE25fHIrbqjjjXQ',
        mapStyle: 'mapbox://styles/mapbox/light-v9'
      }
    },
    created() {
      this.mapbox = Mapbox;
    },
    methods: {
      onMapLoad(event) {
        // Here we cathing 'load' map event
        const asyncActions = event.component.actions

        const newParams =  asyncActions.flyTo({
          center: [125.615624,7.086488],
          zoom: 15,
          speed: 1
        })
        console.log(newParams)
        /* => {
                center: [30, 30],
                zoom: 9,
                bearing: 9,
                pitch: 7
              }
        */
      }
    }
  };
</script>

<style src="@/pages/Maps/Google.scss" lang="scss" scoped />
