<template lang="html">
    <div>
        <h1>{{ product.title }}</h1>
        <div class="ps-product__meta">
            <p>
                Brand:
                <nuxt-link to="/shop">
                    <a class="ml-2 text-capitalize">
                        <!-- {{ product.vendor }} -->
                        <!-- {{ product.name }} -->
                    </a>
                </nuxt-link>
            </p>
            <div class="ps-product__rating">
                <rating />
                <span>(1 review)</span>
            </div>
        </div>
        <h4 class="ps-product__price sale">
            <del class="mr-2" v-if="product.price"> {{ currency }} {{ Number.parseFloat(product.price).toFixed(2) }}</del>
             {{ currency }} {{ Number.parseFloat(product.selling_price).toFixed(2) }}
        </h4>
        <!-- <h4 v-if="!product.variants" class="ps-product__price sale">
            <del class="mr-2" v-if="product.price"> {{ currency }} {{ Number.parseFloat(product.price).toFixed(2) }}</del>
             {{ currency }} {{ Number.parseFloat(product.selling_price).toFixed(2) }}
        </h4> -->
        <!-- <h4 v-else class="ps-product__price sale">
            <del class="mr-2" v-if="product.variants[0].price"> {{ currency }} {{ Number.parseFloat(product.variants[0].price).toFixed(2) }}</del>
            {{ currency }} {{ Number.parseFloat(product.variants[0].selling_price).toFixed(2) }}
        </h4> -->
    </div>
</template>

<script>
import Rating from '~/components/elements/Rating';
import { mapState } from 'vuex';

export default {
    name: 'ModuleProductInfo',
    components: { Rating },
    props: {
        product: {
            type: Object,
            default: () => {}
        }
    },
     computed: {
        ...mapState({
            currency: state => state.app.currency
        }),
    },
};
</script>

<style lang="scss" scoped></style>
