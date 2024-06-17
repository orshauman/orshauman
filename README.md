- 👋 Hi, I’m @orshauman
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
orshauman/orshauman is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fashion Recommendation</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0f0f0;
        }
        .container {
            max-width: 600px;
            margin: 50px auto;
            padding: 20px;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }
        h1 {
            text-align: center;
        }
        label {
            display: block;
            margin-top: 10px;
        }
        input, select {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            border-radius: 5px;
            border: 1px solid #ccc;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
            margin-top: 20px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Fashion Recommendation</h1>
        <form id="userForm">
            <label for="age">Age:</label>
            <input type="number" id="age" name="age" required>

            <label for="gender">Gender:</label>
            <select id="gender" name="gender" required>
                <option value="male">Male</option>
                <option value="female">Female</option>
                <option value="other">Other</option>
            </select>

            <label for="budget">Budget ($):</label>
            <input type="number" id="budget" name="budget" required>

            <label for="style">Preferred Style:</label>
            <select id="style" name="style" required>
                <option value="casual">Casual</option>
                <option value="formal">Formal</option>
                <option value="sporty">Sporty</option>
                <option value="bohemian">Bohemian</option>
            </select>

            <button type="submit">Get Recommendations</button>
        </form>
        <div id="recommendations" style="margin-top: 20px;"></div>
    </div>

    <script>
        document.getElementById('userForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const age = document.getElementById('age').value;
            const gender = document.getElementById('gender').value;
            const budget = document.getElementById('budget').value;
            const style = document.getElementById('style').value;

            fetch('/recommend', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({ age, gender, budget, style })
            })
            .then(response => response.json())
            .then(data => {
                const recommendationsDiv = document.getElementById('recommendations');
                recommendationsDiv.innerHTML = `<h2>Recommendations:</h2><ul>${data.recommendations.map(item => `<li>${item}</li>`).join('')}</ul>`;
            });
        });
    </script>
</body>
</html>

