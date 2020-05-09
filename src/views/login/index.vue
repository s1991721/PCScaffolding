<template>
  <div class="login-container">
    <el-form
      :model="loginForm"
      :rules="loginRules"
      ref="loginForm"
      class="login-form"
      auto-complete="on"
      label-position="left"
    >
      <div class="title-container">
        <h3 class="title">Login Form</h3>
      </div>

      <el-form-item prop="account">
        <span class="svg-container">
          <svg-icon icon-class="user" />
        </span>

        <el-input
          ref="account"
          type="text"
          v-model="loginForm.account"
          placeholder="Account"
          auto-complete="on"
          name="account"
          tabindex="1"
        ></el-input>
      </el-form-item>
      <el-form-item label="密码" prop="password">
        <el-input
          ref="password"
          :type="passwordType"
          v-model="loginForm.password"
          placeholder="Password"
          autocomplete="on"
          name="password"
          tabindex="2"
          @keyup.enter.native="login"
        ></el-input>
      </el-form-item>

      <el-button
        :loading="loading"
        type="primary"
        style="width:100%;margin-bottom:30px;"
        @click.native.prevent="submitForm('login')"
      >Login</el-button>
      <!-- @click.native.prevent 用来阻止默认行为 -->
    </el-form>
  </div>
</template>

<script>
export default {
  name: "Login", //组件名
  data() {
    const validateAccount = (rule, value, callback) => {};
    const validatePassword = (rule, value, callback) => {};

    return {
      loginForm: {
        account: "Account",
        password: "Password"
      },
      loginRules: {
        account: [
          { required: true, trigger: "blur", validator: validateAccount }
        ],
        password: [
          { required: true, trigger: "blur", validator: validatePassword }
        ]
      },
      loading: false,
      passwordType: "password"
    };
  },
  methods: {
    login() {}
  }
};
</script>

<style lang="scss" scoped>
$bg: #2d3a4b;
$light_gray: #fff;
$dark_gray: #889aa4;
$cursor: #fff;

.login-container {
  background-color: $bg;
  min-height: 100%;
  width: 100%;

  .el-input {//高度设置后才和svg左右显示
    height: 47px;
    width: 85%;

  }

  .el-form-item{
    border: 1px solid rgba(255, 255, 255, 0.1);
    background: rgba(0, 0, 0, 0.1);
    border-radius: 5px;
    color: #454545;
  }
}

.login-form {
  width: 520px;
  padding: 160px 35px 0; //手动设置垂直居中  方向：上右下左
  margin: 0 auto; //横向居中 0代表上下
  position: relative;
}

.login-container {
  position: relative;
  min-height: 100%;
  width: 100%;
  background-color: $bg;
  overflow: hidden;

  .title {
    font-size: 26px;
    color: $light_gray;
    margin: 0px auto 40px auto auto;
    text-align: center;
    font-weight: bold;
  }
}

.svg-container {
  padding: 6px 5px 6px 15px;
  color: $dark_gray;
  vertical-align: middle;
  width: 30px;
  display: inline-block;
}

.el-form-item {
  border: 1px solid rgba(255, 255, 255, 0.1);
  background: rgba(0, 0, 0, 0.1);
  border-radius: 5px;
  color: #454545;
}
</style>
