<template>
  <div class="fav-page box">
    <div class="title-fav py-3">
      <span class="has-text-weight-semibold is-size-6 px-4">My favorites</span>
    </div>
    <div class="d-fav-list px-4 my-3">
      <div
        v-for="(item, index) in myfav"
        :key="index"
        class="fav-list py-4 is-flex justy-between"
      >
        <ProductFav :item="item" class="profav" />
        <div class="info-fav is-flex ml-6 pr-2">
          <button
            class="button is-small is-font-size16 has-no-border btn-favv is-success is-light"
          >
            <span>Retire from the favorites</span>
          </button>
          <div
            class="add-cart is-flex justy-between mt-4"
            :class="{ 'fited-width': item.qte === 0 }"
          >
            <div
              class="is-flex-self-end"
              :class="{ 'is-flex-self-center': item.qte === 0 }"
            >
              <span
                v-if="item.qte !== 0 || item.disponibility !== null"
                class="buttonss btn-available is-size-6 has-text-weight-semibold"
              >
                In stock
              </span>
              <span
                v-else-if="item.disponibility === null"
                class="buttonss btn-unavailable is-size-6 has-text-weight-semibold"
              >
                Sold out
              </span>
            </div>
            <div v-if="item.qte !== 0" class="field">
              <div class="control is-flex is-col-flex">
                <label
                  class="is-block is-size-6 has-text-weight-semibold pb-1"
                  for="qty"
                  >Quantity (Kilo)</label
                >
                <input
                  id="qty"
                  class="input qte is-block is-flex-self-end"
                  type="number"
                  min="0"
                  placeholder="Qty"
                />
              </div>
            </div>
          </div>
          <div v-if="item.qte !== 0" class="add-cart-btn mt-5 is-flex-self-end">
            <button class="button is-small is-font-size16 btnbtn btn-subscribe">
              <client-only>
                <span class="icon">
                  <i class="fas fa-shopping-cart"></i>
                </span>
              </client-only>
              <span>Add to cart</span>
            </button>
          </div>
          <div
            v-else-if="item.disponibility !== null"
            class="add-cart-btn mt-5 is-flex-self-end"
          >
            <button class="button is-small is-font-size16 btnbtn btn-subscribe">
              <client-only>
                <span class="icon">
                  <i class="fas fa-shopping-basket"></i>
                </span>
              </client-only>
              <span>Pre-order</span>
            </button>
          </div>
          <div v-if="item.qte !== 0" class="add-cart-btn-add mt-5 m-centered">
            <button
              class="button is-small is-font-size16 btnbtn btn-subscribes"
            >
              <client-only>
                <span class="icon">
                  <i class="fas fa-shopping-bag"></i>
                </span>
                <span>Go to cart to order</span>
                <span class="icon">
                  <i class="fas fa-arrow-circle-right"></i>
                </span>
              </client-only>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    myfav() {
      return this.$store.state.myFav
    },
  },
}
</script>
<style scoped>
.btn-subscribes {
  background: #004e66 !important;
  border: #004e66 !important;
  color: rgb(255, 255, 255) !important;
}
.btn-subscribes:hover,
.btn-subscribes:focus,
.btn-subscribes:active {
  background: #004e66e1 !important;
  border: #004e66e1 !important;
}
.fav-page {
  padding: 0;
  position: relative;
  top: 3rem;
  width: 100%;
  min-height: 470px;
}
.btn-favv {
  width: fit-content !important;
}
.info-fav {
  width: 100%;
  flex-direction: column;
}
.title-fav {
  width: 100%;
  border-bottom: 1px solid #d4d4d4;
  background-color: #eeeeee00;
}
.fav-list {
  width: 50%;
  border-bottom: 1px solid #e4e4e4;
  margin: 0 auto;
}
</style>

<style scoped>
.the-prod {
  flex: none;
  width: 205.2px;
  z-index: 0;
}
.fa-heart {
  font-size: 24px !important;
  color: #868686;
}
.btn-fav .icon {
  width: 32px !important;
  height: 32px !important;
  border-radius: 290486px;
}
.btn-fav .icon .fa-heart {
  width: 24px !important;
  height: 24px !important;
  border-radius: 290486px;
}
.unfilled:hover .icon .fa-heart,
.filled:hover .icon .fa-heart {
  background-color: transparent !important;
}
.unfilled:hover .icon,
.filled:hover .icon {
  box-shadow: 0 0 10px rgb(196, 196, 196);
  -webkit-box-shadow: 0 0 10px rgb(196, 196, 196);
  background-color: transparent !important;
}
.filled .fa-heart {
  font-size: 24px !important;
  color: #888888;
}
.filled .icon {
  width: 32px !important;
  height: 32px !important;
  border-radius: 290486px;
}
.filled .icon .fa-heart {
  width: 24px !important;
  height: 24px !important;
  border-radius: 290486px;
}
.filled:hover .icon .fa-heart {
  color: #949494;
}
.btn-fav {
  position: absolute;
  z-index: 999;
  right: 0;
}
.see-post {
  color: #028300;
}
.see-post:hover {
  text-decoration: underline;
}
.products-pop {
  position: relative;
  top: 3rem;
  margin-top: 4rem;
  margin: 0 auto;
}
.wal:hover {
  color: #028300 !important;
}
.prod-img {
  width: 100% !important;
}
.prod-taille {
  flex: none;
  width: 205.2px;
  z-index: 0;
}
@media screen and (max-width: 956px) {
  .fav-list {
    width: 80%;
  }
}
@media screen and (max-width: 690px) {
  .fav-list {
    width: 100% !important;
  }
}
@media screen and (max-width: 575px) {
  .info-fav {
    margin-left: 0.5rem !important;
  }
}
@media screen and (max-width: 535px) {
  .fav-list {
    flex-direction: column;
  }
  .profav {
    width: fit-content;
    margin: 0 auto;
  }
  .info-fav {
    margin-top: 1.5rem;
  }
}
.most-card {
  padding-bottom: 0rem;
}

.db-prod {
  position: relative;
  overflow: scroll;
  overflow-x: hidden;
  z-index: 0;
}
.qte {
  width: 70px;
  height: 28px;
  font-size: 0.9rem;
}
.btn-available {
  background: #ffffff2c !important;
  border: #ffffff2c !important;
  color: #027900 !important;
}
.btn-unavailable {
  background: #ffffff2c !important;
  border: #ffffff2c !important;
  color: red !important;
}
.add-cart-btn {
  width: 65%;
}
.add-cart-btn-add {
  width: 100%;
}
.btnbtn {
  width: 100%;
}
.fa-shopping-cart {
  color: white !important;
}
.buttonss {
  -moz-appearance: none;
  -webkit-appearance: none;
  align-items: center;
  border: 1px solid transparent;
  border-radius: 4px;
  box-shadow: none;
  display: inline-flex;
  font-size: 0.9rem;
  height: 2.5em;
  justify-content: flex-start;
  line-height: 1.5;
  padding-bottom: calc(0.5em - 1px);
  padding-left: calc(0.75em - 1px);
  padding-right: calc(0.75em - 1px);
  padding-top: calc(0.5em - 1px);
  position: relative;
  vertical-align: top;
}
/* 
@media screen and (max-width: 1215px) {
  .prod-taille {
    width: 25%;
  }
}
@media screen and (max-width: 1000px) {
  .prod-taille {
    width: 25%;
  }
  .db-prod {
    width: fit-content !important;
    margin-left: 2rem;
  }
}
@media screen and (max-width: 980px) {
  .prod-taille {
    width: 33%;
  }
  .db-prod {
    width: fit-content !important;
    margin-left: -0.6rem;
  }
}
@media screen and (max-width: 798px) {
  .register-form {
    margin-top: 4rem !important;
  }
}
@media screen and (max-width: 768px) {
  .db-prod {
    display: flex !important;
  }
  .prod-taille {
    width: 33%;
  }
  .d-item {
    display: flex !important;
  }
}
@media screen and (max-width: 750px) {
  .d-item {
    flex-wrap: wrap;
  }
}
@media screen and (max-width: 700px) {
  .prod-taille {
    width: 50%;
  }
}
@media screen and (max-width: 540px) {
  .prod-taille {
    width: 80%;
  }
}
@media screen and (max-width: 380px) {
  .prod-taille {
    width: 100%;
  }
} */
.reductible {
  align-self: flex-end;
  padding: 0rem 0.3rem 0rem 0.3rem;
  background-color: rgba(2, 131, 0, 0.192);
}
.tittle {
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}
.priceold {
  text-decoration: line-through;
}
.info {
  flex-direction: column;
}
@keyframes appear {
  0% {
    transform: translateZ(10px);
  }
}
@keyframes appearZ {
  0% {
    transform: translateZ(10px);
    opacity: 0;
  }
}
</style>
