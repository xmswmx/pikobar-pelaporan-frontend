<template>
  <v-card
    class="chart mx-auto"
    outlined
  >
    <v-card-title class="title ml-0 black--text">
      {{ $t('label.daily_number') }} {{ $t('label.pdp') }}
    </v-card-title>
    <v-divider class="mt-0 mb-2" />
    <v-card-text>
      <chart-bar
        v-if="loaded"
        :chart-data="chartData"
        :options="chartOptions"
        :styles="chartStyles"
      />
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: 'ChartDailyPatientUnderInvestigation',
  props: {
    chartHeight: {
      type: Number,
      default: 300
    }
  },
  data() {
    return {
      loaded: false,
      chartData: {
        labels: [
          '01/04',
          '02/04',
          '03/04',
          '04/04',
          '05/04',
          '06/04',
          '07/04',
          '08/04',
          '09/04',
          '10/04',
          '11/04',
          '12/04'
        ],
        datasets: [
          {
            label: this.$t('label.done'),
            backgroundColor: '#EED138',
            hoverBackgroundColor: '#EED138',
            data: [40, 20, 12, 39, 10, 40, 39, 80, 40, 20, 12, 11]
          },
          {
            label: this.$t('label.process'),
            backgroundColor: '#E08D3B',
            hoverBackgroundColor: '#E08D3B',
            data: [40, 20, 12, 39, 10, 40, 39, 10, 40, 20, 12, 11]
          }
        ]
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false,
        scales: {
          xAxes: [
            {
              gridLines: {
                display: false
              },
              stacked: true
            }
          ],
          yAxes: [
            {
              ticks: {
                min: 0
              },
              gridLines: {
                drawBorder: false
              },
              scaleLabel: {
                display: true,
                labelString: 'Value'
              },
              stacked: true
            }
          ]
        },
        legend: {
          display: true,
          position: 'bottom',
          labels: {
            boxWidth: 10
          },
          reverse: true
        },
        tooltips: {
          displayColors: false,
          mode: 'index',
          intersect: false
        }
      }
    }
  },
  computed: {
    chartStyles() {
      return {
        height: `${this.chartHeight}px`,
        position: 'relative'
      }
    }
  },
  async mounted() {
    this.loaded = true
  }
}
</script>

<style scoped>
  .chart .title {
    text-transform: none;
  }
</style>
