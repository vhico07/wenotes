<template>
    <div>
        <ul>
            <li v-for="(row, index) in notes" :key="index">
                <button class="btn-note" @click="editNote(row.id)">
                    <label>{{ row.title }}</label>
                    <span>{{ row.description }}</span>
                </button>
            </li>
        </ul>
    </div>
</template>

<script type="text/javascript">

    export default {
       name: 'listNotes',
       data: function () {
           return {
                notes : [{ id:1, title: 'wenote', description: 'Ini isi wenotes' }, { id:2,  title: 'Super user', description: 'Ini isi super user'  }] //{ id:1, title: 'wenote', description: 'Ini isi wenotes' }, { id:2,  title: 'Super user', description: 'Ini isi super user'  }
           }
       },
        props: {
            propNotes : {
                type: Array
            },
            propEditNote : {
                type: Function
            }
        },
        methods:{
            editNote(id){
                let dataForm = this.notes.find(note => note.id === id);
                this.$root.$emit('emitForm', dataForm);
            },
        }
    }
</script>

<style>
ul {
    list-style-type: none;
    padding: 0;
    margin:0px;
}
.btn-note {
    text-align: left;
    border: none;
    border-bottom: 1px solid gainsboro;
    padding: 0px 15px;
    cursor: pointer;
    outline: none;
    background: #f7f7f7;
    height: 150px;
    width: 100%;
}
.btn-note:hover {
    background:#eaeaea;
}
.btn-note label{
    display:block;
    color: #444444;
    font-size: 1.5em;
    margin-bottom: 15px;
}
.btn-note span{
   color: #545454;
}
</style>
