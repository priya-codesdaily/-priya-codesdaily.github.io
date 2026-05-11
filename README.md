<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Anshu Priya | Flutter Developer</title>
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@300;400;500;600&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg: #050507;
      --surface: #0c0c10;
      --card: #111116;
      --border: #1c1c24;
      --green: #00e87a;
      --amber: #f5a623;
      --cyan: #00d4ff;
      --red: #ff4444;
      --text: #efefef;
      --muted: #5a5a6e;
      --light: #9090a8;
    }
    * { margin: 0; padding: 0; box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body { background: var(--bg); color: var(--text); font-family: 'DM Sans', sans-serif; overflow-x: hidden; }
    body::after {
      content: ''; position: fixed; inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
      pointer-events: none; z-index: 999;
    }

    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      padding: 1.2rem 2.5rem; display: flex; justify-content: space-between; align-items: center;
      border-bottom: 1px solid var(--border); background: rgba(5,5,7,0.92); backdrop-filter: blur(16px);
    }
    .nav-logo { font-family: 'DM Mono', monospace; font-size: 0.8rem; color: var(--green); letter-spacing: 0.2em; }
    .nav-links { display: flex; gap: 2rem; list-style: none; }
    .nav-links a { color: var(--muted); text-decoration: none; font-size: 0.85rem; transition: color 0.2s; }
    .nav-links a:hover { color: var(--text); }

    /* HERO */
    .hero {
      min-height: 100vh; display: flex; align-items: center;
      padding: 8rem 2.5rem 4rem; position: relative; overflow: hidden;
    }
    .hero-bg {
      position: absolute; inset: 0;
      background: radial-gradient(ellipse 60% 50% at 75% 50%, rgba(0,232,122,0.05) 0%, transparent 70%),
                  radial-gradient(ellipse 40% 40% at 20% 80%, rgba(0,212,255,0.03) 0%, transparent 60%);
    }
    .hero-grid {
      position: absolute; inset: 0;
      background-image: linear-gradient(rgba(0,232,122,0.02) 1px, transparent 1px),
                        linear-gradient(90deg, rgba(0,232,122,0.02) 1px, transparent 1px);
      background-size: 80px 80px;
    }
    .hero-content { position: relative; max-width: 780px; }
    .hero-tag {
      display: inline-flex; align-items: center; gap: 0.5rem;
      font-family: 'DM Mono', monospace; font-size: 0.72rem; color: var(--green);
      letter-spacing: 0.2em; margin-bottom: 1.5rem;
      padding: 0.4rem 1rem; border: 1px solid rgba(0,232,122,0.2); border-radius: 2px;
    }
    .hero-tag::before { content: ''; width: 6px; height: 6px; background: var(--green); border-radius: 50%; animation: blink 2s infinite; }
    @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0.2; } }

    .hero-headline {
      font-size: clamp(1.4rem, 3vw, 2rem);
      font-weight: 600;
      color: var(--text);
      line-height: 1.3;
      margin-bottom: 1rem;
    }

    .hero h1 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(4rem, 10vw, 8.5rem);
      line-height: 0.9; letter-spacing: 0.02em; margin-bottom: 0.5rem;
    }
    .hero h1 .line1 { display: block; color: var(--text); }
    .hero h1 .line2 { display: block; color: transparent; -webkit-text-stroke: 1px rgba(255,255,255,0.12); }

    .hero-role {
      font-family: 'DM Mono', monospace;
      font-size: 0.85rem;
      color: var(--green);
      letter-spacing: 0.15em;
      margin-bottom: 1.2rem;
    }

    .hero-sub { font-size: 1rem; color: var(--light); line-height: 1.7; max-width: 540px; margin-bottom: 1.2rem; }
    .hero-proof {
      font-size: 0.88rem;
      color: var(--text);
      background: rgba(0,232,122,0.06);
      border: 1px solid rgba(0,232,122,0.15);
      border-left: 3px solid var(--green);
      padding: 0.8rem 1rem;
      border-radius: 0 4px 4px 0;
      margin-bottom: 2rem;
      max-width: 540px;
      line-height: 1.6;
    }
    .hero-cta { display: flex; gap: 1rem; flex-wrap: wrap; }

    .btn-primary {
      display: inline-flex; align-items: center; gap: 0.5rem;
      padding: 0.75rem 1.8rem; background: var(--green); color: #000;
      font-family: 'DM Mono', monospace; font-size: 0.78rem; font-weight: 500;
      letter-spacing: 0.08em; text-decoration: none; border-radius: 2px;
      transition: transform 0.2s, box-shadow 0.2s;
    }
    .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 8px 30px rgba(0,232,122,0.25); }

    .btn-outline {
      display: inline-flex; align-items: center; gap: 0.5rem;
      padding: 0.75rem 1.8rem; border: 1px solid var(--border); color: var(--light);
      font-family: 'DM Mono', monospace; font-size: 0.78rem;
      letter-spacing: 0.08em; text-decoration: none; border-radius: 2px;
      transition: border-color 0.2s, color 0.2s;
    }
    .btn-outline:hover { border-color: var(--green); color: var(--green); }

    .hero-stats {
      position: absolute; right: 2.5rem; bottom: 4rem;
      display: flex; flex-direction: column; gap: 1.5rem; text-align: right;
    }
    .stat-item .num { font-family: 'Bebas Neue', sans-serif; font-size: 2.5rem; color: var(--green); line-height: 1; }
    .stat-item .label { font-family: 'DM Mono', monospace; font-size: 0.65rem; color: var(--muted); letter-spacing: 0.15em; }

    /* SECTIONS */
    .section { padding: 6rem 2.5rem; max-width: 1100px; margin: 0 auto; }
    .section-eyebrow { font-family: 'DM Mono', monospace; font-size: 0.68rem; color: var(--green); letter-spacing: 0.25em; margin-bottom: 0.6rem; }
    .section-title { font-family: 'Bebas Neue', sans-serif; font-size: clamp(2.5rem, 5vw, 4rem); letter-spacing: 0.03em; margin-bottom: 3rem; line-height: 1; }
    hr.divider { border: none; border-top: 1px solid var(--border); }

    /* ABOUT */
    .about-grid { display: grid; grid-template-columns: 1.2fr 0.8fr; gap: 4rem; align-items: start; }
    .about-text p { color: var(--light); line-height: 1.8; margin-bottom: 1rem; font-size: 0.95rem; }
    .about-text p strong { color: var(--text); font-weight: 500; }
    .about-text blockquote {
      border-left: 2px solid var(--green); padding-left: 1.2rem; margin: 1.5rem 0;
      font-style: italic; color: var(--green); font-size: 0.88rem; line-height: 1.6;
    }
    .focus-list { list-style: none; margin-top: 1rem; }
    .focus-list li {
      color: var(--light); font-size: 0.88rem; padding: 0.4rem 0;
      border-bottom: 1px solid var(--border); display: flex; align-items: center; gap: 0.6rem;
    }
    .focus-list li::before { content: '→'; color: var(--green); font-family: 'DM Mono', monospace; flex-shrink: 0; }
    .stat-cards { display: grid; grid-template-columns: 1fr 1fr; gap: 0.8rem; }
    .stat-card { background: var(--card); border: 1px solid var(--border); padding: 1.2rem; border-radius: 2px; }
    .stat-card .n { font-family: 'Bebas Neue', sans-serif; font-size: 2.2rem; color: var(--green); line-height: 1; }
    .stat-card .l { font-size: 0.75rem; color: var(--muted); margin-top: 0.2rem; }

    /* PROJECTS */
    .featured-badge {
      display: inline-flex; align-items: center; gap: 0.4rem;
      font-family: 'DM Mono', monospace; font-size: 0.68rem;
      color: var(--amber); background: rgba(245,166,35,0.1);
      border: 1px solid rgba(245,166,35,0.2);
      padding: 0.25rem 0.7rem; border-radius: 2px;
      margin-bottom: 1.5rem;
    }

    .project-card-featured {
      background: var(--card); border: 1px solid var(--border);
      border-radius: 2px; overflow: hidden;
      transition: border-color 0.3s, transform 0.3s;
      margin-bottom: 1.5rem;
    }
    .project-card-featured:hover { transform: translateY(-3px); border-color: var(--green); }
    .project-card-featured .project-accent { height: 3px; background: linear-gradient(90deg, var(--green), var(--cyan)); }

    .project-card-secondary {
      background: var(--card); border: 1px solid var(--border);
      border-radius: 2px; overflow: hidden;
      transition: border-color 0.3s, transform 0.3s;
    }
    .project-card-secondary:hover { transform: translateY(-3px); border-color: var(--red); }
    .project-card-secondary .project-accent { height: 3px; background: linear-gradient(90deg, var(--red), #ff8800); }

    .project-body { padding: 2rem; }
    .project-header { display: flex; align-items: flex-start; justify-content: space-between; margin-bottom: 1rem; gap: 1rem; }
    .project-icon { font-size: 2rem; }
    .project-name { font-family: 'Bebas Neue', sans-serif; font-size: 2.2rem; letter-spacing: 0.05em; }
    .project-card-featured .project-name { color: var(--green); }
    .project-card-secondary .project-name { color: #ff6644; }
    .project-tagline { font-size: 0.75rem; color: var(--muted); font-family: 'DM Mono', monospace; margin-bottom: 1rem; }
    .project-desc { color: var(--light); font-size: 0.9rem; line-height: 1.7; margin-bottom: 1.2rem; }

    .innovations { margin-bottom: 1.2rem; }
    .innovations-title { font-family: 'DM Mono', monospace; font-size: 0.68rem; color: var(--green); letter-spacing: 0.15em; margin-bottom: 0.6rem; }
    .innovation-item { display: flex; align-items: flex-start; gap: 0.6rem; margin-bottom: 0.4rem; font-size: 0.85rem; color: var(--light); line-height: 1.5; }
    .innovation-item::before { content: '→'; color: var(--green); font-family: 'DM Mono', monospace; flex-shrink: 0; margin-top: 0.05rem; }

    .impact-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 0.6rem; margin-bottom: 1.2rem; }
    .impact-item { background: var(--surface); border: 1px solid var(--border); padding: 0.7rem; border-radius: 2px; font-size: 0.78rem; color: var(--muted); line-height: 1.4; }
    .impact-item strong { display: block; color: var(--green); font-family: 'DM Mono', monospace; font-size: 0.85rem; margin-bottom: 0.2rem; }

    .feature-pills { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-bottom: 1.5rem; }
    .pill { font-family: 'DM Mono', monospace; font-size: 0.68rem; padding: 0.25rem 0.6rem; background: var(--surface); border: 1px solid var(--border); border-radius: 2px; color: var(--muted); }

    .project-links { display: flex; gap: 0.8rem; flex-wrap: wrap; }
    .proj-btn { font-family: 'DM Mono', monospace; font-size: 0.72rem; padding: 0.55rem 1.1rem; text-decoration: none; border-radius: 2px; letter-spacing: 0.05em; transition: all 0.2s; display: inline-flex; align-items: center; gap: 0.4rem; }
    .proj-btn-green { background: var(--green); color: #000; }
    .proj-btn-green:hover { opacity: 0.85; }
    .proj-btn-amber { background: rgba(245,166,35,0.15); border: 1px solid rgba(245,166,35,0.3); color: var(--amber); }
    .proj-btn-amber:hover { background: rgba(245,166,35,0.25); }
    .proj-btn-outline { border: 1px solid var(--border); color: var(--light); }
    .proj-btn-outline:hover { border-color: var(--green); color: var(--green); }

    /* SKILLS */
    .skills-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(130px, 1fr)); gap: 0.6rem; }
    .skill { background: var(--card); border: 1px solid var(--border); padding: 0.8rem 1rem; border-radius: 2px; font-family: 'DM Mono', monospace; font-size: 0.72rem; color: var(--muted); display: flex; align-items: center; gap: 0.5rem; transition: border-color 0.2s, color 0.2s; }
    .skill:hover { border-color: var(--green); color: var(--green); }
    .skill .dot { width: 5px; height: 5px; border-radius: 50%; flex-shrink: 0; }
    .dot-green { background: var(--green); }
    .dot-cyan { background: var(--cyan); }
    .dot-amber { background: var(--amber); }

    /* CONTACT */
    .contact-wrap { background: var(--card); border: 1px solid var(--border); padding: 3.5rem; border-radius: 2px; position: relative; overflow: hidden; }
    .contact-wrap::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px; background: linear-gradient(90deg, var(--green), var(--cyan), var(--amber)); }
    .contact-title { font-family: 'Bebas Neue', sans-serif; font-size: clamp(2rem, 4vw, 3.5rem); margin-bottom: 0.8rem; }
    .contact-sub { color: var(--light); margin-bottom: 2rem; font-size: 0.95rem; line-height: 1.6; }
    .contact-links { display: flex; gap: 1rem; flex-wrap: wrap; }

    footer { border-top: 1px solid var(--border); padding: 1.5rem 2.5rem; display: flex; justify-content: space-between; align-items: center; }
    footer p { font-family: 'DM Mono', monospace; font-size: 0.68rem; color: var(--muted); }
    .open-badge { display: flex; align-items: center; gap: 0.4rem; font-family: 'DM Mono', monospace; font-size: 0.68rem; color: var(--green); }
    .open-badge::before { content: ''; width: 5px; height: 5px; background: var(--green); border-radius: 50%; animation: blink 2s infinite; }

    .fade-up { opacity: 0; transform: translateY(24px); transition: opacity 0.6s ease, transform 0.6s ease; }
    .fade-up.visible { opacity: 1; transform: translateY(0); }

    @media (max-width: 768px) {
      nav { padding: 1rem 1.5rem; }
      .nav-links { display: none; }
      .hero { padding: 7rem 1.5rem 3rem; }
      .hero-stats { display: none; }
      .section { padding: 4rem 1.5rem; }
      .about-grid { grid-template-columns: 1fr; gap: 2rem; }
      .impact-grid { grid-template-columns: 1fr; }
      .contact-wrap { padding: 2rem 1.5rem; }
      footer { flex-direction: column; gap: 0.5rem; }
    }
  </style>
</head>
<body>

<nav>
  <span class="nav-logo">ANSHU.PRIYA</span>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<div class="hero">
  <div class="hero-bg"></div>
  <div class="hero-grid"></div>
  <div class="hero-content">
    <div class="hero-tag">AVAILABLE FOR WORK</div>
    <p class="hero-headline">I build real-world apps that solve real problems.</p>
    <h1>
      <span class="line1">ANSHU</span>
      <span class="line2">PRIYA</span>
    </h1>
    <p class="hero-role">FLUTTER DEVELOPER · AGRITECH & SAFETY</p>
    <p class="hero-sub">
      Turning real-life problems into scalable products using data, logic, and user-first design.
      Self-taught. Age 20. From Odisha, India.
    </p>
    <div class="hero-proof">
      🌾 Built AgroPredict — a crop price intelligence app using live government data to help farmers make profit-driven selling decisions.
    </div>
    <div class="hero-cta">
      <a href="#projects" class="btn-primary">View Projects →</a>
      <a href="https://github.com/priya-codesdaily" target="_blank" class="btn-outline">GitHub</a>
      <a href="mailto:priyatech.logic@gmail.com" class="btn-outline">Email Me</a>
    </div>
  </div>
  <div class="hero-stats">
    <div class="stat-item"><div class="num">2</div><div class="label">REAL APPS BUILT</div></div>
    <div class="stat-item"><div class="num">140M</div><div class="label">FARMERS TARGETED</div></div>
    <div class="stat-item"><div class="num">0</div><div class="label">TUTORIAL PROJECTS</div></div>
  </div>
</div>

<hr class="divider"/>

<!-- ABOUT -->
<section class="section fade-up" id="about">
  <p class="section-eyebrow">// 01 — ABOUT</p>
  <h2 class="section-title">WHO I AM</h2>
  <div class="about-grid">
    <div class="about-text">
      <p>I'm <strong>Anshu Priya</strong>, a self-taught Flutter developer from Odisha, India. No placement cell. No family guidance in tech. Just curiosity, a laptop, and problems worth solving.</p>
      <p>I don't just build apps — I solve problems I've personally seen. <strong>AgroPredict</strong> came from watching my father struggle with crop pricing decisions. <strong>REPSHIELD</strong> came from understanding how delayed reactions can cost safety.</p>
      <blockquote>
        "My mother made aamchur instead of selling fresh mangoes — that's value addition. I built AgroPredict so every farmer can make the same smart decision."
      </blockquote>
      <p>I focus on:</p>
      <ul class="focus-list">
        <li>Real-world problem solving — not just UI</li>
        <li>Clean logic + decision-making systems</li>
        <li>Building for impact, not just portfolios</li>
        <li>Accessibility — Hindi, voice, low-literacy users</li>
      </ul>
      <p style="margin-top:1rem;">Currently looking for opportunities where I can <strong>contribute to meaningful products</strong> and grow as a developer. Remote preferred. Open to Hyderabad.</p>
    </div>
    <div class="stat-cards">
      <div class="stat-card"><div class="n">20</div><div class="l">YEARS OLD</div></div>
      <div class="stat-card"><div class="n">2</div><div class="l">REAL APPS LIVE</div></div>
      <div class="stat-card"><div class="n">6+</div><div class="l">PACKAGES USED</div></div>
      <div class="stat-card"><div class="n">∞</div><div class="l">DRIVE TO BUILD</div></div>
    </div>
  </div>
</section>

<hr class="divider"/>

<!-- PROJECTS -->
<section class="section fade-up" id="projects">
  <p class="section-eyebrow">// 02 — PROJECTS</p>
  <h2 class="section-title">WHAT I BUILT</h2>

  <!-- AGROPREDICT FEATURED -->
  <div class="featured-badge">⭐ FEATURED PROJECT</div>
  <div class="project-card-featured">
    <div class="project-accent"></div>
    <div class="project-body">
      <div class="project-header">
        <div>
          <div class="project-icon">🌾</div>
          <div class="project-name">AGROPREDICT</div>
          <div class="project-tagline">AgriTech · Flutter · Live Government Data · Hindi + Voice</div>
        </div>
      </div>

      <p class="project-desc">
        AI-powered crop price intelligence app that helps farmers decide <strong style="color:var(--text)">WHERE and WHEN to sell</strong> for maximum profit.
        Built using India's AGMARKNET data, AgroPredict goes beyond price display — it calculates real profit after transport cost and gives actionable sell/wait advice.
      </p>

      <div class="innovations">
        <div class="innovations-title">KEY INNOVATIONS</div>
        <div class="innovation-item">Combines mandi price + transport cost → real profit decision (not just price display)</div>
        <div class="innovation-item">Smart SELL / WAIT logic based on price variance and trend analysis</div>
        <div class="innovation-item">Designed for low-literacy users — Hindi UI + voice input for accessibility</div>
      </div>

      <div class="impact-grid">
        <div class="impact-item"><strong>3000+</strong>Mandis covered across India</div>
        <div class="impact-item"><strong>140M+</strong>Farmers who need this</div>
        <div class="impact-item"><strong>20-30%</strong>Better selling opportunities</div>
      </div>

      <div class="feature-pills">
        <span class="pill">AGMARKNET API</span>
        <span class="pill">Smart Sell Decision</span>
        <span class="pill">Transport Calculator</span>
        <span class="pill">Price Chart</span>
        <span class="pill">Hindi Language</span>
        <span class="pill">Voice Input</span>
      </div>

      <div class="project-links">
        <a href="https://github.com/priya-codesdaily/agropredict" target="_blank" class="proj-btn proj-btn-green">💻 GitHub →</a>
        <a href="https://github.com/priya-codesdaily/agropredict" target="_blank" class="proj-btn proj-btn-amber">🎥 Demo Coming Soon</a>
      </div>
    </div>
  </div>

  <!-- REPSHIELD -->
  <div class="project-card-secondary">
    <div class="project-accent"></div>
    <div class="project-body">
      <div class="project-icon">🔐</div>
      <div class="project-name">REPSHIELD</div>
      <div class="project-tagline">Safety App · Android · Emergency Tech · v1.0.0</div>

      <p class="project-desc">
        A personal safety app designed for real emergency situations where time matters.
        Triggers SOS alerts instantly with a shake — <strong style="color:var(--text)">no unlock, no delay</strong> — ensuring faster response in critical moments.
      </p>

      <div class="innovations">
        <div class="innovations-title">WHY IT MATTERS</div>
        <div class="innovation-item">In India, 1 woman is assaulted every 15 minutes — most safety apps require 3 steps to activate</div>
        <div class="innovation-item">REPSHIELD reduces emergency response to one shake — no unlock, no typing required</div>
        <div class="innovation-item">Built for real-world scenarios where every second counts</div>
      </div>

      <div class="feature-pills">
        <span class="pill">Shake-to-SOS</span>
        <span class="pill">Live GPS</span>
        <span class="pill">Trusted Contacts</span>
        <span class="pill">Stealth Mode</span>
        <span class="pill">SHA-256 Journal</span>
        <span class="pill">Safety Timer</span>
      </div>

      <div class="project-links">
        <a href="https://github.com/priya-codesdaily/REPSHIELD" target="_blank" class="proj-btn proj-btn-green">💻 GitHub →</a>
        <a href="https://github.com/priya-codesdaily/REPSHIELD/releases/tag/v1.0.0" target="_blank" class="proj-btn proj-btn-outline">📲 Download APK</a>
      </div>
    </div>
  </div>
</section>

<hr class="divider"/>

<!-- SKILLS -->
<section class="section fade-up" id="skills">
  <p class="section-eyebrow">// 03 — SKILLS</p>
  <h2 class="section-title">TECH STACK</h2>
  <div class="skills-grid">
    <div class="skill"><span class="dot dot-green"></span>Flutter</div>
    <div class="skill"><span class="dot dot-green"></span>Dart</div>
    <div class="skill"><span class="dot dot-cyan"></span>Python</div>
    <div class="skill"><span class="dot dot-green"></span>Geolocator</div>
    <div class="skill"><span class="dot dot-green"></span>sensors_plus</div>
    <div class="skill"><span class="dot dot-green"></span>speech_to_text</div>
    <div class="skill"><span class="dot dot-cyan"></span>REST APIs</div>
    <div class="skill"><span class="dot dot-cyan"></span>Firebase</div>
    <div class="skill"><span class="dot dot-cyan"></span>Git & GitHub</div>
    <div class="skill"><span class="dot dot-cyan"></span>Android Build</div>
    <div class="skill"><span class="dot dot-amber"></span>fl_chart</div>
    <div class="skill"><span class="dot dot-amber"></span>shared_prefs</div>
    <div class="skill"><span class="dot dot-cyan"></span>Gradle / NDK</div>
    <div class="skill"><span class="dot dot-green"></span>State Mgmt</div>
    <div class="skill"><span class="dot dot-amber"></span>UI/UX Design</div>
    <div class="skill"><span class="dot dot-cyan"></span>VS Code</div>
  </div>
</section>

<hr class="divider"/>

<!-- CONTACT -->
<section class="section fade-up" id="contact">
  <div class="contact-wrap">
    <p class="section-eyebrow">// 04 — CONTACT</p>
    <h2 class="contact-title">LET'S WORK TOGETHER</h2>
    <p class="contact-sub">
      I'm actively looking for Flutter developer opportunities — full-time, internship, or remote.<br/>
      I'm more interested in building meaningful products than just working on features.<br/>
      If your team solves real problems — let's talk.
    </p>
    <div class="contact-links">
      <a href="https://github.com/priya-codesdaily" target="_blank" class="btn-primary">GitHub →</a>
      <a href="https://linkedin.com/in/a-priya-dev" target="_blank" class="btn-outline">LinkedIn</a>
      <a href="mailto:priyatech.logic@gmail.com" class="btn-outline">Email Me</a>
    </div>
  </div>
</section>

<footer>
  <p>© 2026 Anshu Priya · Flutter Developer · Odisha, India</p>
  <span class="open-badge">OPEN TO WORK</span>
</footer>

<script>
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.1 });
  document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));
</script>
</body>
</html>
