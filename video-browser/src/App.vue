<template>
    <div>
        <SearchBar @termChange='onTermChange'></SearchBar>
        <VideoList></VideoList>
    </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar'
import VideoList from './components/VideoList'
const API_KEY = 'AIzaSyC1T9NVS_vKr4iFaPMYWbLavrEUeoZ5r4k'


export default {
    name: 'App',
    components: {
        SearchBar, 
        VideoList
    },
    methods: {
        onTermChange(searchTerm) {
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(response => console.log(response))
        }
    }
}
</script>