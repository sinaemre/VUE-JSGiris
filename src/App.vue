<script>
  export default{
    data(){
      return {
        message: "Hello World!",
        alinacaklar: ["patates", "domates"],
        urun: "",
        goster: false, 
        acikMi : false,
        deneme: 'on-lamp.png'
      }
    },
    methods: {
      ekle(event) {
        event.preventDefault();
        this.alinacaklar.push(this.urun);
        this.urun = "";
      },
      sil(index, event) {
        event.preventDefault();
        this.alinacaklar.splice(index,1);
      } 
    },
    computed:{
      lambaAcmaKapama : function(){
        return this.acikMi ? "Lambayı Kapat" : "Lambayı Aç"
      }
    }
  }
</script>

<template>
  <h1>Vue Öğreniyorum</h1>  
  
  Your message : <input type="text" v-model="message">
  
  <h2>{{message}}----()----{{message}}----()---{{message}}--()--{{message}}</h2>

  <hr />

  <h2>Alışveriş Listesi</h2>
  Alınacak: 
  <form @submit="ekle">
    <input type="text" v-model="urun" required/>
    <button>Ekle</button>
    
    <ul>
      <li v-for="(alinacak,i) in alinacaklar">
        <a href="#" @click="sil(i,$event)">&times</a>
        {{alinacak}}
      </li>
    </ul>

    <hr />

    <input type="checkbox" v-model="goster"/> Aşağıdaki paragrafı göster

    <p v-if="goster">Lorem ipsum, dolor sit amet consectetur adipisicing elit. Voluptatibus animi quasi totam voluptatum expedita quis error possimus asperiores, omnis neque.</p>

    <hr />
  </form>

  <button @click="acikMi = !acikMi">{{ lambaAcmaKapama }}</button>
  <div>
    <img v-if="acikMi" src="./assets/img/on-lamp.png" alt="açik lamba" width="100">
    <img v-else src="./assets/img/off-lamp.png" alt="açik lamba" width="100">
  </div>
</template>

<style>
@import './assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  font-weight: normal;
}

</style>
