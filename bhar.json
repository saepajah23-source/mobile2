<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Multi Dialog System v1.0</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #111;
      color: #fff;
      padding: 20px;
    }

    .config {
      background: #1e1e1e;
      padding: 15px;
      border-radius: 10px;
      margin-bottom: 20px;
    }

    .config input, .config select {
      width: 100%;
      padding: 8px;
      margin-top: 6px;
      margin-bottom: 10px;
      border-radius: 6px;
      border: none;
    }

    .btn {
      padding: 10px 20px;
      border-radius: 8px;
      border: none;
      background: linear-gradient(135deg, #00f2ff, #0047ff);
      color: #fff;
      font-weight: bold;
      cursor: pointer;
    }

    /* BACKDROP */
    .backdrop {
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: rgba(0,0,0,0.6);
      display: none;
      z-index: 90;
    }

    /* DIALOG BASE */
    .dialog {
      position: fixed;
      min-width: 280px;
      max-width: 90%;
      padding: 20px;
      border-radius: 18px;
      box-shadow: 0 10px 40px rgba(0,0,0,0.6);
      z-index: 100;
      display: none;
      animation: pop 0.3s ease;
    }

    @keyframes pop {
      from { transform: scale(0.7); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }

    .dialog img {
      width: 100%;
      border-radius: 12px;
      margin-bottom: 12px;
    }

    .dialog h3 {
      margin: 0 0 10px 0;
    }

    .dialog button {
      margin-top: 15px;
      width: 100%;
      padding: 10px;
      border-radius: 10px;
      border: none;
      background: #00e0ff;
      font-weight: bold;
    }

    /* 5 STYLE THEME */
    .style1 { background: #1f1f1f; }
    .style2 { background: linear-gradient(135deg, #ff512f, #dd2476); }
    .style3 { background: linear-gradient(135deg, #11998e, #38ef7d); color: #000; }
    .style4 { background: linear-gradient(135deg, #fc4a1a, #f7b733); color: #000; }
    .style5 { background: linear-gradient(135deg, #8360c3, #2ebf91); }

    /* ALIGNMENT */
    .center { top: 50%; left: 50%; transform: translate(-50%, -50%); }
    .top { top: 20px; left: 50%; transform: translateX(-50%); }
    .bottom { bottom: 20px; left: 50%; transform: translateX(-50%); }

    /* TOAST */
    .toast {
      position: fixed;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      background: #222;
      padding: 12px 20px;
      border-radius: 30px;
      box-shadow: 0 5px 20px rgba(0,0,0,0.5);
      display: none;
    }
  </style>
</head>
<body>

<h2>Multi Dialog System (GitHub Ready)</h2>

<div class="config">
  <label>JSON URL</label>
  <input id="jsonUrl" value="https://apkmohalla3.wasmer.app/multi_json.php">

  <label>Style</label>
  <select id="style">
    <option value="style1">Style 1</option>
    <option value="style2">Style 2</option>
    <option value="style3">Style 3</option>
    <option value="style4">Style 4</option>
    <option value="style5">Style 5 (With Image)</option>
  </select>

  <label>Alignment</label>
  <select id="align">
    <option value="center">Center</option>
    <option value="top">Top</option>
    <option value="bottom">Bottom</option>
  </select>

  <label>Mode</label>
  <select id="mode">
    <option value="dialog">Dialog</option>
    <option value="toast">Toast</option>
  </select>

  <button class="btn" onclick="loadDialog()">LOAD DIALOG</button>
</div>

<div class="backdrop" id="backdrop"></div>

<div class="dialog" id="dialog">
  <img id="dialogImg" style="display:none;">
  <h3 id="dialogTitle"></h3>
  <p id="dialogMsg"></p>
  <button onclick="closeDialog()">TUTUP</button>
</div>

<div class="toast" id="toast"></div>

<script>
  function loadDialog() {
    const url = document.getElementById('jsonUrl').value;
    const style = document.getElementById('style').value;
    const align = document.getElementById('align').value;
    const mode = document.getElementById('mode').value;

    fetch(url)
      .then(res => res.json())
      .then(data => {
        if (mode === 'toast') {
          showToast(data.message || 'Toast Message');
        } else {
          showDialog(data, style, align);
        }
      })
      .catch(() => {
        alert('Gagal mengambil JSON');
      });
  }

  function showDialog(data, style, align) {
    const dialog = document.getElementById('dialog');
    const backdrop = document.getElementById('backdrop');
    const img = document.getElementById('dialogImg');

    dialog.className = `dialog ${style} ${align}`;
    document.getElementById('dialogTitle').innerText = data.title || 'No Title';
    document.getElementById('dialogMsg').innerText = data.message || 'No message';

    if (style === 'style5' && data.image) {
      img.src = data.image;
      img.style.display = 'block';
    } else {
      img.style.display = 'none';
    }

    backdrop.style.display = 'block';
    dialog.style.display = 'block';
  }

  function closeDialog() {
    document.getElementById('dialog').style.display = 'none';
    document.getElementById('backdrop').style.display = 'none';
  }

  function showToast(text) {
    const toast = document.getElementById('toast');
    toast.innerText = text;
    toast.style.display = 'block';

    setTimeout(() => {
      toast.style.display = 'none';
    }, 2500);
  }
</script>

</body>
</html>
