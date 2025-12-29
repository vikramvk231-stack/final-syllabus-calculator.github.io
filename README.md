# final-syllabus-calculator.github.io
syllabus calculator website by Vikram
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Class 9 Syllabus Tracker</title>
  <style>
    body {
      margin: 0;
      font-family: 'Arial', sans-serif;
      background: linear-gradient(to right, #6a11cb, #2575fc);
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
    }

    .container {
      background: rgba(0,0,0,0.7);
      padding: 30px 40px;
      border-radius: 15px;
      width: 90%;
      max-width: 700px;
      box-shadow: 0 0 20px rgba(0,0,0,0.5);
    }

    h1 {
      text-align: center;
      margin-bottom: 25px;
      font-size: 28px;
    }

    .subject {
      display: flex;
      justify-content: space-between;
      margin-bottom: 15px;
    }

    label {
      flex: 1;
    }

    input {
      width: 70px;
      padding: 5px;
      margin-left: 10px;
      border: none;
      border-radius: 5px;
    }

    button {
      width: 100%;
      padding: 12px;
      background: #ff9800;
      color: #000;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      cursor: pointer;
      margin-top: 20px;
    }

    button:hover {
      background: #ffa733;
    }

    .results {
      margin-top: 25px;
    }

    .progress-bar {
      background: #ddd;
      border-radius: 5px;
      overflow: hidden;
      margin-top: 5px;
    }

    .progress {
      height: 20px;
      background: #4CAF50;
      text-align: center;
      color: white;
      line-height: 20px;
    }

    .overall {
      font-size: 18px;
      margin-top: 20px;
      text-align: center;
      font-weight: bold;
    }

    .footer {
      text-align: center;
      margin-top: 20px;
      font-size: 14px;
      color: #ddd;
    }

    @media (max-width: 600px) {
      input {
        width: 50px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Class 9 Syllabus Tracker</h1>
    <form id="syllabusForm">
      <div class="subject">
        <label>Hindi (Completed/Total)</label>
        <input type="number" min="0" id="HindiCompleted" placeholder="6">
        <input type="number" min="1" id="HindiTotal" placeholder="10">
      </div>
      <div class="subject">
        <label>English</label>
        <input type="number" min="0" id="EnglishCompleted" placeholder="7">
        <input type="number" min="1" id="EnglishTotal" placeholder="10">
      </div>
      <div class="subject">
        <label>Maths</label>
        <input type="number" min="0" id="MathsCompleted" placeholder="9">
        <input type="number" min="1" id="MathsTotal" placeholder="15">
      </div>
      <div class="subject">
        <label>Physics</label>
        <input type="number" min="0" id="PhysicsCompleted" placeholder="6">
        <input type="number" min="1" id="PhysicsTotal" placeholder="12">
      </div>
      <div class="subject">
        <label>Chemistry</label>
        <input type="number" min="0" id="ChemistryCompleted" placeholder="8">
        <input type="number" min="1" id="ChemistryTotal" placeholder="12">
      </div>
      <div class="subject">
        <label>Biology</label>
        <input type="number" min="0" id="BiologyCompleted" placeholder="7">
        <input type="number" min="1" id="BiologyTotal" placeholder="10">
      </div>
      <div class="subject">
        <label>Banking</label>
        <input type="number" min="0" id="BankingCompleted" placeholder="2">
        <input type="number" min="1" id="BankingTotal" placeholder="5">
      </div>
      <div class="subject">
        <label>History</label>
        <input type="number" min="0" id="HistoryCompleted" placeholder="5">
        <input type="number" min="1" id="HistoryTotal" placeholder="8">
      </div>
      <div class="subject">
        <label>Geography</label>
        <input type="number" min="0" id="GeographyCompleted" placeholder="4">
        <input type="number" min="1" id="GeographyTotal" placeholder="8">
      </div>
      <div class="subject">
        <label>Civics</label>
        <input type="number" min="0" id="CivicsCompleted" placeholder="3">
        <input type="number" min="1" id="CivicsTotal" placeholder="7">
      </div>
      <div class="subject">
        <label>Economics</label>
        <input type="number" min="0" id="EconomicsCompleted" placeholder="2">
        <input type="number" min="1" id="EconomicsTotal" placeholder="6">
      </div>
      <button type="button" onclick="calculateProgress()">Calculate Completion</button>
    </form>
    <div class="results" id="results"></div>
    <div class="overall" id="overall"></div>
    <div class="footer">Created by Vikram</div>
  </div>

  <script>
    function calculateProgress() {
      const subjects = ["Hindi","English","Maths","Physics","Chemistry","Biology","Banking","History","Geography","Civics","Economics"];
      let totalCompleted = 0;
      let totalChapters = 0;
      let resultsDiv = document.getElementById("results");
      resultsDiv.innerHTML = "";

      subjects.forEach(subject => {
        let completed = parseInt(document.getElementById(subject + "Completed").value) || 0;
        let total = parseInt(document.getElementById(subject + "Total").value) || 1;

        if(completed > total) completed = total;

        let percent = ((completed / total) * 100).toFixed(1);

        totalCompleted += completed;
        totalChapters += total;

        resultsDiv.innerHTML += `<strong>${subject}:</strong> ${percent}% 
        <div class="progress-bar"><div class="progress" style="width:${percent}%">${percent}%</div></div><br>`;
      });

      let overallPercent = ((totalCompleted / totalChapters) * 100).toFixed(1);
      document.getElementById("overall").innerText = "Overall Syllabus Completion: " + overallPercent + "%";
    }
  </script>
</body>
</html>
