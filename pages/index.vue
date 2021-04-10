<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        Hello Explorers
      </h1>
      <div v-for="article in articles" v-bind:key="article.id">
        <div class="">
          <NuxtLink :to="{ path: article.slug, query: {id: article.id }}">
            <h2 class="text-3xl font-medium mb-4">{{ article.title }} <span class="text-lg">{{article.date}}</span></h2>
          </NuxtLink>
          <p class="mb-8">{{ article.description }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { allArticlesQuery } from "~/graphql/queries";
export default {
  data() {
    return {
      articles: [],
    };
  },
  apollo: {
    articles: {
      prefetch: true,
      query: allArticlesQuery,
    },
  },
};
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
