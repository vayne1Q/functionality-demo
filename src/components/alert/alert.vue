<template>
  <transition name="fade">
    <div v-show="show" class="message" :class="type">
      <i class="icon" />
      <span class="text">{{ text }}</span>
    </div>
  </transition>
</template>
<script>

export default {
  name: 'Alert',
  props: {
    type: {
      type: String,
      default: 'info',
      validator: val => ['info', 'success', 'warning', 'error'].includes(val)
      // ['info', 'success', 'warning', 'error'] 表示type只接收这四个字符串作为参数传入message组件
    },
    text: {
      type: String,
      default: ''
    },
    show: {
      type: Boolean,
      default: false
    }
  }
}
</script>
<style lang="scss">
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity .3s
  }

  .fade-enter,
  .fade-leave-to {
    opacity: 0
  }

  .message {
    position:fixed;
    top: 40px;
    text-align: center;
    left: 50%;
    transform: translateX(-50%);
    min-width: 400px;
    padding: 10px 20px;
    background: #f5f5f5;
    font-size: 14px;
    line-height: 1.4;
    border-radius: 4px;
    z-index: 1000;
    box-shadow: 0 0 10px rgba(0, 0, 0, .3);
    &.info {
      color: #000;
    }
    &.success {
      color: #67C23A;
    }
    &.error {
      color: #F56C6C;
    }
    &.warning {
      color: #E6A23C;
    }
  }

</style>
