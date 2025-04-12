<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>World's Best Calculator</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: linear-gradient(to right, #2c3e50, #3498db);
      margin: 0;
    }
    .calculator {
      background-color: #ecf0f1;
      border-radius: 20px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.3);
      padding: 20px;
      width: 320px;
      transition: all 0.3s ease-in-out;
    }
    .display {
      background: #fff;
      padding: 20px;
      font-size: 2rem;
      border-radius: 10px;
      text-align: right;
      margin-bottom: 20px;
      box-shadow: inset 0 2px 5px rgba(0,0,0,0.1);
      overflow-x: auto;
    }
    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 15px;
    }
    button {
      padding: 20px;
      font-size: 1.2rem;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      transition: background 0.2s ease, transform 0.1s ease;
    }
    button:hover {
      background-color: #dcdde1;
      transform: scale(1.05);
    }
    .operator {
      background-color: #f39c12;
      color: white;
    }
    .equal {
      background-color: #27ae60;
      color: white;
      grid-column: span 2;
    }
    .clear {
      background-color: #e74c3c;
      color: white;
    }
    .dark-mode-toggle {
      margin-top: 15px;
      text-align: center;
    }
    .dark-mode-toggle button {
      background-color: #34495e;
      color: white;
      padding: 10px 20px;
      border-radius: 8px;
    }
    body.dark {
      background: linear-gradient(to right, #000000, #434343);
    }
    body.dark .calculator {
      background-color: #2c3e50;
    }
    body.dark .display {
      background-color: #34495e;
      color: #ecf0f1;
    }
    body.dark button {
      background-color: #7f8c8d;
      color: white;
    }
    body.dark .operator {
      background-color: #e67e22;
    }
    body.dark .equal {
      background-color: #2ecc71;
    }
    body.dark .clear {
      background-color: #c0392b;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <div class="display" id="display">0</div>
    <div class="buttons">
      <button class="clear" onclick="clearDisplay()">C</button>
      <button onclick="appendValue('(')">(</button>
      <button onclick="appendValue(')')">)</button>
      <button class="operator" onclick="appendValue('/')">÷</button>

      <button onclick="appendValue('7')">7</button>
      <button onclick="appendValue('8')">8</button>
      <button onclick="appendValue('9')">9</button>
      <button class="operator" onclick="appendValue('*')">×</button>

      <button onclick="appendValue('4')">4</button>
      <button onclick="appendValue('5')">5</button>
      <button onclick="appendValue('6')">6</button>
      <button class="operator" onclick="appendValue('-')">−</button>

      <button onclick="appendValue('1')">1</button>
      <button onclick="appendValue('2')">2</button>
      <button onclick="appendValue('3')">3</button>
      <button class="operator" onclick="appendValue('+')">+</button>

      <button onclick="appendValue('0')">0</button>
      <button onclick="appendValue('.')">.</button>
      <button class="equal" onclick="calculate()">=</button>
    </div>
    <div class="dark-mode-toggle">
      <button onclick="toggleDarkMode()">Toggle Dark Mode</button>
    </div>
  </div>

  <script>
    const display = document.getElementById('display');

    function appendValue(val) {
      if (display.innerText === "0" || display.innerText === "Error") {
        display.innerText = val;
      } else {
        display.innerText += val;
      }
    }

    function clearDisplay() {
      display.innerText = "0";
    }

    function calculate() {
      try {
        display.innerText = eval(display.innerText);
      } catch {
        display.innerText = "Error";
      }
    }

    function toggleDarkMode() {
      document.body.classList.toggle('dark');
    }
  </script>
</body>
</html>
