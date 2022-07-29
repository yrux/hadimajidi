<template>
  <!-- <Tutorial/> -->
  <div class="min-h-screen bg-gray-100">
    <div class="grid grid-cols-12 gap-4 pl-10 pr-10 pt-10">
      <div class="col-span-5">
        <input v-model="department" placeholder="Department Name" type="text" class="p-1 w-100 w-full shadow"/>
      </div>
      <div class="col-span-12">
        <table class="table-auto border-collapse border border-slate-500">
          <thead>
            <tr>
              <th class="border border-slate-600 text-center p-1">Work Name</th>
              <th class="border border-slate-600 text-center p-1">ID</th>
              <th class="border border-slate-600 text-center p-1">Unit</th>
              <th class="border border-slate-600 text-center p-1">CO</th>
              <th class="border border-slate-600 text-center p-1">Value</th>
              <th class="border border-slate-600 text-center p-1">PHI</th>
              <th class="border border-slate-600 text-center p-1">&nbsp;</th>
              <th class="border border-slate-600 text-center p-1">Amount</th>
              <th class="border border-slate-600 text-center p-1">Action</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(row, rowKey) in rows" :key="rowKey">
              <td class="border border-slate-700 text-center p-1">
                <input v-model="row.work_name" placeholder="Work Name" type="text" class="p-1 w-100 w-full shadow"/>
              </td>
              <td class="border border-slate-700 text-center p-1">
                <input v-model="row.id" placeholder="ID" type="text" class="p-1 w-100 w-full shadow"/>
              </td>
              <td class="border border-slate-700 text-center p-1">
                <input v-model="row.unit" placeholder="Unit" type="text" class="p-1 w-100 w-full shadow"/>
              </td>
              <td class="border border-slate-700 text-center p-1">
                <input v-model="row.co" placeholder="CO" type="text" class="p-1 w-100 w-full shadow"/>
              </td>
              <td class="border border-slate-700 text-center p-1">
                <input v-model="row.value" placeholder="Value" type="text" class="p-1 w-100 w-full shadow"/>
              </td>
              <td class="border border-slate-700 text-center p-1">
                <input v-model="row.phi" placeholder="PHI" type="text" class="p-1 w-100 w-full shadow"/>
              </td>
              <td class="border border-slate-700 text-center p-1">
                <button type="button" class="p-1 rounded text-sm border border-green-300 shadow bg-green-300 text-white hover:bg-green-400 hover:border-green-400">Show Material</button>
              </td>
              <td class="border border-slate-700 text-center p-1">
                <input v-model="row.amount" placeholder="Amount" type="text" class="p-1 w-100 w-full shadow"/>
              </td>
              <td class="border border-slate-700 text-center p-1">
                <button @click="removeRow(rowKey)" type="button" class="p-1 rounded text-sm border border-red-300 shadow bg-red-300 text-white hover:bg-red-400 hover:border-red-400">X</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="col-span-2">
        <button @click="addRow" type="button" class="p-1 w-full rounded border border-green-400 shadow bg-green-400 text-white hover:bg-green-500 hover:border-green-500">New Item</button>
      </div>
      <div class="col-span-2">
        <button @click="addDepartment" type="button" class="p-1 w-full rounded border border-blue-400 shadow bg-blue-400 text-white hover:bg-blue-500 hover:border-blue-500">New Department</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data(){
    return{
      rows: [
        {
          workName: '',
          id: '',
          unit: '',
          co: '',
          value: '',
          phi: '',
          amount: '',
        },
      ],
      departments: [],
      department: '',
    }
  },
  methods:{
    addRow(){
      this.rows.push({
        workName: '',
        id: '',
        unit: '',
        co: '',
        value: '',
        phi: '',
        amount: '',
      })
    },
    removeRow(rowKey){
      this.rows.splice(rowKey, 1)
    },
    addDepartment(){
      if(this.department!=''){
        this.departments.push(this.department)
        this.department=''
      }else{
        alert('Department name cannot be empty')
      }
    }
  }
}
</script>
