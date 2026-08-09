<!DOCTYPE html>

<html lang="mn"> <head> <meta charset="UTF-8"> <meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Сокод зориулсан 💌</title>

<style> * { box-sizing: border-box; } body { margin: 0; min-height: 100vh; font-family: Arial, sans-serif; background: linear-gradient(135deg, #ffd6e8, #e8d5ff); display: flex; justify-content: center; align-items: center; color: #422735; } .card { width: 92%; max-width: 430px; background: white; border-radius: 28px; padding: 30px 24px; text-align: center; box-shadow: 0 15px 50px rgba(70, 30, 60, 0.2); } .emoji { font-size: 55px; } h1 { font-size: 27px; margin: 10px 0; } h2 { font-size: 22px; } p { color: #765765; line-height: 1.6; } button { border: none; border-radius: 50px; padding: 14px 24px; font-size: 16px; font-weight: bold; cursor: pointer; } .yes { background: #ff5b91; color: white; } .no { background: #eeeeee; color: #555; position: absolute; } .button-area { height: 100px; position: relative; margin-top: 25px; } .activity { text-align: left; background: #fff3f7; border-radius: 18px; padding: 16px; margin: 20px 0; } .activity div { padding: 8px 0; } textarea, input { width: 100%; padding: 14px; border: 2px solid #f0d1de; border-radius: 15px; font-size: 16px; margin-top: 8px; outline: none; } textarea { height: 90px; resize: none; } .next { width: 100%; background: #ff5b91; color: white; margin-top: 20px; } .result { background: #fff2f7; padding: 15px; border-radius: 15px; margin-top: 15px; } .small { font-size: 13px; color: #9b7b89; } </style>

</head>

<body>

<div class="card" id="app">

<div class="emoji">💌</div>

<h1>Соко, нэг жижиг асуулт байна...</h1>

<p>
    Чамтай холбоотой маш чухал судалгаа хийх хэрэг гараад байна. 👀
</p>

<h2>Надтай болзох уу? ❤️</h2>

<div class="button-area" id="buttonArea">

    <button class="yes" onclick="yesClicked()">
        ТИЙМ ❤️
    </button>

    <button
        class="no"
        id="noButton"
        onmouseover="moveNo()"
        onclick="moveNo()">
        ҮГҮЙ 🥺
    </button>

</div>

<p class="small">
    * Үгүй товч жаахан ичимхий юм байна 😂
</p>

</div>

<script> function moveNo() { const button = document.getElementById("noButton"); const area = document.getElementById("buttonArea"); const maxX = area.clientWidth - button.offsetWidth; const maxY = area.clientHeight - button.offsetHeight; const x = Math.random() * Math.max(maxX, 10); const y = Math.random() * Math.max(maxY, 10); button.style.left = x + "px"; button.style.top = y + "px"; const texts = [ "Нээрээ юу? 😭", "Бодоод үз дээ 👀", "Арай ч дээ 🥺", "Энэ товч зугтаад байна 😂", "Тийм гэж дараарай ❤️" ]; button.innerText = texts[Math.floor(Math.random() * texts.length)]; } function yesClicked() { document.getElementById("app").innerHTML = ` <div class="emoji">🎉</div> <h1>Зөв хариулт! ❤️</h1> <p> За Соко, одоо болзооны төлөвлөгөөгөө хамт гаргая. 😌 </p> <h2>Болзоонд хийх зүйлс 👀</h2> <div class="activity"> <div>🍽️ Хамт хоол идэх</div> <div>🎮 Хөгжилтэй тоглоом тоглох</div> <div>🎬 Кино үзэх</div> <div>🌃 Гадуур хамт алхах</div> </div> <p> ✨ Мэдээж чи өөрийнхөө хиймээр байгаа зүйлсийг нэмэж болно шүү. </p> <textarea id="myIdea" placeholder="Чиний хиймээр байгаа зүйл... 👀"> </textarea>

    <button class="next" onclick="goToDate()">
        Дараагийнх ❤️
    </button>

`;

}

function goToDate() {

const idea =
    document.getElementById("myIdea").value;

document.getElementById("app").innerHTML = `

    <div class="emoji">📅</div>

    <h1>Одоо хамгийн чухал асуулт...</h1>

    <h2>
        Соко хэдний өдөр завтай вэ? 🥰
    </h2>

    <p>
        Болзоонд уулзах боломжтой өдрөө сонгоорой.
    </p>

    <input
        type="date"
        id="dateInput">

    <button
        class="next"
        onclick="finish('${encodeURIComponent(idea)}')">
        Баталгаажуулах ❤️
    </button>

`;

}

function finish(encodedIdea) {

const date =
    document.getElementById("dateInput").value;

if (!date) {

    alert("Завтай өдрөө сонгоорой, Соко 🥺❤️");

    return;
}

const idea =
    decodeURIComponent(encodedIdea);

const dateObject =
    new Date(date + "T00:00:00");

const formattedDate =
    dateObject.toLocaleDateString("mn-MN", {
        year: "numeric",
        month: "long",
        day: "numeric"
    });

document.getElementById("app").innerHTML = `

    <div class="emoji">🥰</div>

    <h1>
        Судалгаа амжилттай дууслаа! ❤️
    </h1>

    <p>
        Сокогийн болзооны төлөвлөгөө
        амжилттай бүртгэгдлээ. 😂
    </p>

    <div class="result">

        📅 <strong>Завтай өдөр:</strong><br>

        ${formattedDate}

    </div>

    <div class="result">

        🍽️ Хоол идэх<br>
        🎮 Хөгжилтэй тоглоом<br>
        🎬 Кино үзэх<br>
        🌃 Гадуур алхах

    </div>

    ${
        idea.trim()
        ? `
            <div class="result">

                ✨ <strong>Сокогийн нэмэлт санаа:</strong><br><br>

                ${escapeHTML(idea)}

            </div>
          `
        : ""
    }

    <p style="margin-top:25px;">

        Энэ чинь зүгээр нэг судалгаа биш
        болчихлоо шүү. 😂❤️

    </p>

    <h2>
        Тэгэхээр тэр өдөр уулзъя, Соко. 🫶
    </h2>

`;

}

function escapeHTML(text) {

return text
    .replace(/&/g, "&amp;")
    .replace(/</g, "&lt;")
    .replace(/>/g, "&gt;")
    .replace(/"/g, "&quot;")
    .replace(/'/g, "&#039;");

}

</script>

</body> </html>
