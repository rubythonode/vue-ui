<template>
  <div id="app">
    <layout>
      <div class="content-section introduction" id="component">
        <div>
          <span class="feature-title">Captcha</span>
          <span>Captcha is a form validation component based on Recaptcha.</span>
        </div>
      </div>
      <div id="wrapper">

        <h2>Features</h2>

        <h3>1. Basic</h3>

        <p>Captcha is used with a siteKey and a callback to verify the response..</p>

        <vueui-captcha siteKey="6Lf2XQkTAAAAANcvOwYqPxWL4iZDksFqHpS39GDA" ></vueui-captcha>

        <h3>2. Verification</h3>

        <p>To ensure if a response token is valid then verification against recaptcha api needs to be done at backend using onResponse event.</p>
        <p v-if="verified">The verification is successful</p>

        <vueui-captcha siteKey="6Lf2XQkTAAAAANcvOwYqPxWL4iZDksFqHpS39GDA" @response="showResponse($event)"></vueui-captcha>

        <h3>3. Expiration</h3>

        <p>The recaptcha response expires and the user needs to solve a new CAPTCHA acknowledge by onExpire event.</p>

        <vueui-captcha siteKey="6Lf2XQkTAAAAANcvOwYqPxWL4iZDksFqHpS39GDA" @expire="onExpire($event)"></vueui-captcha>
        <p v-if="expired">The captcha is expired</p>

      </div>
    </layout>
  </div>
</template>
<script>
  import Layout from "../layout";
  let verified = false;
  let expired = false;
  export default {
    name: 'captchademo',
    components: {Layout},
    data: function () {
      return {verified, expired}

    },
    methods: {
      showResponse: function (event) {
        this.verification = true;
      },
      onExpire: function (event) {
        this.expired = true;
      }
    }
  };
</script>

