<template>
  <div class="root-element"> 
      <img src="../assets/timg.jpg" alt="妙智旅行">
  <el-form :model="ruleForm2" :rules="rules2" ref="ruleForm2" label-position="left" label-width="0px" class="demo-ruleForm login-container">

    <h3 class="title">我的世界</h3>
    <el-form-item prop="account">
      <el-input type="text" v-model="ruleForm2.account" auto-complete="off" placeholder="账号"></el-input>
    </el-form-item>
    <el-form-item prop="checkPass">
      <el-input type="password" v-model="ruleForm2.checkPass" auto-complete="off" placeholder="密码"></el-input>
    </el-form-item>
    <el-checkbox v-model="checked" checked class="remember">记住密码</el-checkbox>
    <el-form-item style="width:100%;">
      <el-button type="primary" style="width:100%;" @click.native.prevent="handleSubmit2" :loading="logining">登录</el-button>
      <!--<el-button @click.native.prevent="handleReset2">重置</el-button>-->
    </el-form-item>
  </el-form>
  </div>
</template>

<script>
  import logoSrc from '../assets/avatar.jpg'
  //import NProgress from 'nprogress'
  export default {
    created(){
      // console.log(logoSrc)
      
    },
    mounted() {
      console.log('this is home --->', this.$router)
    },
    data() {
      return {
        logining: false,
        ruleForm2: {
          account: 'admin',
          checkPass: '123456'
        },
        rules2: {
          account: [
            { required: true, message: '请输入账号', trigger: 'blur' },
            //{ validator: validaePass }
          ],
          checkPass: [
            { required: true, message: '请输入密码', trigger: 'blur' },
            //{ validator: validaePass2 }
          ]
        },
        checked: true
      };
    },
    methods: {
      handleReset2() {
        this.$refs.ruleForm2.resetFields();
      },
      handleSubmit2(ev) {
        if (this.ruleForm2.account=='admin'&&this.ruleForm2.checkPass=='123456') {
          let user = {
            id: 1,
            username: 'admin',
            password: '123456',
            avatar: logoSrc,
            name: '程某某'
          }
          sessionStorage.setItem('user', JSON.stringify(user));
          console.log(this.$router)
          sessionStorage.setItem('router', JSON.stringify(this.$router.options.routes[2].children));
          this.$router.push({ path: '/page6' });
        }
        
        // var _this = this;
        // this.$refs.ruleForm2.validate((valid) => {
        //   if (valid) {
        //     //_this.$router.replace('/table');
        //     this.logining = true;
        //     //NProgress.start();
        //     var loginParams = { username: this.ruleForm2.account, password: this.ruleForm2.checkPass };
        //     console.log(requestLogin)
        //     requestLogin(loginParams).then(data => {
        //       this.logining = false;
        //       //NProgress.done();
        //       let { msg, code, user } = data;
        //       if (code !== 200) {
        //         this.$message({
        //           message: msg,
        //           type: 'error'
        //         });
        //       } else {
        //         sessionStorage.setItem('user', JSON.stringify(user));
        //         this.$router.push({ path: '/main' });
        //       }
        //     });
        //   } else {
        //     console.log('error submit!!');
        //     return false;
        //   }
        // });
      }
    }
  }

</script>

<style lang="scss" scoped>
  .el-checkbox{
    color: #fff;
  }
  .login-container {
    /*box-shadow: 0 0px 8px 0 rgba(0, 0, 0, 0.06), 0 1px 0px 0 rgba(0, 0, 0, 0.02);*/
    -webkit-border-radius: 5px;
    border-radius: 5px;
    -moz-border-radius: 5px;
    background-clip: padding-box;
    margin: 180px auto;
    width: 350px;
    padding: 35px 35px 15px 35px;
    background: #fff;
    border: 1px solid #eaeaea;
    box-shadow: 0 0 25px #cac6c6;
    background-color: #000;
    opacity: 0.5;
    .title {
      margin: 0px auto 40px auto;
      text-align: center;
      color: #fff;
    }
    .remember {
      margin: 0px 0px 35px 0px;
    }
  }
  .root-element{
    position: absolute; 
    bottom: 0;
    top: 0;
    width: 100%;
    /*height: 100%; */
    img{
      position: absolute; 
      width: 100%;
      height: 100%;  
      -webkit-user-drag:none;
    }
    .el-form{
        position:absolute;
        top: 10%; 
        left: 84%;  
        margin-left: -211px;
    }

  }
</style>