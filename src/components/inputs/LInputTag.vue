<template>
  <v-combobox
    v-model="inputValue"
    v-bind="$attrs"
    multiple
    chips
    deletable-chips
    outlined
    dense
    small-chips
    hide-details
    class="LInputTag"
    v-on="$listeners"
  >
    <template
      v-if="expand"
      v-slot:append-outer
    >
      <v-btn
        text
        tile
        color="primary"
        @click="clickAppendOuter"
        v-on="$attrs.iconListeners"
      >
        e+
      </v-btn>
    </template>
  </v-combobox>
</template>

<script>
export default {
  name: 'LInputTag',
  props: {
    value: {
      type: [String, Number, Array],
      default: null
    },
    expand: Boolean
  },
  computed: {
    inputValue: {
      get () {
        return this.value
      },
      set (value) {
        this.$emit('input', value)
      }
    }
  },
  methods: {
    clickAppendOuter () {
      this.$emit('clickAppendOuter')
    }
  }
}
</script>

<style lang="scss" scoped>
.LInputTag {
  ::v-deep {
    @extend .commonInput;
    @extend .commonCombobox;
  }
}
</style>
