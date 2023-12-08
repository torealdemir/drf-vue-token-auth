<template>
    <div class="sign-up">
        <h1>Sign up</h1>
        <form v-on:submit.prevent="submitForm">
            <input type="email" name="username" v-model="username">
            <input type="password" name="password" v-model="password">
            <button type="submit">SignUp!</button>

        </form>
    </div>
</template>

<script>
import { toHandlers } from 'vue';
import axios from 'axios';

export default {
    name: 'SignUp',
    data(){
        return {
            username:'',
            password:''
        }
    },
    methods: {
        submiForm(e){
            const formData = {
                username: this.username,
                password: this.password
            }
            axios.post('/api/v1/users/', formData).then(response =>{
                this.$router.push('/log-in')
                console.log(response)
            }).catch(error => {
                console.log(error)
            })
        }
    }
}

</script>