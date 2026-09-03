<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Last Thread</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@500;600;700;800&family=Nunito+Sans:wght@400;600;700;800;900&display=swap" rel="stylesheet">
<style>
  :root{
    --cream:#FBF2E2;
    --cream-deep:#F3E6C9;
    --card:#FFFCF4;
    --moss:#8CA37E;
    --moss-deep:#4F6B47;
    --indigo:#5C6DA0;
    --indigo-deep:#37416A;
    --madder:#D5806E;
    --madder-deep:#AD5240;
    --turmeric:#E8B155;
    --turmeric-deep:#C9902F;
    --ink:#2E2818;
    --ink-soft:#6B6151;
    --radius:24px;
    --radius-lg:36px;
    --shadow:0 14px 34px rgba(90,65,25,0.12);
    --shadow-sm:0 6px 16px rgba(90,65,25,0.09);
  }
  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    margin:0; background:var(--cream); color:var(--ink);
    font-family:'Nunito Sans',sans-serif; line-height:1.65; overflow-x:hidden;
  }
  h1,h2,h3,h4{font-family:'Baloo 2',sans-serif; font-weight:700; color:var(--indigo-deep); margin:0;}
  p{margin:0 0 14px;}
  a{color:var(--madder-deep);}
  .wrap{max-width:1100px; margin:0 auto; padding:0 28px; position:relative;}
  section{padding:110px 0; position:relative; overflow:hidden;}
  img,svg{max-width:100%; display:block;}

  /* decorative blobs */
  .blob{position:absolute; border-radius:50%; filter:blur(2px); z-index:0; opacity:0.5;}

  /* stitched divider */
  .stitch-divider{width:100%; height:34px; display:block; margin:0 auto;}

  /* NAV */
  nav{position:sticky; top:0; z-index:50; background:rgba(251,242,226,0.88); backdrop-filter:blur(10px); border-bottom:1px solid rgba(55,65,106,0.08);}
  nav .navwrap{max-width:1100px; margin:0 auto; padding:16px 28px; display:flex; align-items:center; justify-content:space-between;}
  .brand{display:flex; align-items:center; gap:9px; text-decoration:none; font-family:'Baloo 2',sans-serif; font-weight:700; font-size:20px; color:var(--indigo-deep);}
  .brand svg{width:30px; height:30px;}
  .navlinks{display:flex; align-items:center; gap:5px; background:var(--card); padding:6px; border-radius:999px; box-shadow:var(--shadow-sm);}
  .navlinks a{text-decoration:none; color:var(--ink-soft); font-size:14px; font-weight:800; padding:10px 17px; border-radius:999px; transition:.15s;}
  .navlinks a:hover{background:var(--cream-deep); color:var(--ink);}
  .navlinks a.cta{background:var(--moss-deep); color:#fff;}
  .navlinks a.cta:hover{background:var(--moss); color:#fff;}
  @media(max-width:760px){.navlinks span{display:none;}}

  /* BUTTONS */
  .btn{display:inline-flex; align-items:center; gap:8px; font-weight:800; font-size:15px; text-decoration:none; padding:15px 28px; border-radius:999px; box-shadow:var(--shadow-sm); transition:transform .15s ease, box-shadow .15s;}
  .btn:hover{transform:translateY(-3px); box-shadow:var(--shadow);}
  .btn-primary{background:var(--madder-deep); color:#fff;}
  .btn-ghost{background:var(--card); color:var(--indigo-deep); border:2px solid rgba(55,65,106,0.15);}

  /* HERO */
  .hero{padding:76px 0 20px; text-align:center;}
  .badge-pill{display:inline-flex; align-items:center; gap:8px; background:var(--card); box-shadow:var(--shadow-sm); padding:10px 20px; border-radius:999px; font-size:13.5px; font-weight:800; color:var(--moss-deep); margin-bottom:28px;}
  .hero h1{font-size:clamp(48px,8.5vw,92px); line-height:1.0; margin:0 0 22px;}
  .hero h1 .accent{color:var(--madder-deep);}
  .hero .lede{font-size:19.5px; max-width:600px; margin:0 auto 36px; color:var(--ink-soft); font-weight:600;}
  .hero-actions{display:flex; gap:14px; justify-content:center; flex-wrap:wrap; margin-bottom:20px;}
  .hero-stage{position:relative; max-width:680px; margin:50px auto 10px;}
  .credit{font-size:13px; color:var(--ink-soft); margin-top:40px; font-weight:700;}

  /* mascot floaty bits */
  .float-leaf{position:absolute; animation:bob 5s ease-in-out infinite;}
  @keyframes bob{0%,100%{transform:translateY(0) rotate(0deg);}50%{transform:translateY(-14px) rotate(6deg);}}

  /* SECTION LABELS */
  .section-head{text-align:center; max-width:680px; margin:0 auto 54px; position:relative; z-index:1;}
  .kicker{display:inline-flex; align-items:center; gap:6px; background:var(--card); color:var(--madder-deep); font-weight:900; font-size:12.5px; letter-spacing:0.3px; padding:8px 18px; border-radius:999px; box-shadow:var(--shadow-sm); margin-bottom:18px;}
  h2.title{font-size:clamp(32px,4.4vw,48px); margin:0 0 16px;}
  .lead-center{font-size:17.5px; color:var(--ink-soft); max-width:580px; margin:0 auto; font-weight:600;}

  /* STATS */
  .stat-row{display:flex; gap:24px; flex-wrap:wrap; justify-content:center; position:relative; z-index:1;}
  .stat-card{background:var(--card); border-radius:var(--radius); box-shadow:var(--shadow); padding:32px 28px; width:255px; text-align:left; border-bottom:5px solid var(--accent,var(--madder));}
  .stat-card .num{font-family:'Baloo 2',sans-serif; font-size:44px; color:var(--accent,var(--madder-deep)); font-weight:800; line-height:1;}
  .stat-card .label{font-size:14px; color:var(--ink-soft); margin-top:12px; font-weight:700;}

  /* ORIGIN / FIG numbered cards */
  .num-grid{display:grid; grid-template-columns:1fr 1fr; gap:28px; margin-top:14px; position:relative; z-index:1;}
  .num-card{background:var(--card); border-radius:var(--radius-lg); box-shadow:var(--shadow); padding:40px 36px; position:relative;}
  .num-badge{width:44px; height:44px; border-radius:50%; background:var(--moss); color:#fff; font-family:'Baloo 2',sans-serif; font-weight:700; display:flex; align-items:center; justify-content:center; margin-bottom:20px; font-size:19px; box-shadow:var(--shadow-sm);}
  .num-card h3{font-size:22px; margin:0 0 12px;}
  .num-card p{font-size:15.5px; color:var(--ink-soft); margin:0; font-weight:600;}
  @media(max-width:760px){.num-grid{grid-template-columns:1fr;}}

  /* FIELDWORK */
  .species-chip-row{display:flex; flex-wrap:wrap; gap:10px; justify-content:center; margin:30px 0 50px; position:relative; z-index:1;}
  .species-chip{background:var(--card); border-radius:999px; padding:9px 18px; font-size:13.5px; font-weight:800; color:var(--indigo-deep); box-shadow:var(--shadow-sm); display:flex; align-items:center; gap:6px;}
  .cozy-grid{display:grid; grid-template-columns:1fr 1fr; gap:24px; position:relative; z-index:1;}
  .cozy-card{background:var(--card); border-radius:var(--radius); box-shadow:var(--shadow); padding:32px 30px; text-align:left;}
  .icon-circle{width:54px; height:54px; border-radius:50%; display:flex; align-items:center; justify-content:center; margin-bottom:18px; font-size:24px; box-shadow:var(--shadow-sm);}
  .cozy-card h3{font-size:20px; margin:0 0 10px;}
  .cozy-card p{font-size:15px; color:var(--ink-soft); margin:0; font-weight:600;}
  @media(max-width:760px){.cozy-grid{grid-template-columns:1fr;}}

  /* CASE STUDY location cards + tabs */
  .location-cards{display:grid; grid-template-columns:1fr 1fr; gap:16px; margin-bottom:36px; position:relative; z-index:1;}
  .location-card{
    background:var(--card); border-radius:var(--radius); box-shadow:var(--shadow-sm); padding:22px 24px; cursor:pointer;
    border:3px solid transparent; transition:.18s; text-align:left; display:flex; gap:16px; align-items:center;
  }
  .location-card.active{border-color:var(--indigo-deep); box-shadow:var(--shadow);}
  .location-card .thumb{width:56px; height:56px; border-radius:16px; flex-shrink:0; display:flex; align-items:center; justify-content:center; font-size:26px;}
  .location-card h4{font-size:16.5px; margin:0 0 4px; color:var(--indigo-deep);}
  .location-card p{font-size:13px; color:var(--ink-soft); margin:0; font-weight:700;}
  @media(max-width:700px){.location-cards{grid-template-columns:1fr;}}

  .tab-panel{display:none; background:var(--card); border-radius:var(--radius-lg); box-shadow:var(--shadow); padding:48px; position:relative; z-index:1;}
  .tab-panel.active{display:block;}
  .tab-panel h3{font-size:28px; margin:0 0 18px;}
  .tab-panel p{font-size:16px; color:var(--ink-soft); max-width:660px; font-weight:600;}
  .fact-chip{display:inline-block; background:rgba(213,128,110,0.16); color:var(--madder-deep); font-weight:900; font-size:13px; padding:9px 18px; border-radius:999px; margin:18px 0;}

  .mini-timeline{margin:26px 0;}
  .mini-timeline .tl-row{display:flex; gap:18px; padding:14px 0; border-bottom:2px dashed rgba(55,65,106,0.15);}
  .mini-timeline .tl-row:last-child{border-bottom:none;}
  .tl-dot{width:10px; height:10px; border-radius:50%; background:var(--turmeric); margin-top:6px; flex-shrink:0;}
  .tl-date{font-family:'Baloo 2',sans-serif; font-size:14px; color:var(--madder-deep); min-width:120px; font-weight:700;}
  .tl-text{font-size:14.5px; color:var(--ink-soft); font-weight:600;}

  .compare-grid{display:grid; grid-template-columns:1fr 1fr; gap:18px; margin:24px 0;}
  .compare-card{border-radius:20px; padding:22px 24px;}
  .compare-card.a{background:rgba(213,128,110,0.12);}
  .compare-card.b{background:rgba(140,163,126,0.16);}
  .compare-card h5{font-family:'Baloo 2',sans-serif; font-size:16px; margin:0 0 4px; color:var(--indigo-deep);}
  .compare-card .sub{font-size:12px; color:var(--ink-soft); font-weight:800; margin-bottom:10px;}
  .compare-card p{font-size:13.5px; margin:0; color:var(--ink-soft); font-weight:600;}
  @media(max-width:700px){.compare-grid{grid-template-columns:1fr;} .tab-panel{padding:32px 26px;}}

  /* ACTION CARDS */
  .action-grid{display:grid; grid-template-columns:repeat(2,1fr); gap:24px; margin-top:48px; position:relative; z-index:1;}
  .action-card{background:var(--card); border-radius:var(--radius); box-shadow:var(--shadow); padding:30px 28px;}
  .action-num{font-family:'Baloo 2',sans-serif; font-size:15px; color:var(--turmeric-deep); font-weight:700; margin-bottom:12px;}
  .action-card h4{font-size:18px; margin:0 0 10px;}
  .action-card p{font-size:14.5px; color:var(--ink-soft); margin:0; font-weight:600;}
  @media(max-width:760px){.action-grid{grid-template-columns:1fr;}}

  /* QUOTES */
  .quote-grid{display:grid; grid-template-columns:repeat(3,1fr); gap:20px; position:relative; z-index:1;}
  .quote-card{background:var(--card); border-radius:var(--radius); box-shadow:var(--shadow); padding:30px 26px;}
  .quote-card .mark{font-family:'Baloo 2',sans-serif; font-size:38px; color:var(--turmeric); line-height:0.4; display:block; margin-bottom:12px;}
  .quote-card p{font-size:15px; color:var(--ink); font-style:italic; margin:0 0 12px; font-weight:600;}
  .quote-card .attr{font-size:12.5px; color:var(--ink-soft); font-weight:800;}
  @media(max-width:820px){.quote-grid{grid-template-columns:1fr;}}

  /* FOOTER BANNER */
  .footer-banner{background:var(--indigo-deep); border-radius:var(--radius-lg); margin:0 28px; padding:70px 40px; text-align:center; color:#fff; position:relative; overflow:hidden;}
  .footer-banner h2{color:#fff; font-size:clamp(30px,4.4vw,42px); margin:0 0 22px;}
  .btn-primary.on-dark{background:var(--turmeric); color:var(--indigo-deep);}
  .btn-ghost.on-dark{background:transparent; border:2px solid rgba(255,255,255,0.4); color:#fff;}

  footer.site-footer{padding:64px 28px 44px; text-align:center;}
  .team-list{display:flex; flex-wrap:wrap; gap:8px 18px; justify-content:center; margin:24px 0; font-size:14px; color:var(--ink-soft); font-weight:800;}
  .footer-meta{font-size:12.5px; color:var(--ink-soft); margin-top:10px; font-weight:700;}

  @media(max-width:640px){
    section{padding:76px 0;}
    .footer-banner{margin:0 16px; padding:50px 24px;}
  }
</style>
</head>
<body>

<nav>
  <div class="navwrap">
    <a class="brand" href="#top">
      <svg viewBox="0 0 40 40"><circle cx="20" cy="20" r="20" fill="#D5806E"/><path d="M10,20 C14,14 18,26 22,20 C26,14 30,26 32,20" stroke="#FFFCF4" stroke-width="3" fill="none" stroke-linecap="round"/></svg>
      The Last Thread
    </a>
    <div class="navlinks">
      <a href="#stakes"><span>Why It Matters</span></a>
      <a href="#fieldwork"><span>Fieldwork</span></a>
      <a href="#threats"><span>The Threads</span></a>
      <a href="#action"><span>Take Action</span></a>
      <a href="#stories"><span>Share a Story</span></a>
      <a href="#join" class="cta">Join Us</a>
    </div>
  </div>
</nav>

<div class="hero wrap" id="top">
  <div class="blob" style="width:340px;height:340px;background:radial-gradient(circle,#E8B155 0%,transparent 70%);top:-80px;left:-140px;"></div>
  <div class="blob" style="width:300px;height:300px;background:radial-gradient(circle,#8CA37E 0%,transparent 70%);top:60px;right:-120px;"></div>

  <div class="badge-pill">🧵 A Wipro Earthian project &middot; Modern High School International</div>
  <h1>Every species is a<br><span class="accent">thread</span> we weave.</h1>
  <p class="lede">Pull one thread from a fabric and it barely notices. Pull enough, and it comes apart. This is where some of those threads are already fraying, close to home and far away, and what it takes to stop the unraveling.</p>
  <div class="hero-actions">
    <a class="btn btn-primary" href="#threats">See what's unraveling</a>
    <a class="btn btn-ghost" href="#action">What you can do</a>
  </div>

  <div class="hero-stage">
    <svg class="float-leaf" style="width:44px; top:10px; left:0;" viewBox="0 0 40 40"><path d="M20,4 C30,10 32,26 20,36 C8,26 10,10 20,4 Z" fill="#8CA37E"/><path d="M20,6 L20,34" stroke="#4F6B47" stroke-width="1.5"/></svg>
    <svg class="float-leaf" style="width:34px; top:40px; right:10px; animation-delay:1.2s;" viewBox="0 0 40 40"><circle cx="20" cy="20" r="16" fill="#E8B155"/></svg>
    <svg class="float-leaf" style="width:30px; bottom:20px; left:30px; animation-delay:2s;" viewBox="0 0 40 40"><path d="M20,4 C30,10 32,26 20,36 C8,26 10,10 20,4 Z" fill="#D5806E"/></svg>

    <svg viewBox="0 0 640 380" xmlns="http://www.w3.org/2000/svg">
      <ellipse cx="320" cy="330" rx="240" ry="26" fill="#EFDFB8"/>
      <circle cx="320" cy="190" r="150" fill="#FFFCF4" stroke="#E8B155" stroke-width="7" stroke-dasharray="2 15" stroke-linecap="round"/>
      <path d="M180,190 C230,120 280,240 320,190 C360,140 410,240 460,190" fill="none" stroke="#5C6DA0" stroke-width="11" stroke-linecap="round"/>
      <path d="M180,230 C230,270 280,160 320,230 C360,280 410,160 460,230" fill="none" stroke="#D5806E" stroke-width="11" stroke-linecap="round"/>
      <path d="M205,270 C250,245 280,290 320,270 C350,255 375,285 400,270" fill="none" stroke="#8CA37E" stroke-width="10" stroke-linecap="round"/>
      <path d="M400,270 C420,264 435,272 445,280" fill="none" stroke="#8CA37E" stroke-width="10" stroke-linecap="round" stroke-dasharray="2 11"/>
      <!-- needle -->
      <line x1="320" y1="40" x2="320" y2="150" stroke="#AD5240" stroke-width="4" stroke-linecap="round"/>
      <ellipse cx="320" cy="35" rx="7" ry="14" fill="none" stroke="#AD5240" stroke-width="4"/>
      <!-- mascot bird perched on the hoop -->
      <g transform="translate(455,120)">
        <ellipse cx="0" cy="10" rx="26" ry="20" fill="#D5806E"/>
        <circle cx="20" cy="-6" r="14" fill="#D5806E"/>
        <path d="M32,-8 L44,-4 L32,0 Z" fill="#E8B155"/>
        <circle cx="24" cy="-9" r="2.4" fill="#2E2818"/>
        <path d="M-6,26 C-10,34 -2,36 2,30" stroke="#AD5240" stroke-width="3" fill="none" stroke-linecap="round"/>
        <path d="M6,28 C4,36 12,36 14,30" stroke="#AD5240" stroke-width="3" fill="none" stroke-linecap="round"/>
        <path d="M-20,6 C-28,10 -26,20 -14,18" fill="#C46A57"/>
      </g>
    </svg>
  </div>
  <p class="credit">Sharyn Singh &middot; Ava I. Agarwal &middot; Ushoshi Chandra &middot; Anwoy Chatterjee &middot; Anika Jhunjhunwala</p>
</div>

<svg class="stitch-divider" viewBox="0 0 1100 34" preserveAspectRatio="none"><path d="M0,17 Q27,2 55,17 T110,17 T165,17 T220,17 T275,17 T330,17 T385,17 T440,17 T495,17 T550,17 T605,17 T660,17 T715,17 T770,17 T825,17 T880,17 T935,17 T990,17 T1045,17 T1100,17" fill="none" stroke="#D5806E" stroke-width="2.5" stroke-dasharray="1 9" stroke-linecap="round" opacity="0.6"/></svg>

<section id="stakes">
  <div class="blob" style="width:380px;height:380px;background:radial-gradient(circle,#5C6DA0 0%,transparent 70%);bottom:-160px;left:-160px;"></div>
  <div class="wrap">
    <div class="section-head">
      <span class="kicker">🌍 why this isn't someone else's problem</span>
      <h2 class="title">Biodiversity loss doesn't announce itself.</h2>
      <p class="lead-center">It just goes quiet. A pollinator visits a little less. A pond stops holding water through the dry season. By the time it's obvious, the thread is already gone.</p>
    </div>
    <div class="stat-row">
      <div class="stat-card" style="--accent:#AD5240;">
        <div class="num">~73%</div>
        <div class="label">average decline in monitored wildlife populations worldwide since 1970. WWF Living Planet Report, 2024.</div>
      </div>
      <div class="stat-card" style="--accent:#4F6B47;">
        <div class="num">~8%</div>
        <div class="label">of all recorded species on Earth live in India, on just 2.4% of its land.</div>
      </div>
      <div class="stat-card" style="--accent:#C9902F;">
        <div class="num">4</div>
        <div class="label">global biodiversity hotspots run through India, including our own coastline and wetlands.</div>
      </div>
    </div>
  </div>
</section>

<section>
  <div class="wrap">
    <div class="section-head">
      <span class="kicker">🧵 how we got here</span>
      <h2 class="title">A thread, and a fig.</h2>
      <p class="lead-center">The story behind our name, and the small fruit that ended up meaning a lot more than we expected.</p>
    </div>
    <div class="num-grid">
      <div class="num-card">
        <div class="num-badge">1</div>
        <h3>Threads in a fabric</h3>
        <p>Species aren't separate. Plants, animals, fungi, insects and people weave one shared fabric. Losing one changes the pattern quietly, and losing enough pulls the whole thing apart. It was never about saving one species alone. It's about keeping the fabric intact.</p>
      </div>
      <div class="num-card">
        <div class="num-badge">2</div>
        <h3>Why a fig</h3>
        <p>A hopscotch game at our own exhibition traced the tangled bond between a fig tree, the birds that depend on it, and the seeds it spreads. It reminded us of Sylvia Plath's fig tree in The Bell Jar: a tree full of possible futures, all lost to hesitation. That's the risk we care about most, waiting too long to choose.</p>
      </div>
    </div>
  </div>
</section>

<svg class="stitch-divider" viewBox="0 0 1100 34" preserveAspectRatio="none"><path d="M0,17 Q27,32 55,17 T110,17 T165,17 T220,17 T275,17 T330,17 T385,17 T440,17 T495,17 T550,17 T605,17 T660,17 T715,17 T770,17 T825,17 T880,17 T935,17 T990,17 T1045,17 T1100,17" fill="none" stroke="#8CA37E" stroke-width="2.5" stroke-dasharray="1 9" stroke-linecap="round" opacity="0.6"/></svg>

<section id="fieldwork">
  <div class="blob" style="width:320px;height:320px;background:radial-gradient(circle,#E8B155 0%,transparent 70%);top:-100px;right:-140px;"></div>
  <div class="wrap">
    <div class="section-head">
      <span class="kicker">🔍 close to home</span>
      <h2 class="title">Even our own school field is a habitat.</h2>
      <p class="lead-center">Before we studied a wetland or an island, we studied a patch of our own campus, and found nearly three dozen species we'd walked past without noticing.</p>
    </div>

    <div class="species-chip-row">
      <span class="species-chip">🌱 21 plant species</span>
      <span class="species-chip">🐛 12 animal species</span>
      <span class="species-chip">🍄 2 fungi species</span>
      <span class="species-chip">🐿️ squirrels foraging near trunks</span>
      <span class="species-chip">🐝 honeybees on flowering shrubs</span>
      <span class="species-chip">🦋 purple sunbird flitting branches</span>
    </div>

    <div class="cozy-grid">
      <div class="cozy-card">
        <div class="icon-circle" style="background:#DDEAD3;">🌿</div>
        <h3>What thrives</h3>
        <p>The busiest corner of our school wasn't a flowerbed. It was the shaded walking path, where shrubs, ferns and old trees gave insects and birds enough cover and food to actually settle in.</p>
      </div>
      <div class="cozy-card">
        <div class="icon-circle" style="background:#F1DCC6;">🧱</div>
        <h3>What doesn't</h3>
        <p>The bare concrete stretches nearby held nothing living at all. No soil to root in, no shade, nowhere small to hide. Habitat isn't a given. It has to be left room to exist.</p>
      </div>
    </div>
  </div>
</section>

<svg class="stitch-divider" viewBox="0 0 1100 34" preserveAspectRatio="none"><path d="M0,17 Q27,2 55,17 T110,17 T165,17 T220,17 T275,17 T330,17 T385,17 T440,17 T495,17 T550,17 T605,17 T660,17 T715,17 T770,17 T825,17 T880,17 T935,17 T990,17 T1045,17 T1100,17" fill="none" stroke="#E8B155" stroke-width="2.5" stroke-dasharray="1 9" stroke-linecap="round" opacity="0.6"/></svg>

<section id="threats">
  <div class="blob" style="width:360px;height:360px;background:radial-gradient(circle,#D5806E 0%,transparent 70%);bottom:-140px;right:-140px;"></div>
  <div class="wrap">
    <div class="section-head">
      <span class="kicker">🧨 two threads, pulled hard</span>
      <h2 class="title">What it looks like when a thread breaks.</h2>
      <p class="lead-center">One place on the far edge of the country, one in our own city's backyard. Different scale, same pattern.</p>
    </div>

    <div class="location-cards">
      <div class="location-card active" data-tab="nicobar">
        <div class="thumb" style="background:#DCE4F2;">🐢</div>
        <div><h4>Great Nicobar Island</h4><p>Galathea Bay &amp; the leatherback turtles</p></div>
      </div>
      <div class="location-card" data-tab="kolkata">
        <div class="thumb" style="background:#DDEAD3;">💧</div>
        <div><h4>South of Kolkata</h4><p>Rajpur, Sonarpur &amp; the wetlands</p></div>
      </div>
    </div>

    <div class="tab-panel active" id="nicobar">
      <div class="fact-chip" style="margin-top:0;">🐢 Ramsar wetland &middot; leatherback nesting site</div>
      <h3>A nesting beach traded for a shipping route.</h3>
      <p>Galathea Bay was a protected sanctuary for giant leatherback turtles until 2021, when it lost that status to clear the way for a new deep-water port. The bay sits close to one of the busiest shipping corridors on Earth, which is exactly why it became valuable to everyone except the turtles, the Nicobar megapode, and the Shompen and Nicobarese communities who've lived alongside them for generations.</p>
      <div class="mini-timeline">
        <div class="tl-row"><div class="tl-dot"></div><div class="tl-date">Jan 2021</div><div class="tl-text">The National Board for Wildlife approves lifting the sanctuary's protection.</div></div>
        <div class="tl-row"><div class="tl-dot"></div><div class="tl-date">May 2021</div><div class="tl-text">The port and township project is formally proposed.</div></div>
        <div class="tl-row"><div class="tl-dot"></div><div class="tl-date">Oct 2022</div><div class="tl-text">Forest and environmental clearances are granted.</div></div>
        <div class="tl-row"><div class="tl-dot"></div><div class="tl-date">Since then</div><div class="tl-text">Scientists and conservation groups keep pushing back, while construction moves ahead.</div></div>
      </div>
      <p>The lesson that stuck with us: undoing legal protection for a habitat takes an administrative signature. Undoing the damage after takes decades, if it's even possible.</p>
    </div>

    <div class="tab-panel" id="kolkata">
      <div class="fact-chip" style="margin-top:0;">💧 12,500 hectares &middot; 1,287 documented species</div>
      <h3>A wetland disappearing one housing block at a time.</h3>
      <p>The land just south of the East Kolkata Wetlands used to work the same way the protected wetlands still do: ponds and paddies that cooled the area and soaked up monsoon rain. Three decades of unplanned growth turned most of it into concrete. One local study linked the lost greenery and water bodies to a local temperature rise of nearly 7°C.</p>
      <p>Inside the wetlands themselves, we compared two ponds a few kilometres apart:</p>
      <div class="compare-grid">
        <div class="compare-card a">
          <h5>Near the tanneries</h5>
          <div class="sub">Bantala leather cluster</div>
          <p>Heavy-metal traces in the water. Only pollution-tolerant fish and plants survive here. Farmers nearby told us their crops fail when this water reaches their fields.</p>
        </div>
        <div class="compare-card b">
          <h5>Downstream, protected</h5>
          <div class="sub">Nalban &amp; Captain Bheri</div>
          <p>Clean enough to seed fish hatcheries. One of the region's richest bird populations, with native lotus and reeds still growing freely.</p>
        </div>
      </div>
      <p>The difference isn't inevitable. It's just proximity to unchecked runoff.</p>
    </div>
  </div>
</section>

<svg class="stitch-divider" viewBox="0 0 1100 34" preserveAspectRatio="none"><path d="M0,17 Q27,32 55,17 T110,17 T165,17 T220,17 T275,17 T330,17 T385,17 T440,17 T495,17 T550,17 T605,17 T660,17 T715,17 T770,17 T825,17 T880,17 T935,17 T990,17 T1045,17 T1100,17" fill="none" stroke="#5C6DA0" stroke-width="2.5" stroke-dasharray="1 9" stroke-linecap="round" opacity="0.6"/></svg>

<section id="action">
  <div class="blob" style="width:340px;height:340px;background:radial-gradient(circle,#8CA37E 0%,transparent 70%);top:-100px;left:-140px;"></div>
  <div class="wrap">
    <div class="section-head">
      <span class="kicker">🙌 this part is for you</span>
      <h2 class="title">You don't have to be a scientist to hold a thread in place.</h2>
      <p class="lead-center">None of this gets fixed by one report or one exhibition. It gets fixed by enough people deciding not to look away.</p>
    </div>
    <div class="action-grid">
      <div class="action-card">
        <div class="action-num">01</div>
        <h4>Look at your own patch of ground</h4>
        <p>You don't need a wetland. A balcony, a school field, or a nearby park likely holds more species than you'd guess. Notice what's there before it isn't.</p>
      </div>
      <div class="action-card">
        <div class="action-num">02</div>
        <h4>Follow where things come from</h4>
        <p>Leather, seafood and produce all carry an environmental cost upstream. Asking where something was made or grown is a small habit with real weight.</p>
      </div>
      <div class="action-card">
        <div class="action-num">03</div>
        <h4>Back the people already fighting for this</h4>
        <p>Wetland and coastal conservation groups, Indigenous rights organisations and local environmental petitions all need public pressure to outlast administrative decisions.</p>
      </div>
      <div class="action-card">
        <div class="action-num">04</div>
        <h4>Talk about it, out loud</h4>
        <p>Most biodiversity loss stays invisible simply because no one's discussing it. Share what you learn here with one person who hasn't thought about it yet.</p>
      </div>
    </div>
  </div>
</section>

<section>
  <div class="wrap">
    <div class="section-head">
      <span class="kicker">💭 what stayed with us</span>
      <h2 class="title">Small moments, from the field.</h2>
    </div>
    <div class="quote-grid">
      <div class="quote-card">
        <span class="mark">"</span>
        <p>A garden lizard, resting so still on the wall that I almost walked right past it.</p>
        <div class="attr">On our campus biodiversity walk</div>
      </div>
      <div class="quote-card">
        <span class="mark">"</span>
        <p>We could just keep digging and planting for hours. Watching dragonfly nymphs show up in a pond we built ourselves was the best part.</p>
        <div class="attr">On building our miniature pond ecosystem</div>
      </div>
      <div class="quote-card">
        <span class="mark">"</span>
        <p>Water like that reaches the fields, and the crop just doesn't survive it.</p>
        <div class="attr">A farmer, near the East Kolkata Wetlands</div>
      </div>
    </div>
  </div>
</section>

<svg class="stitch-divider" viewBox="0 0 1100 34" preserveAspectRatio="none"><path d="M0,17 Q27,2 55,17 T110,17 T165,17 T220,17 T275,17 T330,17 T385,17 T440,17 T495,17 T550,17 T605,17 T660,17 T715,17 T770,17 T825,17 T880,17 T935,17 T990,17 T1045,17 T1100,17" fill="none" stroke="#8CA37E" stroke-width="2.5" stroke-dasharray="1 9" stroke-linecap="round" opacity="0.6"/></svg>

<section id="stories">
  <div class="blob" style="width:320px;height:320px;background:radial-gradient(circle,#D5806E 0%,transparent 70%);top:-100px;right:-140px;"></div>
  <div class="wrap">
    <div class="section-head">
      <span class="kicker">🧵 add your own thread</span>
      <h2 class="title">Seen a species worth noticing? Tell us about it.</h2>
      <p class="lead-center">A backyard bird, a pond that dried up, a tree that finally flowered again. Send us your story or a photo and we'll feature the ones that fit right here on the site, alongside our own.</p>
    </div>

    <div class="cozy-grid">
      <div class="cozy-card" style="text-align:center;">
        <div class="icon-circle" style="background:#F1DCC6; margin:0 auto 18px;">📸</div>
        <h3>Share it on Instagram</h3>
        <p>DM us your story or tag us in a post. We read every one, and the best get reposted and added to the site.</p>
        <a class="btn btn-ghost" style="margin-top:18px;" href="https://www.instagram.com/_the.last.thread_?igsi=MWJzZzBhMHY4OTlhdQ==" target="_blank" rel="noopener">@thelastthread on Instagram</a>
      </div>
      <div class="cozy-card" style="text-align:center;">
        <div class="icon-circle" style="background:#DCE4F2; margin:0 auto 18px;">✉️</div>
        <h3>Email us your story</h3>
        <p>Prefer writing it out properly, or sending more than one photo? Email works just as well.</p>
        <a class="btn btn-ghost" style="margin-top:18px;" href="mailto:sharynsingh1@gmail.com?subject=My%20Thread%20Story">Send a story</a>
      </div>
    </div>
  </div>
</section>

<section id="join" style="padding-top:0;">
  <div class="footer-banner">
    <div class="blob" style="width:260px;height:260px;background:radial-gradient(circle,#E8B155 0%,transparent 70%);top:-90px;left:-90px;opacity:0.35;"></div>
    <div class="blob" style="width:240px;height:240px;background:radial-gradient(circle,#D5806E 0%,transparent 70%);bottom:-90px;right:-70px;opacity:0.35;"></div>
    <h2>Every thread counts.</h2>
    <p style="color:#DCE1F0; max-width:480px; margin:0 auto 30px; font-weight:600;">Reach out if you want to help us hold onto a few more.</p>
    <div class="hero-actions">
      <a class="btn btn-primary on-dark" href="mailto:sharynsingh1@gmail.com">hello@thelastthread.org</a>
      <a class="btn btn-ghost on-dark" href="https://www.instagram.com/_the.last.thread_?igsi=MWJzZzBhMHY4OTlhdQ==" target="_blank" rel="noopener">@thelastthread on Instagram</a>
    </div>
  </div>
</section>

<footer class="site-footer">
  <div class="team-list">
    <span>Sharyn Singh</span><span>&middot;</span><span>Ava I. Agarwal</span><span>&middot;</span><span>Ushoshi Chandra</span><span>&middot;</span><span>Anwoy Chatterjee</span><span>&middot;</span><span>Anika Jhunjhunwala</span>
  </div>
  <div class="footer-meta">Modern High School International, Wipro Earthian Programme, Biodiversity &amp; Sustainability</div>
</footer>

<script>
  document.querySelectorAll('.location-card').forEach(card => {
    card.addEventListener('click', () => {
      document.querySelectorAll('.location-card').forEach(c => c.classList.remove('active'));
      document.querySelectorAll('.tab-panel').forEach(p => p.classList.remove('active'));
      card.classList.add('active');
      document.getElementById(card.dataset.tab).classList.add('active');
    });
  });
</script>

</body>
</html>
