<template>
  <div class="container">
    <div>
      <h1 class="title">
        my-todos
      </h1>
      <p class="text"><input v-model="inputData" type="text" name="content"/></p>
      <div>
        <button class="green" type="submit" @click="addTodos">
          save
        </button>
        <button class="grey" @click="findTodos">
          find
        </button>
        <button class="delete" @click="allDelete(index)">
          allDelete
        </button>
      </div>
        <div class="list">
          <ul>
            <li v-for="(item,index) in ShowName" :key="index"><p class="todotext">{{ item }}</p>
              <button class="deletebtn" @click="todoDelete(index)">削除</button>
              <p>進行状況</p>
              <form>
                <label><input type="radio" name="picked">完了</label>
                <label><input type="radio" name="picked">処理中</label>
                <label><input type="radio" name="picked">未処理</label>
              </form>
              </li>
          </ul>
        </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'

@Component({})
export default class Mytodo extends Vue {

    inputData: any = ''
    box: Array<string> = []
    flug:boolean = false

    get ShowName() {
      if (this.flug === true) {
        const serch = this.box.filter((i) => this.inputData === i)
        this.flug = false
        return serch
      }
      return this.box
    }
    addTodos() {
      console.log('ggag')
      this.box.push(this.inputData)
    }
    todoDelete(index: any) {
      this.box.splice(index, 1)
    }
    allDelete(index: any) {
      this.box = []
    }
    findTodos() {
      console.log('gg')
      this.flug = true
    }
  }
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #279993;
  letter-spacing: 1px;
  padding-bottom: 100px;
}

input[type="text"] {
  width: 20em;
  font-size: 20px;
}

.todotext {
  font-size: 25px;
}

.green {
  font-weight: bold;
  font-size: 1.4em;
  position: relative;
  top: 10px;
}
.grey {
  font-weight: bold;
  font-size: 1.4em;
  position: relative;
  top: 10px;
  left: 15px;
}
.delete {
  font-weight: bold;
  font-size: 1.4em;
  position: relative;
  top: 10px;
  left: 30px;
}

.list {
  padding-top: 30px;
}

ul {
  list-style-type: none;
}

li {
  border: solid;
  padding:  10px;
}

.deletebtn {
  font-weight: bold;
  font-size: 1.0em;
  display: block;
  margin: 0 0 0 auto;
}

</style>
