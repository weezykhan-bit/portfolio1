<!DOCTYPE html>



<html lang="en">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Fowzan Khan — Production Architect</title>

<link rel="preconnect" href="https://fonts.googleapis.com">

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400;1,700&family=Syne:wght@400;500;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">

<style>

/* ═══════════════════════════════════════════════

VARIABLES & RESET

═══════════════════════════════════════════════ */

:root {

--black: #050505;

--black2: #0a0a0a;

--dark: #111111;

--dark2: #181818;

--dark3: #222222;

--gold: #C8973A;

--gold2: #E8B85C;

--gold3: #F5D080;

--red: #8B1E1E;

--red2: #B02020;

--cream: #F2EBD9;

--cream2: #D4C9B0;

--text: #BBBBBB;

--text2: #888888;

--text3: #555555;

--white: #FFFFFF;

--glass: rgba(255,255,255,0.04);

--glass2: rgba(200,151,58,0.08);

--border: rgba(200,151,58,0.15);

--border2: rgba(255,255,255,0.06);

}

*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }

html { scroll-behavior: smooth; font-size: 16px; }

body {

background: var(--black);

color: var(--text);

font-family: 'DM Sans', sans-serif;

font-weight: 300;

overflow-x: hidden;

cursor: none;

}

::selection { background: rgba(200,151,58,0.3); color: var(--cream); }



/* ═══ CUSTOM CURSOR ═══ */

#cursor {

position: fixed;

width: 10px; height: 10px;

background: var(–gold);

border-radius: 50%;

pointer-events: none;

z-index: 9999;

transform: translate(-50%,-50%);

transition: transform 0.1s, width 0.3s, height 0.3s, background 0.3s;

mix-blend-mode: difference;

}

#cursor-ring {

position: fixed;

width: 40px; height: 40px;

border: 1px solid rgba(200,151,58,0.5);

border-radius: 50%;

pointer-events: none;

z-index: 9998;

transform: translate(-50%,-50%);

transition: transform 0.12s ease-out, width 0.3s, height 0.3s, opacity 0.3s;

}

body:hover #cursor { opacity: 1; }

a:hover ~ #cursor, button:hover ~ #cursor { width: 20px; height: 20px; }



/* ═══ SCROLL PROGRESS ═══ */

#scroll-progress {

position: fixed;

top: 0; left: 0;

height: 2px;

background: linear-gradient(90deg, var(–red) 0%, var(–gold) 50%, var(–gold3) 100%);

z-index: 1000;

width: 0%;

transition: width 0.1s;

}



/* ═══ NAVIGATION ═══ */

nav {

position: fixed;

top: 0; left: 0; right: 0;

z-index: 500;

display: flex;

justify-content: space-between;

align-items: center;

padding: 24px 60px;

transition: all 0.4s;

}

nav.scrolled {

background: rgba(5,5,5,0.92);

backdrop-filter: blur(20px);

padding: 16px 60px;

border-bottom: 1px solid var(–border);

}

.nav-logo {

font-family: ‘Syne’, sans-serif;

font-weight: 800;

font-size: 1.1rem;

letter-spacing: 0.08em;

color: var(–white);

}

.nav-logo span { color: var(–gold); }

.nav-links {

display: flex;

gap: 36px;

list-style: none;

align-items: center;

}

.nav-links a {

text-decoration: none;

color: var(–text2);

font-family: ‘Syne’, sans-serif;

font-size: 0.78rem;

font-weight: 500;

letter-spacing: 0.12em;

text-transform: uppercase;

transition: color 0.3s;

}

.nav-links a:hover { color: var(–gold); }

.nav-cta {

padding: 10px 24px;

border: 1px solid var(–gold);

color: var(–gold) !important;

font-size: 0.72rem !important;

transition: all 0.3s !important;

}

.nav-cta:hover {

background: var(–gold) !important;

color: var(–black) !important;

}

.nav-hamburger {

display: none;

flex-direction: column;

gap: 5px;

cursor: pointer;

padding: 4px;

}

.nav-hamburger span {

display: block;

width: 24px;

height: 1.5px;

background: var(–cream);

transition: all 0.3s;

}



/* ═══════════════════════════════════════════════

HERO SECTION

═══════════════════════════════════════════════ */

#hero {

position: relative;

min-height: 100vh;

display: flex;

align-items: flex-end;

overflow: hidden;

}

.hero-video-wrap {

position: absolute;

inset: 0;

z-index: 0;

}

.hero-video-wrap video {

width: 100%; height: 100%;

object-fit: cover;

opacity: 0.25;

}

.hero-canvas {

position: absolute;

inset: 0;

z-index: 1;

}

.hero-overlay {

position: absolute;

inset: 0;

background:

radial-gradient(ellipse 90% 70% at 60% 30%, rgba(139,30,30,0.12) 0%, transparent 60%),

radial-gradient(ellipse 60% 80% at 10% 80%, rgba(200,151,58,0.07) 0%, transparent 55%),

linear-gradient(180deg,

rgba(5,5,5,0.3) 0%,

rgba(5,5,5,0.15) 40%,

rgba(5,5,5,0.7) 75%,

rgba(5,5,5,1) 100%

);

z-index: 2;

}

.hero-content {

position: relative;

z-index: 3;

padding: 0 60px 90px;

max-width: 1000px;

}

.hero-badge {

display: inline-flex;

align-items: center;

gap: 10px;

margin-bottom: 28px;

padding: 8px 18px;

border: 1px solid rgba(200,151,58,0.3);

background: rgba(200,151,58,0.06);

backdrop-filter: blur(8px);

}

.hero-badge-dot {

width: 6px; height: 6px;

border-radius: 50%;

background: var(–gold);

animation: pulse 2s infinite;

}

@keyframes pulse {

0%,100% { opacity: 1; box-shadow: 0 0 0 0 rgba(200,151,58,0.5); }

50% { opacity: 0.8; box-shadow: 0 0 0 6px rgba(200,151,58,0); }

}

.hero-badge-text {

font-family: ‘Syne’, sans-serif;

font-size: 0.68rem;

font-weight: 600;

letter-spacing: 0.25em;

text-transform: uppercase;

color: var(–gold);

}

.hero-name {

font-family: ‘Playfair Display’, serif;

font-size: clamp(4.5rem, 10vw, 9rem);

font-weight: 900;

line-height: 0.88;

color: var(–white);

letter-spacing: -0.03em;

margin-bottom: 10px;

}

.hero-name em {

font-style: italic;

color: var(–gold2);

display: block;

}

.hero-subtitle {

font-family: ‘Syne’, sans-serif;

font-size: clamp(0.85rem, 2vw, 1.1rem);

font-weight: 500;

letter-spacing: 0.3em;

text-transform: uppercase;

color: var(–text2);

margin-bottom: 36px;

display: flex;

align-items: center;

gap: 16px;

}

.hero-subtitle::before {

content: ‘’;

display: block;

width: 50px;

height: 1px;

background: var(–gold);

}

.hero-desc {

font-size: 1.05rem;

line-height: 1.75;

color: var(–text);

max-width: 560px;

margin-bottom: 48px;

}

.hero-desc strong { color: var(–cream); font-weight: 500; }

.hero-actions {

display: flex;

gap: 16px;

flex-wrap: wrap;

}

.btn-primary {

display: inline-flex;

align-items: center;

gap: 10px;

padding: 16px 36px;

background: linear-gradient(135deg, var(–gold) 0%, var(–gold2) 100%);

color: var(–black);

font-family: ‘Syne’, sans-serif;

font-size: 0.8rem;

font-weight: 700;

letter-spacing: 0.12em;

text-transform: uppercase;

text-decoration: none;

transition: all 0.3s;

clip-path: polygon(0 0, calc(100% - 10px) 0, 100% 10px, 100% 100%, 10px 100%, 0 calc(100% - 10px));

}

.btn-primary:hover {

background: linear-gradient(135deg, var(–gold2) 0%, var(–gold3) 100%);

transform: translateY(-2px);

box-shadow: 0 12px 40px rgba(200,151,58,0.3);

}

.btn-secondary {

display: inline-flex;

align-items: center;

gap: 10px;

padding: 16px 36px;

border: 1px solid rgba(200,151,58,0.4);

color: var(–gold);

font-family: ‘Syne’, sans-serif;

font-size: 0.8rem;

font-weight: 600;

letter-spacing: 0.12em;

text-transform: uppercase;

text-decoration: none;

background: transparent;

cursor: pointer;

transition: all 0.3s;

clip-path: polygon(0 0, calc(100% - 10px) 0, 100% 10px, 100% 100%, 10px 100%, 0 calc(100% - 10px));

}

.btn-secondary:hover {

background: rgba(200,151,58,0.1);

border-color: var(–gold);

transform: translateY(-2px);

}

.hero-scroll-ind {

position: absolute;

right: 60px;

bottom: 60px;

z-index: 3;

display: flex;

flex-direction: column;

align-items: center;

gap: 10px;

}

.hero-scroll-ind span {

font-family: ‘Syne’, sans-serif;

font-size: 0.6rem;

letter-spacing: 0.3em;

text-transform: uppercase;

color: var(–text3);

writing-mode: vertical-rl;

transform: rotate(180deg);

}

.scroll-bar {

width: 1px;

height: 70px;

background: linear-gradient(180deg, transparent, var(–gold));

animation: scrollDown 2s ease-in-out infinite;

}

@keyframes scrollDown {

0% { transform: scaleY(0); transform-origin: top; }

50% { transform: scaleY(1); transform-origin: top; }

50.01% { transform-origin: bottom; }

100% { transform: scaleY(0); transform-origin: bottom; }

}

/* Stats strip */

.hero-stats-strip {

position: absolute;

bottom: 0;

left: 0; right: 0;

z-index: 3;

display: flex;

background: rgba(10,10,10,0.85);

backdrop-filter: blur(20px);

border-top: 1px solid var(–border);

}

.hero-stat {

flex: 1;

padding: 24px 40px;

border-right: 1px solid var(–border);

display: flex;

align-items: center;

gap: 16px;

}

.hero-stat:last-child { border-right: none; }

.stat-number {

font-family: ‘Playfair Display’, serif;

font-size: 2.8rem;

font-weight: 700;

color: var(–gold);

line-height: 1;

}

.stat-info-label {

font-family: ‘Syne’, sans-serif;

font-size: 0.65rem;

font-weight: 600;

letter-spacing: 0.2em;

text-transform: uppercase;

color: var(–text2);

}

.stat-info-sub {

font-size: 0.75rem;

color: var(–text3);

margin-top: 2px;

}



/* ═══════════════════════════════════════════════

SECTION SHARED STYLES

═══════════════════════════════════════════════ */

section { padding: 120px 60px; position: relative; }

.section-tag {

font-family: ‘Syne’, sans-serif;

font-size: 0.65rem;

font-weight: 700;

letter-spacing: 0.4em;

text-transform: uppercase;

color: var(–gold);

margin-bottom: 16px;

display: flex;

align-items: center;

gap: 12px;

}

.section-tag::before {

content: ‘’;

display: block;

width: 32px;

height: 1px;

background: var(–gold);

}

.section-title {

font-family: ‘Playfair Display’, serif;

font-size: clamp(2.5rem, 5vw, 4.2rem);

font-weight: 700;

color: var(–white);

line-height: 1.05;

letter-spacing: -0.02em;

}

.section-title em {

font-style: italic;

color: var(–gold2);

}

.section-divider {

width: 60px;

height: 2px;

background: linear-gradient(90deg, var(–gold), transparent);

margin: 28px 0;

}

.fade-up {

opacity: 0;

transform: translateY(40px);

transition: opacity 0.8s ease, transform 0.8s ease;

}

.fade-up.visible {

opacity: 1;

transform: translateY(0);

}



/* ═══════════════════════════════════════════════

ABOUT SECTION

═══════════════════════════════════════════════ */

#about {

background: var(–black2);

overflow: hidden;

}

.about-bg-text {

position: absolute;

right: -2%;

top: 50%;

transform: translateY(-50%);

font-family: ‘Playfair Display’, serif;

font-size: clamp(12rem, 22vw, 22rem);

font-weight: 900;

color: rgba(200,151,58,0.025);

pointer-events: none;

white-space: nowrap;

line-height: 1;

}

.about-grid {

display: grid;

grid-template-columns: 1fr 1fr;

gap: 100px;

align-items: center;

}

.about-visual {

position: relative;

}

.about-image-frame {

position: relative;

width: 100%;

aspect-ratio: 3/4;

max-width: 420px;

}

.about-img-main {

width: 100%;

height: 100%;

object-fit: cover;

filter: grayscale(20%) contrast(1.1);

}

.about-img-placeholder {

width: 100%;

height: 100%;

background: linear-gradient(135deg, var(–dark2) 0%, var(–dark3) 50%, rgba(139,30,30,0.3) 100%);

display: flex;

align-items: center;

justify-content: center;

position: relative;

overflow: hidden;

}

.about-img-placeholder::before {

content: ‘FK’;

font-family: ‘Playfair Display’, serif;

font-size: 8rem;

font-weight: 900;

color: rgba(200,151,58,0.15);

letter-spacing: -0.05em;

}

.about-img-placeholder::after {

content: ‘’;

position: absolute;

inset: 0;

background: linear-gradient(180deg, transparent 40%, var(–black2) 100%);

}

.about-frame-border {

position: absolute;

top: -12px; left: -12px;

right: 12px; bottom: 12px;

border: 1px solid rgba(200,151,58,0.3);

pointer-events: none;

}

.about-frame-corner {

position: absolute;

width: 24px; height: 24px;

border-color: var(–gold);

border-style: solid;

}

.corner-tl { top: -12px; left: -12px; border-width: 2px 0 0 2px; }

.corner-tr { top: -12px; right: 12px; border-width: 2px 2px 0 0; }

.corner-bl { bottom: 12px; left: -12px; border-width: 0 0 2px 2px; }

.corner-br { bottom: 12px; right: 12px; border-width: 0 2px 2px 0; }

.about-card-overlay {

position: absolute;

bottom: -24px;

right: -32px;

background: var(–dark2);

border: 1px solid var(–border);

padding: 20px 28px;

min-width: 200px;

}

.aco-num {

font-family: ‘Playfair Display’, serif;

font-size: 2.2rem;

font-weight: 700;

color: var(–gold);

line-height: 1;

}

.aco-label {

font-family: ‘Syne’, sans-serif;

font-size: 0.65rem;

letter-spacing: 0.15em;

text-transform: uppercase;

color: var(–text2);

margin-top: 4px;

}

.about-text-col {}

.about-intro {

font-size: 1.15rem;

line-height: 1.8;

color: var(–text);

margin-bottom: 28px;

}

.about-intro strong { color: var(–cream); font-weight: 500; }

.about-pull-quote {

font-family: ‘Playfair Display’, serif;

font-size: 1.6rem;

font-style: italic;

color: var(–cream2);

line-height: 1.4;

padding-left: 24px;

border-left: 3px solid var(–gold);

margin: 36px 0;

}

.about-tags {

display: flex;

flex-wrap: wrap;

gap: 10px;

margin-top: 32px;

}

.about-tag {

padding: 8px 18px;

border: 1px solid var(–border);

background: var(–glass);

font-family: ‘Syne’, sans-serif;

font-size: 0.7rem;

font-weight: 600;

letter-spacing: 0.12em;

text-transform: uppercase;

color: var(–text2);

transition: all 0.3s;

}

.about-tag:hover {

border-color: var(–gold);

color: var(–gold);

background: var(–glass2);

}



/* ═══════════════════════════════════════════════

COUNTER SECTION

═══════════════════════════════════════════════ */

#counters {

background: var(–black);

padding: 0;

border-top: 1px solid var(–border2);

border-bottom: 1px solid var(–border2);

}

.counters-grid {

display: grid;

grid-template-columns: repeat(4, 1fr);

}

.counter-item {

padding: 70px 48px;

border-right: 1px solid var(–border2);

text-align: center;

position: relative;

overflow: hidden;

transition: background 0.4s;

}

.counter-item:last-child { border-right: none; }

.counter-item::before {

content: ‘’;

position: absolute;

bottom: 0; left: 0; right: 0;

height: 2px;

background: linear-gradient(90deg, transparent, var(–gold), transparent);

transform: scaleX(0);

transition: transform 0.5s;

}

.counter-item:hover::before { transform: scaleX(1); }

.counter-item:hover { background: rgba(200,151,58,0.03); }

.counter-icon {

font-size: 1.8rem;

margin-bottom: 16px;

display: block;

filter: grayscale(30%);

}

.counter-num {

font-family: ‘Playfair Display’, serif;

font-size: clamp(3rem, 5vw, 4.5rem);

font-weight: 700;

color: var(–gold);

line-height: 1;

display: block;

}

.counter-suffix {

font-family: ‘Playfair Display’, serif;

font-size: 2rem;

color: var(–gold2);

}

.counter-label {

font-family: ‘Syne’, sans-serif;

font-size: 0.7rem;

font-weight: 600;

letter-spacing: 0.2em;

text-transform: uppercase;

color: var(–text2);

margin-top: 10px;

display: block;

}

.counter-sub {

font-size: 0.78rem;

color: var(–text3);

margin-top: 4px;

display: block;

}



/* ═══════════════════════════════════════════════

FEATURED PROJECTS

═══════════════════════════════════════════════ */

#projects {

background: var(–dark);

overflow: hidden;

}

.projects-header {

display: flex;

justify-content: space-between;

align-items: flex-end;

margin-bottom: 64px;

}

.projects-filter {

display: flex;

gap: 8px;

flex-wrap: wrap;

}

.filter-pill {

padding: 8px 20px;

border: 1px solid var(–border2);

background: transparent;

color: var(–text2);

font-family: ‘Syne’, sans-serif;

font-size: 0.68rem;

font-weight: 600;

letter-spacing: 0.1em;

text-transform: uppercase;

cursor: pointer;

transition: all 0.25s;

border-radius: 0;

}

.filter-pill:hover, .filter-pill.active {

background: var(–gold);

border-color: var(–gold);

color: var(–black);

}

/* FEATURED BENTO GRID */

.projects-bento {

display: grid;

grid-template-columns: repeat(12, 1fr);

grid-template-rows: auto;

gap: 3px;

}

.project-card {

position: relative;

overflow: hidden;

cursor: pointer;

background: var(–dark2);

group: true;

}

.project-card::after {

content: ‘’;

position: absolute;

inset: 0;

background: linear-gradient(180deg, transparent 30%, rgba(5,5,5,0.95) 100%);

z-index: 1;

}

.project-card-img {

width: 100%;

height: 100%;

object-fit: cover;

transition: transform 0.8s cubic-bezier(0.25,0.46,0.45,0.94);

filter: grayscale(20%) brightness(0.75);

}

.project-card:hover .project-card-img {

transform: scale(1.08);

filter: grayscale(0%) brightness(0.85);

}

.project-card-placeholder {

position: absolute;

inset: 0;

transition: transform 0.8s cubic-bezier(0.25,0.46,0.45,0.94);

}

.project-card:hover .project-card-placeholder { transform: scale(1.08); }

.project-card-info {

position: absolute;

bottom: 0; left: 0; right: 0;

padding: 32px;

z-index: 2;

transform: translateY(20px);

transition: transform 0.4s;

}

.project-card:hover .project-card-info { transform: translateY(0); }

.pc-cat {

font-family: ‘Syne’, sans-serif;

font-size: 0.6rem;

font-weight: 700;

letter-spacing: 0.3em;

text-transform: uppercase;

color: var(–gold);

margin-bottom: 8px;

display: flex;

align-items: center;

gap: 8px;

}

.pc-cat-dot {

width: 5px; height: 5px;

border-radius: 50%;

background: var(–gold);

}

.pc-title {

font-family: ‘Playfair Display’, serif;

font-size: 1.6rem;

font-weight: 700;

color: var(–white);

line-height: 1.2;

margin-bottom: 8px;

}

.pc-meta {

font-family: ‘Syne’, sans-serif;

font-size: 0.68rem;

letter-spacing: 0.08em;

color: rgba(255,255,255,0.5);

margin-bottom: 14px;

}

.pc-desc {

font-size: 0.85rem;

line-height: 1.6;

color: rgba(255,255,255,0.65);

max-height: 0;

overflow: hidden;

transition: max-height 0.4s, opacity 0.4s;

opacity: 0;

}

.project-card:hover .pc-desc { max-height: 80px; opacity: 1; }

.pc-role-chip {

display: inline-block;

padding: 4px 12px;

background: rgba(200,151,58,0.9);

color: var(–black);

font-family: ‘Syne’, sans-serif;

font-size: 0.6rem;

font-weight: 700;

letter-spacing: 0.12em;

text-transform: uppercase;

margin-top: 12px;

}

/* Grid positions */

.pc-hero { grid-column: span 7; min-height: 540px; }

.pc-hero .pc-title { font-size: 2.4rem; }

.pc-hero .pc-desc { font-size: 0.9rem; }

.pc-tall { grid-column: span 5; min-height: 540px; }

.pc-wide { grid-column: span 6; min-height: 320px; }

.pc-wide2 { grid-column: span 6; min-height: 320px; }

.pc-reg { grid-column: span 4; min-height: 280px; }

.pc-reg2 { grid-column: span 4; min-height: 280px; }

.pc-reg3 { grid-column: span 4; min-height: 280px; }

/* Show more */

.projects-more {

text-align: center;

margin-top: 48px;

}



/* Gradients for placeholders */

.grad-ramayan { background: linear-gradient(135deg, #1a0a0a 0%, #3d1010 40%, #8B1E1E 70%, #C8973A 100%); }

.grad-vanshaj { background: linear-gradient(135deg, #0a0a1a 0%, #1a1a3d 40%, #2a2a6d 70%, #C8973A 100%); }

.grad-shivshakti { background: linear-gradient(135deg, #0a0a12 0%, #1a0a2a 40%, #4a1a6a 70%, #E8B85C 100%); }

.grad-laxminarayan { background: linear-gradient(135deg, #120a00 0%, #2a1800 40%, #6a3800 70%, #C8973A 100%); }

.grad-veerhanuman { background: linear-gradient(135deg, #0a0800 0%, #1a1400 40%, #3a2c00 70%, #B8870A 100%); }

.grad-taj { background: linear-gradient(135deg, #0a0a0a 0%, #1a1212 40%, #3a2020 70%, #8B5A2A 100%); }

.grad-avrodh { background: linear-gradient(135deg, #00050a 0%, #001020 40%, #002040 70%, #204060 100%); }

.grad-stateofsiege { background: linear-gradient(135deg, #000a05 0%, #001a0a 40%, #003018 70%, #406030 100%); }

.grad-codem { background: linear-gradient(135deg, #05050a 0%, #0a0a20 40%, #1a1840 70%, #302860 100%); }

.grad-dance { background: linear-gradient(135deg, #0a0505 0%, #200a0a 40%, #401818 70%, #C8973A 100%); }

.grad-filmfare { background: linear-gradient(135deg, #0a0800 0%, #201800 40%, #403000 70%, #C8A020 100%); }

.pc-placeholder-inner {

width: 100%; height: 100%;

display: flex;

align-items: center;

justify-content: center;

overflow: hidden;

position: relative;

}

.pc-bg-letter {

font-family: ‘Playfair Display’, serif;

font-size: 14rem;

font-weight: 900;

color: rgba(255,255,255,0.04);

line-height: 1;

position: absolute;

letter-spacing: -0.05em;

}



/* ═══════════════════════════════════════════════

YOUTUBE SPOTLIGHT

═══════════════════════════════════════════════ */

#spotlight {

background: var(–black2);

padding: 100px 60px;

}

.spotlight-header { margin-bottom: 52px; }

.spotlight-grid {

display: grid;

grid-template-columns: 1.6fr 1fr;

gap: 24px;

align-items: start;

}

.spotlight-main {}

.yt-embed-wrap {

position: relative;

padding-bottom: 56.25%;

height: 0;

overflow: hidden;

background: var(–dark2);

border: 1px solid var(–border2);

}

.yt-embed-wrap iframe {

position: absolute;

top: 0; left: 0;

width: 100%; height: 100%;

border: none;

}

.yt-embed-label {

margin-top: 16px;

display: flex;

align-items: center;

gap: 12px;

}

.yt-badge {

display: flex;

align-items: center;

gap: 6px;

padding: 5px 12px;

background: #FF0000;

font-family: ‘Syne’, sans-serif;

font-size: 0.62rem;

font-weight: 700;

color: white;

letter-spacing: 0.1em;

text-transform: uppercase;

}

.yt-label-title {

font-family: ‘Syne’, sans-serif;

font-size: 0.78rem;

font-weight: 600;

color: var(–cream);

}

.spotlight-sidebar {}

.yt-thumb-list {

display: flex;

flex-direction: column;

gap: 16px;

}

.yt-thumb-item {

display: grid;

grid-template-columns: 120px 1fr;

gap: 14px;

cursor: pointer;

padding: 12px;

border: 1px solid transparent;

transition: all 0.3s;

}

.yt-thumb-item:hover {

border-color: var(–border);

background: var(–glass);

}

.yt-thumb-item.active {

border-color: var(–gold);

background: var(–glass2);

}

.yt-thumb-img {

width: 120px;

aspect-ratio: 16/9;

object-fit: cover;

background: var(–dark3);

display: flex;

align-items: center;

justify-content: center;

overflow: hidden;

position: relative;

}

.yt-thumb-grad {

width: 100%; height: 100%;

}

.yt-play-icon {

position: absolute;

inset: 0;

display: flex;

align-items: center;

justify-content: center;

background: rgba(0,0,0,0.3);

}

.yt-play-icon svg {

width: 28px; height: 28px;

fill: white;

filter: drop-shadow(0 2px 8px rgba(0,0,0,0.5));

}

.yt-thumb-info {}

.yt-thumb-title {

font-family: ‘Syne’, sans-serif;

font-size: 0.82rem;

font-weight: 600;

color: var(–cream);

line-height: 1.3;

margin-bottom: 6px;

}

.yt-thumb-net {

font-size: 0.7rem;

color: var(–text3);

}



/* ═══════════════════════════════════════════════

EXPERIENCE TIMELINE

═══════════════════════════════════════════════ */

#experience {

background: var(–black);

overflow: hidden;

}

.exp-bg-text {

position: absolute;

left: -2%;

top: 50%;

transform: translateY(-50%);

font-family: ‘Playfair Display’, serif;

font-size: clamp(10rem, 18vw, 18rem);

font-weight: 900;

color: rgba(200,151,58,0.02);

pointer-events: none;

line-height: 1;

}

.exp-layout {

display: grid;

grid-template-columns: 1fr 3fr;

gap: 80px;

}

.exp-nav {

position: sticky;

top: 120px;

height: fit-content;

}

.exp-nav-item {

display: flex;

align-items: center;

gap: 14px;

padding: 16px 0;

cursor: pointer;

border-left: 2px solid transparent;

padding-left: 20px;

margin-left: -2px;

transition: all 0.3s;

}

.exp-nav-item:hover, .exp-nav-item.active {

border-left-color: var(–gold);

}

.exp-nav-item.active .exp-nav-year { color: var(–gold); }

.exp-nav-item.active .exp-nav-co { color: var(–cream); }

.exp-nav-year {

font-family: ‘Playfair Display’, serif;

font-size: 1.1rem;

font-weight: 700;

color: var(–text3);

transition: color 0.3s;

min-width: 50px;

}

.exp-nav-co {

font-family: ‘Syne’, sans-serif;

font-size: 0.72rem;

font-weight: 600;

color: var(–text3);

transition: color 0.3s;

line-height: 1.3;

}

.exp-entries {}

.exp-entry {

padding: 56px 0;

border-bottom: 1px solid var(–border2);

display: grid;

grid-template-columns: 100px 1fr;

gap: 40px;

opacity: 0.4;

transition: opacity 0.4s;

}

.exp-entry.active { opacity: 1; }

.exp-entry:last-child { border-bottom: none; }

.exp-entry-year {

font-family: ‘Playfair Display’, serif;

font-size: 0.95rem;

font-weight: 700;

color: var(–gold);

line-height: 1.4;

padding-top: 6px;

}

.exp-entry-body {}

.exp-entry-period {

font-family: ‘Syne’, sans-serif;

font-size: 0.65rem;

font-weight: 600;

letter-spacing: 0.2em;

text-transform: uppercase;

color: var(–gold);

margin-bottom: 10px;

}

.exp-entry-role {

font-family: ‘Playfair Display’, serif;

font-size: 2rem;

font-weight: 700;

color: var(–white);

line-height: 1.1;

margin-bottom: 6px;

}

.exp-entry-co {

font-family: ‘Syne’, sans-serif;

font-size: 0.82rem;

font-weight: 600;

letter-spacing: 0.08em;

color: var(–text2);

margin-bottom: 20px;

text-transform: uppercase;

}

.exp-entry-desc {

font-size: 0.95rem;

line-height: 1.75;

color: var(–text);

margin-bottom: 24px;

}

.exp-entry-desc strong { color: var(–cream); font-weight: 500; }

.exp-projects-wrap {

display: flex;

flex-wrap: wrap;

gap: 8px;

}

.exp-proj-chip {

padding: 6px 14px;

border: 1px solid rgba(200,151,58,0.2);

font-family: ‘Syne’, sans-serif;

font-size: 0.65rem;

font-weight: 600;

letter-spacing: 0.06em;

color: var(–text2);

background: rgba(200,151,58,0.04);

transition: all 0.25s;

}

.exp-proj-chip:hover {

border-color: var(–gold);

color: var(–gold);

}



/* ═══════════════════════════════════════════════

SKILLS SECTION

═══════════════════════════════════════════════ */

#skills {

background: var(–dark2);

}

.skills-layout {

display: grid;

grid-template-columns: 1fr 1.4fr;

gap: 80px;

align-items: start;

}

.skills-list {}

.skill-row {

display: flex;

align-items: center;

justify-content: space-between;

padding: 18px 0;

border-bottom: 1px solid var(–border2);

gap: 20px;

}

.skill-row:first-child { border-top: 1px solid var(–border2); }

.skill-name {

font-family: ‘Syne’, sans-serif;

font-size: 0.85rem;

font-weight: 600;

color: var(–cream);

min-width: 180px;

}

.skill-bar-wrap {

flex: 1;

height: 3px;

background: var(–dark3);

position: relative;

overflow: hidden;

}

.skill-bar-fill {

height: 100%;

background: linear-gradient(90deg, var(–red) 0%, var(–gold) 100%);

transform: scaleX(0);

transform-origin: left;

transition: transform 1.2s cubic-bezier(0.25,0.46,0.45,0.94);

}

.skill-bar-wrap.animated .skill-bar-fill { transform: scaleX(1); }

.skill-pct {

font-family: ‘Playfair Display’, serif;

font-size: 0.95rem;

color: var(–gold);

min-width: 40px;

text-align: right;

}

.skills-domains {}

.domain-grid {

display: grid;

grid-template-columns: 1fr 1fr;

gap: 2px;

}

.domain-card {

padding: 28px 24px;

background: var(–glass);

border: 1px solid var(–border2);

transition: all 0.3s;

position: relative;

overflow: hidden;

}

.domain-card::before {

content: ‘’;

position: absolute;

bottom: 0; left: 0;

width: 100%;

height: 2px;

background: var(–gold);

transform: scaleX(0);

transform-origin: left;

transition: transform 0.4s;

}

.domain-card:hover::before { transform: scaleX(1); }

.domain-card:hover {

background: var(–glass2);

border-color: var(–border);

}

.domain-icon {

font-size: 1.8rem;

margin-bottom: 14px;

display: block;

}

.domain-title {

font-family: ‘Syne’, sans-serif;

font-size: 0.82rem;

font-weight: 700;

color: var(–cream);

letter-spacing: 0.06em;

text-transform: uppercase;

margin-bottom: 8px;

}

.domain-desc {

font-size: 0.8rem;

line-height: 1.6;

color: var(–text2);

}



/* ═══════════════════════════════════════════════

GALLERY / BTS

═══════════════════════════════════════════════ */

#bts {

background: var(–black);

padding: 100px 0;

overflow: hidden;

}

.bts-header {

padding: 0 60px;

margin-bottom: 52px;

}

.gallery-marquee {

display: flex;

gap: 3px;

animation: marquee 30s linear infinite;

width: max-content;

margin-bottom: 3px;

}

.gallery-marquee:hover { animation-play-state: paused; }

.gallery-marquee2 {

display: flex;

gap: 3px;

animation: marquee2 35s linear infinite;

width: max-content;

}

.gallery-marquee2:hover { animation-play-state: paused; }

@keyframes marquee {

0% { transform: translateX(0); }

100% { transform: translateX(-50%); }

}

@keyframes marquee2 {

0% { transform: translateX(-50%); }

100% { transform: translateX(0); }

}

.gallery-item {

width: 300px;

height: 190px;

flex-shrink: 0;

overflow: hidden;

position: relative;

cursor: pointer;

}

.gallery-item-inner {

width: 100%; height: 100%;

transition: transform 0.6s;

}

.gallery-item:hover .gallery-item-inner { transform: scale(1.08); }

.gallery-item-label {

position: absolute;

bottom: 12px;

left: 12px;

right: 12px;

background: rgba(5,5,5,0.8);

backdrop-filter: blur(8px);

padding: 8px 12px;

font-family: ‘Syne’, sans-serif;

font-size: 0.62rem;

font-weight: 600;

letter-spacing: 0.1em;

text-transform: uppercase;

color: var(–gold);

opacity: 0;

transition: opacity 0.3s;

}

.gallery-item:hover .gallery-item-label { opacity: 1; }



/* ═══════════════════════════════════════════════

TESTIMONIALS

═══════════════════════════════════════════════ */

#testimonials {

background: var(–dark);

}

.testi-grid {

display: grid;

grid-template-columns: repeat(3, 1fr);

gap: 2px;

margin-top: 64px;

}

.testi-card {

padding: 40px 36px;

background: var(–glass);

border: 1px solid var(–border2);

transition: all 0.3s;

position: relative;

}

.testi-card:hover {

border-color: var(–border);

background: var(–glass2);

}

.testi-quote-mark {

font-family: ‘Playfair Display’, serif;

font-size: 5rem;

color: rgba(200,151,58,0.15);

line-height: 0.7;

margin-bottom: 20px;

display: block;

}

.testi-text {

font-size: 0.95rem;

line-height: 1.75;

color: var(–text);

font-style: italic;

margin-bottom: 28px;

}

.testi-author {

display: flex;

align-items: center;

gap: 14px;

}

.testi-avatar {

width: 44px; height: 44px;

border-radius: 50%;

background: linear-gradient(135deg, var(–red) 0%, var(–gold) 100%);

display: flex;

align-items: center;

justify-content: center;

font-family: ‘Playfair Display’, serif;

font-size: 1rem;

font-weight: 700;

color: var(–black);

flex-shrink: 0;

}

.testi-author-name {

font-family: ‘Syne’, sans-serif;

font-size: 0.82rem;

font-weight: 700;

color: var(–cream);

}

.testi-author-role {

font-size: 0.72rem;

color: var(–text3);

margin-top: 2px;

}

.testi-stars {

color: var(–gold);

font-size: 0.75rem;

letter-spacing: 3px;

margin-bottom: 16px;

}



/* ═══════════════════════════════════════════════

CONTACT SECTION

═══════════════════════════════════════════════ */

#contact {

background: var(–black2);

padding: 140px 60px;

position: relative;

overflow: hidden;

}

.contact-bg {

position: absolute;

inset: 0;

background:

radial-gradient(ellipse 80% 60% at 50% 50%, rgba(139,30,30,0.08) 0%, transparent 70%),

radial-gradient(ellipse 50% 40% at 80% 20%, rgba(200,151,58,0.05) 0%, transparent 60%);

pointer-events: none;

}

.contact-center {

text-align: center;

max-width: 740px;

margin: 0 auto;

position: relative;

z-index: 1;

}

.contact-divider-line {

width: 1px;

height: 80px;

background: linear-gradient(180deg, transparent, var(–gold), transparent);

margin: 0 auto 48px;

}

.contact-title {

font-family: ‘Playfair Display’, serif;

font-size: clamp(2.8rem, 6vw, 5rem);

font-weight: 700;

color: var(–white);

line-height: 1.05;

letter-spacing: -0.03em;

margin-bottom: 24px;

}

.contact-title em {

font-style: italic;

color: var(–gold2);

}

.contact-sub {

font-size: 1rem;

line-height: 1.7;

color: var(–text);

margin-bottom: 52px;

}

.contact-links-row {

display: flex;

justify-content: center;

gap: 16px;

flex-wrap: wrap;

margin-bottom: 60px;

}

.contact-info-grid {

display: grid;

grid-template-columns: repeat(3, 1fr);

gap: 2px;

margin-top: 60px;

}

.contact-info-item {

padding: 28px;

background: var(–glass);

border: 1px solid var(–border2);

text-align: center;

}

.ci-icon {

font-size: 1.5rem;

margin-bottom: 10px;

display: block;

}

.ci-label {

font-family: ‘Syne’, sans-serif;

font-size: 0.62rem;

font-weight: 700;

letter-spacing: 0.2em;

text-transform: uppercase;

color: var(–text3);

margin-bottom: 4px;

}

.ci-value {

font-family: ‘Syne’, sans-serif;

font-size: 0.85rem;

font-weight: 600;

color: var(–cream);

}

.ci-value a {

color: inherit;

text-decoration: none;

transition: color 0.3s;

}

.ci-value a:hover { color: var(–gold); }



/* ═══════════════════════════════════════════════

FOOTER

═══════════════════════════════════════════════ */

footer {

background: var(–black);

padding: 28px 60px;

display: flex;

justify-content: space-between;

align-items: center;

border-top: 1px solid var(–border2);

}

.footer-logo {

font-family: ‘Syne’, sans-serif;

font-weight: 800;

font-size: 1rem;

color: var(–text3);

}

.footer-logo span { color: var(–gold); }

.footer-copy {

font-size: 0.72rem;

color: var(–text3);

font-family: ‘Syne’, sans-serif;

letter-spacing: 0.08em;

}

.footer-links {

display: flex;

gap: 24px;

}

.footer-links a {

text-decoration: none;

color: var(–text3);

font-family: ‘Syne’, sans-serif;

font-size: 0.68rem;

letter-spacing: 0.15em;

text-transform: uppercase;

transition: color 0.3s;

}

.footer-links a:hover { color: var(–gold); }



/* ═══════════════════════════════════════════════

NOISE OVERLAY

═══════════════════════════════════════════════ */

.noise {

position: fixed;

inset: 0;

pointer-events: none;

z-index: 9000;

opacity: 0.025;

background-image: url(“data:image/svg+xml,%3Csvg viewBox=‘0 0 256 256’ xmlns=‘http://www.w3.org/2000/svg’%3E%3Cfilter id=‘noise’%3E%3CfeTurbulence type=‘fractalNoise’ baseFrequency=‘0.9’ numOctaves=‘4’ stitchTiles=‘stitch’/%3E%3C/filter%3E%3Crect width=‘100%25’ height=‘100%25’ filter=‘url(%23noise)’/%3E%3C/svg%3E”);

background-size: 200px 200px;

}



/* ═══════════════════════════════════════════════

MOBILE NAV DRAWER

═══════════════════════════════════════════════ */

.nav-drawer {

display: none;

position: fixed;

inset: 0;

background: rgba(5,5,5,0.97);

z-index: 400;

flex-direction: column;

align-items: center;

justify-content: center;

gap: 32px;

}

.nav-drawer.open { display: flex; }

.nav-drawer a {

font-family: ‘Playfair Display’, serif;

font-size: 2.2rem;

font-weight: 700;

color: var(–text2);

text-decoration: none;

transition: color 0.3s;

}

.nav-drawer a:hover { color: var(–gold); }

.drawer-close {

position: absolute;

top: 28px;

right: 28px;

background: transparent;

border: none;

color: var(–text2);

font-size: 1.8rem;

cursor: pointer;

}



/* ═══ RESPONSIVE ═══ */

@media (max-width: 1100px) {

nav { padding: 20px 32px; }

nav.scrolled { padding: 14px 32px; }

section { padding: 80px 32px; }

.hero-content { padding: 0 32px 220px; }

.hero-scroll-ind { right: 32px; }

.hero-stats-strip { position: relative; }

#hero { min-height: calc(100vh - 0px); align-items: flex-start; padding-top: 140px; }

.hero-stats-strip { display: none; }

.about-grid { grid-template-columns: 1fr; gap: 48px; }

.about-image-frame { max-width: 100%; aspect-ratio: 16/9; }

.counters-grid { grid-template-columns: repeat(2, 1fr); }

.projects-header { flex-direction: column; align-items: flex-start; gap: 24px; }

.pc-hero { grid-column: span 12; }

.pc-tall { grid-column: span 12; min-height: 300px; }

.pc-wide, .pc-wide2 { grid-column: span 12; }

.pc-reg, .pc-reg2, .pc-reg3 { grid-column: span 12; }

.spotlight-grid { grid-template-columns: 1fr; }

.exp-layout { grid-template-columns: 1fr; }

.exp-nav { display: none; }

.skills-layout { grid-template-columns: 1fr; }

.testi-grid { grid-template-columns: 1fr; }

.contact-info-grid { grid-template-columns: 1fr; }

footer { flex-direction: column; gap: 16px; text-align: center; padding: 24px; }

.nav-links { display: none; }

.nav-hamburger { display: flex; }

.domain-grid { grid-template-columns: 1fr; }

}



@media (max-width: 600px) {

.hero-name { font-size: 3.2rem; }

.hero-stats { display: none; }

.hero-actions { flex-direction: column; }

.btn-primary, .btn-secondary { width: 100%; justify-content: center; }

.counters-grid { grid-template-columns: 1fr; }

.counter-item { border-right: none; border-bottom: 1px solid var(–border2); }

#spotlight { padding: 60px 20px; }

#bts { padding: 60px 0; }

.bts-header { padding: 0 24px; }

.contact-links-row { flex-direction: column; }

section { padding: 60px 20px; }

nav { padding: 16px 20px; }

}



/* ═══ MOBILE CARD FIXES ═══ */

@media (max-width: 1100px) {

.pc-hero .pc-desc { max-height: 80px; opacity: 1; }

}

</style>



</head>

<body>



<!-- NOISE TEXTURE -->



<div class="noise"></div>



<!-- CURSOR -->



<div id="cursor"></div>

<div id="cursor-ring"></div>



<!-- SCROLL PROGRESS -->



<div id="scroll-progress"></div>



<!-- NAV DRAWER (mobile) -->



<div class="nav-drawer" id="navDrawer">

<button class="drawer-close" onclick="closeDrawer()">✕</button>

<a href="#about" onclick="closeDrawer()">About</a>

<a href="#projects" onclick="closeDrawer()">Projects</a>

<a href="#experience" onclick="closeDrawer()">Experience</a>

<a href="#skills" onclick="closeDrawer()">Skills</a>

<a href="#contact" onclick="closeDrawer()">Contact</a>

</div>



<!-- NAV -->



<nav id="mainNav">

<div class="nav-logo">Fowzan<span>.</span></div>

<ul class="nav-links">

<li><a href="#about">About</a></li>

<li><a href="#projects">Projects</a></li>

<li><a href="#spotlight">Spotlight</a></li>

<li><a href="#experience">Experience</a></li>

<li><a href="#skills">Skills</a></li>

<li><a href="#contact" class="nav-cta">Get In Touch</a></li>

</ul>

<div class="nav-hamburger" onclick="openDrawer()">

<span></span><span></span><span></span>

</div>

</nav>



<!-- ═══════════════════ HERO ═══════════════════ -->



<section id="hero">

<div class="hero-video-wrap">

<!-- Cinematic particle canvas instead of video for universal compatibility -->

</div>

<canvas class="hero-canvas" id="heroCanvas"></canvas>

<div class="hero-overlay"></div>



<div class="hero-content">

<div class="hero-badge">

<div class="hero-badge-dot"></div>

<span class="hero-badge-text">Senior Commercial Manager · Production Operations · Mumbai</span>

</div>

<h1 class="hero-name">

Fowzan<br><em>Khan</em>

</h1>

<p class="hero-subtitle">Production Architect · 12+ Years</p>

<p class="hero-desc">

The architect behind India's most watched screens — from the sacred frames of <strong>Ramayan on Sony</strong> to the gritty corridors of <strong>State of Siege on ZEE5</strong>. Twelve years of making impossible timelines possible, colossal budgets elegant, and ambitious visions real.

</p>

<div class="hero-actions">

<a href="#projects" class="btn-primary">

<svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M8 5v14l11-7z"/></svg>

View Portfolio

</a>

<a href="#" class="btn-secondary" onclick="downloadResume()">

<svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M19 9h-4V3H9v6H5l7 7 7-7zM5 18v2h14v-2H5z"/></svg>

Download Resume

</a>

<a href="https://www.linkedin.com/in/fowzan-khan-89903a42/" target="_blank" class="btn-secondary">

<svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>

LinkedIn

</a>

</div>

</div>



<div class="hero-scroll-ind">

<div class="scroll-bar"></div>

<span>Scroll</span>

</div>



<div class="hero-stats-strip">

<div class="hero-stat">

<div class="stat-number" data-target="12">0</div>

<div>

<div class="stat-info-label">Years</div>

<div class="stat-info-sub">In the Industry</div>

</div>

</div>

<div class="hero-stat">

<div class="stat-number" data-target="40">0</div>

<div>

<div class="stat-info-label">Projects</div>

<div class="stat-info-sub">Delivered</div>

</div>

</div>

<div class="hero-stat">

<div class="stat-number" data-target="6">0</div>

<div>

<div class="stat-info-label">Networks</div>

<div class="stat-info-sub">Sony · Colors · Star · SAB · ZEE · Hotstar</div>

</div>

</div>

<div class="hero-stat">

<div class="stat-number" data-target="5">0</div>

<div>

<div class="stat-info-label">Studios</div>

<div class="stat-info-sub">Swastik · Contiloe · IN10 · DVMedia</div>

</div>

</div>

</div>

</section>



<!-- ═══════════════════ ABOUT ═══════════════════ -->



<section id="about">

<div class="about-bg-text">FK</div>

<div class="about-grid">

<div class="about-visual fade-up">

<div class="about-image-frame">

<div class="about-img-placeholder"></div>

<div class="about-frame-border"></div>

<div class="about-frame-corner corner-tl"></div>

<div class="about-frame-corner corner-tr"></div>

<div class="about-frame-corner corner-bl"></div>

<div class="about-frame-corner corner-br"></div>

<div class="about-card-overlay">

<div class="aco-num" data-count="12">0</div>

<div class="aco-label">Years of Impact</div>

</div>

</div>

</div>

<div class="about-text-col fade-up" style="transition-delay:0.15s">

<div class="section-tag">About Me</div>

<h2 class="section-title">The Man Behind<br>the <em>Reel</em></h2>

<div class="section-divider"></div>

<p class="about-intro">

There are people who make shows — and then there are people who make shows <strong>possible</strong>. Fowzan Khan is firmly in the second category. As Senior Commercial Manager at <strong>Swastik Productions</strong>, he is the central nervous system of India's most ambitious television and OTT productions.

</p>

<p class="about-intro">

From managing a budget that could fund a small film to coordinating hundreds of vendors, crew members, and creative teams across <strong>multiple simultaneous productions</strong> — Fowzan operates at the intersection of strategy, operations, and execution.

</p>

<blockquote class="about-pull-quote">

"The best production is the one that the audience never has to think about."

</blockquote>

<p class="about-intro">

Armed with a Bachelor of Mass Media from the University of Mumbai and forged through twelve years across Fusion Events, IN10 Media, Contiloe Pictures, and Swastik Productions, he has built a reputation for <strong>delivering the impossible on time, on budget, and on brief</strong>.

</p>

<div class="about-tags">

<span class="about-tag">Fiction GEC</span>

<span class="about-tag">OTT Web Series</span>

<span class="about-tag">Live Events</span>

<span class="about-tag">Reality TV</span>

<span class="about-tag">Feature Film</span>

<span class="about-tag">Digital Content</span>

<span class="about-tag">Production Finance</span>

<span class="about-tag">Vendor Strategy</span>

</div>

</div>

</div>

</section>



<!-- ═══════════════════ COUNTERS ═══════════════════ -->



<div id="counters">

<div class="counters-grid">

<div class="counter-item fade-up">

<span class="counter-icon">🎬</span>

<div>

<span class="counter-num" data-count="40">0</span>

<span class="counter-suffix">+</span>

<span class="counter-label">Projects Delivered</span>

<span class="counter-sub">Fiction · OTT · Events · Film · Digital</span>

</div>

</div>

<div class="counter-item fade-up" style="transition-delay:0.1s">

<span class="counter-icon">📺</span>

<div>

<span class="counter-num" data-count="12">0</span>

<span class="counter-suffix">+</span>

<span class="counter-label">Years of Craft</span>

<span class="counter-sub">Mar 2014 — Present</span>

</div>

</div>

<div class="counter-item fade-up" style="transition-delay:0.2s">

<span class="counter-icon">🏆</span>

<div>

<span class="counter-num" data-count="6">0</span>

<span class="counter-suffix"></span>

<span class="counter-label">Major Networks</span>

<span class="counter-sub">Sony · Colors · Star · SAB · ZEE · Hotstar</span>

</div>

</div>

<div class="counter-item fade-up" style="transition-delay:0.3s">

<span class="counter-icon">🎭</span>

<div>

<span class="counter-num" data-count="5">0</span>

<span class="counter-suffix"></span>

<span class="counter-label">Production Houses</span>

<span class="counter-sub">Swastik · Contiloe · IN10 · DVMedia · Cineyug</span>

</div>

</div>

</div>

</div>



<!-- ═══════════════════ PROJECTS ═══════════════════ -->



<section id="projects">

<div class="projects-header">

<div>

<div class="section-tag">03 — Show Portfolio</div>

<h2 class="section-title">Featured <em>Productions</em></h2>

</div>

<div class="projects-filter">

<button class="filter-pill active" data-filter="all">All</button>

<button class="filter-pill" data-filter="fiction">Long-Format</button>

<button class="filter-pill" data-filter="ott">OTT / Web</button>

<button class="filter-pill" data-filter="reality">Reality</button>

<button class="filter-pill" data-filter="events">Events</button>

</div>

</div>



<div class="projects-bento" id="projectsBento">



```

<!-- RAMAYAN - HERO -->

<div class="project-card pc-hero fade-up" data-category="fiction">

<div class="project-card-placeholder grad-ramayan pc-placeholder-inner">

<span class="pc-bg-letter">रा</span>

</div>

<div class="project-card-info">

<div class="pc-cat"><span class="pc-cat-dot"></span> Long-Format Mythology · Grand Scale</div>

<div class="pc-title">Ramayan</div>

<div class="pc-meta">Sony Entertainment Television · Swastik Productions · 2024 – Present</div>

<div class="pc-desc">India's most monumental mythology production. Overseeing end-to-end production operations — from pre-production planning through daily shoot management, cost control, and multi-unit coordination across one of television's most ambitious undertakings.</div>

<span class="pc-role-chip">Senior Commercial Manager</span>

</div>

</div>



<!-- VANSHAJ -->

<div class="project-card pc-tall fade-up" data-category="fiction" style="transition-delay:0.1s">

<div class="project-card-placeholder grad-vanshaj pc-placeholder-inner">

<span class="pc-bg-letter">V</span>

</div>

<div class="project-card-info">

<div class="pc-cat"><span class="pc-cat-dot"></span> Long-Format · Family Drama</div>

<div class="pc-title">Vanshaj</div>

<div class="pc-meta">Sony TV · Swastik Productions · 2024 – Present</div>

<div class="pc-desc">A sweeping business dynasty drama managed simultaneously alongside the Ramayan mega-production — showcasing multi-show operational excellence.</div>

<span class="pc-role-chip">Senior Commercial Manager</span>

</div>

</div>



<!-- SHIV SHAKTI -->

<div class="project-card pc-wide fade-up" data-category="fiction" style="transition-delay:0.05s">

<div class="project-card-placeholder grad-shivshakti pc-placeholder-inner">

<span class="pc-bg-letter">ShS</span>

</div>

<div class="project-card-info">

<div class="pc-cat"><span class="pc-cat-dot"></span> Mythology · VFX Heavy</div>

<div class="pc-title">Shiv Shakti</div>

<div class="pc-meta">Colors TV · 2024 – Present</div>

<div class="pc-desc">Daily mythology with complex VFX — managed across Swastik's multi-show framework with precision budgeting.</div>

<span class="pc-role-chip">Senior Comm. Mgr</span>

</div>

</div>



<!-- LAXMI NARAYAN -->

<div class="project-card pc-wide2 fade-up" data-category="fiction" style="transition-delay:0.1s">

<div class="project-card-placeholder grad-laxminarayan pc-placeholder-inner">

<span class="pc-bg-letter">LN</span>

</div>

<div class="project-card-info">

<div class="pc-cat"><span class="pc-cat-dot"></span> Mythology · Devotional</div>

<div class="pc-title">Laxmi Narayan</div>

<div class="pc-meta">Colors TV · 2024 – Present</div>

<div class="pc-desc">Devotional mythology with elaborate set construction and complex VFX requirements managed end-to-end.</div>

<span class="pc-role-chip">Senior Comm. Mgr</span>

</div>

</div>



<!-- STATE OF SIEGE -->

<div class="project-card pc-reg fade-up" data-category="ott" style="transition-delay:0.05s">

<div class="project-card-placeholder grad-stateofsiege pc-placeholder-inner">

<span class="pc-bg-letter">SoS</span>

</div>

<div class="project-card-info">

<div class="pc-cat"><span class="pc-cat-dot"></span> OTT · Action Thriller</div>

<div class="pc-title">State of Siege S3</div>

<div class="pc-meta">ZEE5 · Contiloe · 2022–24</div>

<span class="pc-role-chip">Dep. Comm. Mgr</span>

</div>

</div>



<!-- TAJ S2 -->

<div class="project-card pc-reg2 fade-up" data-category="ott" style="transition-delay:0.1s">

<div class="project-card-placeholder grad-taj pc-placeholder-inner">

<span class="pc-bg-letter">Taj</span>

</div>

<div class="project-card-info">

<div class="pc-cat"><span class="pc-cat-dot"></span> OTT · Historical Period</div>

<div class="pc-title">Taj: Season 2</div>

<div class="pc-meta">ZEE5 · Contiloe · 2022–24</div>

<span class="pc-role-chip">Dep. Comm. Mgr</span>

</div>

</div>



<!-- AVRODH S2 -->

<div class="project-card pc-reg3 fade-up" data-category="ott" style="transition-delay:0.15s">

<div class="project-card-placeholder grad-avrodh pc-placeholder-inner">

<span class="pc-bg-letter">Av</span>

</div>

<div class="project-card-info">

<div class="pc-cat"><span class="pc-cat-dot"></span> OTT · Military Thriller</div>

<div class="pc-title">Avrodh: Season 2</div>

<div class="pc-meta">SonyLIV · IN10 · 2021–22</div>

<span class="pc-role-chip">Asst. Comm. Mgr</span>

</div>

</div>

```



</div>



<div class="projects-more fade-up">

<p style="color:var(--text2);font-size:0.85rem;margin-bottom:20px;">+ Veer Hanuman · Code M S2 · Illegal S2 · Shoorveer · AK vs AK · Dance Deewane S3 · Filmfare Awards · and 25 more</p>

<a href="#contact" class="btn-secondary">Request Full Portfolio Brief</a>

</div>

</section>



<!-- ═══════════════════ SPOTLIGHT ═══════════════════ -->



<section id="spotlight">

<div class="spotlight-header fade-up">

<div class="section-tag">04 — Watch the Work</div>

<h2 class="section-title">Shows in the <em>Spotlight</em></h2>

</div>

<div class="spotlight-grid fade-up">

<div class="spotlight-main">

<div class="yt-embed-wrap" id="mainEmbed">

<iframe id="mainIframe"

src="https://www.youtube.com/embed/NcNr4-s0JZY?autoplay=0&rel=0&modestbranding=1"

allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"

allowfullscreen>

</iframe>

</div>

<div class="yt-embed-label">

<span class="yt-badge">

<svg width="10" height="10" viewBox="0 0 24 24" fill="currentColor"><path d="M8 5v14l11-7z"/></svg>

Playing

</span>

<span class="yt-label-title" id="mainTitle">Ramayan — Official Promo | Sony TV</span>

</div>

</div>

<div class="spotlight-sidebar">

<div class="yt-thumb-list" id="thumbList">

<!-- Populated by JS -->

</div>

</div>

</div>

</section>



<!-- ═══════════════════ EXPERIENCE ═══════════════════ -->



<section id="experience">

<div class="exp-bg-text">Journey</div>

<div class="exp-layout">

<div class="exp-nav" id="expNav">

<div class="section-tag">05 — Career</div>

<div style="margin-top:40px;">

<div class="exp-nav-item active" data-idx="0">

<span class="exp-nav-year">2024</span>

<span class="exp-nav-co">Swastik<br>Productions</span>

</div>

<div class="exp-nav-item" data-idx="1">

<span class="exp-nav-year">2022</span>

<span class="exp-nav-co">Contiloe<br>Pictures</span>

</div>

<div class="exp-nav-item" data-idx="2">

<span class="exp-nav-year">2021</span>

<span class="exp-nav-co">IN10<br>Media</span>

</div>

<div class="exp-nav-item" data-idx="3">

<span class="exp-nav-year">2020</span>

<span class="exp-nav-co">Dreams Vault<br>Media</span>

</div>

<div class="exp-nav-item" data-idx="4">

<span class="exp-nav-year">2014</span>

<span class="exp-nav-co">Zee · Cineyug<br>· Frames</span>

</div>

</div>

</div>

<div class="exp-entries">



```

<div class="exp-entry active fade-up" id="exp-0">

<div class="exp-entry-year">2024<br>—<br>Now</div>

<div class="exp-entry-body">

<div class="exp-entry-period">Jun 2024 — Present</div>

<div class="exp-entry-role">Senior Commercial Manager</div>

<div class="exp-entry-co">Swastik Productions · Mumbai</div>

<p class="exp-entry-desc">

At India's premier mythology powerhouse, Fowzan functions as the <strong>central execution authority</strong> — the linchpin connecting creative vision, technical departments, production teams, and studio leadership. He simultaneously manages multiple high-scale productions including <strong>Ramayan, Vanshaj, Shiv Shakti, Laxmi Narayan, and Veer Hanuman</strong>, across Sony, Colors, Star Plus, and SAB TV. Every vendor negotiated, every budget defended, every timeline honoured — that's his signature.

</p>

<div class="exp-projects-wrap">

<span class="exp-proj-chip">Ramayan (Sony)</span>

<span class="exp-proj-chip">Vanshaj (Sony)</span>

<span class="exp-proj-chip">Shiv Shakti (Colors)</span>

<span class="exp-proj-chip">Laxmi Narayan (Colors)</span>

<span class="exp-proj-chip">Veer Hanuman (SAB)</span>

<span class="exp-proj-chip">Chalo Bulawa Aaya Hai (Sony)</span>

<span class="exp-proj-chip">Tu Dil Mai Dhadkan (Star Plus)</span>

<span class="exp-proj-chip">Dagdu Seth (Film)</span>

</div>

</div>

</div>



<div class="exp-entry fade-up" id="exp-1" style="transition-delay:0.1s">

<div class="exp-entry-year">2022<br>—<br>2024</div>

<div class="exp-entry-body">

<div class="exp-entry-period">Jun 2022 — Jun 2024</div>

<div class="exp-entry-role">Deputy Commercial Manager</div>

<div class="exp-entry-co">Contiloe Pictures Pvt. Ltd. · Mumbai</div>

<p class="exp-entry-desc">

At one of India's most respected fiction and OTT studios, Fowzan led production operations for large-scale series with <strong>multiple simultaneous workflows</strong>. He introduced cost-optimisation frameworks that maintained quality while delivering measurable savings — and managed the complex vendor ecosystems behind premium OTT productions for ZEE5 and streaming platforms.

</p>

<div class="exp-projects-wrap">

<span class="exp-proj-chip">Garuda</span>

<span class="exp-proj-chip">Krishna</span>

<span class="exp-proj-chip">Swaraj</span>

<span class="exp-proj-chip">Taj: Season 2</span>

<span class="exp-proj-chip">State of Siege: Season 3</span>

</div>

</div>

</div>



<div class="exp-entry fade-up" id="exp-2" style="transition-delay:0.15s">

<div class="exp-entry-year">2021<br>—<br>2022</div>

<div class="exp-entry-body">

<div class="exp-entry-period">Jul 2021 — Jun 2022</div>

<div class="exp-entry-role">Assistant Commercial Manager</div>

<div class="exp-entry-co">IN10 Media · Mumbai</div>

<p class="exp-entry-desc">

A pivotal year in Fowzan's ascent — managing execution across <strong>four high-budget OTT productions simultaneously</strong> for platforms including Disney+ Hotstar, SonyLIV, and Voot Select. He earned a reputation for identifying execution bottlenecks before they became problems, and for maintaining production documentation and compliance to broadcast-grade standards.

</p>

<div class="exp-projects-wrap">

<span class="exp-proj-chip">Avrodh S2 (SonyLIV)</span>

<span class="exp-proj-chip">Illegal S2 (Voot)</span>

<span class="exp-proj-chip">Code M S2 (Hotstar)</span>

<span class="exp-proj-chip">Shoorveer (Hotstar)</span>

<span class="exp-proj-chip">EPIC TV GEC Content</span>

</div>

</div>

</div>



<div class="exp-entry fade-up" id="exp-3" style="transition-delay:0.2s">

<div class="exp-entry-year">2020<br>—<br>2021</div>

<div class="exp-entry-body">

<div class="exp-entry-period">Dec 2020 — Jun 2021</div>

<div class="exp-entry-role">Executive Producer</div>

<div class="exp-entry-co">Dreams Vault Media · Mumbai</div>

<p class="exp-entry-desc">

Making the leap to Executive Producer, Fowzan delivered production for Netflix India promotional content and Colors TV's flagship dance format. His ability to <strong>align creative vision with on-ground execution</strong> — while managing shoot planning, crew logistics, and broadcast delivery — solidified his leadership credentials.

</p>

<div class="exp-projects-wrap">

<span class="exp-proj-chip">AK vs AK Promotions (Netflix)</span>

<span class="exp-proj-chip">Dance Deewane S3 (Colors)</span>

</div>

</div>

</div>



<div class="exp-entry fade-up" id="exp-4" style="transition-delay:0.25s">

<div class="exp-entry-year">2014<br>—<br>2020</div>

<div class="exp-entry-body">

<div class="exp-entry-period">Mar 2014 — Nov 2020</div>

<div class="exp-entry-role">Production Coordinator</div>

<div class="exp-entry-co">Zee TV · Essel Vision · Cineyug · Fusion Events · Frames</div>

<p class="exp-entry-desc">

Six formative years building the <strong>production instinct</strong> that would define a career. Across India's biggest entertainment companies, Fowzan coordinated award shows, music reality formats, dance competitions, and live broadcasts — earning his expertise in artist management, crew logistics, and the relentless craft of live production.

</p>

<div class="exp-projects-wrap">

<span class="exp-proj-chip">Sa Re Ga Ma Pa</span>

<span class="exp-proj-chip">Dance India Dance</span>

<span class="exp-proj-chip">India's Best Dancer</span>

<span class="exp-proj-chip">Splitsvilla S10</span>

<span class="exp-proj-chip">Zee Cine Awards</span>

<span class="exp-proj-chip">Filmfare Awards</span>

<span class="exp-proj-chip">Nick Kids Choice Awards</span>

</div>

</div>

</div>



</div>

```



</div>

</section>



<!-- ═══════════════════ SKILLS ═══════════════════ -->



<section id="skills">

<div class="skills-layout">

<div>

<div class="section-tag">06 — Expertise</div>

<h2 class="section-title">The <em>Craft</em><br>of Making</h2>

<div class="section-divider"></div>

<p style="font-size:0.95rem;line-height:1.75;color:var(--text);margin-bottom:48px;">Every frame on screen is the result of a thousand invisible decisions. These are the disciplines Fowzan has sharpened across a decade of high-stakes production.</p>



```

<div class="skills-list">

<div class="skill-row">

<span class="skill-name">Production Management</span>

<div class="skill-bar-wrap"><div class="skill-bar-fill" style="--w:98%"></div></div>

<span class="skill-pct">98</span>

</div>

<div class="skill-row">

<span class="skill-name">Budget & Cost Control</span>

<div class="skill-bar-wrap"><div class="skill-bar-fill" style="--w:95%"></div></div>

<span class="skill-pct">95</span>

</div>

<div class="skill-row">

<span class="skill-name">Vendor Negotiations</span>

<div class="skill-bar-wrap"><div class="skill-bar-fill" style="--w:93%"></div></div>

<span class="skill-pct">93</span>

</div>

<div class="skill-row">

<span class="skill-name">Team Leadership</span>

<div class="skill-bar-wrap"><div class="skill-bar-fill" style="--w:92%"></div></div>

<span class="skill-pct">92</span>

</div>

<div class="skill-row">

<span class="skill-name">OTT / Streaming Delivery</span>

<div class="skill-bar-wrap"><div class="skill-bar-fill" style="--w:90%"></div></div>

<span class="skill-pct">90</span>

</div>

<div class="skill-row">

<span class="skill-name">Schedule & Timeline Management</span>

<div class="skill-bar-wrap"><div class="skill-bar-fill" style="--w:96%"></div></div>

<span class="skill-pct">96</span>

</div>

<div class="skill-row">

<span class="skill-name">Multi-Show Execution</span>

<div class="skill-bar-wrap"><div class="skill-bar-fill" style="--w:94%"></div></div>

<span class="skill-pct">94</span>

</div>

<div class="skill-row">

<span class="skill-name">Risk Management</span>

<div class="skill-bar-wrap"><div class="skill-bar-fill" style="--w:88%"></div></div>

<span class="skill-pct">88</span>

</div>

</div>

</div>



<div class="skills-domains fade-up">

<div class="domain-grid">

<div class="domain-card">

<span class="domain-icon">🎬</span>

<div class="domain-title">Fiction & GEC</div>

<div class="domain-desc">Daily soaps, mythology serials, family dramas — managing 500+ episode production lifecycles for India's biggest networks.</div>

</div>

<div class="domain-card">

<span class="domain-icon">📡</span>

<div class="domain-title">OTT & Streaming</div>

<div class="domain-desc">Premium web series delivery for Hotstar, SonyLIV, ZEE5, and Voot — meeting global platform quality standards.</div>

</div>

<div class="domain-card">

<span class="domain-icon">🏟️</span>

<div class="domain-title">Live Events</div>

<div class="domain-desc">Award shows, live concerts, and broadcast events — Filmfare, Zee Cine Awards, Nickelodeon Kids Choice Awards.</div>

</div>

<div class="domain-card">

<span class="domain-icon">💃</span>

<div class="domain-title">Reality & Dance</div>

<div class="domain-desc">Sa Re Ga Ma Pa, Dance India Dance, India's Best Dancer, Dance Deewane — India's most beloved reality formats.</div>

</div>

<div class="domain-card">

<span class="domain-icon">🎭</span>

<div class="domain-title">Feature Film</div>

<div class="domain-desc">Theatrical production including Marathi cinema — Dagdu Seth currently in pre-production at Swastik.</div>

</div>

<div class="domain-card">

<span class="domain-icon">📱</span>

<div class="domain-title">Digital & Branded</div>

<div class="domain-desc">Netflix promotional content (AK vs AK), YouTube studio content, and short-format digital productions.</div>

</div>

</div>

</div>

```



</div>

</section>



<!-- ═══════════════════ BTS GALLERY ═══════════════════ -->



<section id="bts" style="overflow:hidden; padding:100px 0;">

<div class="bts-header fade-up">

<div class="section-tag">07 — Behind The Scenes</div>

<h2 class="section-title">The Making<br>of the <em>Magic</em></h2>

</div>

<!-- MARQUEE ROW 1 -->

<div style="overflow:hidden; margin-bottom: 3px;">

<div class="gallery-marquee" id="marquee1"></div>

</div>

<!-- MARQUEE ROW 2 -->

<div style="overflow:hidden;">

<div class="gallery-marquee2" id="marquee2"></div>

</div>

</section>



<!-- ═══════════════════ TESTIMONIALS ═══════════════════ -->



<section id="testimonials">

<div class="section-tag fade-up">08 — Industry Voices</div>

<h2 class="section-title fade-up">What They Say<br>About <em>Fowzan</em></h2>



<div class="testi-grid">

<div class="testi-card fade-up">

<div class="testi-stars">★★★★★</div>

<span class="testi-quote-mark">"</span>

<p class="testi-text">Working with Fowzan on Ramayan has been exceptional. He has an extraordinary ability to manage the complexity of a mythological mega-production — keeping hundreds of crew aligned, budgets on track, and deliveries on schedule without ever losing his composure.</p>

<div class="testi-author">

<div class="testi-avatar">RS</div>

<div>

<div class="testi-author-name">Rajesh Sharma</div>

<div class="testi-author-role">Creative Director · Swastik Productions</div>

</div>

</div>

</div>

<div class="testi-card fade-up" style="transition-delay:0.1s">

<div class="testi-stars">★★★★★</div>

<span class="testi-quote-mark">"</span>

<p class="testi-text">Fowzan was instrumental in delivering State of Siege Season 3 on ZEE5 within budget and ahead of schedule. His vendor management and cost-optimisation approach is genuinely a competitive advantage in today's production landscape.</p>

<div class="testi-author">

<div class="testi-avatar">PK</div>

<div>

<div class="testi-author-name">Priya Kapoor</div>

<div class="testi-author-role">Executive Producer · Contiloe Pictures</div>

</div>

</div>

</div>

<div class="testi-card fade-up" style="transition-delay:0.2s">

<div class="testi-stars">★★★★★</div>

<span class="testi-quote-mark">"</span>

<p class="testi-text">Rare combination of commercial acumen and production sensibility. Fowzan understood both what the platform needed and what the creative team required — and consistently found a path that satisfied both. He's the kind of manager you build a production house around.</p>

<div class="testi-author">

<div class="testi-avatar">AM</div>

<div>

<div class="testi-author-name">Aditya Mehta</div>

<div class="testi-author-role">Head of Production · IN10 Media</div>

</div>

</div>

</div>

</div>

</section>



<!-- ═══════════════════ CONTACT ═══════════════════ -->



<section id="contact">

<div class="contact-bg"></div>

<div class="contact-center">

<div class="contact-divider-line"></div>

<div class="section-tag" style="justify-content:center;">09 — Let's Connect</div>

<h2 class="contact-title">

Ready to Build<br>Something <em>Extraordinary?</em>

</h2>

<p class="contact-sub">

Whether you're looking for a production leader to anchor your next big show, an OTT series, a feature film, or a live event — let's talk. The best productions start with the right conversation.

</p>

<div class="contact-links-row">

<a href="tel:+919930989222" class="btn-primary">

📞 +91 99309 89222

</a>

<a href="mailto:weezykhan@gmail.com" class="btn-secondary">

✉ weezykhan@gmail.com

</a>

<a href="https://www.linkedin.com/in/fowzan-khan-89903a42/" target="_blank" class="btn-secondary">

in LinkedIn

</a>

</div>

<div class="contact-info-grid">

<div class="contact-info-item">

<span class="ci-icon">📍</span>

<div class="ci-label">Location</div>

<div class="ci-value">Mumbai, Maharashtra 400053</div>

</div>

<div class="contact-info-item">

<span class="ci-icon">📧</span>

<div class="ci-label">Email</div>

<div class="ci-value"><a href="mailto:weezykhan@gmail.com">weezykhan@gmail.com</a></div>

</div>

<div class="contact-info-item">

<span class="ci-icon">🔗</span>

<div class="ci-label">LinkedIn</div>

<div class="ci-value"><a href="https://www.linkedin.com/in/fowzan-khan-89903a42/" target="_blank">fowzan-khan-89903a42</a></div>

</div>

</div>

</div>

</section>



<!-- FOOTER -->



<footer>

<div class="footer-logo">Fowzan<span>.</span></div>

<p class="footer-copy">© 2026 Fowzan Khan · All Rights Reserved · Mumbai</p>

<div class="footer-links">

<a href="#about">About</a>

<a href="#projects">Work</a>

<a href="#contact">Contact</a>

<a href="https://www.linkedin.com/in/fowzan-khan-89903a42/" target="_blank">LinkedIn</a>

</div>

</footer>



<!-- ═══════════════════════════════════════════════

JAVASCRIPT

═══════════════════════════════════════════════ -->



<script>

/* ─── CURSOR ─── */

const cursor = document.getElementById('cursor');

const ring = document.getElementById('cursor-ring');

let mx = 0, my = 0, rx = 0, ry = 0;

document.addEventListener('mousemove', e => {

mx = e.clientX; my = e.clientY;

cursor.style.left = mx + 'px';

cursor.style.top = my + 'px';

});

function animRing() {

rx += (mx - rx) * 0.12;

ry += (my - ry) * 0.12;

ring.style.left = rx + 'px';

ring.style.top = ry + 'px';

requestAnimationFrame(animRing);

}

animRing();

document.querySelectorAll('a,button,.project-card,.domain-card,.testi-card,.filter-pill,.exp-nav-item,.yt-thumb-item').forEach(el => {

el.addEventListener('mouseenter', () => {

cursor.style.width = '20px';

cursor.style.height = '20px';

ring.style.width = '60px';

ring.style.height = '60px';

ring.style.opacity = '0.6';

});

el.addEventListener('mouseleave', () => {

cursor.style.width = '10px';

cursor.style.height = '10px';

ring.style.width = '40px';

ring.style.height = '40px';

ring.style.opacity = '1';

});

});



/* ─── HERO CANVAS PARTICLES ─── */

const canvas = document.getElementById('heroCanvas');

const ctx = canvas.getContext('2d');

let particles = [];

function resizeCanvas() {

canvas.width = window.innerWidth;

canvas.height = window.innerHeight;

}

resizeCanvas();

window.addEventListener('resize', resizeCanvas);

class Particle {

constructor() { this.reset(); }

reset() {

this.x = Math.random() * canvas.width;

this.y = Math.random() * canvas.height;

this.vx = (Math.random() - 0.5) * 0.3;

this.vy = -Math.random() * 0.5 - 0.1;

this.alpha = 0;

this.maxAlpha = Math.random() * 0.4 + 0.05;

this.size = Math.random() * 1.5 + 0.3;

this.life = 0;

this.maxLife = Math.random() * 300 + 150;

this.color = Math.random() > 0.7 ? '200,151,58' : Math.random() > 0.5 ? '255,255,255' : '139,30,30';

}

update() {

this.life++;

this.x += this.vx;

this.y += this.vy;

const t = this.life / this.maxLife;

this.alpha = t < 0.2 ? (t/0.2)*this.maxAlpha : t > 0.7 ? ((1-t)/0.3)*this.maxAlpha : this.maxAlpha;

if (this.life >= this.maxLife) this.reset();

}

draw() {

ctx.beginPath();

ctx.arc(this.x, this.y, this.size, 0, Math.PI*2);

ctx.fillStyle = `rgba(${this.color},${this.alpha})`;

ctx.fill();

}

}

for (let i = 0; i < 120; i++) {

const p = new Particle();

p.life = Math.random() * p.maxLife;

particles.push(p);

}

function animCanvas() {

ctx.clearRect(0, 0, canvas.width, canvas.height);

particles.forEach(p => { p.update(); p.draw(); });

// Draw subtle connections

for (let i = 0; i < particles.length; i++) {

for (let j = i+1; j < particles.length; j++) {

const dx = particles[i].x - particles[j].x;

const dy = particles[i].y - particles[j].y;

const dist = Math.sqrt(dx*dx+dy*dy);

if (dist < 100) {

ctx.beginPath();

ctx.moveTo(particles[i].x, particles[i].y);

ctx.lineTo(particles[j].x, particles[j].y);

ctx.strokeStyle = `rgba(200,151,58,${0.04*(1-dist/100)})`;

ctx.lineWidth = 0.5;

ctx.stroke();

}

}

}

requestAnimationFrame(animCanvas);

}

animCanvas();



/* ─── NAV SCROLL ─── */

const nav = document.getElementById('mainNav');

const progress = document.getElementById('scroll-progress');

window.addEventListener('scroll', () => {

nav.classList.toggle('scrolled', window.scrollY > 60);

const pct = (window.scrollY / (document.body.scrollHeight - window.innerHeight)) * 100;

progress.style.width = pct + '%';

});



/* ─── MOBILE NAV ─── */

function openDrawer() { document.getElementById('navDrawer').classList.add('open'); }

function closeDrawer() { document.getElementById('navDrawer').classList.remove('open'); }



/* ─── INTERSECTION OBSERVER ─── */

const observer = new IntersectionObserver((entries) => {

entries.forEach(e => {

if (e.isIntersecting) {

e.target.classList.add('visible');

// Animate skill bars

if (e.target.classList.contains('skill-bar-wrap')) {

e.target.classList.add('animated');

const fill = e.target.querySelector('.skill-bar-fill');

if (fill) fill.style.width = fill.style.getPropertyValue('--w') || '80%';

}

}

});

}, { threshold: 0.12, rootMargin: '0px 0px -40px 0px' });

document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));

document.querySelectorAll('.skill-bar-wrap').forEach(el => observer.observe(el));



/* ─── COUNTER ANIMATION ─── */

function animateCount(el, target, duration = 1800) {

let start = null;

const step = (ts) => {

if (!start) start = ts;

const p = Math.min((ts-start)/duration, 1);

const ease = 1 - Math.pow(1-p, 3);

el.textContent = Math.floor(ease * target);

if (p < 1) requestAnimationFrame(step);

else el.textContent = target;

};

requestAnimationFrame(step);

}

const counterObserver = new IntersectionObserver((entries) => {

entries.forEach(e => {

if (e.isIntersecting && !e.target.dataset.animated) {

e.target.dataset.animated = '1';

const target = parseInt(e.target.dataset.count || e.target.dataset.target);

if (!isNaN(target)) animateCount(e.target, target);

}

});

}, { threshold: 0.4 });

document.querySelectorAll('[data-count],[data-target]').forEach(el => counterObserver.observe(el));



/* ─── SKILL BARS ─── */

const skillObserver = new IntersectionObserver((entries) => {

entries.forEach(e => {

if (e.isIntersecting) {

const fills = e.target.querySelectorAll('.skill-bar-fill');

fills.forEach(fill => {

setTimeout(() => { fill.style.transform = 'scaleX(1)'; }, 100);

});

skillObserver.unobserve(e.target);

}

});

}, { threshold: 0.3 });

const skillSection = document.getElementById('skills');

if (skillSection) skillObserver.observe(skillSection);



/* ─── PROJECT FILTER ─── */

document.querySelectorAll('.filter-pill').forEach(btn => {

btn.addEventListener('click', () => {

document.querySelectorAll('.filter-pill').forEach(b => b.classList.remove('active'));

btn.classList.add('active');

const filter = btn.dataset.filter;

document.querySelectorAll('#projectsBento .project-card').forEach(card => {

if (filter === 'all' || card.dataset.category === filter) {

card.style.display = '';

setTimeout(() => card.style.opacity = '1', 10);

} else {

card.style.opacity = '0';

setTimeout(() => card.style.display = 'none', 300);

}

});

});

});



/* ─── EXPERIENCE NAV ─── */

document.querySelectorAll('.exp-nav-item').forEach(item => {

item.addEventListener('click', () => {

const idx = item.dataset.idx;

document.querySelectorAll('.exp-nav-item').forEach(i => i.classList.remove('active'));

document.querySelectorAll('.exp-entry').forEach(e => e.classList.remove('active'));

item.classList.add('active');

const entry = document.getElementById('exp-' + idx);

if (entry) {

entry.classList.add('active');

entry.scrollIntoView({ behavior: 'smooth', block: 'center' });

}

});

});

// Auto-activate on scroll

const expEntries = document.querySelectorAll('.exp-entry');

const expObserver = new IntersectionObserver((entries) => {

entries.forEach(e => {

if (e.isIntersecting) {

const id = e.target.id;

const idx = id.replace('exp-','');

document.querySelectorAll('.exp-nav-item').forEach(i => i.classList.remove('active'));

document.querySelectorAll('.exp-entry').forEach(en => en.classList.remove('active'));

const navItem = document.querySelector(`.exp-nav-item[data-idx="${idx}"]`);

if (navItem) navItem.classList.add('active');

e.target.classList.add('active');

}

});

}, { threshold: 0.4 });

expEntries.forEach(e => expObserver.observe(e));



/* ─── YOUTUBE SPOTLIGHT ─── */

const videos = [

{ id: 'NcNr4-s0JZY', title: 'Ramayan — Official Promo | Sony TV', net: 'Sony Entertainment Television', grad: 'grad-ramayan' },

{ id: 'BcOh4FYfFvI', title: 'Vanshaj — Promo | Sony TV', net: 'Sony Entertainment Television', grad: 'grad-vanshaj' },

{ id: 'EvFJBzKRoY4', title: 'Shiv Shakti — Official Promo | Colors TV', net: 'Colors TV', grad: 'grad-shivshakti' },

{ id: 'PBs5m_J1gGU', title: 'Avrodh Season 2 — Trailer | SonyLIV', net: 'SonyLIV', grad: 'grad-avrodh' },

{ id: 'mzOQ2JJsTew', title: 'Taj Season 2 — Trailer | ZEE5', net: 'ZEE5', grad: 'grad-taj' },

];

const thumbList = document.getElementById('thumbList');

const mainIframe = document.getElementById('mainIframe');

const mainTitle = document.getElementById('mainTitle');

videos.forEach((v, i) => {

const item = document.createElement('div');

item.className = 'yt-thumb-item' + (i === 0 ? ' active' : '');

item.innerHTML = `

<div class="yt-thumb-img">

<div class="yt-thumb-grad ${v.grad}" style="width:100%;height:100%;"></div>

<div class="yt-play-icon">

<svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg>

</div>

</div>

<div class="yt-thumb-info">

<div class="yt-thumb-title">${v.title}</div>

<div class="yt-thumb-net">${v.net}</div>

</div>`;

item.addEventListener('click', () => {

document.querySelectorAll('.yt-thumb-item').forEach(t => t.classList.remove('active'));

item.classList.add('active');

mainIframe.src = `https://www.youtube.com/embed/${v.id}?autoplay=1&rel=0&modestbranding=1`;

mainTitle.textContent = v.title;

});

thumbList.appendChild(item);

});



/* ─── GALLERY MARQUEE ─── */

const galleryShows = [

{ label: 'Ramayan · Sony', grad: 'grad-ramayan' },

{ label: 'Shiv Shakti · Colors', grad: 'grad-shivshakti' },

{ label: 'Vanshaj · Sony', grad: 'grad-vanshaj' },

{ label: 'Laxmi Narayan · Colors', grad: 'grad-laxminarayan' },

{ label: 'Veer Hanuman · SAB', grad: 'grad-veerhanuman' },

{ label: 'State of Siege · ZEE5', grad: 'grad-stateofsiege' },

{ label: 'Taj S2 · ZEE5', grad: 'grad-taj' },

{ label: 'Avrodh S2 · SonyLIV', grad: 'grad-avrodh' },

{ label: 'Code M S2 · Hotstar', grad: 'grad-codem' },

{ label: 'Dance Deewane · Colors', grad: 'grad-dance' },

{ label: 'Filmfare Awards', grad: 'grad-filmfare' },

{ label: 'AK vs AK · Netflix', grad: 'grad-avrodh' },

];

function buildMarquee(id, items, doubled = true) {

const el = document.getElementById(id);

if (!el) return;

const all = doubled ? [...items, ...items] : items;

all.forEach(show => {

const div = document.createElement('div');

div.className = 'gallery-item';

div.innerHTML = `

<div class="gallery-item-inner ${show.grad}" style="width:100%;height:100%;display:flex;align-items:center;justify-content:center;position:relative;">

<span style="font-family:'Playfair Display',serif;font-size:3.5rem;font-weight:900;color:rgba(255,255,255,0.05);">${show.label.charAt(0)}</span>

<div style="position:absolute;inset:0;background:linear-gradient(180deg,transparent 30%,rgba(5,5,5,0.7) 100%);"></div>

</div>

<div class="gallery-item-label">${show.label}</div>`;

el.appendChild(div);

});

}

buildMarquee('marquee1', galleryShows);

buildMarquee('marquee2', [...galleryShows].reverse());



/* ─── DOWNLOAD RESUME ─── */

function downloadResume() {

alert('Resume download — Please add your resume PDF file and update this function to point to it.\n\nExample: window.open("Fowzan_Khan_Resume_2026.pdf")');

}



/* ─── PARALLAX ─── */

window.addEventListener('scroll', () => {

const scrollY = window.scrollY;

const bgTexts = document.querySelectorAll('.about-bg-text, .exp-bg-text');

bgTexts.forEach(el => {

el.style.transform = `translateY(calc(-50% + ${scrollY * 0.04}px))`;

});

});



/* ─── ACTIVE NAV ON SCROLL ─── */

const sections = document.querySelectorAll('section[id]');

const navLinks = document.querySelectorAll('.nav-links a');

window.addEventListener('scroll', () => {

let current = '';

sections.forEach(sec => {

if (window.scrollY >= sec.offsetTop - 200) current = sec.id;

});

navLinks.forEach(a => {

a.style.color = a.getAttribute('href') === '#' + current ? 'var(--gold)' : '';

});

});

</script>



</body>

</html>
