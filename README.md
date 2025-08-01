# SAFINA_birthday2
to the birthday safina
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Happy Birthday, Safina! 🎂</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      background: linear-gradient(to right, #ffe6f0, #e6f9ff);
      font-family: 'Courier New', monospace;
      overflow: hidden;
      height: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }

    h1 {
      font-size: 48px;
      color: #d63384;
      animation: glow 1s ease-in-out infinite alternate;
      text-align: center;
      z-index: 2;
    }

    @keyframes glow {
      from { text-shadow: 0 0 10px #f78fcd; }
      to { text-shadow: 0 0 20px #d63384; }
    }

    .heart {
      font-size: 80px;
      cursor: pointer;
      color: red;
      animation: beat 1s infinite alternate;
      z-index: 2;
    }

    @keyframes beat {
      from { transform: scale(1); }
      to { transform: scale(1.3); }
    }

    .message {
      display: none;
      font-size: 20px;
      color: #333;
      margin-top: 30px;
      max-width: 80%;
      text-align: center;
      z-index: 2;
      background-color: rgba(255,255,255,0.8);
      padding: 20px;
      border-radius: 12px;
    }

    .signature {
      margin-top: 40px;
      font-size: 18px;
      color: #444;
      z-index: 2;
    }

    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: 1;
    }
  </style>
</head>
<body>

  <canvas id="canvas"></canvas>

  <div class="heart" onclick="showMessage()">❤</div>
  <h1>Happy Birthday to You, Safina!</h1>

  <div class="message" id="hiddenMessage">
    💌 <strong>Сафина, с днём рождения, моя дорогая подруга!</strong><br><br>

    🎉 Пусть этот день будет таким же прекрасным, как ты сама!<br><br>

    🌸 Ты — невероятная, сильная и добрая. Ты умеешь поддерживать, вдохновлять и делать день особенным для всех, кто рядом.<br><br>

    💻 Я хочу, чтобы твоя жизнь была как идеально работающий код — без ошибок, без багов, и с бесконечным циклом счастья.<br><br>

    🚀 Пусть твои мечты сбываются со скоростью света! Пусть рядом будут только настоящие и тёплые люди, которые поддержат тебя в любой момент.<br><br>

    🌈 Я очень горжусь, что ты моя подруга. Спасибо тебе за всё!<br><br>

    🎂 С днём рождения, Сафина! Люблю тебя без комментариев и без условий! 💖
  </div>

  <div class="signature">— Твоя подруга 💕</div>

  <script>
    function showMessage() {
      document.getElementById("hiddenMessage").style.display = "block";
    }

    // 🎆 Fireworks
    const canvas = document.getElementById('canvas');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const particles = [];

    function random(min, max) {
      return Math.random() * (max - min) + min;
    }

    function createFirework(x, y) {
      const count = 100;
      for (let i = 0; i < count; i++) {
        particles.push({
          x: x,
          y: y,
          angle: Math.random() * 2 * Math.PI,
          speed: random(2, 6),
          radius: 2,
          alpha: 1,
          decay: random(0.01, 0.03),
          color: hsl(${Math.floor(Math.random() * 360)}, 100%, 60%)
        });
      }
    }

    function updateParticles() {
      for (let i = particles.length - 1; i >= 0; i--) {
        const p = particles[i];
        p.x += Math.cos(p.angle) * p.speed;
        p.y += Math.sin(p.angle) * p.speed;
        p.alpha -= p.decay;
        if (p.alpha <= 0) {
          particles.splice(i, 1);
        }
      }
    }

    function drawParticles() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      particles.forEach(p => {
        ctx.globalAlpha = p.alpha;
        ctx.beginPath();
        ctx.arc(p.x, p.y, p.radius, 0, 2 * Math.PI);
        ctx.fillStyle = p.color;
        ctx.fill();
      });
    }

    function loop() {
      updateParticles();
      drawParticles();
      requestAnimationFrame(loop);
    }

    setInterval(() => {
      createFirework(random(100, canvas.width - 100), random(100, canvas.height - 100));
    }, 800);

    loop();
  </script>

</body>
</html>
