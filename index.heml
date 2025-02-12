<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>単語学習サイト</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>単語学習サイト</h1>
    </header>
    <nav id="navbar">
        <a href="javascript:void(0);" class="icon" onclick="toggleMenu()">
            &#9776; <!-- ハンバーガーアイコン -->
        </a>
        <a href="#" onclick="showSection('learning')">単語学習</a>
        <a href="#" onclick="showSection('list')">単語一覧</a>
        <a href="#" onclick="showSection('login')">管理者ログイン</a>
    </nav>

    <section id="learningSection">
        <div class="meaning" id="meaning">意味表示エリア</div>
        <div class="input-area">
            <input type="text" id="userInput" placeholder="単語を入力してください">
            <button onclick="checkAnswer()">確認</button>
        </div>
        <div id="result"></div>
        <button id="nextButton" class="hidden" onclick="displayWord()">次の単語へ</button>
    </section>

    <section id="listSection" class="hidden">
        <h2>登録された単語</h2>
        <ul id="wordList"></ul>
    </section>

    <section id="adminSection" class="hidden">
        <h2>単語管理</h2>
        <input type="text" id="newWord" placeholder="新しい単語">
        <input type="text" id="newMeaning" placeholder="意味">
        <button onclick="addWord()">単語を追加</button>
    </section>
    
    <section id="loginSection" class="hidden">
        <h2>管理者ログイン</h2>
        <input type="password" id="password" placeholder="パスワード">
        <button onclick="login()">ログイン</button>
    </section>

    <script>
        let words = {
            "apple": "りんご",
            "banana": "バナナ",
            "grape": "ぶどう",
            "orange": "オレンジ",
            "peach": "もも"
        };
        let currentWord = "";
        const adminPassword = "admin123"; // 管理者パスワード
        let isAdmin = false; // 管理者かどうかのフラグ

        function displayWord() {
            const keys = Object.keys(words);
            currentWord = keys[Math.floor(Math.random() * keys.length)];
            document.getElementById("meaning").textContent = "意味: " + words[currentWord];
            document.getElementById("result").textContent = "";
            document.getElementById("userInput").value = "";
            document.getElementById("nextButton").classList.add("hidden"); // 次の単語ボタンを非表示
        }

        function checkAnswer() {
            const userInput = document.getElementById("userInput").value;
            if (userInput === currentWord) {
                document.getElementById("result").textContent = "正解！";
                document.getElementById("nextButton").classList.remove("hidden"); // 次の単語ボタンを表示
            } else {
                document.getElementById("result").textContent = "不正解。正しい答えは " + currentWord + " です。";
                document.getElementById("nextButton").classList.remove("hidden"); // 次の単語ボタンを表示
            }
        }

        function login() {
            const password = document.getElementById("password").value;
            if (password === adminPassword) {
                isAdmin = true; // 管理者フラグを立てる
                document.getElementById("loginSection").classList.add("hidden");
                document.getElementById("adminSection").classList.remove("hidden");
                alert("ログイン成功！");
            } else {
                alert("パスワードが間違っています。");
            }
        }

        function addWord() {
            if (!isAdmin) {
                alert("管理者としてログインしてください。");
                return;
            }
            const newWord = document.getElementById("newWord").value;
            const newMeaning = document.getElementById("newMeaning").value;
            if (newWord && newMeaning) {
                words[newWord] = newMeaning;
                alert("単語が追加されました！");
                document.getElementById("newWord").value = "";
                document.getElementById("newMeaning").value = "";
            } else {
                alert("単語と意味を入力してください。");
            }
        }

        function displayWords() {
            const wordList = document.getElementById("wordList");
            wordList.innerHTML = ""; // 既存のリストをクリア
            const sortedWords = Object.keys(words).sort(); // 単語をアルファベット順にソート

            sortedWords.forEach(word => {
                const listItem = document.createElement("li");
                listItem.textContent = `${word}: ${words[word]}`;
                wordList.appendChild(listItem);
            });

            if (sortedWords.length === 0) {
                const listItem = document.createElement("li");
                listItem.textContent = "登録された単語はありません。";
                wordList.appendChild(listItem);
            }
        }

        function showSection(section) {
            document.getElementById("learningSection").classList.add("hidden");
            document.getElementById("listSection").classList.add("hidden");
            document.getElementById("adminSection").classList.add("hidden");
            document.getElementById("loginSection").classList.add("hidden");

            if (section === 'learning') {
                document.getElementById("learningSection").classList.remove("hidden");
                displayWord();
            } else if (section === 'list') {
                document.getElementById("listSection").classList.remove("hidden");
                displayWords();
            } else if (section === 'login') {
                document.getElementById("loginSection").classList.remove("hidden");
            }
        }

        function toggleMenu() {
            const navbar = document.getElementById("navbar");
            navbar.classList.toggle("responsive");
        }

        // ページが読み込まれた時に学習セクションを表示
        window.onload = function() {
            showSection('learning');
        };
    </script>
</body>
</html>
