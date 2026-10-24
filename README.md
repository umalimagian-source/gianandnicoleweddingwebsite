<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Gian & Nicole — Wedding Celebration</title>
  
  <!-- Google Fonts for Luxury & Romantic Wedding Styling -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,400&family=Montserrat:wght@300;400;500;600&family=Playfair+Display:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">

  <style>
    :root {
      --burgundy: #5B1323;
      --burgundy-light: #7A1C30;
      --navy: #152238;
      --navy-light: #1E314D;
      --cream: #FAF7F2;
      --gold: #C5A059;
      --gold-light: #E0C895;
      --text-dark: #222222;
      --text-muted: #666666;
      --shadow: 0 10px 30px rgba(0,0,0,0.12);
      --transition: all 0.4s ease;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Montserrat', sans-serif;
      background-color: var(--cream);
      color: var(--text-dark);
      overflow-x: hidden;
    }

    h1, h2, h3, .font-serif {
      font-family: 'Playfair Display', serif;
    }

    .cursive {
      font-family: 'Cormorant Garamond', serif;
      font-style: italic;
    }

    /* Screen Views */
    .screen {
      min-height: 100vh;
      width: 100%;
      display: none;
      opacity: 0;
      transition: opacity 0.5s ease-in-out;
    }

    .screen.active {
      display: flex;
      flex-direction: column;
      opacity: 1;
    }

    /* --- NAVIGATION --- */
    nav {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      padding: 1.5rem 2.5rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      z-index: 100;
    }

    .nav-logo {
      font-family: 'Playfair Display', serif;
      font-size: 1.4rem;
      letter-spacing: 2px;
      color: var(--gold);
      text-decoration: none;
      font-weight: 600;
    }

    .nav-links button {
      background: transparent;
      border: 1px solid var(--gold);
      color: var(--cream);
      padding: 0.6rem 1.4rem;
      font-size: 0.85rem;
      letter-spacing: 1.5px;
      text-transform: uppercase;
      cursor: pointer;
      border-radius: 30px;
      transition: var(--transition);
      margin-left: 10px;
    }

    .nav-links button:hover {
      background: var(--gold);
      color: var(--navy);
    }

    /* --- HOME SCREEN --- */
    #home-screen {
      background: linear-gradient(135deg, rgba(21, 34, 56, 0.95), rgba(91, 19, 35, 0.92)),
                  url('https://images.unsplash.com/photo-1519741497674-611481863552?auto=format&fit=crop&w=1920&q=80') center/cover no-repeat;
      color: #fff;
      text-align: center;
      justify-content: center;
      align-items: center;
      padding: 2rem;
      position: relative;
    }

    .sub-heading {
      letter-spacing: 4px;
      text-transform: uppercase;
      font-size: 0.9rem;
      color: var(--gold-light);
      margin-bottom: 1.5rem;
    }

    .main-title {
      font-size: clamp(3rem, 7vw, 6rem);
      font-weight: 400;
      margin-bottom: 1rem;
      letter-spacing: 2px;
      color: #fff;
    }

    .main-title span {
      color: var(--gold);
      font-family: 'Cormorant Garamond', serif;
      font-style: italic;
    }

    .wedding-date-tag {
      font-size: 1.25rem;
      letter-spacing: 3px;
      margin-bottom: 3rem;
      color: rgba(255,255,255,0.85);
      border-top: 1px solid rgba(197, 160, 89, 0.4);
      border-bottom: 1px solid rgba(197, 160, 89, 0.4);
      display: inline-block;
      padding: 0.6rem 2rem;
    }

    .action-group {
      display: flex;
      flex-wrap: wrap;
      gap: 1.5rem;
      justify-content: center;
      align-items: center;
    }

    .btn-save-date {
      background-color: var(--burgundy);
      color: #fff;
      border: 1px solid var(--burgundy-light);
      padding: 1rem 2.5rem;
      font-size: 0.9rem;
      text-transform: uppercase;
      letter-spacing: 2px;
      cursor: pointer;
      border-radius: 40px;
      box-shadow: 0 5px 20px rgba(0,0,0,0.3);
      transition: var(--transition);
    }

    .btn-save-date:hover {
      background-color: var(--burgundy-light);
      transform: translateY(-3px);
      box-shadow: 0 8px 25px rgba(122, 28, 48, 0.5);
    }

    /* RSVP Clickable Logo Button */
    .rsvp-logo-btn {
      display: flex;
      align-items: center;
      gap: 10px;
      background: rgba(255, 255, 255, 0.08);
      border: 1.5px solid var(--gold);
      color: var(--gold);
      padding: 0.85rem 2rem;
      font-size: 0.9rem;
      text-transform: uppercase;
      letter-spacing: 2px;
      cursor: pointer;
      border-radius: 40px;
      backdrop-filter: blur(5px);
      transition: var(--transition);
    }

    .rsvp-logo-btn svg {
      width: 22px;
      height: 22px;
      fill: currentColor;
    }

    .rsvp-logo-btn:hover {
      background: var(--gold);
      color: var(--navy);
      transform: translateY(-3px);
      box-shadow: 0 8px 25px rgba(197, 160, 89, 0.4);
    }

    /* --- COUNTDOWN SCREEN --- */
    #countdown-screen {
      background: radial-gradient(circle at center, var(--navy-light) 0%, var(--navy) 100%);
      color: white;
      text-align: center;
      justify-content: center;
      align-items: center;
      padding: 2rem;
      position: relative;
    }

    .countdown-card {
      background: rgba(255, 255, 255, 0.03);
      border: 1px solid rgba(197, 160, 89, 0.3);
      padding: 3rem 2.5rem;
      border-radius: 20px;
      max-width: 800px;
      width: 90%;
      box-shadow: var(--shadow);
      backdrop-filter: blur(8px);
    }

    .countdown-timer-box {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 1rem;
      margin: 2.5rem 0;
    }

    .time-unit {
      background: rgba(91, 19, 35, 0.4);
      border: 1px solid rgba(197, 160, 89, 0.25);
      border-radius: 12px;
      padding: 1.5rem 0.5rem;
    }

    .time-num {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2rem, 5vw, 3.5rem);
      color: var(--gold);
      font-weight: 600;
      line-height: 1;
    }

    .time-label {
      font-size: 0.75rem;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: rgba(255, 255, 255, 0.7);
      margin-top: 0.5rem;
    }

    .back-btn {
      background: transparent;
      border: 1px solid rgba(255, 255, 255, 0.3);
      color: #fff;
      padding: 0.75rem 2rem;
      border-radius: 30px;
      cursor: pointer;
      text-transform: uppercase;
      letter-spacing: 1.5px;
      font-size: 0.8rem;
      transition: var(--transition);
      margin-top: 1rem;
    }

    .back-btn:hover {
      background: rgba(255, 255, 255, 0.1);
      border-color: #fff;
    }

    /* --- RSVP MODAL --- */
    .modal-overlay {
      position: fixed;
      inset: 0;
      background: rgba(10, 16, 26, 0.85);
      backdrop-filter: blur(6px);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      padding: 1.5rem;
    }

    .modal-overlay.active {
      display: flex;
    }

    .modal-content {
      background: var(--cream);
      border-top: 5px solid var(--burgundy);
      width: 100%;
      max-width: 520px;
      border-radius: 12px;
      padding: 2.5rem;
      position: relative;
      box-shadow: 0 20px 40px rgba(0,0,0,0.4);
      color: var(--navy);
    }

    .modal-close {
      position: absolute;
      top: 1.2rem;
      right: 1.2rem;
      background: transparent;
      border: none;
      font-size: 1.5rem;
      cursor: pointer;
      color: var(--text-muted);
    }

    .rsvp-header {
      text-align: center;
      margin-bottom: 2rem;
    }

    .rsvp-header h2 {
      font-size: 2rem;
      color: var(--burgundy);
      margin-bottom: 0.3rem;
    }

    .form-group {
      margin-bottom: 1.5rem;
    }

    .form-label {
      display: block;
      font-size: 0.85rem;
      text-transform: uppercase;
      letter-spacing: 1.5px;
      font-weight: 600;
      margin-bottom: 0.75rem;
      color: var(--navy);
    }

    /* Radio button options */
    .rsvp-options {
      display: flex;
      flex-direction: column;
      gap: 0.8rem;
    }

    .option-card {
      border: 1.5px solid #dcd7cf;
      padding: 1rem;
      border-radius: 8px;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 12px;
      transition: var(--transition);
      font-weight: 500;
      font-size: 0.95rem;
    }

    .option-card:hover {
      border-color: var(--burgundy);
      background: rgba(91, 19, 35, 0.03);
    }

    .option-card input[type="radio"] {
      accent-color: var(--burgundy);
      width: 18px;
      height: 18px;
    }

    .option-card.selected {
      border-color: var(--burgundy);
      background: rgba(91, 19, 35, 0.05);
      color: var(--burgundy);
    }

    /* Guest Name input (dynamic) */
    #name-group {
      display: none;
      animation: fadeIn 0.4s ease forwards;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(-5px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .input-field {
      width: 100%;
      padding: 0.85rem 1rem;
      border: 1.5px solid #dcd7cf;
      border-radius: 6px;
      font-size: 0.95rem;
      font-family: inherit;
      outline: none;
      transition: var(--transition);
    }

    .input-field:focus {
      border-color: var(--burgundy);
      box-shadow: 0 0 0 3px rgba(91, 19, 35, 0.15);
    }

    .btn-submit {
      width: 100%;
      background: var(--navy);
      color: white;
      border: none;
      padding: 1rem;
      border-radius: 8px;
      font-size: 0.9rem;
      text-transform: uppercase;
      letter-spacing: 2px;
      font-weight: 600;
      cursor: pointer;
      transition: var(--transition);
      margin-top: 1rem;
    }

    .btn-submit:hover {
      background: var(--burgundy);
    }

    .email-hint {
      font-size: 0.75rem;
      color: var(--text-muted);
      text-align: center;
      margin-top: 1rem;
    }

    @media (max-width: 600px) {
      .countdown-timer-box {
        grid-template-columns: repeat(2, 1fr);
      }
      .nav-logo {
        font-size: 1.1rem;
      }
    }
  </style>
</head>
<body>

  <!-- ================= TOP NAV ================= -->
  <nav>
    <a href="#" class="nav-logo" onclick="showScreen('home-screen')">G & N</a>
    <div class="nav-links">
      <button onclick="openRSVP()">RSVP</button>
    </div>
  </nav>

  <!-- ================= SCREEN 1: HOME ================= -->
  <section id="home-screen" class="screen active">
    <p class="sub-heading">We are getting married</p>
    <h1 class="main-title">Gian <span>&</span> Nicole</h1>
    <div class="wedding-date-tag">NOVEMBER 30, 2026 • 8:00 AM</div>
    
    <div class="action-group">
      <!-- Save the Date button (opens Countdown screen) -->
      <button class="btn-save-date" onclick="showScreen('countdown-screen')">
        Save the Date
      </button>

      <!-- Clickable RSVP Logo Button -->
      <button class="rsvp-logo-btn" onclick="openRSVP()" title="Click to RSVP">
        <!-- Elegant Monogram/Seal SVG Logo -->
        <svg viewBox="0 0 24 24">
          <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm-1-13h2v6h-2zm0 8h2v2h-2z"/>
        </svg>
        <span>RSVP Now</span>
      </button>
    </div>
  </section>

  <!-- ================= SCREEN 2: COUNTDOWN ================= -->
  <section id="countdown-screen" class="screen">
    <div class="countdown-card">
      <p class="sub-heading">Save The Date</p>
      <h2 style="font-size: clamp(2rem, 4vw, 3rem); margin-bottom: 0.5rem; color: #fff;">Gian & Nicole</h2>
      <p style="color: var(--gold-light); font-size: 1rem; letter-spacing: 2px;">NOVEMBER 30, 2026 AT 8:00 AM</p>

      <div class="countdown-timer-box">
        <div class="time-unit">
          <div class="time-num" id="days">00</div>
          <div class="time-label">Days</div>
        </div>
        <div class="time-unit">
          <div class="time-num" id="hours">00</div>
          <div class="time-label">Hours</div>
        </div>
        <div class="time-unit">
          <div class="time-num" id="minutes">00</div>
          <div class="time-label">Minutes</div>
        </div>
        <div class="time-unit">
          <div class="time-num" id="seconds">00</div>
          <div class="time-label">Seconds</div>
        </div>
      </div>

      <p style="color: rgba(255,255,255,0.7); font-size: 0.9rem; margin-bottom: 1.5rem;">
        Counting down the moments until we say "I do!"
      </p>

      <div style="display: flex; gap: 1rem; justify-content: center;">
        <button class="back-btn" onclick="showScreen('home-screen')">← Back to Home</button>
        <button class="rsvp-logo-btn" style="padding: 0.6rem 1.8rem;" onclick="openRSVP()">RSVP</button>
      </div>
    </div>
  </section>

  <!-- ================= RSVP MODAL ================= -->
  <div class="modal-overlay" id="rsvp-modal">
    <div class="modal-content">
      <button class="modal-close" onclick="closeRSVP()">&times;</button>
      
      <div class="rsvp-header">
        <h2>RSVP</h2>
        <p style="color: var(--text-muted); font-size: 0.85rem; letter-spacing: 1px;">Gian & Nicole's Wedding Celebration</p>
      </div>

      <form id="rsvp-form" onsubmit="handleRSVPSubmit(event)">
        <!-- Options -->
        <div class="form-group">
          <label class="form-label">Will you be attending?</label>
          <div class="rsvp-options">
            <label class="option-card" id="card-yes" onclick="selectOption('yes')">
              <input type="radio" name="attendance" value="I will definitely come" id="opt-yes" required>
              <span>I will definitely come</span>
            </label>
            <label class="option-card" id="card-no" onclick="selectOption('no')">
              <input type="radio" name="attendance" value="Sorry, I won't make it" id="opt-no">
              <span>Sorry, I won't make it</span>
            </label>
          </div>
        </div>

        <!-- Dynamic Name Field (Displayed when 'I will definitely come' is chosen) -->
        <div class="form-group" id="name-group">
          <label class="form-label" for="guest-name">Full Name(s) of Guest(s)</label>
          <input type="text" id="guest-name" class="input-field" placeholder="e.g. Maria Santos / Maria & Guest">
        </div>

        <button type="submit" class="btn-submit">Confirm Response</button>

        <p class="email-hint">
          Responses will be recorded and notified to <strong>umalimagian@gmail.com</strong>
        </p>
      </form>
    </div>
  </div>

  <!-- ================= JAVASCRIPT LOGIC ================= -->
  <script>
    /* -----------------------------
       SCREEN SWITCHING LOGIC
    ------------------------------ */
    function showScreen(screenId) {
      document.querySelectorAll('.screen').forEach(el => el.classList.remove('active'));
      const target = document.getElementById(screenId);
      target.classList.add('active');
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    /* -----------------------------
       COUNTDOWN LOGIC
       Target: November 30, 2026, 8:00 AM
    ------------------------------ */
    const targetDate = new Date("2026-11-30T08:00:00").getTime();

    function updateCountdown() {
      const now = new Date().getTime();
      const distance = targetDate - now;

      if (distance < 0) {
        document.getElementById("days").innerText = "00";
        document.getElementById("hours").innerText = "00";
        document.getElementById("minutes").innerText = "00";
        document.getElementById("seconds").innerText = "00";
        return;
      }

      const days = Math.floor(distance / (1000 * 60 * 60 * 24));
      const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
      const seconds = Math.floor((distance % (1000 * 60)) / 1000);

      document.getElementById("days").innerText = days.toString().padStart(2, '0');
      document.getElementById("hours").innerText = hours.toString().padStart(2, '0');
      document.getElementById("minutes").innerText = minutes.toString().padStart(2, '0');
      document.getElementById("seconds").innerText = seconds.toString().padStart(2, '0');
    }

    // Start timer interval immediately
    setInterval(updateCountdown, 1000);
    updateCountdown();

    /* -----------------------------
       RSVP MODAL LOGIC
    ------------------------------ */
    const rsvpModal = document.getElementById("rsvp-modal");
    const nameGroup = document.getElementById("name-group");
    const guestNameInput = document.getElementById("guest-name");

    function openRSVP() {
      rsvpModal.classList.add("active");
    }

    function closeRSVP() {
      rsvpModal.classList.remove("active");
    }

    function selectOption(choice) {
      document.getElementById("card-yes").classList.toggle("selected", choice === 'yes');
      document.getElementById("card-no").classList.toggle("selected", choice === 'no');

      if (choice === 'yes') {
        nameGroup.style.display = "block";
        guestNameInput.setAttribute("required", "required");
      } else {
        nameGroup.style.display = "none";
        guestNameInput.removeAttribute("required");
        guestNameInput.value = "";
      }
    }

    /* -----------------------------
       FORM SUBMISSION TO GOOGLE SHEETS / EMAIL
    ------------------------------ */
    function handleRSVPSubmit(event) {
      event.preventDefault();
      
      const attendance = document.querySelector('input[name="attendance"]:checked').value;
      const guestName = guestNameInput.value.trim() || "Declined / No name provided";

      // 1. You can paste your Google Form or Google Apps Script Web App URL below:
      const GOOGLE_SCRIPT_WEBAPP_URL = ""; 

      if (GOOGLE_SCRIPT_WEBAPP_URL) {
        fetch(GOOGLE_SCRIPT_WEBAPP_URL, {
          method: "POST",
          mode: "no-cors",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify({
            name: guestName,
            status: attendance,
            date: new Date().toLocaleString()
          })
        }).then(() => {
          alert(`Thank you! Your RSVP (${attendance}) has been recorded.`);
          closeRSVP();
        });
      } else {
        // Fallback: Opens their mail client pre-addressed to your email
        const subject = encodeURIComponent(`Wedding RSVP: ${guestName} - ${attendance}`);
        const body = encodeURIComponent(
          `Hello Gian & Nicole,\n\nHere is my RSVP response:\n\nGuest Name: ${guestName}\nResponse: ${attendance}\n\nSent to: umalimagian@gmail.com`
        );
        
        window.location.href = `mailto:umalimagian@gmail.com?subject=${subject}&body=${body}`;
        
        alert(`Thank you! Your RSVP choice was selected: "${attendance}".\nAn email draft to umalimagian@gmail.com has been opened to confirm!`);
        closeRSVP();
      }
    }

    // Close modal when clicking outside of it
    window.onclick = function(event) {
      if (event.target === rsvpModal) {
        closeRSVP();
      }
    };
  </script>
</body>
</html>
