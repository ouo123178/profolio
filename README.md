<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>114-2 高三科技應用專題作品集 - 杜韋諺</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Noto+Sans+TC:wght@300;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-dark: #050507;
            --panel-bg: rgba(15, 15, 20, 0.9);
            --neon-blue: #00f3ff;
            --neon-pink: #ff00ff;
            --neon-green: #39ff14;
            --text-main: #e0e0e0;
            --accent-border: rgba(0, 243, 255, 0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: var(--bg-dark);
            color: var(--text-main);
            font-family: 'Noto Sans TC', sans-serif;
            height: 100vh;
            display: flex;
            flex-direction: column;
            overflow: hidden;
            background-image: 
                linear-gradient(rgba(0, 243, 255, 0.05) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 243, 255, 0.05) 1px, transparent 1px);
            background-size: 50px 50px;
        }

        /* 上方橫幅 - RGB 燈條感 */
        header {
            height: 70px;
            background: #000;
            border-bottom: 3px solid var(--neon-blue);
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 0 20px rgba(0, 243, 255, 0.5);
            z-index: 10;
            position: relative;
        }

        header h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.4rem;
            letter-spacing: 4px;
            color: var(--neon-blue);
            text-shadow: 0 0 8px var(--neon-blue);
        }

        /* 佈局容器 */
        .container {
            display: flex;
            flex: 1;
            overflow: hidden;
        }

        /* 左方選單 */
        nav {
            width: 260px;
            background: rgba(10, 10, 10, 0.95);
            border-right: 1px solid var(--accent-border);
            padding: 30px 15px;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .menu-item {
            padding: 15px;
            border: 1px solid transparent;
            background: rgba(255, 255, 255, 0.02);
            color: #888;
            cursor: pointer;
            transition: 0.3s;
            text-transform: uppercase;
            font-size: 0.9rem;
            position: relative;
        }

        .menu-item:hover, .menu-item.active {
            border: 1px solid var(--neon-blue);
            background: rgba(0, 243, 255, 0.1);
            color: #fff;
            box-shadow: 0 0 10px rgba(0, 243, 255, 0.2);
        }

        .menu-item.active::after {
            content: "◆";
            position: absolute;
            right: 10px;
            color: var(--neon-blue);
        }

        /* 右方內容區 */
        main {
            flex: 1;
            padding: 40px;
            overflow-y: auto;
            position: relative;
            background: radial-gradient(circle at top right, rgba(255, 0, 255, 0.05), transparent 40%);
        }

        /* 滑入動畫內容 */
        .content-section {
            display: none;
            max-width: 900px;
            margin: 0 auto;
            opacity: 0;
            transform: translateX(50px);
            transition: all 0.5s ease-out;
        }

        .content-section.active {
            display: block;
            opacity: 1;
            transform: translateX(0);
        }

        .card {
            background: var(--panel-bg);
            border-left: 5px solid var(--neon-pink);
            padding: 30px;
            border-radius: 0 8px 8px 0;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        h2 { 
            color: var(--neon-pink); 
            font-family: 'Orbitron', sans-serif;
            margin-bottom: 20px;
            border-bottom: 1px solid rgba(255, 0, 255, 0.2);
            padding-bottom: 10px;
        }

        p { line-height: 1.8; margin-bottom: 15px; color: #ccc; }

        .btn-link {
            display: inline-block;
            margin-top: 20px;
            padding: 10px 25px;
            border: 1px solid var(--neon-blue);
            color: var(--neon-blue);
            text-decoration: none;
            transition: 0.3s;
            font-weight: bold;
        }

        .btn-link:hover {
            background: var(--neon-blue);
            color: #000;
            box-shadow: 0 0 20px var(--neon-blue);
        }

        .hint-tag {
            background: rgba(57, 255, 20, 0.1);
            color: var(--neon-green);
            padding: 4px 10px;
            font-size: 0.8rem;
            border: 1px solid var(--neon-green);
            cursor: help;
            display: inline-block;
            margin-bottom: 15px;
        }

        /* 彈出視窗 */
        .modal-overlay {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.85);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 100;
            backdrop-filter: blur(5px);
        }

        .modal {
            background: #111;
            border: 2px solid var(--neon-pink);
            padding: 30px;
            max-width: 450px;
            box-shadow: 0 0 30px var(--neon-pink);
        }

        .modal h3 { color: var(--neon-pink); margin-bottom: 15px; }
        .modal button {
            background: var(--neon-pink);
            border: none;
            padding: 8px 20px;
            margin-top: 20px;
            cursor: pointer;
            font-weight: bold;
        }

    </style>
</head>
<body>

<header>
    <h1>114-2 高三科技應用專題作品集 - 31014 杜韋諺</h1>
</header>

<div class="container">
    <nav>
        <div class="menu-item active" onclick="showTab('home')">系統狀態</div>
        <div class="menu-item" onclick="showTab('game')">網頁遊戲：貪吃蛇</div>
        <div class="menu-item" onclick="showTab('3d')">3D 作品集：老鼠</div>
        <div class="menu-item" onclick="showTab('reflection')">學習反思與總結</div>
    </nav>

    <main>
        <div id="home" class="content-section active">
            <div class="card">
                <h2>> INITIALIZING SYSTEM...</h2>
                <p>歡迎進入數位檔案儲存庫。本網頁由 Gemini AI 協作生成，紀錄了高三期間在科技應用專題課的開發成果。</p>
                <div class="hint-tag" onclick="alertMsg('系統提示', '點擊左側導覽列即可切換不同專案模組。')">查看操作指引</div>
            </div>
        </div>

        <div id="game" class="content-section">
            <div class="card">
                <h2>網頁遊戲：貪吃蛇</h2>
                <p><strong>創作心得：</strong></p>
                <p>我覺得用AI做網頁小遊戲真的非常方便，之前還要慢慢地打程式碼跟除錯，現在不用了，我只需要把我的想法跟AI說，他就會依照我的想法生成出我要做的東西！</p>
                <div class="hint-tag" onclick="alertMsg('AI 協作亮點', 'Google AI Studio 生成網頁遊戲令我印象深刻，它能精準捕捉我對 3D 物件製作的需求。')">關鍵技術筆記</div>
                <br>
                <a href="https://ouo123178.github.io/GAME/ai_studio_code.html" target="_blank" class="btn-link">進入遊戲傳送門</a>
            </div>
        </div>

        <div id="3d" class="content-section">
            <div class="card">
                <h2>3D 作品集 A：老鼠</h2>
                <p><strong>作品簡介：</strong> 一隻在電臀老鼠。</p>
                <p><strong>創作心得：</strong> 這個作品是使用 monster mash 完成的，因為老鼠本身就不討人喜歡，加上電臀令人反感。</p>
                <div class="hint-tag" onclick="alertMsg('技術說明', 'Monster Mash 提供了一種基於草圖的快速建模方式，讓 2D 圖案能迅速轉化為 3D 動態物件。')">了解建模工具</div>
                <br>
                <a href="https://ouo123178.github.io/3d/" target="_blank" class="btn-link">查看 3D 模型實體</a>
            </div>
        </div>

        <div id="reflection" class="content-section">
            <div class="card">
                <h2>學習反思與總結</h2>
                <p>本門課程完整涵蓋了四個核心技術領域：</p>
                <ul style="list-style: none; padding-left: 10px; color: #aaa; line-height: 2;">
                    <li>1. 使用 Monster Mash 及 Polycam 製作 3D 物件</li>
                    <li>2. 使用 Google AI Studio 生成網頁遊戲</li>
                    <li>3. 使用 GitHub 上傳與部署網頁</li>
                    <li>4. 使用 Gemini 生成個人學習成果網站</li>
                </ul>
                <br>
                <div class="hint-tag" onclick="alertMsg('核心感觸', '我覺得最難的是網頁上傳到 GitHub 過程很瑣碎，碰到了非常多的難關，還好一一解決，最後也得到滿滿的成就感。')">⚠ 偵測到開發瓶頸</div>
                <p style="margin-top:20px;">整體而言，製作 3D 物件的過程非常有趣，雖然在技術部署（GitHub）上遇到挑戰，但這些困難最終都轉化為成長的動力。</p>
            </div>
        </div>
    </main>
</div>

<div id="modalOverlay" class="modal-overlay">
    <div class="modal">
        <h3 id="modalTitle">系統訊息</h3>
        <p id="modalContent"></p>
        <button onclick="closeMsg()">確認收信</button>
    </div>
</div>

<script>
    function showTab(tabId) {
        // 更新選單樣式
        document.querySelectorAll('.menu-item').forEach(item => {
            item.classList.remove('active');
        });
        event.currentTarget.classList.add('active');

        // 切換內容並觸發滑入動畫
        document.querySelectorAll('.content-section').forEach(section => {
            section.classList.remove('active');
        });
        
        const activeSection = document.getElementById(tabId);
        activeSection.style.display = 'block';
        setTimeout(() => {
            activeSection.classList.add('active');
        }, 10);
    }

    function alertMsg(title, content) {
        document.getElementById('modalTitle').innerText = title;
        document.getElementById('modalContent').innerText = content;
        document.getElementById('modalOverlay').style.display = 'flex';
    }

    function closeMsg() {
        document.getElementById('modalOverlay').style.display = 'none';
    }
</script>

</body>
</html>
