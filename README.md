<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Asif Mahmud | Gaming Video Editor & Motion Designer</title>
    
    <meta name="description" content="Portfolio of Asif Mahmud, a professional Gaming Video Editor & Motion Designer specializing in esports edits, high-energy fragmovies, motion graphics, and content creation.">
    <meta name="keywords" content="Gaming Video Editor, Esports Editor, Asif Mahmud, Motion Designer, Premiere Pro, After Effects, Fragmovie, YouTube Gaming">
    <meta name="author" content="Asif Mahmud">

    <meta property="og:type" content="website">
    <meta property="og:title" content="Asif Mahmud | Gaming Video Editor & Motion Designer">
    <meta property="og:description" content="I turn raw gameplay and footage into epic high-octane stories worth watching. Explore gaming edits, showreel, and motion work.">
    <meta property="og:image" content="https://images.unsplash.com/photo-1542751371-adc38448a05e?auto=format&fit=crop&w=1200&q=80">

    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Syne:wght@700;800&display=swap" rel="stylesheet">

    <style>
        /* --- CSS VARIABLES & BASE RESET --- */
        :root {
            --bg: #050505;
            --surface: #0d0d0d;
            --surface-light: #151515;
            --text: #ffffff;
            --muted: #888888;
            --accent: #ff0000;
            --accent-glow: rgba(255, 0, 0, 0.35);
            --border: #292929;
            --font-main: 'Space Grotesk', sans-serif;
            --font-heading: 'Syne', sans-serif;
            --transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
            background-color: var(--bg);
            color: var(--text);
            font-family: var(--font-main);
            overflow-x: hidden;
        }

        body {
            position: relative;
            line-height: 1.6;
            background-color: var(--bg);
        }

        /* --- BACKGROUND TECHNICAL GRID & CANVAS --- */
        #particle-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .tech-grid {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(to right, rgba(255, 0, 0, 0.03) 1px, transparent 1px),
                linear-gradient(to bottom, rgba(255, 255, 255, 0.02) 1px, transparent 1px);
            background-size: 60px 60px;
            pointer-events: none;
            z-index: 0;
        }

        /* --- TYPOGRAPHY & REUSABLE COMPONENTS --- */
        h1, h2, h3, h4 {
            font-family: var(--font-heading);
            text-transform: uppercase;
            letter-spacing: -0.02em;
        }

        a {
            color: inherit;
            text-decoration: none;
        }

        .container {
            max-width: 1280px;
            margin: 0 auto;
            padding: 0 24px;
            position: relative;
            z-index: 2;
        }

        .section-padding {
            padding: 120px 0;
        }

        .section-header {
            margin-bottom: 60px;
        }

        .section-tag {
            color: var(--accent);
            font-size: 0.85rem;
            font-weight: 600;
            letter-spacing: 2px;
            text-transform: uppercase;
            display: inline-block;
            margin-bottom: 12px;
        }

        .section-title {
            font-size: clamp(2rem, 5vw, 3.5rem);
            font-weight: 800;
            line-height: 1.1;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            padding: 14px 28px;
            font-size: 0.85rem;
            font-weight: 600;
            letter-spacing: 1.5px;
            text-transform: uppercase;
            border-radius: 2px;
            transition: var(--transition);
            cursor: pointer;
            border: 1px solid var(--border);
            background: var(--surface-light);
            color: var(--text);
            position: relative;
            overflow: hidden;
        }

        .btn-primary {
            background: var(--accent);
            border-color: var(--accent);
            color: #fff;
            box-shadow: 0 0 15px var(--accent-glow);
        }

        .btn-primary:hover {
            background: #d40000;
            box-shadow: 0 0 25px rgba(255, 0, 0, 0.6);
            transform: translateY(-2px);
        }

        .btn-outline:hover {
            border-color: var(--accent);
            background: var(--surface);
            color: var(--text);
            box-shadow: 0 0 15px rgba(255, 0, 0, 0.2);
            transform: translateY(-2px);
        }

        /* --- NAVBAR --- */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            padding: 20px 0;
            transition: var(--transition);
        }

        .navbar.scrolled {
            background: rgba(5, 5, 5, 0.85);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-bottom: 1px solid var(--border);
            padding: 14px 0;
        }

        .nav-container {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .logo {
            font-family: var(--font-heading);
            font-size: 1.25rem;
            font-weight: 800;
            letter-spacing: 1px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .logo-dot {
            width: 8px;
            height: 8px;
            background: var(--accent);
            border-radius: 50%;
            box-shadow: 0 0 8px var(--accent);
        }

        .nav-links {
            display: flex;
            align-items: center;
            gap: 32px;
            list-style: none;
        }

        .nav-links a {
            font-size: 0.85rem;
            letter-spacing: 1px;
            font-weight: 500;
            color: var(--muted);
            transition: var(--transition);
        }

        .nav-links a:hover {
            color: var(--text);
            text-shadow: 0 0 8px rgba(255, 255, 255, 0.5);
        }

        .nav-right {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .availability {
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 0.75rem;
            color: var(--muted);
            letter-spacing: 1px;
            padding: 6px 12px;
            background: var(--surface-light);
            border: 1px solid var(--border);
            border-radius: 20px;
        }

        .status-dot {
            width: 6px;
            height: 6px;
            background: #00ff66;
            border-radius: 50%;
            box-shadow: 0 0 8px #00ff66;
            animation: pulse 2s infinite;
        }

        .hamburger {
            display: none;
            flex-direction: column;
            gap: 6px;
            cursor: pointer;
            z-index: 1001;
            background: none;
            border: none;
        }

        .hamburger span {
            width: 24px;
            height: 2px;
            background: var(--text);
            transition: var(--transition);
        }

        /* --- HERO SECTION --- */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            padding-top: 100px;
            position: relative;
        }

        .hero-grid {
            display: grid;
            grid-template-columns: 1.2fr 0.8fr;
            gap: 60px;
            align-items: center;
        }

        .hero-subtitle {
            font-size: 0.85rem;
            letter-spacing: 3px;
            color: var(--accent);
            font-weight: 600;
            margin-bottom: 12px;
        }

        .hero-title {
            font-size: clamp(2.5rem, 6vw, 4.5rem);
            line-height: 1;
            margin-bottom: 8px;
            font-weight: 800;
        }

        .hero-role {
            font-size: clamp(1rem, 2vw, 1.5rem);
            color: var(--muted);
            font-weight: 500;
            letter-spacing: 1px;
            margin-bottom: 24px;
        }

        .hero-tagline {
            font-size: 1.15rem;
            color: #ccc;
            max-width: 480px;
            margin-bottom: 40px;
        }

        .hero-btns {
            display: flex;
            gap: 16px;
            flex-wrap: wrap;
        }

        /* Camera Frame Profile */
        .camera-frame-container {
            position: relative;
            padding: 12px;
            background: var(--surface);
            border: 1px solid var(--border);
            border-radius: 4px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.8), 0 0 30px rgba(255, 0, 0, 0.1);
        }

        .camera-overlay {
            position: absolute;
            inset: 12px;
            pointer-events: none;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            padding: 16px;
            z-index: 2;
            font-family: monospace;
            font-size: 0.75rem;
        }

        .cam-top, .cam-bottom {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .rec-indicator {
            display: flex;
            align-items: center;
            gap: 6px;
            color: var(--accent);
            font-weight: bold;
        }

        .rec-dot {
            width: 8px;
            height: 8px;
            background: var(--accent);
            border-radius: 50%;
            animation: pulse 1s infinite;
        }

        .cam-specs {
            color: rgba(255,255,255,0.7);
        }

        .frame-corners::before, .frame-corners::after {
            content: '';
            position: absolute;
            width: 20px;
            height: 20px;
            border: 2px solid rgba(255,0,0,0.6);
            pointer-events: none;
        }

        .frame-corners::before { top: 20px; left: 20px; border-right: 0; border-bottom: 0; }
        .frame-corners::after { bottom: 20px; right: 20px; border-left: 0; border-top: 0; }

        .hero-img-wrapper {
            position: relative;
            width: 100%;
            height: 480px;
            overflow: hidden;
            background: #000;
        }

        .hero-img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            object-position: top center;
            filter: contrast(105%) brightness(95%);
            transition: var(--transition);
        }

        .camera-frame-container:hover .hero-img {
            filter: contrast(110%) brightness(105%);
            transform: scale(1.03);
        }

        /* --- WORK SECTION --- */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 40px;
        }

        .project-card {
            background: var(--surface);
            border: 1px solid var(--border);
            overflow: hidden;
            border-radius: 4px;
            position: relative;
            transition: var(--transition);
        }

        .project-card:first-child {
            grid-column: span 2;
        }

        .project-card:hover {
            border-color: rgba(255, 0, 0, 0.5);
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(255, 0, 0, 0.15);
        }

        .project-thumb {
            position: relative;
            width: 100%;
            height: 360px;
            overflow: hidden;
        }

        .project-card:first-child .project-thumb {
            height: 480px;
        }

        .project-thumb img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.6s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .project-card:hover .project-thumb img {
            transform: scale(1.08);
        }

        .project-overlay {
            position: absolute;
            inset: 0;
            background: linear-gradient(to top, rgba(5,5,5,0.95), transparent 60%);
            opacity: 0.8;
            transition: var(--transition);
        }

        .project-card:hover .project-overlay {
            opacity: 0.95;
        }

        .project-info {
            padding: 24px;
            position: relative;
            z-index: 2;
        }

        .project-meta {
            display: flex;
            justify-content: space-between;
            font-size: 0.75rem;
            color: var(--accent);
            font-weight: 600;
            letter-spacing: 1px;
            margin-bottom: 8px;
        }

        .project-title {
            font-size: 1.5rem;
            margin-bottom: 12px;
        }

        .project-desc {
            color: var(--muted);
            font-size: 0.9rem;
            margin-bottom: 16px;
        }

        .project-tech {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
            margin-bottom: 20px;
        }

        .tech-tag {
            font-size: 0.7rem;
            padding: 4px 8px;
            background: var(--surface-light);
            border: 1px solid var(--border);
            color: var(--muted);
            border-radius: 2px;
        }

        /* --- SHOWREEL SECTION --- */
        .showreel-box {
            position: relative;
            background: var(--surface);
            border: 1px solid var(--border);
            border-radius: 4px;
            padding: 16px;
            box-shadow: 0 0 30px rgba(0,0,0,0.8);
        }

        .showreel-wrapper {
            position: relative;
            padding-top: 56.25%; /* 16:9 Aspect Ratio */
            background: #000;
            overflow: hidden;
        }

        .showreel-wrapper iframe, .showreel-wrapper video {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }

        .showreel-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding-top: 12px;
            font-family: monospace;
            font-size: 0.8rem;
            color: var(--muted);
        }

        /* --- ABOUT & STATS --- */
        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
            align-items: center;
        }

        .about-text {
            font-size: 1.1rem;
            color: #ccc;
            margin-bottom: 24px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 24px;
        }

        .stat-card {
            background: var(--surface);
            border: 1px solid var(--border);
            padding: 24px;
            border-radius: 4px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 2px;
            height: 100%;
            background: var(--accent);
            box-shadow: 0 0 10px var(--accent);
        }

        .stat-number {
            font-family: var(--font-heading);
            font-size: 2.8rem;
            font-weight: 800;
            color: var(--text);
            line-height: 1;
            margin-bottom: 8px;
        }

        .stat-label {
            font-size: 0.75rem;
            letter-spacing: 1px;
            color: var(--muted);
            text-transform: uppercase;
        }

        /* --- SKILLS --- */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 16px;
        }

        .skill-card {
            background: var(--surface);
            border: 1px solid var(--border);
            padding: 20px;
            border-radius: 4px;
            text-align: center;
            font-weight: 600;
            font-size: 0.9rem;
            letter-spacing: 0.5px;
            transition: var(--transition);
            display: flex;
            align-items: center;
            justify-content: center;
            min-height: 80px;
        }

        .skill-card:hover {
            border-color: var(--accent);
            background: var(--surface-light);
            color: #fff;
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(255, 0, 0, 0.25);
        }

        /* --- SERVICES --- */
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 24px;
        }

        .service-card {
            background: var(--surface);
            border: 1px solid var(--border);
            padding: 32px;
            border-radius: 4px;
            transition: var(--transition);
            position: relative;
        }

        .service-card:hover {
            border-color: rgba(255, 0, 0, 0.4);
            background: var(--surface-light);
            transform: translateY(-4px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.5);
        }

        .service-num {
            font-family: var(--font-heading);
            font-size: 0.85rem;
            color: var(--accent);
            margin-bottom: 16px;
            font-weight: bold;
        }

        .service-title {
            font-size: 1.2rem;
            margin-bottom: 12px;
        }

        .service-desc {
            font-size: 0.85rem;
            color: var(--muted);
        }

        /* --- EXPERIENCE TIMELINE --- */
        .timeline {
            position: relative;
            max-width: 800px;
            margin: 0 auto;
        }

        .timeline::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 1px;
            height: 100%;
            background: var(--border);
        }

        .timeline-item {
            position: relative;
            padding-left: 32px;
            margin-bottom: 40px;
        }

        .timeline-item::before {
            content: '';
            position: absolute;
            top: 4px;
            left: -4px;
            width: 9px;
            height: 9px;
            background: var(--accent);
            border-radius: 50%;
            box-shadow: 0 0 8px var(--accent);
        }

        .timeline-year {
            font-size: 0.8rem;
            color: var(--accent);
            font-weight: 700;
            letter-spacing: 1px;
            margin-bottom: 4px;
        }

        .timeline-role {
            font-size: 1.2rem;
            font-weight: 700;
        }

        .timeline-company {
            font-size: 0.9rem;
            color: var(--muted);
            margin-bottom: 12px;
        }

        .timeline-desc {
            font-size: 0.9rem;
            color: #ccc;
        }

        /* --- CONTACT SECTION --- */
        .contact-box {
            background: var(--surface);
            border: 1px solid var(--border);
            padding: 60px;
            border-radius: 4px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .contact-box::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 200px;
            height: 2px;
            background: var(--accent);
            box-shadow: 0 0 20px var(--accent);
        }

        .contact-title {
            font-size: clamp(2rem, 4vw, 3rem);
            margin-bottom: 16px;
        }

        .contact-desc {
            color: var(--muted);
            max-width: 500px;
            margin: 0 auto 36px;
            font-size: 1rem;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 40px;
        }

        .social-link {
            font-size: 0.85rem;
            letter-spacing: 1px;
            color: var(--muted);
            transition: var(--transition);
        }

        .social-link:hover {
            color: var(--accent);
            text-shadow: 0 0 10px var(--accent-glow);
        }

        /* --- FOOTER --- */
        .footer {
            border-top: 1px solid var(--border);
            padding: 40px 0;
            background: #020202;
        }

        .footer-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 20px;
        }

        .footer-copy {
            font-size: 0.75rem;
            color: var(--muted);
            letter-spacing: 1px;
        }

        /* --- ANIMATIONS --- */
        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.4; }
            100% { opacity: 1; }
        }

        .reveal {
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 0.8s ease, transform 0.8s ease;
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* --- RESPONSIVE DESIGN --- */
        @media (max-width: 992px) {
            .hero-grid {
                grid-template-columns: 1fr;
                gap: 40px;
            }

            .about-grid {
                grid-template-columns: 1fr;
            }

            .projects-grid {
                grid-template-columns: 1fr;
            }

            .project-card:first-child {
                grid-column: span 1;
            }

            .project-card:first-child .project-thumb {
                height: 360px;
            }
        }

        @media (max-width: 768px) {
            .hamburger {
                display: flex;
            }

            .nav-links {
                position: fixed;
                top: 0;
                right: -100%;
                width: 80%;
                max-width: 300px;
                height: 100vh;
                background: var(--surface);
                border-left: 1px solid var(--border);
                flex-direction: column;
                justify-content: center;
                align-items: center;
                transition: var(--transition);
                z-index: 1000;
            }

            .nav-links.active {
                right: 0;
            }

            .availability {
                display: none;
            }

            .contact-box {
                padding: 40px 20px;
            }

            .section-padding {
                padding: 80px 0;
            }
        }
    </style>
</head>
<body>

    <canvas id="particle-canvas"></canvas>
    <div class="tech-grid"></div>

    <nav class="navbar" id="navbar">
        <div class="container nav-container">
            <a href="#" class="logo">
                ASIF EDITS<span class="logo-dot"></span>
            </a>

            <ul class="nav-links" id="nav-links">
                <li><a href="#work" class="nav-item">WORK</a></li>
                <li><a href="#showreel" class="nav-item">SHOWREEL</a></li>
                <li><a href="#about" class="nav-item">ABOUT</a></li>
                <li><a href="#experience" class="nav-item">EXPERIENCE</a></li>
                <li><a href="#contact" class="nav-item">CONTACT</a></li>
            </ul>

            <div class="nav-right">
                <div class="availability">
                    <span class="status-dot"></span> AVAILABLE FOR WORK
                </div>
                <a href="#contact" class="btn btn-primary" style="padding: 8px 16px; font-size: 0.75rem;">LET'S TALK</a>
                <button class="hamburger" id="hamburger" aria-label="Toggle Navigation">
                    <span></span>
                    <span></span>
                    <span></span>
                </button>
            </div>
        </div>
    </nav>

    <section class="hero" id="hero">
        <div class="container hero-grid">
            <div class="hero-content">
                <div class="hero-subtitle">CREATIVE REEL 2026</div>
                <h1 class="hero-title">ASIF MAHMUD</h1>
                <div class="hero-role">VIDEO EDITOR & MOTION DESIGNER</div>
                <p class="hero-tagline">I turn raw footage into stories worth watching.</p>
                <div class="hero-btns">
                    <a href="#work" class="btn btn-primary">EXPLORE WORK</a>
                    <a href="#showreel" class="btn btn-outline">WATCH SHOWREEL</a>
                </div>
            </div>

            <div class="camera-frame-container">
                <div class="frame-corners"></div>
                <div class="camera-overlay">
                    <div class="cam-top">
                        <div class="rec-indicator"><span class="rec-dot"></span> REC</div>
                        <div class="cam-specs">RAW 12-BIT</div>
                    </div>
                    <div class="cam-bottom">
                        <div class="cam-specs">4K 60FPS</div>
                        <div class="cam-specs">F2.8 | 1/120s</div>
                    </div>
                </div>
                <div class="hero-img-wrapper">
                    <img src="Formal Photo.jpg" alt="Asif Mahmud - Gaming Video Editor & Motion Designer" class="hero-img" loading="lazy">
                </div>
            </div>
        </div>
    </section>

    <section class="section-padding" id="work">
        <div class="container">
            <div class="section-header reveal">
                <span class="section-tag">PORTFOLIO</span>
                <h2 class="section-title">SELECTED WORK</h2>
            </div>

            <div class="projects-grid">
                <div class="project-card reveal">
                    <div class="project-thumb">
                        <img src="https://images.unsplash.com/photo-1542751371-adc38448a05e?auto=format&fit=crop&w=1200&q=80" alt="Cinematic Edit" loading="lazy">
                        <div class="project-overlay"></div>
                    </div>
                    <div class="project-info">
                        <div class="project-meta">
                            <span>01 — COMMERCIAL / CINEMATIC</span>
                            <span>2026</span>
                        </div>
                        <h3 class="project-title">ESPORTS CHAMPIONSHIP TRAILER</h3>
                        <p class="project-desc">High-energy cinematic editing combined with fast-paced visual rhythm, 3D camera tracking, and intense color grading for an international tournament launch.</p>
                        <div class="project-tech">
                            <span class="tech-tag">Premiere Pro</span>
                            <span class="tech-tag">After Effects</span>
                            <span class="tech-tag">DaVinci Resolve</span>
                        </div>
                        <a href="#showreel" class="btn btn-outline" style="padding: 10px 20px; font-size: 0.75rem;">WATCH PROJECT &rarr;</a>
                    </div>
                </div>

                <div class="project-card reveal">
                    <div class="project-thumb">
                        <img src="https://images.unsplash.com/photo-1612287230202-1ff1d85d1bdf?auto=format&fit=crop&w=800&q=80" alt="Social Media Campaign" loading="lazy">
                        <div class="project-overlay"></div>
                    </div>
                    <div class="project-info">
                        <div class="project-meta">
                            <span>02 — SHORT FORM / SOCIAL</span>
                            <span>2025</span>
                        </div>
                        <h3 class="project-title">VIRAL GAMING CLIPS & HIGHLIGHTS</h3>
                        <p class="project-desc">Fast-paced short-form edits optimized for high retention across TikTok and Shorts, featuring kinetic subtitle effects and custom SFX.</p>
                        <div class="project-tech">
                            <span class="tech-tag">After Effects</span>
                            <span class="tech-tag">Premiere Pro</span>
                        </div>
                        <a href="#showreel" class="btn btn-outline" style="padding: 10px 20px; font-size: 0.75rem;">WATCH PROJECT &rarr;</a>
                    </div>
                </div>

                <div class="project-card reveal">
                    <div class="project-thumb">
                        <img src="https://images.unsplash.com/photo-1550745165-9bc0b252726f?auto=format&fit=crop&w=800&q=80" alt="Motion Design" loading="lazy">
                        <div class="project-overlay"></div>
                    </div>
                    <div class="project-info">
                        <div class="project-meta">
                            <span>03 — MOTION GRAPHICS</span>
                            <span>2025</span>
                        </div>
                        <h3 class="project-title">STREAM OVERLAY & HUD DESIGN</h3>
                        <p class="project-desc">Futuristic 2D/3D animated broadcast packages, HUD elements, lower thirds, and stream stinger transitions for pro gaming teams.</p>
                        <div class="project-tech">
                            <span class="tech-tag">After Effects</span>
                            <span class="tech-tag">Photoshop</span>
                        </div>
                        <a href="#showreel" class="btn btn-outline" style="padding: 10px 20px; font-size: 0.75rem;">WATCH PROJECT &rarr;</a>
                    </div>
                </div>

                <div class="project-card reveal">
                    <div class="project-thumb">
                        <img src="https://images.unsplash.com/photo-1538481199705-c710c4e965fc?auto=format&fit=crop&w=800&q=80" alt="YouTube Edit" loading="lazy">
                        <div class="project-overlay"></div>
                    </div>
                    <div class="project-info">
                        <div class="project-meta">
                            <span>04 — CONTENT / YOUTUBE</span>
                            <span>2025</span>
                        </div>
                        <h3 class="project-title">CREATOR STORYTELLING & GAMEPLAY</h3>
                        <p class="project-desc">Long-form narrative gaming documentaries maintaining 60%+ average audience retention with meme integrations and sound design.</p>
                        <div class="project-tech">
                            <span class="tech-tag">Premiere Pro</span>
                            <span class="tech-tag">Photoshop</span>
                        </div>
                        <a href="#showreel" class="btn btn-outline" style="padding: 10px 20px; font-size: 0.75rem;">WATCH PROJECT &rarr;</a>
                    </div>
                </div>

                <div class="project-card reveal">
                    <div class="project-thumb">
                        <img src="https://images.unsplash.com/photo-1511512578047-dfb367046420?auto=format&fit=crop&w=800&q=80" alt="Brand Film" loading="lazy">
                        <div class="project-overlay"></div>
                    </div>
                    <div class="project-info">
                        <div class="project-meta">
                            <span>05 — COMMERCIAL</span>
                            <span>2025</span>
                        </div>
                        <h3 class="project-title">GAMING HARDWARE LAUNCH FILM</h3>
                        <p class="project-desc">Cinematic commercial with heavy emphasis on bass-heavy sound design, 3D product integration, and dark cyber aesthetics.</p>
                        <div class="project-tech">
                            <span class="tech-tag">DaVinci Resolve</span>
                            <span class="tech-tag">Sound Design</span>
                        </div>
                        <a href="#showreel" class="btn btn-outline" style="padding: 10px 20px; font-size: 0.75rem;">WATCH PROJECT &rarr;</a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="section-padding" id="showreel" style="background: var(--surface);">
        <div class="container">
            <div class="section-header reveal" style="text-align: center;">
                <span class="section-tag">2026 DEMO REEL</span>
                <h2 class="section-title">SHOWREEL</h2>
                <p style="color: var(--muted); margin-top: 8px;">A selection of my latest edits, motion work, and visual storytelling.</p>
            </div>

            <div class="showreel-box reveal">
                <div class="showreel-wrapper">
                    <iframe src="https://www.youtube-nocookie.com/embed/dQw4w9WgXcQ" title="Showreel Video Player" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                </div>
                <div class="showreel-bar">
                    <span>WATCH REEL — 2026 GAMING & MOTION EDIT</span>
                    <span>02:15 / 02:15</span>
                </div>
            </div>
        </div>
    </section>

    <section class="section-padding" id="about">
        <div class="container">
            <div class="about-grid">
                <div class="reveal">
                    <span class="section-tag">BIOGRAPHY</span>
                    <h2 class="section-title" style="margin-bottom: 20px;">ABOUT ME</h2>
                    <p class="about-text">I transform raw footage into engaging visual stories. My work combines cinematic editing, motion graphics, sound design and visual storytelling to create content that captures attention.</p>
                    <p style="color: var(--muted); font-size: 0.95rem;">From ultra-fast gaming fragmovies and esports promos to high-retention creator YouTube videos, I specialize in keeping audiences hooked with seamless pacing and immersive audio.</p>
                </div>

                <div class="stats-grid reveal">
                    <div class="stat-card">
                        <div class="stat-number" data-target="5">0</div>
                        <div class="stat-label">Years Experience</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" data-target="100">0</div>
                        <div class="stat-label">Projects Completed</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" data-target="30">0</div>
                        <div class="stat-label">Global Clients</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" data-target="10">0</div>
                        <div class="stat-label">Million+ Views Generated</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="section-padding" style="background: var(--surface);">
        <div class="container">
            <div class="section-header reveal">
                <span class="section-tag">TOOLKIT & CAPABILITIES</span>
                <h2 class="section-title">SKILLS & SOFTWARE</h2>
            </div>

            <div class="skills-grid reveal">
                <div class="skill-card">Adobe Premiere Pro</div>
                <div class="skill-card">Adobe After Effects</div>
                <div class="skill-card">DaVinci Resolve</div>
                <div class="skill-card">Adobe Photoshop</div>
                <div class="skill-card">Adobe Illustrator</div>
                <div class="skill-card">Motion Graphics</div>
                <div class="skill-card">Color Grading</div>
                <div class="skill-card">Sound Design</div>
                <div class="skill-card">Short Form Editing</div>
                <div class="skill-card">Long Form Editing</div>
                <div class="skill-card">YouTube Editing</div>
                <div class="skill-card">Commercial Editing</div>
            </div>
        </div>
    </section>

    <section class="section-padding">
        <div class="container">
            <div class="section-header reveal">
                <span class="section-tag">WHAT I DO</span>
                <h2 class="section-title">SERVICES</h2>
            </div>

            <div class="services-grid">
                <div class="service-card reveal">
                    <div class="service-num">01</div>
                    <h3 class="service-title">VIDEO EDITING</h3>
                    <p class="service-desc">Seamless cutting, beat syncing, rhythm mapping, and narrative structuring for cinematic gaming and commercial media.</p>
                </div>

                <div class="service-card reveal">
                    <div class="service-num">02</div>
                    <h3 class="service-title">MOTION GRAPHICS</h3>
                    <p class="service-desc">Dynamic title sequences, stream overlays, HUD elements, kinetic typography, and custom visual effects animations.</p>
                </div>

                <div class="service-card reveal">
                    <div class="service-num">03</div>
                    <h3 class="service-title">YOUTUBE EDITING</h3>
                    <p class="service-desc">High-retention editing engineered to maximize watch time, subscriber conversion, and audience engagement.</p>
                </div>

                <div class="service-card reveal">
                    <div class="service-num">04</div>
                    <h3 class="service-title">SHORT FORM CONTENT</h3>
                    <p class="service-desc">High-octane Reels, TikToks, and YouTube Shorts designed to hook viewers within the first 3 seconds.</p>
                </div>

                <div class="service-card reveal">
                    <div class="service-num">05</div>
                    <h3 class="service-title">COMMERCIAL EDITING</h3>
                    <p class="service-desc">High-production brand films and gaming hardware promos tailored specifically for digital campaigns.</p>
                </div>

                <div class="service-card reveal">
                    <div class="service-num">06</div>
                    <h3 class="service-title">COLOR GRADING</h3>
                    <p class="service-desc">Professional color correction, mood mapping, and cinematic look design using DaVinci Resolve color workflows.</p>
                </div>

                <div class="service-card reveal">
                    <div class="service-num">07</div>
                    <h3 class="service-title">SOUND DESIGN</h3>
                    <p class="service-desc">Impact layering, bass drops, game sound isolation, vocal processing, and high-energy master audio mixing.</p>
                </div>

                <div class="service-card reveal">
                    <div class="service-num">08</div>
                    <h3 class="service-title">SOCIAL MEDIA CONTENT</h3>
                    <p class="service-desc">Complete social video strategy packages crafted to amplify brand reach across all major gaming platforms.</p>
                </div>
            </div>
        </div>
    </section>

    <section class="section-padding" id="experience" style="background: var(--surface);">
        <div class="container">
            <div class="section-header reveal">
                <span class="section-tag">CAREER</span>
                <h2 class="section-title">EXPERIENCE</h2>
            </div>

            <div class="timeline">
                <div class="timeline-item reveal">
                    <div class="timeline-year">2024 — PRESENT</div>
                    <h3 class="timeline-role">Lead Gaming Editor & Motion Specialist</h3>
                    <div class="timeline-company">Apex Esports & Visuals</div>
                    <p class="timeline-desc">Leading post-production for tournament trailers, high-profile esports montages, managing junior editors, and crafting broadcast graphics.</p>
                </div>

                <div class="timeline-item reveal">
                    <div class="timeline-year">2022 — 2024</div>
                    <h3 class="timeline-role">Senior Gaming Content Editor</h3>
                    <div class="timeline-company">Digital Creator Network</div>
                    <p class="timeline-desc">Edited high-volume YouTube gaming content generating over 5M+ views monthly. Built custom motion design assets and audio templates.</p>
                </div>

                <div class="timeline-item reveal">
                    <div class="timeline-year">2021 — 2022</div>
                    <h3 class="timeline-role">Freelance Video Editor</h3>
                    <div class="timeline-company">Self-Employed</div>
                    <p class="timeline-desc">Delivered custom video editing, fragmovies, short-form gaming clips, and motion typography for international creators and brands.</p>
                </div>
            </div>
        </div>
    </section>

    <section class="section-padding" id="contact">
        <div class="container">
            <div class="contact-box reveal">
                <span class="section-tag">GET IN TOUCH</span>
                <h2 class="contact-title">LET'S CREATE SOMETHING WORTH WATCHING.</h2>
                <p class="contact-desc">Have a project in mind? Let's turn your footage into something people remember.</p>
                <div style="display: flex; gap: 16px; justify-content: center; flex-wrap: wrap;">
                    <a href="mailto:asif@example.com" class="btn btn-primary">START A PROJECT</a>
                    <a href="mailto:asif@example.com" class="btn btn-outline">EMAIL ME</a>
                </div>

                <div class="social-links">
                    <a href="https://instagram.com" target="_blank" rel="noopener" class="social-link">INSTAGRAM</a>
                    <a href="https://youtube.com" target="_blank" rel="noopener" class="social-link">YOUTUBE</a>
                    <a href="https://linkedin.com" target="_blank" rel="noopener" class="social-link">LINKEDIN</a>
                    <a href="https://behance.net" target="_blank" rel="noopener" class="social-link">BEHANCE</a>
                </div>
            </div>
        </div>
    </section>

    <footer class="footer">
        <div class="container footer-container">
            <div>
                <div class="logo" style="font-size: 1rem;">ASIF MAHMUD<span class="logo-dot"></span></div>
                <div style="font-size: 0.75rem; color: var(--muted); margin-top: 4px;">VIDEO EDITOR & MOTION DESIGNER</div>
            </div>

            <div class="footer-copy">
                &copy; 2026 ASIF MAHMUD ALL RIGHTS RESERVED.
            </div>
        </div>
    </footer>

    <script>
        // --- MOBILE NAVBAR TOGGLE ---
        const hamburger = document.getElementById('hamburger');
        const navLinks = document.getElementById('nav-links');
        const navItems = document.querySelectorAll('.nav-item');

        hamburger.addEventListener('click', () => {
            navLinks.classList.toggle('active');
        });

        navItems.forEach(item => {
            item.addEventListener('click', () => {
                navLinks.classList.remove('active');
            });
        });

        // --- NAVBAR SCROLL EFFECT ---
        window.addEventListener('scroll', () => {
            const navbar = document.getElementById('navbar');
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // --- SCROLL REVEAL ANIMATION ---
        const revealElements = document.querySelectorAll('.reveal');

        const revealOnScroll = () => {
            const windowHeight = window.innerHeight;
            revealElements.forEach(el => {
                const elementTop = el.getBoundingClientRect().top;
                const elementVisible = 100;
                if (elementTop < windowHeight - elementVisible) {
                    el.classList.add('active');
                }
            });
        };

        window.addEventListener('scroll', revealOnScroll);
        revealOnScroll(); // Trigger initial view check

        // --- NUMBER COUNTER ANIMATION ---
        const statNumbers = document.querySelectorAll('.stat-number');
        let animatedStats = false;

        const animateCounters = () => {
            const statsSection = document.getElementById('about');
            if(!statsSection) return;
            const sectionPos = statsSection.getBoundingClientRect().top;
            const screenPos = window.innerHeight;

            if (sectionPos < screenPos && !animatedStats) {
                animatedStats = true;
                statNumbers.forEach(counter => {
                    const target = +counter.getAttribute('data-target');
                    let count = 0;
                    const speed = target / 50;

                    const updateCount = () => {
                        count += speed;
                        if (count < target) {
                            counter.innerText = Math.ceil(count) + '+';
                            setTimeout(updateCount, 30);
                        } else {
                            counter.innerText = target + '+';
                        }
                    };
                    updateCount();
                });
            }
        };

        window.addEventListener('scroll', animateCounters);

        // --- PARTICLE CANVAS BACKGROUND ---
        const canvas = document.getElementById('particle-canvas');
        const ctx = canvas.getContext('2d');

        let particlesArray = [];
        const numberOfParticles = 50;

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }

        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 1.5 + 0.5;
                this.speedX = (Math.random() - 0.5) * 0.4;
                this.speedY = (Math.random() - 0.5) * 0.4;
                this.opacity = Math.random() * 0.5 + 0.1;
                // Add occasional red particle accents
                this.isAccent = Math.random() < 0.2;
            }

            update() {
                this.x += this.speedX;
                this.y += this.speedY;

                if (this.x > canvas.width) this.x = 0;
                if (this.x < 0) this.x = canvas.width;
                if (this.y > canvas.height) this.y = 0;
                if (this.y < 0) this.y = canvas.height;
            }

            draw() {
                ctx.fillStyle = this.isAccent ? `rgba(255, 0, 0, ${this.opacity + 0.2})` : `rgba(255, 255, 255, ${this.opacity})`;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        function initParticles() {
            particlesArray = [];
            for (let i = 0; i < numberOfParticles; i++) {
                particlesArray.push(new Particle());
            }
        }

        function animateParticles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            for (let i = 0; i < particlesArray.length; i++) {
                particlesArray[i].update();
                particlesArray[i].draw();
            }
            requestAnimationFrame(animateParticles);
        }

        initParticles();
        animateParticles();
    </script>
</body>
</html>
