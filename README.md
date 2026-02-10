<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Question for You...</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Quicksand:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Quicksand', sans-serif;
            background-color: #fff0f5; /* Lavender Blush */
            overflow-x: hidden;
        }

        h1, h2, .handwriting {
            font-family: 'Pacifico', cursive;
        }

        /* Floating Animation */
        @keyframes float {
            0% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(5deg); }
            100% { transform: translateY(0px) rotate(0deg); }
        }

        /* Heartbeat Animation */
        @keyframes heartbeat {
            0% { transform: scale(1); }
            15% { transform: scale(1.3); }
            30% { transform: scale(1); }
            45% { transform: scale(1.15); }
            60% { transform: scale(1); }
        }

        /* Wiggle Animation */
        @keyframes wiggle {
            0%, 100% { transform: rotate(-3deg); }
            50% { transform: rotate(3deg); }
        }

        .animate-float { animation: float 6s ease-in-out infinite; }
        .animate-heartbeat { animation: heartbeat 1.5s ease-in-out infinite; }
        .animate-wiggle { animation: wiggle 1s ease-in-out infinite; }

        /* Custom Bear CSS Art */
        .bear-container {
            position: relative;
            width: 150px;
            height: 150px;
            margin: 0 auto;
        }
        .bear-face {
            width: 120px;
            height: 100px;
            background: #8B4513; /* SaddleBrown */
            border-radius: 50% 50% 40% 40%;
            position: absolute;
            top: 20px;
            left: 15px;
            z-index: 2;
        }
        .bear-ear {
            width: 40px;
            height: 40px;
            background: #8B4513;
            border-radius: 50%;
            position: absolute;
            top: 10px;
            z-index: 1;
        }
        .ear-left { left: 10px; }
        .ear-right { right: 10px; }
        .ear-inner {
            width: 25px;
            height: 25px;
            background: #DEB887; /* Burlywood */
            border-radius: 50%;
            position: absolute;
            top: 8px;
            left: 8px;
        }
        .bear-muzzle {
            width: 60px;
            height: 45px;
            background: #DEB887;
            border-radius: 50%;
            position: absolute;
            top: 50px;
            left: 30px;
            z-index: 3;
        }
        .bear-nose {
            width: 20px;
            height: 15px;
            background: #3e1c0a;
            border-radius: 50%;
            position: absolute;
            top: 10px;
            left: 20px;
        }
        .bear-eye {
            width: 12px;
            height: 12px;
            background: #000;
            border-radius: 50%;
            position: absolute;
            top: 40px;
            z-index: 3;
        }
        .bear-eye::after {
            content: '';
            width: 4px;
            height: 4px;
            background: white;
            border-radius: 50%;
            position: absolute;
            top: 2px;
            right: 2px;
        }
        .eye-left { left: 35px; }
        .eye-right { right: 35px; }
        
        .bear-blush {
            width: 15px;
            height: 10px;
            background: #ffb6c1;
            border-radius: 50%;
            position: absolute;
            top: 55px;
            z-index: 3;
            opacity: 0.6;
        }
        .blush-left { left: 20px; }
        .blush-right { right: 20px; }

        /* Floating Background Emojis */
        .floating-emoji {
            position: fixed;
            font-size: 2rem;
            pointer-events: none;
            opacity: 0.3;
            z-index: 0;
            animation: float-up linear infinite;
        }

        @keyframes float-up {
            from { transform: translateY(100vh) rotate(0deg); }
            to { transform: translateY(-20vh) rotate(360deg); }
        }

        /* Utilities */
        .hidden-section {
            display: none;
            opacity: 0;
            transition: opacity 1s ease-in-out;
        }
        .visible-section {
            display: flex;
            opacity: 1;
        }
        
        .glass-panel {
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(8px);
            border-radius: 24px;
            border: 2px solid white;
            box-shadow: 0 10px 40px rgba(139, 69, 19, 0.1);
        }

        .btn-primary {
            background: #d97706; /* Amber 600 */
            color: white;
            transition: all 0.3s;
        }
        .btn-primary:hover {
            background: #b45309;
            transform: scale(1.05);
        }
    </style>
</head>
<body class="min-h-screen flex flex-col items-center justify-center relative">

    <!-- Background Music (Optional, hidden audio element) -->
    <!-- <audio id="bgMusic" loop>
        <source src="your-music-url.mp3" type="audio/mpeg">
    </audio> -->

    <!-- Floating Background Elements -->
    <div id="background-effects"></div>

    <!-- MAIN CONTAINER -->
    <main class="relative z-10 w-full max-w-md p-4">
        
        <!-- STEP 1: WELCOME -->
        <div id="step-1" class="glass-panel p-8 text-center flex flex-col items-center gap-6 visible-section transition-all duration-700">
            <div class="bear-container animate-float">
                <div class="bear-ear ear-left"><div class="ear-inner"></div></div>
                <div class="bear-ear ear-right"><div class="ear-inner"></div></div>
                <div class="bear-face">
                    <div class="bear-eye eye-left"></div>
                    <div class="bear-eye eye-right"></div>
                    <div class="bear-blush blush-left"></div>
                    <div class="bear-blush blush-right"></div>
                    <div class="bear-muzzle">
                        <div class="bear-nose"></div>
                    </div>
                </div>
            </div>
            
            <h1 class="text-3xl text-amber-800">Hey HONEY PAPA! 🧸</h1>
            <p class="text-gray-600 text-lg">Teddy adginav ga edi thiskoo...</p>
            
            <button onclick="nextStep(2)" class="btn-primary font-bold py-3 px-8 rounded-full shadow-lg text-xl flex items-center gap-2">
                <span>click to enter into my heart I mean your sweet Home</span>
                <span class="animate-bounce">❤️</span>
            </button>
        </div>

        <!-- STEP 2: SLIDESHOW / REASONS -->
        <div id="step-2" class="hidden-section glass-panel p-8 text-center flex-col items-center gap-6 absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-full max-w-md">
            <!-- Dynamic Content Area -->
            <div id="reason-content" class="min-h-[1100px] flex flex-col items-center justify-center">
                <!-- Content injected via JS -->
            </div>

            <div class="flex gap-2 justify-center mt-4">
                <button onclick="nextReason()" class="bg-amber-100 text-amber-800 hover:bg-amber-200 font-bold py-2 px-6 rounded-full transition-colors">
                    Next ➡️
                </button>
            </div>
        </div>

        <!-- STEP 3: THE QUESTION -->
        <div id="step-3" class=" hidden-section glass-panel p-8 text-center flex-col items-center gap-8 absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-full max-w-md">
            
            <div class="text-6xl animate-heartbeat">💍</div>
            
            <h1 class="text-4xl text-pink-600 leading-tight">Will you marry me?</h1>
            
            <p class="text-gray-600 italic">You're my cuddliest bear and my greatest love.</p>
            
            <div class="flex flex-col gap-4 w-full relative h-32 justify-center items-center">
                <button onclick="acceptProposal()" class="btn-primary text-2xl font-bold py-3 px-10 rounded-full shadow-xl w-full z-20">
                    YES! 😍
                </button>
                
                <button id="no-btn" onmouseover="moveButton()" ontouchstart="moveButton()" onclick="moveButton()" class="bg-gray-300 text-gray-500 font-bold py-2 px-6 rounded-full absolute text-sm transition-all duration-200 z-10">
                    No... 😢
                </button>
            </div>
        </div>

        <!-- STEP 4: SUCCESS -->
        <div id="step-4" class="hidden-section glass-panel p-8 text-center flex-col items-center gap-6 absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-full max-w-md">
            <h1 class="text-4xl text-pink-600">SHE SAID YES! 🎉</h1>
            
            <!-- Two Bears Hugging (CSS simplified) -->
            <div class="flex justify-center -space-x-8 mt-4">
                <div class="bear-container transform scale-75 rotate-12">
                     <div class="bear-ear ear-left"><div class="ear-inner"></div></div>
                    <div class="bear-ear ear-right"><div class="ear-inner"></div></div>
                    <div class="bear-face" style="background: #8B4513;">
                         <div class="bear-eye eye-left"></div>
                        <div class="bear-eye eye-right"></div>
                        <div class="bear-muzzle"><div class="bear-nose"></div></div>
                    </div>
                </div>
                 <div class="bear-container transform scale-75 -rotate-12 z-10">
                     <div class="bear-ear ear-left"><div class="ear-inner"></div></div>
                    <div class="bear-ear ear-right"><div class="ear-inner"></div></div>
                    <div class="bear-face" style="background: #A0522D;">
                         <div class="bear-eye eye-left"></div>
                        <div class="bear-eye eye-right"></div>
                         <div class="bear-blush blush-left"></div>
                        <div class="bear-blush blush-right"></div>
                        <div class="bear-muzzle"><div class="bear-nose"></div></div>
                    </div>
                </div>
            </div>

            <p class="text-gray-600 text-lg">You've made me the happiest bear in the world.</p>
            <p class="text-amber-800 text-sm italic mt-2">Forever and ever ❤️</p>
        </div>
        
    </main>

    <script>
        // State
        let currentStep = 1;
        let reasonIndex = 0;
        
        // Reasons content - EDIT THESE!
        const reasons = [
            {
                emoji: "🧸",
                title: "welcome Sweetheart",
                text: "Nanna,Neekosam teddy ivvaleka pothunna kani accept this please!  next page ki ellu u have something more"
            },
            {
                emoji: "🍯",
                title: "Me tho ko hi Gya re there aankho mei",
                text: "Nannaa, I lost somewhere vethkutunna ekkada poya ekada poyanaa aniii chusthe tere ankoh me hi ko gayaaa re .  Neee kantiki katkuka ,ninnu kanu repoala kaasthu neethone neevente unnaa adhi naku  telse sariki  kalam gadichindi ante neeku telse sariki naa Jeevitham gadchipoddi anpinchindii kani ahh Devudu anthaa time ivvaledu manaki neeku thondarlone telsipoyindiii.  Na prema valla nu chalaaa happy ga untav nanna nammakam naaku undi kani nenu chese pichi panula valla nuvvu assalu bhadha padakudadhu Nanna what do you mean illuu naaku illu ante Nu nenu ekkada unte adhe mana illu  adhe na comfort zone adhe na stress free zone adhe   place I love the  most . Nuvu nenu kalisthene adhi illu . I love you sooooo much bangadam 💗 .nee nuditi pai sinduranga pettina ah kunkumane na nuditi pai petkuntaa bujjammaa. Go Go inka aypole hit the next babee"
            },
            {
                emoji: "💫",
                title: "My lovely Angel!",
                text: "Nanna you know how important you are in my life ani okka mata lo chepali  ante Honey leni pranav ledu im nothing without you raa nanna nenu chalaa possessive nu ammaila tho ekkuva close unna naaku nachadu nuvu complete ga naaku mathrame sontham i know im over possesive ani but nakantu unnadi nuvve raa i want you forever in my life chitti evr m ankunna m chesna na cheyyi ninnu eppudu odleyadu ra Im sooo happy to have you ra papaaa ,here edi neeke Naku Bhumi ki unnantha opika undho ledo telidu kanii na chithi velige daaka ninnu mosthune unta nanna.🌏_Na manasu aakasham antha vishalamaina pradhesham kakapoina  nee sthanam kii eh lotu undadhu_☁️Ahh Gaali lonchi oche prathi swaswa nee sparshe gurthu chesthundii bujjammaa_👉🏻👈🏻🌬️_Nenu ahh Agni antha pure kakapovachu kanii ninnu kadhani eh ammaini kala lo kuda thavalenu_☀️ _Na prema ahh Neeru antha swachamainadho kadho telidu kanii ahh samudralaa lothu kuda saripodhuu nee meeda naakunna  premani kolavali ante_ 🌊 ,wait wait inka aypoledu next clickuu Papaaaaa "
            },
            {
                emoji: "❤️",
                title: "THE DAY",
                text: "' Parinitho errabadina na chethulatho errati kunkumani nee nudhuti pai  didhe rojuna' ' 7 janmalu ethina dorakani nee lanti devatha tho 7 adugulu vese samayana' '3 thrimurthulu ashirvadinche ah 3 mullu vese ah kashanana '  ,avadulu leni na santhoshaniki oka pilupu evandi ani  thodu aythe  ika inthakante pedda varam m koragalam Kanyadam chespudu mee nanna na kallu kadugthunaru  na kuthurni nee chethilo pedthunnanu jagratha ani bahusha ayanaki telide mo nee kalu kinda pettanivakunda chuskunta  thana chinnarini ani.Appagithalapudu mee Amma edusthundii thanu anukoni undademo thana kuthurni na kuthuri la chuskuntadu alludu  anii.Intiki peddadanivi ellipothunnav ani chelli badhapadthundii kani intiki peddakodkula thanu prema annaya ani pilichina nenu osthunna ani uhinchaleka poyindii.Andari gurinchii pakkana pedithe Nee kanitiki pettina katunani datii na disti eh thagilettu kanpisthunnav na kallaki intiki vellaka chala pedda gummadikaya tho disti thichanu anduke.  Bangaram kante adhikanka merusthunnav inka bangaram avasaram m undi nee onti meeda anpichela unnav.Nee gajulu avi nee chethiki ochinapudu nee Moham loni santhosham na kallalo kanpisthundii.Ahh mukkupudaka nelavanke asuya padela unte nu  nannu nee vipu lagakunda m aputhundii cheppuu. jilakarabellam pette mundhu varaku na manasu ninnu chudali chudali ani  okate ibbandi pettesthundi ante nammu. Ungaranni oka bindha lo vesi poti padamantunnaru ah devudi tho poti padi ninnu sampinchkunna inka denikosam poti padali ani vallaki Ela cheppalo mo. Annitiki minchi nee konguki naa kanduva kattaru ademi ante  mana bandham eppati vidipovadhu ani anta vallaki telidu chivariki ah devude ochina manalni vidadiyaledu anii.."
            }
        ];

        // Functions
        function nextStep(step) {
            // Hide current
            document.getElementById(`step-${currentStep}`).classList.add('hidden-section');
            document.getElementById(`step-${currentStep}`).classList.remove('visible-section');
            
            // Show next
            currentStep = step;
            const nextEl = document.getElementById(`step-${currentStep}`);
            nextEl.classList.remove('hidden-section');
            
            // Use flex display for layout
            nextEl.style.display = 'flex';
            
            // Trigger animation
            setTimeout(() => {
                nextEl.classList.add('visible-section');
            }, 50);

            if (step === 2) {
                renderReason();
            }
        }

        function renderReason() {
            const container = document.getElementById('reason-content');
            const data = reasons[reasonIndex];
            
            // Create elements with animation
            container.innerHTML = `
                <div class="text-6xl mb-4 animate-bounce">${data.emoji}</div>
                <h2 class="text-2xl text-amber-900 font-bold mb-2">${data.title}</h2>
                <p class="text-gray-700 leading-relaxed text-lg">${data.text}</p>
            `;
        }

        function nextReason() {
            reasonIndex++;
            if (reasonIndex < reasons.length) {
                renderReason();
            } else {
                nextStep(3); // Go to Proposal
            }
        }

        function moveButton() {
            const btn = document.getElementById('no-btn');
            const container = document.getElementById('step-3');
            
            const maxX = container.clientWidth - btn.clientWidth - 40; // 40px buffer
            const maxY = container.clientHeight - btn.clientHeight - 40;

            const randomX = Math.floor(Math.random() * maxX) - (maxX / 2);
            const randomY = Math.floor(Math.random() * maxY) - (maxY / 2);

            btn.style.transform = `translate(${randomX}px, ${randomY}px)`;
            
            // Change text occasionally for fun
            const texts = ["No... 😢", "Are you sure?", "Really?", "Try again!", "Catch me!"];
            btn.innerText = texts[Math.floor(Math.random() * texts.length)];
        }

        function acceptProposal() {
            nextStep(4);
            fireConfetti();
            startFloatingHearts();
        }

        function fireConfetti() {
            const duration = 15 * 1000;
            const animationEnd = Date.now() + duration;
            const defaults = { startVelocity: 30, spread: 360, ticks: 60, zIndex: 0 };

            function random(min, max) {
              return Math.random() * (max - min) + min;
            }

            const interval = setInterval(function() {
              const timeLeft = animationEnd - Date.now();

              if (timeLeft <= 0) {
                return clearInterval(interval);
              }

              const particleCount = 50 * (timeLeft / duration);
              // since particles fall down, start a bit higher than random
              confetti(Object.assign({}, defaults, { particleCount, origin: { x: random(0.1, 0.3), y: Math.random() - 0.2 } }));
              confetti(Object.assign({}, defaults, { particleCount, origin: { x: random(0.7, 0.9), y: Math.random() - 0.2 } }));
            }, 250);
        }

        // Background floating effects
        function createFloatingEmoji() {
            const emojis = ['🧸', '❤️', '🍯', '✨'];
            const el = document.createElement('div');
            el.innerText = emojis[Math.floor(Math.random() * emojis.length)];
            el.className = 'floating-emoji';
            el.style.left = Math.random() * 100 + 'vw';
            el.style.animationDuration = Math.random() * 5 + 5 + 's'; // 5-10s
            el.style.fontSize = Math.random() * 2 + 1 + 'rem';
            
            document.body.appendChild(el);
            
            // Remove after animation
            setTimeout(() => {
                el.remove();
            }, 10000);
        }

        // Start floating emojis loop
        setInterval(createFloatingEmoji, 800);

        function startFloatingHearts() {
            // Intensify the floating effect on success
             setInterval(() => {
                const el = document.createElement('div');
                el.innerText = '❤️';
                el.className = 'floating-emoji';
                el.style.left = Math.random() * 100 + 'vw';
                el.style.animationDuration = '3s'; // Faster
                el.style.color = '#e11d48';
                el.style.fontSize = '3rem';
                el.style.zIndex = '50';
                document.body.appendChild(el);
                setTimeout(() => el.remove(), 3000);
            }, 200);
        }

    </script>
</body>
</html>
