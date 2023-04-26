<script setup>
import {reactive, ref} from 'vue'

defineProps({
  msg: {
    type: String,
    required: true
  }
})

const configA = [
  {
    propValue: "date",
    labelValue: "column1",
    widthValue: "180"
  },
  {
    propValue: "name",
    labelValue: "column2",
    widthValue: "180"
  },
  {
    propValue: "address",
    labelValue: "column3",
    widthValue: "180"
  }
]

const configB = [
  {
    propValue: "date",
    labelValue: "column4",
    widthValue: "180"
  },
  {
    propValue: "age",
    labelValue: "column5",
    widthValue: "180"
  },
  {
    propValue: "info",
    labelValue: "column6",
    widthValue: "180"
  }
]

let columnData = ref(configA)

const tableData = [
  {
    date: '2016-05-03',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
    age: "1",
    info: "user b1"
  },
  {
    date: '2016-05-02',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
    age: "2",
    info: "user b2"
  },
  {
    date: '2016-05-04',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
    age: "3",
    info: "user b3"
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
    age: "4",
    info: "user b4"
  },
]

const radio1 = ref("1")

const changeUser = (value) => {
  console.log(value)
  if (value === '1') {
    columnData.value = configA
    console.log(value, columnData)
  } else {
    columnData.value = configB
    console.log(value, columnData)
  }

}

</script>

<template>
  <div class="greetings">
    <el-radio-group v-model="radio1" @change="changeUser" style="margin-bottom: 30px">
      <el-radio label="1" size="large" border>User A</el-radio>
      <el-radio label="2" size="large" border>User B</el-radio>
    </el-radio-group>
    <el-table :data="tableData" border style="width: 100%">
      <template v-for="item in columnData" :key="item.label">
        <el-table-column :prop="item.propValue" :label="item.labelValue" :width="item.widthValue"/>
      </template>
    </el-table>
  </div>
</template>

<style scoped>
.greetings {
  width: 800px;
  margin: 50px auto;
}
</style>
