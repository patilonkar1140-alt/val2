<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Valentine 💖</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', sans-serif;
    }

    body {
      height: 100vh;
      background: radial-gradient(circle at top, #ff9a9e, #ff4d6d);
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
    }

    .card {
      background: rgba(255,255,255,0.95);
      padding: 45px 30px;
      border-radius: 24px;
      text-align: center;
      box-shadow: 0 20px 40px rgba(0,0,0,0.25);
      width: 90%;
      max-width: 420px;
      z-index: 5;
    }

    h1 {
      color: #ff2f68;
      margin-bottom: 30px;
      font-size: 28px;
    }

    .buttons {
      position: relative;
      height: 170px;
    }

    button {
      position: absolute;
      padding: 15px 34px;
      font-size: 18px;
      border-radius: 40px;
      border: none;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    #yes {
      background: linear-gradient(135deg, #ff4d6d, #ff85a1);
      color: white;
      left: 50%;
      transform: translateX(-50%);
      box-shadow: 0 0 20px rgba(255,77,109,0.8);
    }

    #no {
      background: #f1f1f1;
      color: #444;
      left: 50%;
      top: 90px;
      transform: translateX(-50%);
    }

    /* Floating emojis */
    .heart {
      position: fixed;
      bottom: -30px;
      animation: float 7s linear forwards;
      pointer-events: none;
      filter: drop-shadow(0 0 10px rgba(255,255,255,0.8));
    }

    @keyframes float {
      0% { transform: translateY(0) scale(0.8) rotate(0deg); opacity: 1; }
      100% { transform: translateY(-130vh) scale(2.2) rotate(360deg); opacity: 0; }
    }

    /* Bubbles */
    .bubble {
      position: fixed;
      bottom: -50px;
      width: 40px;
      height: 40px;
      background: rgba(255,255,255,0.25);
      border-radius: 50%;
      animation: bubble 12s linear forwards;
      pointer-events: none;
      backdrop-filter: blur(6px);
    }

    @keyframes bubble {
      to { transform: translateY(-140vh); opacity: 0; }
    }

    /* Final screen */
    .final {
      position: fixed;
      inset: 0;
      background: radial-gradient(circle, #ff85a1, #ff165d);
      display: none;
      justify-content: center;
      align-items: center;
      text-align: center;
      color: white;
      z-index: 10;
      flex-direction: column;
    }

    .final h2 {
      font-size: 34px;
      margin-bottom: 10px;
    }

    .final p {
      font-size: 20px;
    }
  </style>
</head>
<body>

  <!-- Music -->
  <audio autoplay loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
  </audio>

  <div class="card">
    <h1>Gargi Will you be my Valentine?</h1>
    <div class="buttons">
      <button id="yes">Yes</button>
      <button id="no">No</button>
    </div>
  </div>

  <div class="final" id="final">
    <h2>Gargi 💍💖</h2>
    <p>You are officially my Valentine 😘</p>
  </div>

  <script>
    const noBtn = document.getElementById('no');
    const yesBtn = document.getElementById('yes');
    const finalScreen = document.getElementById('final');
    let scale = 1;

    noBtn.addEventListener('mouseenter', () => {
      const box = document.querySelector('.buttons');
      noBtn.style.left = Math.random() * (box.clientWidth - 80) + 'px';
      noBtn.style.top = Math.random() * (box.clientHeight - 40) + 'px';
      scale += 0.18;
      yesBtn.style.transform = `translateX(-50%) scale(${scale})`;
    });

    yesBtn.addEventListener('click', () => {
      finalScreen.style.display = 'flex';
      for (let i = 0; i < 80; i++) createEmoji(true);
    });

    function createEmoji(isCrazy = false) {
      const el = document.createElement('div');
      const emojis = ['❤️','💖','💘','💝','💞','💕','💗','💓','💟','🩷','🫶','😘','😍'];
      el.className = 'heart';
      el.innerText = emojis[Math.floor(Math.random() * emojis.length)];
      el.style.left = Math.random() * 100 + 'vw';
      el.style.fontSize = Math.random() * 24 + 22 + 'px';
      el.style.animationDuration = (Math.random() * (isCrazy ? 2 : 3) + 4) + 's';
      document.body.appendChild(el);
      setTimeout(() => el.remove(), 8000);
    }

    function createBubble() {
      const b = document.createElement('div');
      b.className = 'bubble';
      b.style.left = Math.random() * 100 + 'vw';
      b.style.width = b.style.height = Math.random() * 40 + 20 + 'px';
      document.body.appendChild(b);
      setTimeout(() => b.remove(), 12000);
    }

    setInterval(() => createEmoji(false), 250);
    setInterval(createBubble, 800);
  </script>
</body>
</html>
