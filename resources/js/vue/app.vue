<template>

<div class="body">
<div class="todoListContainer">
    <div class="heading">
        <h2 id="title">Todo List</h2>
        <add-item-form
         v-on:reloadlist="getList()"/>
    </div>
    <list-view 
    :items="items"
    v-on:reloadlist="getList()"/>
</div>
</div>   
</template>

<script>
import addItemForm from "./addItemForm.vue"

import listView from "./listView.vue"
export default {
    components:{
        addItemForm,
        listView
    },
    data: function(){
        return{
            items:[]
        }
    },
    methods:{
        getList(){
          axios.get('api/items')
          .then(response=>{
              this.items=response.data
          })
          .catch(error=>{
              console.log(error);
          })
        }
    },
    created(){
        this.getList();
    }
    
}
</script>

<style scoped>

.body{
    background-image: linear-gradient(rgba(255,255,255,.5), rgba(255,255,255,.5)),url("https://i.pinimg.com/originals/ac/54/a1/ac54a128942c750799c2c1fe144d2467.jpg");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    position: relative;
    height: 100vh; 
    
}
.todoListContainer{
   align-content: center;
    width: 550px;
    margin: auto;
    padding: 20px;
    
     
}

.heading{
    background: #e6e6e6;
    padding: 10px;
    background-color: rgb(181, 173, 228);
}

#title{
    text-align: center;
    font-family: MV Boli, Courier, monospace;
    font-size: 40px;
    
}
</style>

<style>
body{
    margin: 0px;
    margin-bottom: 0px !important;
}
</style>