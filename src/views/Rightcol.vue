<template>
    <div class="aside">
        <h1>Colonne de droite</h1>


        <InputBlock
                v-bind:class="inputdemerde.class"
                v-bind:value="inputdemerde.value"
                v-bind:placeholder="inputdemerde.placeholder"
                v-on:input="inputdemerde.value = $event">
            texte a mettre dans le Slot par défaut
            <template v-slot:label>Texte dans le Slot Label</template>
            <template v-slot:message>{{inputdemerde.message}}</template>
        </InputBlock>



        <hr/>
    </div>
</template>

<script>
// @ is an alias to /src
import InputBlock from '@/components/InputBlock.vue'

export default {
  name: 'rightcol',
  components: {
    InputBlock
  },
  data () {
    return {
      inputdemerde: {
        value: '',
        placeholder: 'placeholder de l\'input',
        class: '',
        message: 'message par défaut'
      }
    }
  },
  watch: {
    'inputdemerde.value': function (val) {
      if (val.length < 5) {
        this.inputdemerde.class = 'error'
        this.inputdemerde.message = 'trop court'
      } else {
        this.inputdemerde.class = ''
        this.inputdemerde.message = 'ok !'
      }
    }
  }
}
</script>

<style scoped="scoped">
    .error {
        background-color: #ff5555;
    }
</style>
