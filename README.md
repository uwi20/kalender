# kalender 2025
                    
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kalender Hewan Lucu</title>
    <style>
        body {
            font-family: 'Comic Sans MS', cursive, sans-serif;
            background: url('wallpaper hewan.jpg') no-repeat center center fixed;
            background-size: cover;
            text-align: center;
            margin: 0;
            padding: 0;https:
        }
        .container {
            max-width: 400px;
            margin: 50px auto;
            padding: 20px;
            background: rgba(255, 255, 255, 0.8);
            border-radius: 15px;
            box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.2);
            position: relative;
        }
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 10px;
        }
        button {
            background: #4da8da;
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background: #3b8bbf;
        }
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            width: 14%;
            padding: 10px;
            text-align: center;
            font-size: 16px;
            border-radius: 10px;
        }
        th {
            background: #66c2ff;
            color: white;
        }
        td {
            background: #a3d5ff;
            cursor: pointer;
            position: relative;
        }
        td:hover {
            background: #87c0ff;
        }
        .highlight {
            background: #ffcc00 !important;
            color: #000;
            font-weight: bold;
        }
        .emoji {
            font-size: 20px;
            position: absolute;
            top: 5px;
            right: 5px;
        }
        .cute-character {
            width: 80px;
            height: 80px;
            position: absolute;
            top: -40px;
            right: -20px;
        }
    </style>
</head>
<body>

    <div class="container">
        <img src ="wallpaper hewan.jpg') no-repeat center center fixed">
        <div class="header">
            <button onclick="prevMonth()">⬅</button>
            <span id="month-year"></span>
            <button onclick="nextMonth()">➡</button>
        </div>
        <table>
            <thead>
                <tr>
                    <th>Min</th>
                    <th>Sen</th>
                    <th>Sel</th>
                    <th>Rab</th>
                    <th>Kam</th>
                    <th>Jum</th>
                    <th>Sab</th>
                </tr>
            </thead>
            <tbody id="calendar-body"></tbody>
        </table>
    </div>

    <script>
        let currentDate = new Date();

        function updateCalendar() {
            const monthYear = document.getElementById("month-year");
            const calendarBody = document.getElementById("calendar-body");

            const months = [
                "Januari", "Februari", "Maret", "April", "Mei", "Juni", 
                "Juli", "Agustus", "September", "Oktober", "November", "Desember"
            ];

            let year = currentDate.getFullYear();
            let month = currentDate.getMonth();

            monthYear.innerText = `${months[month]} ${year}`;

            let firstDay = new Date(year, month, 1).getDay();
            let daysInMonth = new Date(year, month + 1, 0).getDate();

            let specialDays = {
                "1-1": "🎉",  // Tahun Baru
                "14-2": "💖", // Valentine
                "17-8": "🇮🇩", // Hari Kemerdekaan
                "25-12": "🎄"  // Natal
            };

            calendarBody.innerHTML = "";
            let date = 1;

            for (let i = 0; i < 6; i++) {
                let row = document.createElement("tr");

                for (let j = 0; j < 7; j++) {
                    let cell = document.createElement("td");

                    if (i === 0 && j < firstDay) {
                        cell.innerText = "";
                    } else if (date > daysInMonth) {
                        break;
                    } else {
                        cell.innerText = date;
                        let dateKey = `${date}-${month + 1}`;
                        if (specialDays[dateKey]) {
                            let emoji = document.createElement("span");
                            emoji.innerText = specialDays[dateKey];
                            emoji.classList.add("emoji");
                            cell.appendChild(emoji);
                        }
                        if (date === new Date().getDate() && month === new Date().getMonth() && year === new Date().getFullYear()) {
                            cell.classList.add("highlight");
                        }
                        date++;
                    }
                    row.appendChild(cell);
                }
                calendarBody.appendChild(row);
            }
        }

        function prevMonth() {
            currentDate.setMonth(currentDate.getMonth() - 1);
            updateCalendar();
        }

        function nextMonth() {
            currentDate.setMonth(currentDate.getMonth() + 1);
            updateCalendar();
        }

        updateCalendar();
    </script>
