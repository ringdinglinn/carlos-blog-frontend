<template>
    <nuxt-link :to="'/' + slug" class="grid">
        <div class="post-card-date-container" :style="{ animationDelay : `${nr/5 + 0.1}s` }">
            <p class="date-post-card" v-html="date"></p>
            <p class="time-post-card" v-html="time"></p>
        </div>
        <div class="post-card-container" :style="{ animationDelay : `${nr/5 + 0.1}s` }" :id="nr">
            <h3 class="id-post-card" v-html="nr"></h3>
            <h3 class="title-post-card" v-html="title"></h3>
            <p class="excerpt-post-card text-body" v-html="excerpt"></p>
        </div>
        <div class="post-card-image-container">
           <img class="post-card-image" :src="image" />
        </div>
    </nuxt-link>
</template>

<script>
    export default {
        props: [
            'nr',
            'title',
            'excerpt',
            'image',
            'date',
            'time',
            'slug'
        ]
    }
</script>

<style lang="scss">
    .post a {
        grid-column: 1 /4;
        text-decoration: none;

        &:hover{
            color: white;
            img {
                opacity: 1;
            }

            p, div {
                text-decoration: underline;
            }
        }
    }

    .post-card-container {
        grid-column:2;
        color:black;
        padding: $unit;
        padding-right: calc(2*$unit);
        display: grid;
        grid-template-columns: auto 1fr;
        grid-template-rows: auto 1fr;
        column-gap: $unit;
        opacity: 0;
        animation: 0.5s ease 0s 1 fadeIn forwards;
    }

    .post-card-image-container{
        grid-column:3;
        position: relative;
        display: flex;
    }

    .id-post-card{
        grid-row:1;
        grid-column:1;
    }

    .title-post-card{
        grid-row:1;
        grid-column:2;
    }

    .excerpt-post-card{
        grid-row:2;
        grid-column:2;
    }

    .post-card-image{
        opacity: 0;
        position: absolute;
        width:100%;
        transition: 0.3s;
    }

    .post-card-date-container{
        opacity: 0;
        grid-column: 1;
        animation: 0.5s ease 0s 1 fadeIn forwards;
    }

    @media only screen and (max-width: $mobile-res) {
        .post-card-date-container, .post-card-image-container{
            display: none;
        }

        .grid {
            grid-template-columns: 1fr !important;
        }

        .paper-bg {
            grid-column:1 !important;
            grid-row:1 !important;
        }

        .excerpt-post-card{
            display: none;
        }
    }

    @media only screen and (max-width: $tablet-max-res){
        .post-card-image-container{
            display: none;
        }
    } 

</style>