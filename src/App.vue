<template>
    <button @click="createAudio">
        {{ message }}
    </button>
    <button @click="startAudio">
        {{ start }}
    </button>
    <div id="audio-div">
    </div>
    <audio controls id="over" >
      <source src="https://p.scdn.co/mp3-preview/0ba9d38f5d1ad30f0e31fc8ee80c1bebf0345a0c" type="audio/mpeg">
    </audio>
</template>

<script>
export default {
  data () {
    return {
      message: 'Audio生成',
      start: 'Audio再生',
    }
  },
  methods: {
    createAudio() {
      const audioDiv = document.getElementById('audio-div')
      var audio = document.createElement('audio')
      var source = document.createElement('source')
      audio.appendChild(source)
      audio.controls = true
      source.setAttribute('src', './Over_Night.mp3');
      source.setAttribute('type', 'audio/mpeg');
      
      console.log('create audio')
      audio.className = 'audio'
      audioDiv.appendChild(audio)

      audio.addEventListener('ended', () => {
        console.log('end')
        audio.remove();
      });

      audio.addEventListener('click', () => {
        if (audio.paused) {
          console.log('play')
          audio.play();
        } else {
          console.log('pause')
          audio.pause();
        }
      });

    },
    startAudio() {
      console.log('start')
      const audio = document.getElementById('over')

      console.log(audio)
      if (audio.paused) {
          console.log('play')
          audio.play();
        } else {
          console.log('pause')
          audio.pause();
        }

      audio.addEventListener('ended', () => {
        console.log('end')
        audio.remove();
      });

      audio.addEventListener('click', () => {
        if (audio.paused) {
          console.log('play')
          audio.play();
        } else {
          console.log('pause')
          audio.pause();
        }
      });
    }
  },
}
</script>

<style scoped>
  .audio {
    width: 100px;
    height: 100px;
    background-color: red;
  }
</style>