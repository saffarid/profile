<template>
    <div class="head-menu" :style="styleVars">
        <template v-for="(screen, index) of screens" :key="index">
            <TextButtton
                    @click="clickOnItem(index)"
                    :text="screen.title"/>
        </template>
    </div>
</template>

<script>
   import {
      reactive
   }              from 'vue'
   import TextButtton from './input/TextButton'
   export default {
      name: 'HeadMenu',
      components:{
         TextButtton,
      },
      props:{
         screens: {
            type: Array,
            required: true,
         },
      },
      setup(props, context){
         const styleVars = reactive({
            '--screen_count': props.screens.length
         })

         const clickOnItem = (index) => {
            context.emit('clickOnItem', index)
         }

         return {
            styleVars,
            clickOnItem
         }
      }
   }
</script>

<style lang="scss" scoped>
    .head-menu{
        display: grid;
        grid-template-columns: repeat(var(--screen_count), minmax(min-content, 190.5px));
        column-gap: 1px;
        align-self: stretch;
        align-content: stretch;
        align-items: stretch;
        justify-items: stretch;
        justify-content: center;
        justify-self: center;
        padding: 2px 0;
        background: rgba(72, 72, 72, 0.75);
        min-height: 30px;

        .text-button{
            letter-spacing: .1em;
            font-size: 16px;
            font-weight: 500;
            cursor: pointer;
        }
    }

</style>