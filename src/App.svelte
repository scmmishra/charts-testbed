<script>
  import { onMount } from "svelte";
  import arcticData from "./data.js";
  import { Chart } from "frappe-charts/dist/frappe-charts.esm.js";

  let config = {
    data: arcticData,
    title: "Arctic sea ice minimum",
    type: "bar", // or 'bar', 'line', 'pie', 'percentage'
    height: 300,
    tooltipOptions: {
      formatTooltipX: d => (d + "").toUpperCase(),
      formatTooltipY: d => d + " million sq km"
    },
    lineOptions: {
      regionFill: 1
    },
    axisOptions: {
      xIsSeries: true,
      xAxisMode: "tick"
    }
    // colors: ["blue"]
  };
  let chartRef;
  onMount(() => {
    let chart = new Chart(chartRef, config);
  });
</script>

<style global>
  @import "../node_modules/frappe-charts/dist/frappe-charts.min.css";
</style>

<main>
  <div bind:this={chartRef} />
</main>
