<template>
  <div class="payment-container">
    <div class="input-title">결제 금액</div>
    <div class="option-border"></div>
    <div class="pay-block">
      <div class="pay-title" :style="{ flex: 1 }">주문 금액</div>
      <div class="pay-content" :style="{ flex: 2 }">{{ this.orderPrice }} 원</div>
    </div>
    <div class="pay-block">
      <div class="pay-title" :style="{ flex: 1 }">쿠폰/적립금 할인</div>
      <div class="pay-content" :style="{ flex: 2 }">{{ this.discount }} 원</div>
    </div>
    <div class="option-border"></div>
    <div class="pay-block">
      <div class="pay-title" :style="{ flex: 1 }">총 결제금액</div>
      <div class="pay-content-bold" :style="{ flex: 2 }">{{ this.totalPrice }} 원</div>
    </div>

  </div>
</template>
<script>
import store from '@/store';
export default {
  data() {
    return{
      orderPrice : store.state.surveyOption.price,
      discount : 0,
      totalPrice : store.state.surveyOption.price
    }
  },

  mounted(){
  },

  method : {
    priceToString(price) {
      return price.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
    },
  }

}
</script>

<style>
.payment-container {
  display: flex;
  flex-direction: column;
  font-family: 'Noto Sans KR', sans-serif;
  margin: 30px;
  padding: 20px;
  padding-left: 30px;
  background-color: #fafafa;
  box-shadow: 0 2px 2px rgba(0, 0, 0, 0.2);
}

.pay-block {
  margin-top: 15px;
  display: flex;
  flex-direction: row;
  justify-content: left;
}

.pay-warn {
  text-align: left;
  color: gray;
  font-size: 0.7rem;
  font-weight: 500;
  margin-top: 10px;
}

.pay-title {
  text-align: left;
  margin-right: 30px;
  color: gray;
  font-size: 0.9rem;
  font-weight: 500;
}
.pay-content-bold{
  text-align: left;
  font-size: 1.1rem;
  color: #0CAE02;
  font-weight: 600;
}
.pay-content{
  text-align: left;
  font-size: 1rem;
  color: black;
  font-weight: 500;
}


</style>