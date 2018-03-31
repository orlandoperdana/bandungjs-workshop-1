<template>
  <div class="hello">
    <h1 v-if="isNameShown">Nama saya <span v-html="firstName"></span> {{ lastName }}</h1>
    <p>
      <input type="text" name="firstName" v-model="firstName">
      <input type="text" name="lastName" v-model="lastName">
      <input type="text" name="city" v-model="address.city">
      <input type="text" name="province" v-model="address.province">
      <br>
      Masukkan tanggal lahir anda :
      <input type="number" v-model="myBirthYear">
    </p>
    <p>Saya berasal dari {{ address.city }}, {{ address.province }}</p>
    <p><a :href="githubUrl" :title="title"> My GitHub</a></p>
    <p>Tahun depan, berumur {{ age + 1}} tahun</p>
    <p>Saya {{ work ? 'Bekerja' : 'Tidak Bekerja' }}</p>
    <p>Saya
    <span v-if="age < 10 && age > 0">masih anak kecil</span>
    <span v-else-if="age < 20 && age > 10">sudah remaja</span>
    <span v-else>tua</span>
    </p>
    <p>
      <ul>
        <li v-for="merek in daftarMerek" :key="merek.namaMerek">
          {{ merek.namaMerek }}
        </li>
      </ul>
    </p>
    <p>
    Umur saya
      {{ getMyAge }}
      {{ getAddressData }}
    </p>
    <button :disabled="buttonState" v-on:click="showPopup(false)">Click Here</button>
    <button v-on:click="showName()">Toggle Nama</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      firstName: "Orlando",
      lastName : "Perdana",
      work: false,
      age: 23,
      myBirthYear: 1994,
      address: {
        city: 'Medan',
        province: 'Sumatera Utara',
        country: 'Indonesia'
      },
      githubUrl:'https://github.com/orlandoperdana',
      title:'Situs GitHub saya',
      buttonState: false,
      isNameShown: true,
      daftarMerek: [
        {namaMerek: 'asus'},
        {namaMerek: 'acer'},
        {namaMerek: 'toshiba'}
      ],
    };
  },
  methods: {
    showName() {
      this.isNameShown = !this.isNameShown;
    },
    getCurrentYear() {
      let currentYear = new Date().getFullYear();
      return currentYear;
    }
  },
  computed: {
    getMyAge () {
      const currentYear = new Date().getFullYear();
      const myBirthYear = this.myBirthYear;
      let theYear = currentYear - myBirthYear;
      return theYear;
    },
    getAddressData (){
      let {city, province, country} = this.address;
      return city + " " + province + " " + country;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
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
