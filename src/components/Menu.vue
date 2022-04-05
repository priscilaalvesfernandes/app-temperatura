<template><!--Apresentandi na tela imformacões de cidade, data, hr e temperatura-->
    <div class="city">
      <span class="city row q-mt-lg">
        <div class="dados col-6 q-pl-xl">
            <h1> {{ dados.city.name }} - {{ dados.city.country }}</h1>
            <h1> Data: {{today()}} </h1>
            <!-- mostrando cidade e país-->
            <h2> {{hora}} </h2>  <!-- mostrando dia e hr-->
            <h3> Humidade {{dados.list[0].main.humidity}}%</h3> 
        </div>
        <div class="dados1 col-6 q-pl-xl"> 
           <h1> Temperatura {{Math.round(dados.list[0].main.temp)}}ºC </h1>
            <Informacoes
              :dadosApi="this.dados"
              :horaDiaria ="this.hora"
            />
           <h2> {{upercaseString(dados.list[0].weather[0].description)}} </h2>
        </div>
      </span>
    </div>
</template>

<script>
import Informacoes from './Informacoes.vue'
export default {  
  components:{
    Informacoes
  },
  props: {
    //recebendo dados da MPI
    dados:{
      type:Object,
      required:true
    },
    hora:{
      type:String,
      required: true
    },
    inconeTemp: {
      type: String,
      required: true
    },
    bgTemperatura: {
      type: String,
      required: true
    },
    bgCard:{
      type: String,
      required: true
    }
  },
  methods:{
    upercaseString(string){
      return string[0].toUpperCase() + string.slice(1);
    },
    today(){
      const hoje = this.dados.list[0].dt_txt.slice(5,10)
      return hoje
    }
  }
  
}
</script>

<style scope>

div.city{
  width: 95%;
  border-radius: 10px;
  margin: 0 auto;
}
div.dados{
  width: 95%;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 10px; 
  text-align: center; 
}
div.dados1{
  /* background-color: rgb(219, 187, 126); */
  width: 95%;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 10px; 
  text-align: center; 
}

</style>