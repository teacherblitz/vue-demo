<template>
  <el-container>
    <el-header>登录</el-header>
    <el-main>
      <img class="login-logo" src="@/assets/logo.jpg"/>
      <el-form :label-position="labelPosition" :model="ruleForm" :rules="rules" ref="ruleForm" label-width="80px" class="ruleForm">
        <el-form-item label="账号" prop="username">
          <el-input v-model="ruleForm.username" maxlength="11" placeholder="请输入账号"></el-input>
        </el-form-item>
        <el-form-item label="密码" prop="pwd">
          <el-input v-model="ruleForm.pwd" placeholder="请输入密码" show-password></el-input>
        </el-form-item>
        <el-button class="login" type="primary" @click="submitForm('ruleForm')" round>提交</el-button>
      </el-form>
    </el-main>
    <el-footer>
      <div style="display: inline;">
        <el-link disabled>©2020 teacherblitz.com 粤ICP备19112819号-1</el-link>
        <el-link href="http://www.beian.miit.gov.cn" type="primary" target="_blank">粤ICP备19112819号</el-link>
      </div>
    </el-footer>
  </el-container>
</template>

<script>
  export default {
    name: 'login',
    data () {
      return {
        labelPosition: 'left',
        msg: '本APP为个人博客',
        ruleForm: {
          username: '',
          pwd: ''
        },
        rules: {
          username: [
            { required: true, message: '请输入账号', trigger: 'blur' }
          ],
          pwd: [
            { required: true, message: '请输入密码', trigger: 'blur'},
            { min: 6, max: 12, message: '密码长度在6-12位之间', trigger: 'blur'}
          ]
        }
      }
    },
    methods:{
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      }
    }
  }
</script>

<style>
  .login-logo{
    width: 9rem;
    height: 9rem;
    position: relative;
    left: 28%;
    border-radius: 50%;
  }
  .el-container {
    width: 100vw;
    height: 100vh;
  }
  .el-header{
    background-color: #42b983;
    color: white;
    text-align: center;
    line-height: 60px;
    width: 100%;
    height: 20%;
    font-size: 14px;
  }
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    line-height: 100px;
    margin: 5px 0 5px 0;
    width: 100%;
    height: 60%;
  }
  .el-footer {
    background-color: black;
    color: white;
    text-align: center;
    vertical-align:middle;
    width: 100%;
    height: 20%;
    position: absolute;
    bottom: 0;
  }

  body > .el-container {
    margin-bottom: 40px;
  }

  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }

  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }
  .login {
    width: 200px;
    position: relative;
    left: 22%
  }

</style>
