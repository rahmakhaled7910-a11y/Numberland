<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Numberland — Let's Count!</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@500;600;700;800&family=Quicksand:wght@500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --cream:#FFFBF2;
    --cream-2:#FFF3DD;
    --plum:#2E2140;
    --plum-soft:#5A4B6E;
    --sun:#FFC93C;
    --sky:#4EC5F1;
    --grass:#6FCF97;
    --coral:#FF6F59;
    --lavender:#B18CFF;
    --white:#FFFFFF;
    --radius-lg:28px;
    --radius-md:18px;
    --shadow-soft:0 10px 24px rgba(46,33,64,0.12);
    --shadow-pop:0 14px 0 rgba(46,33,64,0.14);
  }
  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{margin:0;background:var(--cream);color:var(--plum);font-family:'Quicksand', sans-serif;font-weight:600;overflow-x:hidden;}
  h1,h2,h3,.display{font-family:'Baloo 2', cursive;font-weight:700;margin:0;color:var(--plum);}
  a{color:inherit;} button{font-family:inherit;} img,svg{display:block;}
  @media (prefers-reduced-motion: reduce){*{animation-duration:0.001ms !important; animation-iteration-count:1 !important; transition-duration:0.001ms !important; scroll-behavior:auto !important;}}
  :focus-visible{outline:4px solid var(--sky);outline-offset:3px;border-radius:8px;}
  .wrap{max-width:1120px;margin:0 auto;padding:0 28px;}

  header{position:sticky;top:0;z-index:50;background:rgba(255,251,242,0.9);backdrop-filter:blur(6px);border-bottom:3px solid var(--plum);}
  .nav{display:flex;align-items:center;justify-content:space-between;padding:16px 28px;max-width:1120px;margin:0 auto;}
  .logo{display:flex;align-items:center;gap:10px;font-size:1.4rem;font-family:'Baloo 2', cursive;font-weight:800;letter-spacing:0.3px;}
  .logo .puff{display:inline-flex;width:34px;height:34px;background:var(--coral);border-radius:50% 50% 50% 8px;align-items:center;justify-content:center;color:white;font-size:1.1rem;transform:rotate(-8deg);}
  nav.links{display:flex;gap:8px;}
  nav.links a{text-decoration:none;font-weight:700;color:var(--plum);padding:10px 16px;border-radius:999px;font-size:0.95rem;transition:background 0.15s ease, transform 0.15s ease;}
  nav.links a:hover{background:var(--sun);transform:translateY(-2px);}

  .hero{padding:56px 0 20px;position:relative;}
  .hero-inner{display:grid;grid-template-columns:1.1fr 0.9fr;gap:40px;align-items:center;}
  .eyebrow{display:inline-flex;align-items:center;gap:8px;background:var(--white);border:2.5px solid var(--plum);padding:6px 16px;border-radius:999px;font-size:0.85rem;font-weight:700;color:var(--plum);box-shadow:0 4px 0 var(--plum);margin-bottom:18px;}
  .hero h1{font-size:clamp(2.4rem, 5vw, 3.6rem);line-height:1.05;}
  .hero h1 span{color:var(--coral);position:relative;display:inline-block;}
  .hero p.lead{font-size:1.15rem;color:var(--plum-soft);margin-top:18px;max-width:46ch;line-height:1.5;}
  .hero-ctas{margin-top:28px;display:flex;gap:14px;flex-wrap:wrap;}
  .btn{border:3px solid var(--plum);background:var(--sun);color:var(--plum);font-weight:800;font-family:'Baloo 2', cursive;font-size:1.02rem;padding:13px 26px;border-radius:999px;cursor:pointer;box-shadow:var(--shadow-pop);transition:transform 0.12s ease, box-shadow 0.12s ease;}
  .btn:hover{transform:translateY(-3px);}
  .btn:active{transform:translateY(2px);box-shadow:0 4px 0 rgba(46,33,64,0.14);}
  .btn.secondary{background:var(--white);}
  .btn.coral{background:var(--coral);color:white;}
  .btn.grass{background:var(--grass);color:var(--plum);}
  .hero-critter{justify-self:center;font-size:9rem;filter:drop-shadow(0 14px 0 rgba(46,33,64,0.08));animation:bob 3.4s ease-in-out infinite;}
  @keyframes bob{0%,100%{transform:translateY(0) rotate(-2deg);}50%{transform:translateY(-14px) rotate(2deg);}}

  .train-section{padding:10px 0 70px;}
  .track-scroll{overflow-x:auto;padding:30px 6px 46px;-webkit-overflow-scrolling:touch;}
  .track{position:relative;display:flex;gap:22px;padding:0 20px 26px;min-width:max-content;}
  .track::after{content:"";position:absolute;left:0;right:0;bottom:14px;height:6px;background-image:repeating-linear-gradient(90deg, var(--plum) 0 22px, transparent 22px 34px);border-radius:3px;}
  .car{border:none;background:none;cursor:pointer;padding:0;position:relative;display:flex;flex-direction:column;align-items:center;gap:8px;}
  .car-body{width:88px;height:96px;border-radius:20px;border:3px solid var(--plum);display:flex;align-items:center;justify-content:center;font-family:'Baloo 2', cursive;font-size:2.2rem;font-weight:800;color:var(--plum);box-shadow:0 8px 0 rgba(46,33,64,0.16);transition:transform 0.16s ease, box-shadow 0.16s ease, filter 0.16s ease;position:relative;}
  .car-body::before{content:"";position:absolute;top:-14px;left:14px;right:14px;height:14px;background:inherit;border:3px solid var(--plum);border-bottom:none;border-radius:10px 10px 0 0;}
  .wheels{display:flex;gap:14px;margin-top:-8px;}
  .wheels span{width:16px;height:16px;background:var(--plum);border-radius:50%;border:3px solid var(--plum);}
  .car:hover .car-body{transform:translateY(-6px);}
  .car[aria-pressed="true"] .car-body{outline:4px solid var(--plum);outline-offset:3px;transform:translateY(-10px) scale(1.04);box-shadow:0 12px 0 rgba(46,33,64,0.2);}
  .car-label{font-size:0.75rem;font-weight:700;color:var(--plum-soft);text-transform:uppercase;letter-spacing:0.5px;}

  section.panel{padding:64px 0;}
  .panel-head{text-align:center;max-width:640px;margin:0 auto 36px;}
  .panel-head h2{font-size:clamp(1.8rem, 3.4vw, 2.4rem);}
  .panel-head p{color:var(--plum-soft);margin-top:10px;font-size:1.05rem;}

  .meadow{background:var(--cream-2);border:3px solid var(--plum);border-radius:var(--radius-lg);padding:40px;display:grid;grid-template-columns:220px 1fr;gap:36px;align-items:center;box-shadow:var(--shadow-soft);}
  .meadow-number{display:flex;flex-direction:column;align-items:center;gap:6px;background:var(--white);border:3px solid var(--plum);border-radius:var(--radius-md);padding:26px 10px;}
  .meadow-number .big-num{font-family:'Baloo 2', cursive;font-size:5rem;font-weight:800;color:var(--coral);line-height:1;}
  .meadow-number .word{font-weight:700;color:var(--plum-soft);text-transform:capitalize;font-size:1.1rem;}
  .critter-grid{display:flex;flex-wrap:wrap;gap:16px;min-height:80px;}
  .critter-grid span{font-size:2.6rem;display:inline-block;animation:pop 0.4s ease both;}
  @keyframes pop{0%{transform:scale(0);opacity:0;}70%{transform:scale(1.15);opacity:1;}100%{transform:scale(1);}}

  .quiz-card{background:var(--white);border:3px solid var(--plum);border-radius:var(--radius-lg);padding:40px;max-width:640px;margin:0 auto;box-shadow:var(--shadow-soft);text-align:center;}
  .quiz-score{display:inline-flex;align-items:center;gap:8px;background:var(--sun);border:2.5px solid var(--plum);padding:6px 16px;border-radius:999px;font-weight:800;font-family:'Baloo 2', cursive;margin-bottom:22px;font-size:0.95rem;}
  .quiz-prompt{font-size:1.05rem;color:var(--plum-soft);margin-bottom:14px;font-weight:700;}
  .quiz-critters{display:flex;flex-wrap:wrap;justify-content:center;gap:14px;min-height:70px;margin-bottom:26px;}
  .quiz-critters span{font-size:2.4rem;animation:pop 0.35s ease both;}
  .quiz-options{display:grid;grid-template-columns:repeat(4, 1fr);gap:12px;margin-bottom:20px;}
  .opt-btn{border:3px solid var(--plum);background:var(--sky);color:var(--plum);font-family:'Baloo 2', cursive;font-weight:800;font-size:1.5rem;padding:16px 0;border-radius:16px;cursor:pointer;box-shadow:0 6px 0 rgba(46,33,64,0.16);transition:transform 0.12s ease;}
  .opt-btn:hover{transform:translateY(-3px);}
  .opt-btn:active{transform:translateY(2px);}
  .opt-btn.correct{background:var(--grass);}
  .opt-btn.wrong{background:var(--coral);color:white;}
  .opt-btn:disabled{cursor:default;}
  .quiz-feedback{min-height:28px;font-weight:800;font-family:'Baloo 2', cursive;color:var(--plum);margin-bottom:16px;}

  footer{background:var(--plum);color:var(--cream);padding:38px 0;margin-top:20px;}
  .footer-inner{display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:14px;}
  footer .logo{color:var(--cream);}
  footer p{color:#C9BFDA;font-size:0.9rem;margin:0;}

  @media (max-width:820px){
    .hero-inner{grid-template-columns:1fr;text-align:center;}
    .hero p.lead{margin-left:auto;margin-right:auto;}
    .hero-ctas{justify-content:center;}
    .hero-critter{font-size:6rem;order:-1;}
    .meadow{grid-template-columns:1fr;text-align:center;}
    .critter-grid{justify-content:center;}
    .quiz-options{grid-template-columns:repeat(2, 1fr);}
    nav.links{display:none;}
  }
</style>
</head>
<body>

<header>
  <div class="nav">
    <div class="logo"><span class="puff">🚂</span> Numberland</div>
    <nav class="links">
      <a href="#train">Ride the Train</a>
      <a href="#meadow">Count</a>
      <a href="#quiz">Play</a>
    </nav>
  </div>
</header>

<section class="hero">
  <div class="wrap hero-inner">
    <div>
      <span class="eyebrow">🌟 For curious counters ages 3–7</span>
      <h1>Hop aboard and learn to count to <span>ten!</span></h1>
      <p class="lead">Numberland turns counting into a ride. Pick a train car, meet a meadow full of friendly critters, and test your skills with a quick game.</p>
      <div class="hero-ctas">
        <button class="btn" onclick="document.getElementById('train').scrollIntoView()">Ride the Train</button>
        <button class="btn secondary" onclick="document.getElementById('quiz').scrollIntoView()">Play a Game</button>
      </div>
    </div>
    <div class="hero-critter" aria-hidden="true">🦊</div>
  </div>
</section>

<section class="train-section" id="train">
  <div class="wrap panel-head">
    <h2>The Number Train</h2>
    <p>Click a car to open its doors — every car carries exactly as many friends as its number.</p>
  </div>
  <div class="track-scroll">
    <div class="track" id="track" role="group" aria-label="Choose a number from 1 to 10"></div>
  </div>
</section>

<section class="panel" id="meadow">
  <div class="wrap">
    <div class="panel-head">
      <h2>Counting Meadow</h2>
      <p>Here's who hopped off the train.</p>
    </div>
    <div class="meadow">
      <div class="meadow-number">
        <span class="big-num" id="meadowNum">1</span>
        <span class="word" id="meadowWord">one</span>
      </div>
      <div class="critter-grid" id="meadowCritters" aria-live="polite"></div>
    </div>
  </div>
</section>

<section class="panel" id="quiz">
  <div class="wrap">
    <div class="panel-head">
      <h2>Quick Count Quiz</h2>
      <p>Count the friends, then tap the matching number.</p>
    </div>
    <div class="quiz-card">
      <div class="quiz-score">⭐ Score: <span id="score">0</span></div>
      <div class="quiz-prompt">How many friends do you see?</div>
      <div class="quiz-critters" id="quizCritters" aria-live="polite"></div>
      <div class="quiz-options" id="quizOptions"></div>
      <div class="quiz-feedback" id="quizFeedback" aria-live="polite"></div>
      <button class="btn grass" id="nextBtn" style="display:none;" onclick="nextQuestion()">Next Round →</button>
    </div>
  </div>
</section>

<footer>
  <div class="wrap footer-inner">
    <div class="logo">🚂 Numberland</div>
    <p>Made with care for little counters everywhere.</p>
  </div>
</footer>

<script>
  const WORDS = ["zero","one","two","three","four","five","six","seven","eight","nine","ten"];
  const CRITTERS = ["🐰","🐻","🦊","🐸","🐱","🐶","🐢","🦋","🐥","🐳"];
  const CAR_COLORS = ["#FFC93C","#4EC5F1","#6FCF97","#FF6F59","#B18CFF"];

  const track = document.getElementById('track');
  const meadowNum = document.getElementById('meadowNum');
  const meadowWord = document.getElementById('meadowWord');
  const meadowCritters = document.getElementById('meadowCritters');

  function critterRow(n, seed){
    const c = CRITTERS[seed % CRITTERS.length];
    return Array.from({length:n}, (_,i) => `<span style="animation-delay:${i*0.06}s">${c}</span>`).join('');
  }

  function selectNumber(n){
    document.querySelectorAll('.car').forEach(btn=>{
      btn.setAttribute('aria-pressed', btn.dataset.n === String(n) ? 'true' : 'false');
    });
    meadowNum.textContent = n;
    meadowWord.textContent = WORDS[n];
    meadowCritters.innerHTML = critterRow(n, n);
  }

  for(let n=1; n<=10; n++){
    const car = document.createElement('button');
    car.className = 'car';
    car.type = 'button';
    car.dataset.n = n;
    car.setAttribute('aria-pressed', n === 1 ? 'true' : 'false');
    car.setAttribute('aria-label', `Number ${n}`);
    car.innerHTML = `
      <div class="car-body" style="background:${CAR_COLORS[n % CAR_COLORS.length]}">${n}</div>
      <div class="wheels"><span></span><span></span></div>
      <div class="car-label">Car ${n}</div>
    `;
    car.addEventListener('click', () => selectNumber(n));
    track.appendChild(car);
  }
  selectNumber(1);

  const quizCritters = document.getElementById('quizCritters');
  const quizOptions = document.getElementById('quizOptions');
  const quizFeedback = document.getElementById('quizFeedback');
  const nextBtn = document.getElementById('nextBtn');
  const scoreEl = document.getElementById('score');
  let score = 0;
  let currentAnswer = 0;

  function randInt(min, max){ return Math.floor(Math.random() * (max - min + 1)) + min; }

  function nextQuestion(){
    quizFeedback.textContent = '';
    nextBtn.style.display = 'none';
    currentAnswer = randInt(1, 10);
    quizCritters.innerHTML = critterRow(currentAnswer, randInt(0,9));

    const options = new Set([currentAnswer]);
    while(options.size < 4){ options.add(randInt(1,10)); }
    const shuffled = Array.from(options).sort(() => Math.random() - 0.5);

    quizOptions.innerHTML = '';
    shuffled.forEach(val => {
      const b = document.createElement('button');
      b.className = 'opt-btn';
      b.type = 'button';
      b.textContent = val;
      b.addEventListener('click', () => checkAnswer(val, b));
      quizOptions.appendChild(b);
    });
  }

  function checkAnswer(val, btn){
    const allBtns = quizOptions.querySelectorAll('.opt-btn');
    allBtns.forEach(b => b.disabled = true);

    if(val === currentAnswer){
      btn.classList.add('correct');
      quizFeedback.textContent = "That's right! 🎉";
      score++;
      scoreEl.textContent = score;
    } else {
      btn.classList.add('wrong');
      quizFeedback.textContent = `Nice try! It was ${currentAnswer}.`;
      allBtns.forEach(b => { if(Number(b.textContent) === currentAnswer) b.classList.add('correct'); });
    }
    nextBtn.style.display = 'inline-block';
  }

  nextQuestion();
</script>

</body>
</html>
