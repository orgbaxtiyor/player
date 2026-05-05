# player

<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <title>Musiqa Pleyer</title>
    <style>
        body {
            background: #121212;
            color: white;
            text-align: center;
            font-family: Arial;
        }
        .player {
            margin-top: 100px;
        }
        button {
            padding: 10px 20px;
            margin: 5px;
            border: none;
            background: #1db954;
            color: white;
            font-size: 16px;
            cursor: pointer;
            border-radius: 5px;
        }
        button:hover {
            background: #17a74a;
        }
        input[type="range"] {
            width: 300px;
        }
    </style>
</head>
<body>

    <h1>🎵 Musiqa Pleyer</h1>

    <div class="player">
        <audio id="audio" src="music.mp3"></audio>

        <div>
            <button onclick="playMusic()">▶️ Play</button>
            <button onclick="pauseMusic()">⏸ Pause</button>
        </div>

        <br>

        <input type="range" id="progress" value="0">

    </div>

    <script>
        const audio = document.getElementById("audio");
        const progress = document.getElementById("progress");

        function playMusic() {
            audio.play();
        }

        function pauseMusic() {
            audio.pause();
        }

        audio.addEventListener("timeupdate", () => {
            progress.value = (audio.currentTime / audio.duration) * 100;
        });

        progress.addEventListener("input", () => {
            audio.currentTime = (progress.value / 100) * audio.duration;
        });
    </script>

</body>
</html>
