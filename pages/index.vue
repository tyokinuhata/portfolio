<template>
  <div>
    <Nav></Nav>
    <main class="contents">
      <About></About>
      <Skills></Skills>
      <Histories></Histories>
      <Certifications></Certifications>
    </main>
  </div>
</template>

<script>
  import Nav from '~/components/Nav.vue';
  import About from '~/components/About.vue';
  import Skills from '~/components/Skills.vue';
  import Histories from '~/components/Histories.vue';
  import Certifications from '~/components/Certifications.vue';

  export default {
    data() {
      return {
        commands: '',
      }
    },
    components: {
      Nav,
      About,
      Skills,
      Histories,
      Certifications,
    },
    mounted() {
      this.nikuman();
      this.konamiCommand();
    },
    methods: {
      konamiCommand() {
        document.addEventListener('keydown', event => {
          if (event.key === 'ArrowUp') {
            this.commands += '上';
          }
          else if (event.key === 'ArrowDown') {
            this.commands += '下';
          }
          else if (event.key === 'ArrowLeft') {
            this.commands += '左';
          }
          else if (event.key === 'ArrowRight') {
            this.commands += '右';
          }
          else if (event.key === 'A') {
            this.commands += 'A';
          }
          else if (event.key === 'B') {
            this.commands += 'B';
          }
          else if (event.key !== 'Shift') {
            this.commands = '';
          }

          if (this.commands.length > 10) {
            this.commands = this.commands.slice(1);
          }

          if (this.commands === '上上下下左右左右BA') {
            this.$router.push('/majime');
          }
        });
      },
      nikuman() {
        console.log('肉まんを...憎まんでください...')
      },
    }
  }
</script>

<style lang="scss">
  @import '~assets/scss/_mixin.scss';
  @import '~assets/scss/_base.scss';

  .contents {
    height: 100vh;
    overflow: scroll;
    scroll-behavior: smooth;
  }
</style>
