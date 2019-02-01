<template>
    <td class="text-center" v-on="!rowsSelectable ? { click: (event) => selectCheckbox(event)} : {}">
        <div class="custom-control custom-checkbox ml-2 mr-0">
          <input type="checkbox" class="custom-control-input vbt-checkbox" v-model="checkboxSelected"/>
          <span class="custom-control-indicator"></span>
        </div>
    </td>
</template>


<script>
    export default {
        name: 'CheckBox',
        props: {
            rowsSelectable: {
                type: Boolean,
                default: false
            },
            rowSelected: {
                type: Boolean,
                required: true
            }
        },
        data: function() {
            return {
                checkboxSelected:false
            }
        },
        methods: {
            selectCheckbox(event) {
                if (this.checkboxSelected) {
                    this.$emit('remove-row', event.shiftKey);
                } else {
                    this.$emit('add-row', event.shiftKey);
                }
            },
        },
        watch: {
            rowSelected(newVal,oldVal) {
                this.checkboxSelected = newVal;
            }
        }
    }
</script>

<style scoped>
.custom-control-label {
  vertical-align: top;
}

</style>
