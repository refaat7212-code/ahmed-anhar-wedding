<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Countdown</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: Arial, sans-serif;
      background: linear-gradient(135deg, #111827, #374151);
      color: white;
      text-align: center;
    }

    .container {
      width: 90%;
      max-width: 600px;
      padding: 35px 20px;
      border-radius: 25px;
      background: rgba(255,255,255,0.08);
      backdrop-filter: blur(10px);
      box-shadow: 0 10px 40px rgba(0,0,0,0.35);
    }

    h1 {
      font-size: 32px;
      margin-bottom: 12px;
    }

    .date {
      font-size: 20px;
      margin-bottom: 30px;
      opacity: 0.9;
    }

    .countdown {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 12px;
    }

    .box {
      background: rgba(255,255,255,0.12);
      padding: 18px 8px;
      border-radius: 15px;
    }

    .number {
      font-size: 32px;
      font-weight: bold;
      display: block;
    }

    .label {
      font-size: 14px;
      margin-top: 5px;
      opacity: 0.8;
    }

    #message {
      margin-top: 25px;
      font-size: 22px;
      font-weight: bold;
    }

    @media (max-width: 500px) {
      h1 {
        font-size: 26px;
      }

      .countdown {
        gap: 7px;
      }

      .number {
        font-size: 25px;
      }

      .label {
        font-size: 12px;
      }
    }
  </style>
</head>

<body>

  <div class="container">
    <h1>🎉 العد التنازلي 🎉</h1>

    <div class="date">
      السبت 26 سبتمبر 2026
    </div>

    <div class="countdown">
      <div class="box">
        <span class="number" id="days">0</span>
        <span class="label">يوم</span>
      </div>

      <div class="box">
        <span class="number" id="hours">0</span>
        <span class="label">ساعة</span>
      </div>

      <div class="box">
        <span class="number" id="minutes">0</span>
        <span class="label">دقيقة</span>
      </div>

      <div class="box">
        <span class="number" id="seconds">0</span>
        <span class="label">ثانية</span>
      </div>
    </div>

    <div id="message"></div>
  </div>

  <script>
    // موعد الفرح: السبت 26/9/2026 الساعة 5 مساءً
    const weddingDate = new Date("September 26, 2026 17:00:00").getTime();

    function updateCountdown() {
      const now = new Date().getTime();
      const distance = weddingDate - now;

      if (distance <= 0) {
        document.getElementById("days").textContent = "0";
        document.getElementById("hours").textContent = "0";
        document.getElementById("minutes").textContent = "0";
        document.getElementById("seconds").textContent = "0";

        document.getElementById("message").textContent =
          "🎊 اليوم هو يوم الفرح! ❤️";

        return;
      }

      const days = Math.floor(distance / (1000 * 60 * 60 * 24));
      const hours = Math.floor(
        (distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
      );
      const minutes = Math.floor(
        (distance % (1000 * 60 * 60)) / (1000 * 60)
      );
      const seconds = Math.floor(
        (distance % (1000 * 60)) / 1000
      );

      document.getElementById("days").textContent = days;
      document.getElementById("hours").textContent = hours;
      document.getElementById("minutes").textContent = minutes;
      document.getElementById("seconds").textContent = seconds;
    }

    updateCountdown();
    setInterval(updateCountdown, 1000);
  </script>

</body>
</html>
