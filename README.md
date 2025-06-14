# barisalimmimedine
<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Barışalım mı?</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      overflow: hidden;
      font-family: 'Segoe UI', sans-serif;
      background-color: #f8f8f8;
      text-align: center;
    }

    h1 {
      font-size: 2.5em;
      margin-top: 20vh;
      color: #333;
    }

    .btn {
      font-size: 1.2em;
      padding: 10px 20px;
      margin: 20px 10px;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      z-index: 1;
    }

    #evetBtn {
      background-color: #4CAF50;
      color: white;
    }

    #hayirBtn {
      background-color: #d9534f;
      color: white;
      position: absolute;
      transition: top 0.3s ease, left 0.3s ease;
    }

    #message {
      display: none;
      font-size: 1.5em;
      color: #fff;
      padding: 20px;
      position: relative;
      z-index: 2;
    }

    .heart {
      position: absolute;
      color: red;
      animation: float 4s linear infinite;
      opacity: 0.8;
      pointer-events: none;
    }

    @keyframes float {
      0% { transform: translateY(0) scale(1); opacity: 1; }
      100% { transform: translateY(-800px) scale(1.5); opacity: 0; }
    }
  </style>
</head>
<body>
  <h1 id="title">Barışalım mı?</h1>
  <button id="evetBtn" class="btn">Evet</button>
  <button id="hayirBtn" class="btn">Hayır</button>
  <div id="message">Her şey için özür dilerim.<br>Barışmak istiyorum.<br>Seni çok seviyorum ❤️</div>

  <script>
    const evetBtn = document.getElementById("evetBtn");
    const hayirBtn = document.getElementById("hayirBtn");
    const title = document.getElementById("title");
    const message = document.getElementById("message");

    let evetBasildi = false;

    // İlk konumlandırma
    function centerButtons() {
      hayirBtn.style.top = "60vh";
      hayirBtn.style.left = "50vw";
    }
    centerButtons();

    // Hayır kaçma
    hayirBtn.addEventListener("touchstart", moveButton);
    hayirBtn.addEventListener("mouseover", moveButton);

    function moveButton() {
      if (!evetBasildi) {
        const maxX = window.innerWidth - hayirBtn.offsetWidth;
        const maxY = window.innerHeight - hayirBtn.offsetHeight;
        const randomX = Math.random() * maxX;
        const randomY = Math.random() * maxY;
        hayirBtn.style.left = `${randomX}px`;
        hayirBtn.style.top = `${randomY}px`;
      }
    }

    // Evet basılınca
    evetBtn.addEventListener("click", () => {
      evetBasildi = true;
      document.body.style.background = "linear-gradient(to bottom, #ff9aa2, #ffdde1)";
      title.style.display = "none";
      evetBtn.style.display = "none";
      hayirBtn.style.display = "none";
      message.style.display = "block";

      // Kalpler
      for (let i = 0; i < 40; i++) {
        const heart = document.createElement("div");
        heart.classList.add("heart");
        heart.innerHTML = "❤️";
        heart.style.left = Math.random() * window.innerWidth + "px";
        heart.style.top = Math.random() * window.innerHeight + "px";
        heart.style.fontSize = `${Math.random() * 20 + 20}px`;
        document.body.appendChild(heart);
      }
    });
  </script>
</body>
</html>
