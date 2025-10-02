<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>推し活相性診断</title>
  <style>
    body { font-family: 'Arial', sans-serif; background: #fdf6f9; text-align: center; padding: 50px; }
    input, button { padding: 10px; font-size: 16px; margin: 10px; }
    .result { margin-top: 30px; font-size: 18px; color: #444; }
  </style>
</head>
<body>
  <h1>🌟 17相性診断 🌟</h1>
  <p>あなたのイチナナIDを入力して、推しとの相性タイプを診断しよう！</p>
  <input type="text" id="userId" placeholder="イチナナIDを入力">
  <button onclick="diagnose()">診断する</button>

  <div class="result" id="result"></div>

  <script>
    function diagnose() {
      const id = document.getElementById("userId").value.trim();
      const resultBox = document.getElementById("result");

      if (!id) {
        resultBox.innerHTML = "IDを入力してください！";
        return;
      }

      const length = id.length;
      const hasEmoji = /[\u{1F600}-\u{1F64F}]/u.test(id);
      const hasNumber = /\d/.test(id);
      const hasSymbol = /[\W_]/.test(id);

      let type = "";
      if (length >= 12 && hasSymbol) {
        type = "🎭 幻想共鳴型クリエイター";
      } else if (hasNumber && hasEmoji) {
        type = "📸 ファンサ重視型リアクター";
      } else if (length <= 6 && !hasSymbol) {
        type = "🔍 考察職人型アナライザー";
      } else {
        type = "🎨 表現共鳴型バランサー";
      }

      resultBox.innerHTML = `
        <strong>診断結果：</strong><br>
        あなたは <span style="color:#e91e63">${type}</span> タイプです！<br><br>
        推しとの相性度：<strong>${Math.floor(70 + Math.random() * 30)}%</strong><br>