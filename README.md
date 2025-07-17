<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Oishik's Weekly Planner ✨</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&display=swap');
    
    :root {
      --primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      --secondary-gradient: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
      --success-gradient: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
      --warning-gradient: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
      --bg-color: #fafbfc;
      --text-color: #2d3748;
      --card-bg: rgba(255, 255, 255, 0.95);
      --shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
      --border-radius: 20px;
      --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .dark-mode {
      --bg-color: #1a1a2e;
      --text-color: #edf2f7;
      --card-bg: rgba(26, 32, 46, 0.95);
      --shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: var(--bg-color);
      color: var(--text-color);
      transition: var(--transition);
      min-height: 100vh;
      background-image: 
        radial-gradient(circle at 20% 80%, rgba(120, 119, 198, 0.3) 0%, transparent 50%),
        radial-gradient(circle at 80% 20%, rgba(255, 119, 198, 0.3) 0%, transparent 50%),
        radial-gradient(circle at 40% 40%, rgba(120, 219, 255, 0.2) 0%, transparent 50%);
      background-attachment: fixed;
      position: relative;
      overflow-x: hidden;
    }

    .dark-mode body {
      background-image: 
        radial-gradient(circle at 20% 80%, rgba(66, 65, 134, 0.4) 0%, transparent 50%),
        radial-gradient(circle at 80% 20%, rgba(134, 65, 134, 0.4) 0%, transparent 50%),
        radial-gradient(circle at 40% 40%, rgba(65, 134, 184, 0.3) 0%, transparent 50%);
    }

    .floating-particles {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 1;
    }

    .particle {
      position: absolute;
      width: 4px;
      height: 4px;
      background: linear-gradient(45deg, #667eea, #764ba2);
      border-radius: 50%;
      animation: float 6s ease-in-out infinite;
      opacity: 0.7;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0px) rotate(0deg); }
      50% { transform: translateY(-20px) rotate(180deg); }
    }

    .container {
      max-width: 1400px;
      margin: 0 auto;
      padding: 20px;
      position: relative;
      z-index: 2;
    }

    .header {
      text-align: center;
      margin-bottom: 40px;
      position: relative;
    }

    .header::before {
      content: '';
      position: absolute;
      top: -20px;
      left: 50%;
      transform: translateX(-50%);
      width: 200px;
      height: 200px;
      background: var(--primary-gradient);
      border-radius: 50%;
      opacity: 0.1;
      z-index: -1;
    }

    h1 {
      font-size: 3.5rem;
      font-weight: 800;
      background: var(--primary-gradient);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin-bottom: 10px;
      position: relative;
      animation: titleGlow 3s ease-in-out infinite alternate;
    }

    @keyframes titleGlow {
      from { filter: drop-shadow(0 0 5px rgba(102, 126, 234, 0.3)); }
      to { filter: drop-shadow(0 0 20px rgba(102, 126, 234, 0.6)); }
    }

    .subtitle {
      font-size: 1.2rem;
      color: var(--text-color);
      opacity: 0.8;
      margin-bottom: 20px;
      animation: fadeInUp 1s ease-out 0.5s both;
    }

    @keyframes fadeInUp {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .stats-bar {
      display: flex;
      justify-content: center;
      gap: 30px;
      margin-bottom: 30px;
      flex-wrap: wrap;
    }

    .stat-item {
      background: var(--card-bg);
      padding: 20px 30px;
      border-radius: var(--border-radius);
      box-shadow: var(--shadow);
      text-align: center;
      transition: var(--transition);
      backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 255, 255, 0.2);
    }

    .stat-item:hover {
      transform: translateY(-5px);
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
    }

    .stat-value {
      font-size: 2rem;
      font-weight: 700;
      background: var(--success-gradient);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .stat-label {
      font-size: 0.9rem;
      opacity: 0.7;
      margin-top: 5px;
    }

    .controls {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 30px;
      flex-wrap: wrap;
      gap: 15px;
    }

    .control-group {
      display: flex;
      align-items: center;
      gap: 15px;
    }

    .toggle-container {
      display: flex;
      align-items: center;
      gap: 10px;
      background: var(--card-bg);
      padding: 15px 20px;
      border-radius: 50px;
      box-shadow: var(--shadow);
      transition: var(--transition);
    }

    .toggle-container:hover {
      transform: translateY(-2px);
      box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
    }

    .toggle-switch {
      position: relative;
      display: inline-block;
      width: 60px;
      height: 30px;
    }

    .toggle-switch input {
      opacity: 0;
      width: 0;
      height: 0;
    }

    .slider {
      position: absolute;
      cursor: pointer;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: #ccc;
      transition: .4s;
      border-radius: 34px;
      background: linear-gradient(45deg, #667eea, #764ba2);
    }

    .slider:before {
      position: absolute;
      content: "";
      height: 22px;
      width: 22px;
      left: 4px;
      bottom: 4px;
      background-color: white;
      transition: .4s;
      border-radius: 50%;
      box-shadow: 0 2px 5px rgba(0,0,0,0.2);
    }

    input:checked + .slider:before {
      transform: translateX(30px);
    }

    .view-selector {
      display: flex;
      background: var(--card-bg);
      border-radius: 50px;
      padding: 5px;
      box-shadow: var(--shadow);
    }

    .view-btn {
      padding: 10px 20px;
      border: none;
      background: transparent;
      border-radius: 50px;
      cursor: pointer;
      font-weight: 600;
      transition: var(--transition);
      color: var(--text-color);
    }

    .view-btn.active {
      background: var(--primary-gradient);
      color: white;
      box-shadow: 0 5px 15px rgba(102, 126, 234, 0.3);
    }

    .table-container {
      background: var(--card-bg);
      border-radius: var(--border-radius);
      overflow: hidden;
      box-shadow: var(--shadow);
      backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 255, 255, 0.2);
      animation: slideInUp 0.8s ease-out;
    }

    @keyframes slideInUp {
      from { opacity: 0; transform: translateY(50px); }
      to { opacity: 1; transform: translateY(0); }
    }

    table {
      width: 100%;
      border-collapse: collapse;
    }

    th, td {
      padding: 15px 10px;
      text-align: center;
      border-bottom: 1px solid rgba(0, 0, 0, 0.05);
    }

    th {
      background: var(--primary-gradient);
      color: white;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 1px;
      font-size: 0.9rem;
      position: sticky;
      top: 0;
      z-index: 10;
    }

    tr:hover {
      background: rgba(102, 126, 234, 0.05);
    }

    .clickable {
      border: none;
      padding: 12px 16px;
      border-radius: 15px;
      cursor: pointer;
      font-weight: 500;
      font-size: 0.9rem;
      transition: var(--transition);
      width: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      position: relative;
      overflow: hidden;
    }

    .clickable::before {
      content: '';
      position: absolute;
      top: 50%;
      left: 50%;
      width: 0;
      height: 0;
      background: rgba(255, 255, 255, 0.3);
      border-radius: 50%;
      transform: translate(-50%, -50%);
      transition: var(--transition);
    }

    .clickable:hover::before {
      width: 100%;
      height: 100%;
    }

    .clickable:hover {
      transform: translateY(-3px) scale(1.05);
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
    }

    .clickable:active {
      transform: translateY(-1px) scale(0.98);
    }

    /* Enhanced activity colors with gradients */
    .College     { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; }
    .Breakfast   { background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%); color: #8b4513; }
    .Study       { background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%); color: #2d3748; }
    .Lunch       { background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%); color: #8b4513; }
    .Snack       { background: linear-gradient(135deg, #fbd3e9 0%, #bb377d 100%); color: white; }
    .Dinner      { background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%); color: #8b4513; }
    .Chat        { background: linear-gradient(135deg, #a18cd1 0%, #fbc2eb 100%); color: white; }
    .Sleep       { background: linear-gradient(135deg, #2c3e50 0%, #4a6741 100%); color: white; }
    .Travel      { background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%); color: #2d3748; }
    .Chores      { background: linear-gradient(135deg, #fa709a 0%, #fee140 100%); color: white; }
    .DSA         { background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%); color: white; }
    .Coding      { background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%); color: #2d3748; }
    .Relax       { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; }
    .Solitude    { background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%); color: white; }

    .modal {
      display: none;
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: var(--card-bg);
      padding: 30px;
      border-radius: var(--border-radius);
      box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
      z-index: 1000;
      width: 500px;
      max-width: 90%;
      backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 255, 255, 0.2);
      animation: modalSlideIn 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    }

    @keyframes modalSlideIn {
      from { 
        opacity: 0; 
        transform: translate(-50%, -50%) scale(0.8);
      }
      to { 
        opacity: 1; 
        transform: translate(-50%, -50%) scale(1);
      }
    }

    .overlay {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background: rgba(0, 0, 0, 0.6);
      z-index: 999;
      backdrop-filter: blur(10px);
    }

    .modal-header {
      display: flex;
      align-items: center;
      gap: 15px;
      margin-bottom: 20px;
      padding-bottom: 15px;
      border-bottom: 2px solid rgba(102, 126, 234, 0.2);
    }

    .modal-icon {
      width: 50px;
      height: 50px;
      background: var(--primary-gradient);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 1.2rem;
    }

    #modal-title {
      font-size: 1.4rem;
      font-weight: 600;
      color: var(--text-color);
    }

    #modal-content {
      font-size: 1.1rem;
      line-height: 1.6;
      color: var(--text-color);
      margin-bottom: 20px;
    }

    .close-btn {
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      color: white;
      border: none;
      padding: 12px 24px;
      border-radius: 50px;
      cursor: pointer;
      font-size: 1rem;
      font-weight: 600;
      transition: var(--transition);
      display: flex;
      align-items: center;
      gap: 8px;
      margin-left: auto;
    }

    .close-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 10px 25px rgba(102, 126, 234, 0.3);
    }

    .legend {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 15px;
      margin: 30px 0;
    }

    .legend-item {
      display: flex;
      align-items: center;
      gap: 12px;
      background: var(--card-bg);
      padding: 15px 20px;
      border-radius: 15px;
      box-shadow: var(--shadow);
      transition: var(--transition);
      backdrop-filter: blur(10px);
    }

    .legend-item:hover {
      transform: translateY(-3px);
      box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
    }

    .legend-color {
      width: 20px;
      height: 20px;
      border-radius: 8px;
      flex-shrink: 0;
    }

    .legend-text {
      font-weight: 500;
      color: var(--text-color);
    }

    .floating-btn {
      position: fixed;
      bottom: 30px;
      right: 30px;
      width: 60px;
      height: 60px;
      border-radius: 50%;
      background: var(--primary-gradient);
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.5rem;
      box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
      cursor: pointer;
      z-index: 100;
      transition: var(--transition);
      border: none;
    }

    .floating-btn:hover {
      transform: translateY(-5px) scale(1.1);
      box-shadow: 0 20px 40px rgba(102, 126, 234, 0.4);
    }

    .time-cell {
      font-weight: 600;
      color: var(--text-color);
      background: rgba(102, 126, 234, 0.1);
      font-size: 0.9rem;
    }

    .progress-bar {
      width: 100%;
      height: 6px;
      background: rgba(102, 126, 234, 0.2);
      border-radius: 3px;
      overflow: hidden;
      margin: 20px 0;
    }

    .progress-fill {
      height: 100%;
      background: var(--primary-gradient);
      border-radius: 3px;
      transition: width 0.5s ease;
      animation: progressPulse 2s ease-in-out infinite;
    }

    @keyframes progressPulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.8; }
    }

    .emoji-float {
      font-size: 1.2rem;
      animation: bounce 2s infinite;
    }

    @keyframes bounce {
      0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
      40% { transform: translateY(-10px); }
      60% { transform: translateY(-5px); }
    }

    @media (max-width: 768px) {
      h1 { font-size: 2.5rem; }
      .container { padding: 15px; }
      .stats-bar { flex-direction: column; align-items: center; }
      .controls { flex-direction: column; }
      th, td { padding: 10px 5px; font-size: 0.8rem; }
      .modal { width: 95%; padding: 20px; }
      .clickable { padding: 8px 12px; font-size: 0.8rem; }
    }
  </style>
</head>
<body>
  <div class="floating-particles"></div>
  
  <div class="container">
    <div class="header">
      <h1>✨ Oishik's Weekly Planner ✨</h1>
      <p class="subtitle">🚀 Organize your week for maximum productivity and balance 🎯</p>
      
      <div class="stats-bar">
        <div class="stat-item">
          <div class="stat-value">168</div>
          <div class="stat-label">📅 Hours/Week</div>
        </div>
        <div class="stat-item">
          <div class="stat-value">49</div>
          <div class="stat-label">💤 Sleep Hours</div>
        </div>
        <div class="stat-item">
          <div class="stat-value">35</div>
          <div class="stat-label">📚 Study Hours</div>
        </div>
        <div class="stat-item">
          <div class="stat-value">21</div>
          <div class="stat-label">🍽️ Meal Times</div>
        </div>
      </div>
      
      <div class="progress-bar">
        <div class="progress-fill" style="width: 75%"></div>
      </div>
    </div>

    <div class="controls">
      <div class="control-group">
        <div class="toggle-container">
          <span class="toggle-label">🌙 Dark Mode</span>
          <label class="toggle-switch">
            <input type="checkbox" id="darkModeToggle">
            <span class="slider"></span>
          </label>
        </div>
      </div>
      
      <div class="view-selector">
        <button class="view-btn active" onclick="switchView('week')">📅 Week View</button>
        <button class="view-btn" onclick="switchView('day')">📋 Day View</button>
      </div>
    </div>
    
    <div class="legend">
      <div class="legend-item">
        <div class="legend-color" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);"></div>
        <div class="legend-text">🎓 College</div>
      </div>
      <div class="legend-item">
        <div class="legend-color" style="background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);"></div>
        <div class="legend-text">📚 Study</div>
      </div>
      <div class="legend-item">
        <div class="legend-color" style="background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);"></div>
        <div class="legend-text">💻 DSA</div>
      </div>
      <div class="legend-item">
        <div class="legend-color" style="background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);"></div>
        <div class="legend-text">⚡ Coding</div>
      </div>
      <div class="legend-item">
        <div class="legend-color" style="background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);"></div>
        <div class="legend-text">🍳 Meals</div>
      </div>
      <div class="legend-item">
        <div class="legend-color" style="background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);"></div>
        <div class="legend-text">🧘 Solitude</div>
      </div>
      <div class="legend-item">
        <div class="legend-color" style="background: linear-gradient(135deg, #2c3e50 0%, #4a6741 100%);"></div>
        <div class="legend-text">😴 Sleep</div>
      </div>
    </div>
    
    <div class="overlay" id="overlay"></div>
    <div class="modal" id="modal">
      <div class="modal-header">
        <div class="modal-icon">
          <i class="fas fa-info-circle"></i>
        </div>
        <h3 id="modal-title">Activity Details</h3>
      </div>
      <p id="modal-content"></p>
      <button class="close-btn" onclick="closeModal()">
        <i class="fas fa-times"></i> Close
      </button>
    </div>
    
    <div class="table-container">
      <table>
        <thead>
          <tr>
            <th>🕐 Time</th>
            <th>📅 Monday</th>
            <th>📅 Tuesday</th>
            <th>📅 Wednesday</th>
            <th>📅 Thursday</th>
            <th>📅 Friday</th>
            <th>📅 Saturday</th>
            <th>📅 Sunday</th>
          </tr>
        </thead>
        <tbody id="schedule-body"></tbody>
      </table>
    </div>
  </div>
  
  <button class="floating-btn" onclick="scrollToTop()">
    <i class="fas fa-arrow-up"></i>
  </button>

  <script>
    // Create floating particles
    function createParticles() {
      const container = document.querySelector('.floating-particles');
      for (let i = 0; i < 50; i++) {
        const particle = document.createElement('div');
        particle.className = 'particle';
        particle.style.left = Math.random() * 100 + '%';
        particle.style.top = Math.random() * 100 + '%';
        particle.style.animationDelay = Math.random() * 6 + 's';
        particle.style.animationDuration = (Math.random() * 3 + 3) + 's';
        container.appendChild(particle);
      }
    }
    
    createParticles();

    // Dark mode state
    let isDarkMode = false;
    
    const days = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'];
    const chores = {
      Monday: [21],
      Tuesday: [13, 21],
      Wednesday: [12, 21],
      Thursday: [21],
      Friday: [11, 21],
      Saturday: [12, 13, 21],
      Sunday: [12, 13, 21]
    };

    const lunches = {
      Monday: '🍛 Soya curry, rice, salad',
      Tuesday: '🥗 Veg curry, rice, salad',
      Wednesday: '🐟 Fish curry, rice, salad',
      Thursday: '🏫 Canteen special',
      Friday: '🥚 Egg curry, rice, salad',
      Saturday: '🧀 Paneer, rice, salad',
      Sunday: '🍗 Chicken curry, rice, salad'
    };

    const lunchTimings = {
      Monday: 15, Tuesday: 14, Wednesday: 13, Thursday: 12, Friday: 12, Saturday: 14, Sunday: 14
    };

    const dinners = {
      Monday: '🍛 Soya curry, roti, salad',
      Tuesday: '🥗 Veg curry, roti, salad',
      Wednesday: '🐟 Fish curry, rice, salad',
      Thursday: '🫓 Roti, chana masala, salad',
      Friday: '🥚 Egg curry, roti, salad',
      Saturday: '🧀 Paneer, roti, salad',
      Sunday: '🍗 Chicken curry, roti, salad'
    };

    const breakfasts = {
      Monday: '🥪 Egg sandwich with brown bread',
      Tuesday: '🥣 Oats without milk, banana, dry fruits',
      Wednesday: '🥤 Sattu, banana, boiled egg, dry fruits',
      Thursday: '🥣 Oats without milk, banana, dry fruits',
      Friday: '🥛 Milk & cornflakes',
      Saturday: '🥤 Sattu, banana, dry fruits',
      Sunday: '🥛 Milk & cornflakes'
    };

    const snacks = {
      Monday: '🍞 Brown bread with milk',
      Tuesday: '🍞 Brown bread with milk',
      Wednesday: '🥛 Milk & cornflakes',
      Thursday: '🥜 Boiled chana & boiled egg',
      Friday: '🍜 Maggie',
      Saturday: '🥛 Milk & cornflakes',
      Sunday: '☕ Tea/Coffee with cookies'
    };

    const travel = {
      Monday: { college: [10,11,12,13], travelTo: [9], travelHome: [14] },
      Tuesday: { college: [10,11], travelTo: [9], travelHome: [12] },
      Wednesday: { college: [15,16,17], travelTo: [14], travelHome: [18] },
      Thursday: { college: [10,11,12,13,14,15,16], travelTo: [9], travelHome: [17] },
      Friday: { college: [14,15], travelTo: [13], travelHome: [16] }
    };

    const detailMap = {
      'Sleep': '😴 Sleep from 1:00 AM to 8:00 AM. Essential for recovery.',
      'Chores': '🧹 Household cleaning, laundry, dishes.',
      'Breakfast': '', // will be customized
      'Lunch': '',     // will be customized
      'Dinner': '',    // will be customized
      'Snack': '',     // will be customized
      'Lemon Water': '🍋 Warm lemon water right after waking up unless breakfast contains milk.',
      'Travel to College': '🚌 Commute to college (1 hour).',
      'Travel Home': '🚌 Return commute (1 hour).',
      'College': '🎓 College class.',
      'DSA Practice': '💻 DSA problems on Leetcode daily.',
      'Coding Practice': '💻 Side projects or HackerRank problems.',
      'Semester Subjects': '📚 Study OS, CN, SE, DBMS.',
      'Chat/Relax': '💬 Chat and gossip with close ones.',
      'Relax/Outing/Movie': '🎬 Time to relax, go out, or watch a movie.',
      'Solitude': '🧘‍♂️ Personal reflection and quiet time'
    };
    
    const emojiMap = {
      'Sleep': '😴',
      'Chores': '🧹',
      'Breakfast': '🍳',
      'Lunch': '🍽️',
      'Dinner': '🍛',
      'Snack': '🍪',
      'Lemon Water': '🍋',
      'Travel to College': '🚌',
      'Travel Home': '🚌',
      'College': '🎓',
      'DSA Practice': '💻',
      'Coding Practice': '💻',
      'Semester Subjects': '📚',
      'Chat/Relax': '💬',
      'Relax/Outing/Movie': '🎬',
      'Solitude': '🧘‍♂️'
    };

    const scheduleBody = document.getElementById('schedule-body');

    // Generate schedule
    function generateSchedule() {
      scheduleBody.innerHTML = ''; 

      const midnightRow = document.createElement('tr');
const midnightTime = document.createElement('td');
midnightTime.className = 'time-cell';
midnightTime.innerText = '00:00';
midnightRow.appendChild(midnightTime);

for (let day of days) {
  const td = document.createElement('td');
  const btn = document.createElement('button');
  btn.className = 'clickable Solitude';
  btn.innerHTML = `${emojiMap['Solitude'] || '🧘‍♂️'} Solitude`;
  const detail = detailMap['Solitude'] || 'Personal reflection and quiet time';
  btn.onclick = () => showModal(`${day} – 00:00`, `Solitude: ${detail}`);
  td.appendChild(btn);
  midnightRow.appendChild(td);
}
scheduleBody.appendChild(midnightRow);
      // Add sleep row
      const sleepRow = document.createElement('tr');
      const sleepTime = document.createElement('td');
      sleepTime.className = 'time-cell';
      sleepTime.innerText = '01:00 – 08:00';
      sleepRow.appendChild(sleepTime);
      
      for (let day of days) {
        const td = document.createElement('td');
        const btn = document.createElement('button');
        btn.className = 'clickable Sleep';
        btn.innerHTML = `${emojiMap['Sleep']} Sleep`;
        const detail = detailMap['Sleep'];
        btn.onclick = () => showModal(`${day} – Sleep`, detail);
        td.appendChild(btn);
        sleepRow.appendChild(td);
      }
      scheduleBody.appendChild(sleepRow);

      // Generate other hours
      for (let h = 8; h < 24; h++) {
        const time = h.toString().padStart(2, '0') + ':00';
        const row = document.createElement('tr');
        const timeCell = document.createElement('td');
        timeCell.className = 'time-cell';
        timeCell.innerText = time;
        row.appendChild(timeCell);
        
        for (let day of days) {
          const td = document.createElement('td');
          let activity = '', className = '', info = '';
          const t = travel[day] || {};
          const ch = chores[day] || [];
          
          // Common activities for all days
          if (h === 8) { 
            activity = 'Breakfast'; 
            className = 'Breakfast'; 
            info = breakfasts[day]; 
          }
          else if (h === lunchTimings[day]) { 
            activity = 'Lunch'; 
            className = 'Lunch'; 
            info = lunches[day]; 
          }
          else if (h === 22) { 
            activity = 'Dinner'; 
            className = 'Dinner'; 
            info = dinners[day]; 
          }
          else if (h === 19 && snacks[day]) { 
            activity = 'Snack'; 
            className = 'Snack'; 
            info = snacks[day]; 
          }
          else if (ch.includes(h)) { 
            activity = 'Chores'; 
            className = 'Chores'; 
          }
          else if (t.travelTo && t.travelTo.includes(h)) { 
            activity = 'Travel to College'; 
            className = 'Travel'; 
          }
          else if (t.college && t.college.includes(h)) { 
            activity = 'College'; 
            className = 'College'; 
          }
          else if (t.travelHome && t.travelHome.includes(h)) { 
            activity = 'Travel Home'; 
            className = 'Travel'; 
          }
          
          // Day-specific activities
          else if (day === 'Monday') {
            if (h >= 16 && h < 18) { 
              activity = 'Semester Subjects'; 
              className = 'Study'; 
            }
            else if (h >= 18 && h < 19) { 
              activity = 'DSA Practice'; 
              className = 'DSA'; 
            }
            else if (h === 20) { 
              activity = 'Coding'; 
              className = 'Coding'; 
            }
            else if (h === 21) { 
              activity = 'Chat/Relax'; 
              className = 'Chat'; 
            }
            else { 
              activity = 'Solitude'; 
              className = 'Chill'; 
            }
          }
          else if (day === 'Tuesday') {
            if (h >= 15 && h < 17) { 
              activity = 'Semester Subjects'; 
              className = 'Study'; 
            }
            else if (h >= 17 && h < 19) { 
              activity = 'DSA Practice'; 
              className = 'DSA'; 
            }
            else if (h === 20) { 
              activity = 'Coding'; 
              className = 'Coding'; 
            }
            else if (h === 21) { 
              activity = 'Chat/Relax'; 
              className = 'Chat'; 
            }
            else { 
              activity = 'Solitude'; 
              className = 'Chill'; 
            }
          }
          else if (day === 'Wednesday') {
            if (h >= 9 && h < 11) { 
              activity = 'Semester Subjects'; 
              className = 'Study'; 
            }
            else if (h >= 11 && h < 12) { 
              activity = 'DSA Practice'; 
              className = 'DSA'; 
            }
            else if (h === 20) { 
              activity = 'Coding'; 
              className = 'Coding'; 
            }
            else if (h === 21) { 
              activity = 'Chat/Relax'; 
              className = 'Chat'; 
            }
            else { 
             activity = 'Solitude'; 
              className = 'Chill'; 
            }
          }
          else if (day === 'Thursday') {
            if (h === 20) { 
              activity = 'Coding'; 
              className = 'Coding'; 
            }
            else if (h === 21) { 
              activity = 'Chat/Relax'; 
              className = 'Chat'; 
            }
            else { 
               activity = 'Solitude'; 
               className = 'Chill'; 
            }
          }
          else if (day === 'Friday') {
            if (h >= 9 && h < 11) { 
              activity = 'Semester Subjects'; 
              className = 'Study'; 
            }
            else if (h >= 17 && h < 19) { 
              activity = 'DSA Practice'; 
              className = 'DSA'; 
            }
            else if (h === 20) { 
              activity = 'Coding'; 
              className = 'Coding'; 
            }
            else if (h === 21) { 
              activity = 'Chat/Relax'; 
              className = 'Chat'; 
            }
            else { 
               activity = 'Solitude'; 
               className = 'Chill'; 
            }
          }
          else if (day === 'Saturday' || day === 'Sunday') {
            if (h >= 9 && h < 11) { 
              activity = 'Semester Subjects'; 
              className = 'Study'; 
            }
            else if (h >= 11 && h < 12) { 
              activity = 'DSA Practice'; 
              className = 'DSA'; 
            }
            else if (h >= 15 && h < 17) { 
              activity = 'Coding'; 
              className = 'Coding'; 
            }
            else if (h >= 17 && h < 19) { 
              activity = 'Relax/Outing/Movie'; 
              className = 'Relax'; 
            }
            else if (h >= 20 && h < 21) { 
              activity = 'Relax/Outing/Movie'; 
              className = 'Relax'; 
            }
            else { 
              activity = 'Solitude'; 
              className = 'Chill'; 
            }
          }

          const btn = document.createElement('button');
          btn.className = `clickable ${className}`;
          btn.innerHTML = `${emojiMap[activity] || '📝'} ${activity}`;
          const detail = info || detailMap[activity] || activity;
          btn.onclick = () => showModal(`${day} – ${time}`, `${activity}: ${detail}`);
          td.appendChild(btn);
          row.appendChild(td);
        }
        scheduleBody.appendChild(row);
      }
    }

    function showModal(title, content) {
      document.getElementById('modal-title').innerText = title;
      document.getElementById('modal-content').innerText = content;
      document.getElementById('modal').style.display = 'block';
      document.getElementById('overlay').style.display = 'block';
    }

    function closeModal() {
      document.getElementById('modal').style.display = 'none';
      document.getElementById('overlay').style.display = 'none';
    }

    function scrollToTop() {
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    function switchView(view) {
      const buttons = document.querySelectorAll('.view-btn');
      buttons.forEach(btn => btn.classList.remove('active'));
      document.querySelector(`.view-btn[onclick="switchView('${view}')"]`).classList.add('active');
      
      // View switching logic
      if (view === 'day') {
        alert('Day view will be implemented soon!');
      }
    }

    // Dark mode toggle
    const darkModeToggle = document.getElementById('darkModeToggle');
    darkModeToggle.addEventListener('change', function() {
      document.body.classList.toggle('dark-mode', this.checked);
      localStorage.setItem('darkMode', this.checked);
    });

    // Check for saved dark mode preference
    if (localStorage.getItem('darkMode') === 'true') {
      darkModeToggle.checked = true;
      document.body.classList.add('dark-mode');
    }

    // Initialize the schedule
    generateSchedule();
  </script>
</body>
</html>
