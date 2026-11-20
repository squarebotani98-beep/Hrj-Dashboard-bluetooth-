# Hrj-Dashboard-bluetooth-
Bluetooth dashboard 
<!doctype html>
<html lang="id">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>HRJ Dashboard Bluetooth</title>
<style>
:root{--bg:#0b0f14;--card:#151b23;--fg:#e8eef5;--dim:#8a97a6;--acc:#19d3ff;--good:#31d158;--warn:#ffc83d;--bad:#ff4d4d;--line:#263040}
@media (prefers-color-scheme:light){:root{--bg:#f3f6fa;--card:#fff;--fg:#14202e;--dim:#5b6b7d;--acc:#0a8fb5;--good:#1b9e3e;--warn:#b57e00;--bad:#d62c2c;--line:#d5dde7}}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--fg);font:15px/1.4 system-ui,-apple-system,"Segoe UI",Roboto,sans-serif;padding:12px;max-width:760px;margin:auto}
h1{font-size:18px;margin:0}
h2{font-size:13px;letter-spacing:.06em;text-transform:uppercase;color:var(--dim);margin:0 0 10px}
header{display:flex;align-items:center;justify-content:space-between;gap:10px;margin-bottom:10px}
.dot{display:inline-block;width:10px;height:10px;border-radius:50%;background:var(--dim);margin-right:6px}
.dot.on{background:var(--good)}
#st{font-size:13px;color:var(--dim)}
button{font:inherit;border:0;border-radius:10px;padding:10px 14px;background:var(--acc);color:#04222b;font-weight:600;cursor:pointer}
button.sec{background:transparent;color:var(--fg);border:1px solid var(--line)}
button:disabled{opacity:.4;cursor:not-allowed}
.card{background:var(--card);border:1px solid var(--line);border-radius:14px;padding:14px;margin-bottom:12px}
#alert{display:none;background:var(--bad);color:#fff;font-weight:700;text-align:center;padding:10px;border-radius:12px;margin-bottom:12px}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(110px,1fr));gap:10px}
.tile{background:var(--bg);border:1px solid var(--line);border-radius:12px;padding:10px}
.tile small{display:block;color:var(--dim);font-size:11px;text-transform:uppercase;letter-spacing:.05em}
.tile b{font-size:24px;font-variant-numeric:tabular-nums}
.tile.big{grid-column:span 2}.tile.big b{font-size:40px}
.bar{height:8px;background:var(--line);border-radius:4px;margin-top:6px;overflow:hidden}
.bar i{display:block;height:100%;width:0;background:var(--acc);transition:width .2s}
.chips{display:flex;gap:8px;flex-wrap:wrap;margin-top:10px}
.chip{font-size:12px;padding:4px 10px;border-radius:99px;border:1px solid var(--line);color:var(--dim)}
.chip.on{color:var(--fg);border-color:var(--good)}
label{display:block;font-size:12px;color:var(--dim);margin:8px 0 3px}
input,select{width:100%;font:inherit;color:var(--fg);background:var(--bg);border:1px solid var(--line);border-radius:10px;padding:9px}
.row{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.btns{display:flex;gap:8px;margin-top:12px;flex-wrap:wrap}
#log{font:12px/1.5 ui-monospace,Consolas,monospace;max-height:200px;overflow:auto;background:var(--bg);border:1px solid var(--line);border-radius:10px;padding:8px;white-space:pre-wrap}
.note{font-size:12px;color:var(--dim);margin-top:8px}
</style>
</head>
<body>
<header>
  <div><h1>HRJ Dashboard</h1><div id="st"><span class="dot" id="dot"></span><span id="stx">Belum terhubung</span></div></div>
  <div><button id="bc" onclick="connectBt()">Sambungkan</button> <button id="bd" class="sec" onclick="disc()" disabled>Putus</button></div>
</header>
<div id="alert"></div>

<div class="card">
