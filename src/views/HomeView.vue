<script setup>
import {ref } from 'vue'
const selectedUser = ref([])
const selectedFor = ref([])
const ofUser = ref([
      {
    "id": 1,
    "name": "Shoes 1"
  },
  {
    "id": 2,
    "name": "Shoes 2"
  },
  {
    "id": 3,
    "name": "Shoes 3"
  },
  {
    "id": 4,
    "name": "Shoes 4"
  },
  {
    "id": 5,
    "name": "T-shirt 1"
  },
  {
    "id": 6,
    "name": "T-shirt 2"
  },
  {
    "id": 7,
    "name": "T-shirt 3"
  },
  {
    "id": 8,
    "name": "T-shirt 4"
  }
])

const ofFor = ref([
      {
    "id": 11,
    "name": "Jacket 1"
  },
  {
    "id": 12,
    "name": "Jacket 2"
  },
  {
    "id": 13,
    "name": "Jacket 3"
  },
  {
    "id": 14,
    "name": "Jacket 4"
  },
  {
    "id": 15,
    "name": "Hoodie 1"
  },
  {
    "id": 16,
    "name": "Hoodie 2"
  },
  {
    "id": 17,
    "name": "Hoodie 3"
  },
  {
    "id": 18,
    "name": "Hoodie 4"
  }
])
const noEvent = (e) => {
  e.currentTarget.closest('.item').classList.add('disabled');
}
</script>

<template>
  <div class="flex">
    <div class="flex-item-small">
    <div class="item-selected" v-for="item in selectedUser" :key="item">
      {{ item }}
    </div>
    </div>
    <div class="flex-item-small">
      
      <div class="item-selected" v-for="item in selectedFor" :key="item">
        {{ item }}
      </div>
    </div>
  </div>
  <div class="flex">
      <div class="flex-item">
        <label class="item" v-for="{id,name} in ofUser" :key="id" :for="id">
          {{ name }}
          <input type="checkbox" :value="name" :id="id"  v-model="selectedUser" @change="noEvent">
        </label>
      </div>
    
      <div class="flex-item">
          <label class="item" v-for="{ id, name } in ofFor" :key="id" :for="id">
            {{ name }}
            <input type="checkbox"  :value="name" :id="id"  v-model="selectedFor" @change="noEvent">
          </label>
        </div>
    </div>
</template>

<style scoped>
.flex{
  display: flex;
  width: 100%;
  justify-content: space-between;
  margin-bottom: 50px;
}
.flex-item{
  width: calc(50% - 40px);
  padding: 20px;
  border: 1px solid #000;
  display: grid;
  grid-template-columns: repeat(3,1fr);
  grid-auto-flow: row;
  grid-gap: 20px;
}
.flex-item-small{
  width: 400px;
  padding: 20px;
  border: 1px solid red;
  display: grid;
  grid-template-columns: repeat(3,1fr);
  grid-gap: 15px;
}
.item{
  min-height: 150px;
  background-color: green;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-weight: 600;
  cursor: pointer;
}
.item input{
  display: none;
}
.item-selected{
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid blue;
}
.disabled{
  pointer-events: none;
  opacity: .3;
}
</style>