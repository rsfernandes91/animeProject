<template>
  <a-card title="Animes">
    <div class="animeList">
      <a-table :columns="colunas" :rowKey="anime => anime.id" :dataSource="animes">
        <template slot="genero" slot-scope="genero">
          <p>{{genero.join(", ")}}</p>
        </template>
      </a-table>
    </div>
  </a-card>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import AnimeList from "@/assets/animes.json";

const colunas = [
  {
    title: "Nome",
    dataIndex: "nome"
  },
  {
    title: "Episodios",
    dataIndex: "eps"
  },
  {
    title: "Genero",
    dataIndex: "genero",
    scopedSlots: { customRender: "genero" }
  }
];
export default {
  data() {
    return {
      animes: AnimeList,
      colunas
    };
  }
};
</script>