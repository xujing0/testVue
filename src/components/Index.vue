<template>
  <div>
    <table>
      <tr>
        <td>id</td>
        <td>用户名</td>
        <td>密码</td>
        <td>年龄</td>
        <td>地址</td>
      </tr>
      <tr v-for="item in users">
        <td>{{item.id}}</td>
        <td>{{item.username}}</td>
        <td>{{item.password}}</td>
        <td>{{item.age}}</td>
        <td>{{item.address}}</td>
      </tr>
    </table>
    {{msg}}
  </div>
</template>

<script>
    export default {
        name: "index",
        created() {
            const _this = this
            axios.get("http://localhost:8181/user/findAll").then(function (resp) {
                // console.log(resp);
                _this.users = resp.data;
            })
        },
        data() {
            return {
                msg: "Hello Vue",
                users: []
            }
        }
    }
</script>

<style scoped>

</style>
