<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta http-equiv="Content-Security-Policy" content="default-src 'none'; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; font-src https://fonts.gstatic.com; script-src 'self' 'unsafe-inline'; img-src 'self' data:; connect-src 'none'; object-src 'none'; base-uri 'none'; form-action 'none'; frame-ancestors 'none';">
<meta http-equiv="X-Content-Type-Options" content="nosniff">
<meta name="referrer" content="no-referrer">
<title>GWT CREATIONS</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@600;800;900&family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  * { box-sizing: border-box; }
  html, body { height: 100%; }
  body {
    margin: 0;
    font-family: 'Poppins', 'Segoe UI', Arial, sans-serif;
    background: #050506;
    min-height: 100vh;
    color: #f2eeee;
    padding: 24px 20px;
    position: relative;
    overflow-x: hidden;
    -webkit-font-smoothing: antialiased;
  }

  /* ---- Battlefield / gaming-console background layers ---- */
  #bg-fx {
    position: fixed;
    inset: 0;
    z-index: 0;
    pointer-events: none;
    overflow: hidden;
    background:
      radial-gradient(circle at 12% 18%, rgba(90,95,90,0.15) 0, rgba(90,95,90,0.15) 7%, transparent 8%),
      radial-gradient(circle at 78% 8%, rgba(70,75,70,0.12) 0, rgba(70,75,70,0.12) 9%, transparent 10%),
      radial-gradient(circle at 90% 55%, rgba(60,70,65,0.14) 0, rgba(60,70,65,0.14) 11%, transparent 12%),
      radial-gradient(circle at 25% 85%, rgba(80,85,75,0.12) 0, rgba(80,85,75,0.12) 8%, transparent 9%),
      radial-gradient(circle at 55% 40%, rgba(50,55,55,0.1) 0, rgba(50,55,55,0.1) 14%, transparent 15%),
      radial-gradient(ellipse at 50% 105%, rgba(6,214,209,0.09), transparent 55%),
      radial-gradient(ellipse at 50% -5%, rgba(6,214,209,0.06), transparent 50%),
      linear-gradient(180deg, #060406 0%, #0c0708 45%, #060406 100%);
  }
  /* Hex-grid HUD overlay */
  #bg-fx::before {
    content: "";
    position: absolute;
    inset: -10%;
    opacity: 0.35;
    background-image:
      linear-gradient(30deg, rgba(6,214,209,0.05) 1px, transparent 1px),
      linear-gradient(150deg, rgba(6,214,209,0.05) 1px, transparent 1px),
      linear-gradient(90deg, rgba(6,214,209,0.03) 1px, transparent 1px);
    background-size: 46px 80px, 46px 80px, 46px 80px;
  }
  /* Slow radar sweep */
  #bg-fx::after {
    content: "";
    position: absolute;
    top: -35vw; right: -35vw;
    width: 70vw; height: 70vw;
    border-radius: 50%;
    background: conic-gradient(from 0deg, rgba(6,214,209,0.1), transparent 25%);
    animation: radarSpin 11s linear infinite;
    opacity: 0.4;
  }
  @keyframes radarSpin { to { transform: rotate(360deg); } }

  /* Subtle film-grain texture for a matte premium finish */
  .grain-fx {
    position: fixed; inset: 0; z-index: 1; pointer-events: none;
    opacity: 0.035;
    mix-blend-mode: overlay;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='120' height='120'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='2' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
  }
  /* CRT scanlines */
  .scanlines {
    position: fixed; inset: 0; z-index: 1; pointer-events: none;
    background: repeating-linear-gradient(
      0deg, rgba(255,255,255,0.018) 0px, rgba(255,255,255,0.018) 1px,
      transparent 1px, transparent 3px
    );
    mix-blend-mode: overlay;
  }
  /* Vignette */
  .vignette {
    position: fixed; inset: 0; z-index: 1; pointer-events: none;
    background: radial-gradient(ellipse at center, transparent 40%, rgba(0,0,0,0.72) 100%);
  }
  /* Crosshair watermark */
  .crosshair-fx {
    position: fixed; bottom: -60px; right: -60px; z-index: 0; pointer-events: none;
    width: 320px; height: 320px; opacity: 0.05;
  }
  .crosshair-fx svg { width: 100%; height: 100%; }

  /* Generic soldier silhouette (bottom-left) */
  .soldier-fx {
    position: fixed; bottom: 0; left: -20px; z-index: 0; pointer-events: none;
    width: 260px; height: 420px; opacity: 0.08;
  }
  .soldier-fx svg { width: 100%; height: 100%; }

  /* Generic game-controller silhouette (top-right) */
  .controller-fx {
    position: fixed; top: 30px; right: 20px; z-index: 0; pointer-events: none;
    width: 150px; height: 100px; opacity: 0.07;
  }
  .controller-fx svg { width: 100%; height: 100%; }

  /* Generic parachute silhouette (top-left, drifting animation) */
  .parachute-fx {
    position: fixed; top: 60px; left: 6vw; z-index: 0; pointer-events: none;
    width: 110px; height: 140px; opacity: 0.06;
    animation: driftFx 12s ease-in-out infinite;
  }
  .parachute-fx svg { width: 100%; height: 100%; }
  @keyframes driftFx {
    0%, 100% { transform: translateY(0) translateX(0); }
    50% { transform: translateY(18px) translateX(-10px); }
  }

  .container { max-width: 720px; margin: 0 auto; position: relative; z-index: 2; }
  .view { display: none; animation: fadeIn 0.4s cubic-bezier(0.16,1,0.3,1); }
  .view.active { display: block; }
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ---------- Brand header ---------- */
  .brand-wrap { text-align: center; margin-bottom: 8px; }
  .logo-badge {
    width: 84px; height: 84px; margin: 0 auto 10px;
    filter: drop-shadow(0 0 14px rgba(6,214,209,0.35));
    animation: logoFloat 4s ease-in-out infinite;
  }
  @keyframes logoFloat {
    0%, 100% { transform: translateY(0) rotate(0deg); filter: drop-shadow(0 0 14px rgba(6,214,209,0.35)); }
    50% { transform: translateY(-6px) rotate(2deg); filter: drop-shadow(0 0 22px rgba(6,214,209,0.55)); }
  }
  .logo-badge svg { width: 100%; height: 100%; }
  .brand {
    font-family: 'Orbitron', sans-serif;
    font-size: 38px;
    font-weight: 900;
    letter-spacing: 5px;
    background: linear-gradient(90deg, #06d6d1 0%, #ffffff 25%, #e7c469 50%, #ffffff 75%, #06d6d1 100%);
    background-size: 250% 100%;
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
    text-shadow: 0 0 30px rgba(6,214,209,0.35);
    margin: 0;
    animation: shimmer 5s linear infinite;
  }
  @keyframes shimmer {
    0% { background-position: 0% 50%; }
    100% { background-position: -250% 50%; }
  }
  .brand-divider { display: flex; justify-content: center; margin: 14px auto; opacity: 0.9; }
  .brand-divider svg { width: 160px; height: 20px; }
  .brand-sub {
    text-align: center;
    color: #8a8b8f;
    margin: 0 0 40px;
    font-size: 11px;
    letter-spacing: 3px;
    text-transform: uppercase;
    font-weight: 500;
  }
  .founder-tag {
    text-align: center;
    font-size: 12px;
    color: #5f6c73;
    margin-bottom: 34px;
    letter-spacing: 0.5px;
  }
  .founder-tag b { color: #06d6d1; font-weight: 600; }

  /* ---------- Menu cards ---------- */
  .menu-cards { display: flex; flex-direction: column; gap: 18px; }
  .menu-card {
    position: relative;
    display: flex;
    align-items: center;
    gap: 18px;
    background: linear-gradient(155deg, rgba(24,17,18,0.9), rgba(10,8,9,0.95));
    border: 1px solid rgba(6,214,209,0.18);
    border-radius: 18px;
    padding: 22px 24px;
    text-align: left;
    cursor: pointer;
    overflow: hidden;
    box-shadow: 0 1px 0 rgba(255,255,255,0.03) inset, 0 12px 24px rgba(0,0,0,0.35);
    transition: transform 0.3s cubic-bezier(0.16,1,0.3,1), border-color 0.3s, box-shadow 0.3s;
    animation: cardIn 0.6s cubic-bezier(0.16,1,0.3,1) backwards;
  }
  .menu-card:nth-child(1) { animation-delay: 0.05s; }
  .menu-card:nth-child(2) { animation-delay: 0.15s; }
  @keyframes cardIn {
    from { opacity: 0; transform: translateY(16px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .menu-card::after {
    content: "";
    position: absolute; inset: 0; border-radius: 18px;
    padding: 1px;
    background: linear-gradient(135deg, rgba(231,196,105,0.5), transparent 40%, rgba(6,214,209,0.4));
    -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
    -webkit-mask-composite: xor;
    mask-composite: exclude;
    opacity: 0.6;
    pointer-events: none;
  }
  .menu-card:hover {
    transform: translateY(-4px);
    border-color: rgba(6,214,209,0.4);
    box-shadow: 0 1px 0 rgba(255,255,255,0.05) inset, 0 20px 40px rgba(0,0,0,0.5), 0 0 30px rgba(6,214,209,0.1);
  }
  .menu-card:active { transform: translateY(-1px) scale(0.99); }
  .menu-icon {
    flex-shrink: 0;
    width: 58px; height: 58px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 26px;
    background: radial-gradient(circle at 35% 30%, rgba(6,214,209,0.25), rgba(0,0,0,0.4));
    border: 1px solid rgba(6,214,209,0.35);
    box-shadow: 0 0 18px rgba(6,214,209,0.2) inset, 0 4px 10px rgba(0,0,0,0.4);
    transition: transform 0.35s cubic-bezier(0.16,1,0.3,1), box-shadow 0.35s;
  }
  .menu-card:hover .menu-icon {
    transform: scale(1.1) rotate(-6deg);
    box-shadow: 0 0 26px rgba(6,214,209,0.4) inset, 0 4px 14px rgba(0,0,0,0.5);
  }
  .menu-text { flex: 1; }
  .menu-title {
    font-family: 'Orbitron', sans-serif;
    font-size: 16px; font-weight: 700; margin-bottom: 4px;
    color: #fff;
    letter-spacing: 1.2px;
  }
  .menu-sub { font-size: 12.5px; color: #9a9ba0; line-height: 1.4; }
  .menu-arrow {
    flex-shrink: 0; color: #06d6d1; font-size: 20px; opacity: 0.7;
    transition: transform 0.3s;
  }
  .menu-card:hover .menu-arrow { transform: translateX(4px); opacity: 1; }

  /* ---------- Our Work columns ---------- */
  .work-heading {
    font-family: 'Orbitron', sans-serif;
    font-size: 13px; font-weight: 700; letter-spacing: 2px;
    color: #8f9498; text-align: center;
    margin: 40px 0 18px;
  }
  .work-heading span { color: #06d6d1; }
  .work-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
  }
  .work-col {
    background: linear-gradient(155deg, rgba(20,15,16,0.85), rgba(8,7,8,0.9));
    border: 1px solid rgba(6,214,209,0.14);
    border-radius: 14px;
    padding: 16px 12px;
    text-align: center;
    transition: transform 0.3s cubic-bezier(0.16,1,0.3,1), border-color 0.3s, box-shadow 0.3s;
    animation: cardIn 0.6s cubic-bezier(0.16,1,0.3,1) backwards;
  }
  .work-col:nth-child(1) { animation-delay: 0.25s; }
  .work-col:nth-child(2) { animation-delay: 0.32s; }
  .work-col:nth-child(3) { animation-delay: 0.39s; }
  .work-col:hover {
    transform: translateY(-4px);
    border-color: rgba(6,214,209,0.4);
    box-shadow: 0 10px 24px rgba(0,0,0,0.4), 0 0 20px rgba(6,214,209,0.12);
  }
  .work-icon { font-size: 22px; margin-bottom: 8px; transition: transform 0.3s; }
  .work-col:hover .work-icon { transform: scale(1.15); }
  .work-title {
    font-family: 'Orbitron', sans-serif;
    font-size: 11px; font-weight: 700; letter-spacing: 0.6px;
    color: #fff; margin-bottom: 6px;
  }
  .work-desc { font-size: 11px; line-height: 1.4; color: #9a9ba0; }
  @media (max-width: 420px) {
    .work-grid { grid-template-columns: 1fr; }
  }

  /* ---------- Buttons ---------- */
  .back-btn {
    background: rgba(255,255,255,0.03);
    border: 1px solid rgba(255,255,255,0.12);
    color: #d8d9dc;
    padding: 9px 20px;
    border-radius: 10px;
    cursor: pointer;
    font-size: 12.5px;
    font-weight: 600;
    letter-spacing: 1px;
    margin-bottom: 24px;
    transition: background 0.2s, border-color 0.2s, transform 0.15s;
  }
  .back-btn:hover { background: rgba(6,214,209,0.1); border-color: rgba(6,214,209,0.3); color: #fff; }
  .back-btn:active { transform: scale(0.96); }

  h1.page-title, h2.page-title {
    text-align: center;
    font-family: 'Orbitron', sans-serif;
    font-size: 23px;
    font-weight: 800;
    letter-spacing: 2px;
    margin-bottom: 8px;
    background: linear-gradient(180deg, #ffffff, #e7c469 60%, #06d6d1);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
  }
  p.sub { text-align: center; color: #8a8b8f; margin-top: 0; margin-bottom: 28px; font-size: 13px; }

  /* ---------- Name style generator ---------- */
  .input-box { display: flex; gap: 12px; margin-bottom: 26px; }
  input[type="text"] {
    flex: 1; padding: 15px 18px;
    border-radius: 12px; border: 1px solid rgba(255,255,255,0.1);
    font-size: 15px; outline: none;
    background: rgba(255,255,255,0.96); color: #16171a;
    box-shadow: 0 4px 14px rgba(0,0,0,0.25);
    transition: box-shadow 0.2s;
  }
  input[type="text"]::placeholder { color: #8a8b8f; }
  input[type="text"]:focus { box-shadow: 0 0 0 3px rgba(6,214,209,0.3), 0 4px 14px rgba(0,0,0,0.25); }
  button.generate-btn {
    padding: 15px 26px; border: none; border-radius: 12px;
    background: linear-gradient(135deg, #28f0e6, #0891a8);
    color: #fff; font-weight: 700; cursor: pointer; font-size: 14px;
    letter-spacing: 0.6px;
    box-shadow: 0 8px 20px rgba(8,145,168,0.4);
    transition: transform 0.2s, box-shadow 0.2s;
  }
  button.generate-btn:hover { transform: translateY(-2px); box-shadow: 0 12px 26px rgba(8,145,168,0.5); }
  button.generate-btn:active { transform: translateY(0) scale(0.97); }

  .results { display: flex; flex-direction: column; gap: 11px; max-height: 60vh; overflow-y: auto; padding-right: 4px; }
  .style-card {
    background: rgba(255,255,255,0.035);
    border: 1px solid rgba(255,255,255,0.07);
    border-radius: 12px; padding: 14px 16px;
    display: flex; justify-content: space-between; align-items: center; gap: 12px;
    transition: border-color 0.2s, background 0.2s, transform 0.15s;
  }
  .style-card:hover { border-color: rgba(6,214,209,0.35); background: rgba(6,214,209,0.05); transform: translateX(2px); }
  .style-text { font-size: 17px; word-break: break-word; flex: 1; color: #f2eeee; }
  .copy-btn {
    background: rgba(6,214,209,0.1); border: 1px solid rgba(6,214,209,0.35); color: #5eead4;
    padding: 7px 15px; border-radius: 8px; cursor: pointer; font-size: 12px; font-weight: 600; white-space: nowrap;
    letter-spacing: 0.4px;
    transition: background 0.2s, transform 0.15s;
  }
  .copy-btn:hover { background: rgba(6,214,209,0.2); }
  .copy-btn:active { transform: scale(0.94); }
  .copy-btn.copied { background: rgba(45,201,110,0.15); border-color: #2dc96e; color: #4ade80; }
  .empty-msg { text-align: center; color: #64656a; padding: 34px 0; font-size: 14px; }

  /* ---------- Phone grid ---------- */
  .phone-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(148px, 1fr));
    gap: 13px;
  }
  .phone-card {
    background: linear-gradient(155deg, rgba(24,17,18,0.9), rgba(10,8,9,0.95));
    border: 1px solid rgba(6,214,209,0.16);
    border-radius: 14px;
    padding: 20px 12px;
    text-align: center;
    cursor: pointer;
    font-size: 13px;
    font-weight: 600;
    color: #e4e5e8;
    box-shadow: 0 8px 18px rgba(0,0,0,0.3);
    transition: transform 0.2s cubic-bezier(0.16,1,0.3,1), border-color 0.2s, box-shadow 0.2s;
  }
  .phone-card:hover {
    transform: translateY(-4px);
    border-color: rgba(6,214,209,0.45);
    box-shadow: 0 16px 28px rgba(0,0,0,0.45), 0 0 22px rgba(6,214,209,0.12);
  }
  .phone-card:active { transform: translateY(-1px) scale(0.98); }
  .phone-icon {
    width: 44px; height: 44px; margin: 0 auto 10px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 20px;
    background: radial-gradient(circle at 35% 30%, rgba(6,214,209,0.2), rgba(0,0,0,0.4));
    border: 1px solid rgba(6,214,209,0.3);
  }

  /* ---------- Sensitivity detail ---------- */
  .sens-list { display: flex; flex-direction: column; gap: 12px; margin-top: 12px; }
  .sens-row {
    background: rgba(255,255,255,0.035);
    border: 1px solid rgba(255,255,255,0.07);
    border-radius: 12px;
    padding: 14px 16px;
    transition: border-color 0.2s;
  }
  .sens-row:hover { border-color: rgba(6,214,209,0.3); }
  .sens-top { display: flex; justify-content: space-between; align-items: center; margin-bottom: 9px; }
  .sens-label { font-size: 13.5px; color: #c9cad0; font-weight: 600; letter-spacing: 0.5px; }
  .sens-value {
    font-weight: 700;
    color: #fff;
    background: linear-gradient(135deg, #28f0e6, #0891a8);
    padding: 3px 13px;
    border-radius: 6px;
    font-size: 13.5px;
    box-shadow: 0 3px 8px rgba(8,145,168,0.4);
  }
  .sens-bar-track {
    width: 100%; height: 6px; border-radius: 4px;
    background: rgba(255,255,255,0.06); overflow: hidden;
  }
  .sens-bar-fill {
    height: 100%; border-radius: 4px;
    background: linear-gradient(90deg, #0891a8, #28f0e6, #e7c469);
    box-shadow: 0 0 10px rgba(6,214,209,0.5);
  }
  .disclaimer {
    font-size: 11.5px;
    color: #64656a;
    text-align: center;
    margin-top: 24px;
    line-height: 1.7;
  }
  footer {
    text-align: center;
    color: #64656a;
    font-size: 11.5px;
    margin-top: 38px;
    padding-top: 20px;
    border-top: 1px solid rgba(255,255,255,0.06);
    letter-spacing: 0.5px;
  }
  footer b { color: #06d6d1; }

  /* Scrollbar polish */
  .results::-webkit-scrollbar { width: 6px; }
  .results::-webkit-scrollbar-thumb { background: rgba(6,214,209,0.3); border-radius: 3px; }

  /* ---------- Wave column: a dedicated vertical strip of bars pulsing up/down ---------- */
  .wave-column {
    position: fixed; top: 0; bottom: 0; z-index: 0; pointer-events: none;
    width: 46px;
    display: flex; flex-direction: row; align-items: center; justify-content: center;
    gap: 4px;
    opacity: 0.28;
  }
  .wave-column.wave-left { left: 0; }
  .wave-column.wave-right { right: 0; }
  .wave-bar {
    width: 4px; border-radius: 3px;
    background: linear-gradient(180deg, #28f0e6, #e7c469);
    animation: wavePulse 1.3s ease-in-out infinite;
    transform-origin: center;
  }
  @keyframes wavePulse {
    0%, 100% { transform: scaleY(0.25); opacity: 0.5; }
    50% { transform: scaleY(1); opacity: 1; }
  }

  /* ---------- Stat chips ---------- */
  .stats-strip { display: flex; justify-content: center; gap: 10px; margin: 0 0 30px; flex-wrap: wrap; }
  .stat-chip {
    display: flex; align-items: center; gap: 6px;
    background: rgba(6,214,209,0.06);
    border: 1px solid rgba(6,214,209,0.22);
    border-radius: 30px;
    padding: 7px 14px;
    font-size: 11px; font-weight: 600; letter-spacing: 0.5px;
    color: #c9e9e7;
    animation: cardIn 0.6s cubic-bezier(0.16,1,0.3,1) backwards;
  }
  .stat-chip:nth-child(1) { animation-delay: 0.1s; }
  .stat-chip:nth-child(2) { animation-delay: 0.18s; }
  .stat-chip:nth-child(3) { animation-delay: 0.26s; }
  .stat-chip .dot { width: 6px; height: 6px; border-radius: 50%; background: #06d6d1; box-shadow: 0 0 8px #06d6d1; flex-shrink: 0; }

  /* ---------- Search box ---------- */
  .search-box { position: relative; margin-bottom: 20px; }
  .search-box input[type="search"] {
    width: 100%; padding: 13px 16px 13px 40px;
    border-radius: 12px; border: 1px solid rgba(255,255,255,0.1);
    font-size: 14px; outline: none;
    background: rgba(255,255,255,0.04); color: #f2eeee;
    transition: border-color 0.2s, background 0.2s;
    font-family: 'Poppins', sans-serif;
  }
  .search-box input[type="search"]::placeholder { color: #6a6b70; }
  .search-box input[type="search"]:focus { border-color: rgba(6,214,209,0.5); background: rgba(6,214,209,0.05); }
  .search-box::before {
    content: "⌕"; position: absolute; left: 14px; top: 50%; transform: translateY(-50%);
    color: #5eead4; font-size: 17px; pointer-events: none;
  }
  .no-results { text-align: center; color: #64656a; padding: 24px 0; font-size: 13px; grid-column: 1 / -1; }

  /* ---------- Results toolbar / copy-all ---------- */
  .results-toolbar { display: flex; justify-content: flex-end; margin: -14px 0 14px; }
  .co
