<template>
  <div class="hello">
    <h1> Current Time </h1>
    <h2>{{ time }}</h2>
    <div class="row">
      <div class="col-sm">
        Year ends
        <h2>{{ year }}</h2>
      </div>
      <div class="col-sm">
        Month ends
        <h2>{{ month }}</h2>
      </div>
      <div class="col-sm">
        Week ends
        <h2>{{ week }}</h2>
      </div>
      <div class="col-sm">
        Day ends
        <h2>{{ day }}</h2>
      </div>
    </div>
  </div>
</template>

<script>
import moment from "moment";
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data() {
    return { 
      time: moment().format('LLLL'),
      day: "",
      week: "",
      month: "",
      year: "",
      }
  },
  created() {
    setInterval(() => {
      this.time = moment().format('LLLL');
      this.day = this.getDay();
      this.week = this.getWeek();
      this.month = this.getMonth();
      this.year = this.getYear();
    }, 1000)
  },
  methods: {
    getYear() {
      return moment().endOf('year').fromNow();
    },
    getMonth() {
      return moment().endOf('month').fromNow();
    },
    getWeek() {
      return moment().endOf('week').fromNow();
    },
    getDay() {
      return moment().endOf('day').fromNow();
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
