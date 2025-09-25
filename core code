<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VC Fund Model Comparison</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #111827;
            color: #f3f4f6;
        }
        canvas {
            background-color: #1f2937;
            border-radius: 0.75rem;
            border: 1px solid #374151;
        }
        .table-container {
            background-color: #1f2937;
            border-radius: 0.75rem;
            border: 1px solid #374151;
            overflow: hidden;
        }
        th, td {
            padding: 1rem 1.5rem;
            text-align: left;
            border-bottom: 1px solid #374151;
        }
        th {
            background-color: #374151;
            color: #d1d5db;
            font-weight: 600;
        }
        td {
            color: #9ca3af;
        }
        tr:last-child td {
            border-bottom: none;
        }
        .highlight {
            color: #60a5fa;
        }
    </style>
</head>
<body class="p-4 md:p-8">

    <header class="text-center mb-12">
        <h1 class="text-4xl md:text-5xl font-bold text-white mb-2">Venture Capital Fund Models</h1>
        <p class="text-lg text-gray-400">A Visual Comparison: Traditional vs. Evergreen</p>
    </header>

    <main class="grid grid-cols-1 lg:grid-cols-2 gap-8 mb-12">
        <!-- Traditional Close-Ended Fund Diagram -->
        <div class="flex flex-col">
            <h2 class="text-2xl font-semibold text-center mb-4 text-white">Traditional Close-Ended Fund</h2>
            <canvas id="traditionalCanvas" width="800" height="600"></canvas>
        </div>

        <!-- Evergreen Fund Diagram -->
        <div class="flex flex-col">
            <h2 class="text-2xl font-semibold text-center mb-4 text-white">Evergreen Fund</h2>
            <canvas id="evergreenCanvas" width="800" height="600"></canvas>
        </div>
    </main>
    
    <section class="w-full max-w-7xl mx-auto">
        <h2 class="text-3xl font-bold text-center mb-6 text-white">Key Differences & Effects</h2>
        <div class="table-container shadow-lg">
            <table class="w-full">
                <thead>
                    <tr>
                        <th>Criteria</th>
                        <th class="highlight">Traditional Close-Ended Fund</th>
                        <th class="highlight">Evergreen Fund</th>
                        <th>Effect</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Fundraising</strong></td>
                        <td>One-time, intensive period per fund.</td>
                        <td>Continuous and ongoing capital raising.</td>
                        <td>Reduces constant fundraising pressure for GPs; offers more investment flexibility for LPs.</td>
                    </tr>
                    <tr>
                        <td><strong>Fund Life</strong></td>
                        <td>Finite, typically 10-12 years.</td>
                        <td>Perpetual, no fixed end date.</td>
                        <td>Allows for longer-term support for portfolio companies without pressure of a forced exit.</td>
                    </tr>
                    <tr>
                        <td><strong>LP Liquidity</strong></td>
                        <td>Illiquid for the fund's life.</td>
                        <td>Periodic liquidity options (e.g., quarterly redemptions).</td>
                        <td>Provides an exit mechanism, making the asset class more accessible to a broader range of investors.</td>
                    </tr>
                    <tr>
                        <td><strong>Capital Deployment</strong></td>
                        <td>Capital is "called down" as needed.</td>
                        <td>Capital is typically deployed more quickly.</td>
                        <td>Leads to more consistent investment pacing and allows GPs to be more opportunistic.</td>
                    </tr>
                    <tr>
                        <td><strong>Portfolio Management</strong></td>
                        <td>Pressure to achieve exits within the fund's lifecycle.</td>
                        <td>Ability to hold investments longer to maximize value.</td>
                        <td>Enables more patient capital, supporting long-term growth strategies for startups.</td>
                    </tr>
                    <tr>
                        <td><strong>Capital Recycling</strong></td>
                        <td>Limited or no recycling of exit proceeds.</td>
                        <td>Proceeds from exits are reinvested into the fund.</td>
                        <td>Creates a compounding effect and a self-sustaining pool of capital for investment.</td>
                    </tr>
                     <tr>
                        <td><strong>Investor Base</strong></td>
                        <td>Dominated by large institutional investors.</td>
                        <td>Attracts a wider range of investors (HNWIs, family offices).</td>
                        <td>Democratizes access to venture capital as an asset class.</td>
                    </tr>
                    <tr>
                        <td><strong>Co-Investment</strong></td>
                        <td>Opportunities offered on a deal-by-deal basis.</td>
                        <td>Can be structured programmatically or deal-by-deal.</td>
                        <td>Allows LPs to increase exposure to specific high-conviction deals with potentially lower fees.</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </section>

    <script>
        // --- Canvas Drawing Utilities ---
        function drawBox(ctx, x, y, width, height, text, color, textColor = '#f3f4f6') {
            ctx.fillStyle = color;
            ctx.strokeStyle = '#9ca3af';
            ctx.lineWidth = 1.5;
            ctx.beginPath();
            ctx.roundRect(x, y, width, height, 8);
            ctx.fill();
            ctx.stroke();
            
            ctx.fillStyle = textColor;
            ctx.font = 'bold 15px Inter';
            ctx.textAlign = 'center';
            ctx.textBaseline = 'middle';
            wrapText(ctx, text, x + width / 2, y + height / 2, width - 20, 18);
        }

        function drawArrow(ctx, fromX, fromY, toX, toY, label = '', dashed = false, curve = 0) {
            const headlen = 10;
            const angle = Math.atan2(toY - fromY, toX - fromX);
            const controlX = fromX + (toX - fromX) / 2 + (fromY - toY) * curve;
            const controlY = fromY + (toY - fromY) / 2 + (toX - fromX) * curve;

            ctx.save();
            ctx.strokeStyle = '#9ca3af';
            ctx.lineWidth = 1.5;

            if (dashed) {
                ctx.setLineDash([5, 5]);
            }

            ctx.beginPath();
            ctx.moveTo(fromX, fromY);
            if (curve !== 0) {
                ctx.quadraticCurveTo(controlX, controlY, toX, toY);
            } else {
                ctx.lineTo(toX, toY);
            }
            ctx.stroke();

            // Arrowhead
            let endAngle;
            if (curve !== 0) {
                endAngle = Math.atan2(toY - controlY, toX - controlX);
            } else {
                endAngle = angle;
            }

            ctx.beginPath();
            ctx.moveTo(toX, toY);
            ctx.lineTo(toX - headlen * Math.cos(endAngle - Math.PI / 6), toY - headlen * Math.sin(endAngle - Math.PI / 6));
            ctx.lineTo(toX - headlen * Math.cos(endAngle + Math.PI / 6), toY - headlen * Math.sin(endAngle + Math.PI / 6));
            ctx.lineTo(toX, toY);
            ctx.closePath();
            ctx.fillStyle = '#9ca3af';
            ctx.fill();
            
            ctx.setLineDash([]);

            if (label) {
                ctx.fillStyle = '#d1d5db';
                ctx.font = '14px Inter';
                ctx.textAlign = 'center';
                ctx.textBaseline = 'bottom';
                
                let labelX, labelY;
                if (curve !== 0) {
                    labelX = controlX;
                    labelY = controlY - 10;
                } else {
                    labelX = fromX + (toX - fromX) / 2;
                    labelY = fromY + (toY - fromY) / 2 - 10;
                }
                const labelAngle = (curve !== 0) ? Math.atan2(toY-fromY, toX-fromX) : angle;

                ctx.save();
                ctx.translate(labelX, labelY);
                ctx.rotate(labelAngle);
                 if (Math.abs(labelAngle) > Math.PI / 2 && curve === 0) {
                    ctx.rotate(Math.PI);
                }
                ctx.fillText(label, 0, 0);
                ctx.restore();
            }
            ctx.restore();
        }
        
        function wrapText(context, text, x, y, maxWidth, lineHeight) {
            const words = text.split(' ');
            let line = '';
            const lines = [];

            for(let n = 0; n < words.length; n++) {
                const testLine = line + words[n] + ' ';
                const metrics = context.measureText(testLine);
                const testWidth = metrics.width;
                if (testWidth > maxWidth && n > 0) {
                    lines.push(line);
                    line = words[n] + ' ';
                } else {
                    line = testLine;
                }
            }
            lines.push(line);

            let startY = y - (lines.length - 1) * lineHeight / 2;
            for (let i = 0; i < lines.length; i++) {
                context.fillText(lines[i].trim(), x, startY + i * lineHeight);
            }
        }


        // --- Traditional Fund Canvas ---
        const traditionalCanvas = document.getElementById('traditionalCanvas');
        const tCtx = traditionalCanvas.getContext('2d');
        
        function drawTraditional() {
            tCtx.clearRect(0, 0, traditionalCanvas.width, traditionalCanvas.height);
            
            const lpColor = '#1e40af', gpColor = '#065f46', fundColor = '#7c2d12', companyColor = '#5b21b6', coInvestorColor = '#9a3412';
            const boxWidth = 140, boxHeight = 60;

            // Investor Landscape
            tCtx.strokeStyle = '#4b5563';
            tCtx.lineWidth = 1;
            tCtx.setLineDash([5, 5]);
            tCtx.strokeRect(20, 130, 260, 200);
            tCtx.setLineDash([]);
            tCtx.fillStyle = '#d1d5db'; tCtx.font = 'bold 16px Inter'; tCtx.textAlign = 'center';
            tCtx.fillText('Investor Landscape', 150, 150);
            drawBox(tCtx, 80, 180, 140, 50, 'Institutional LPs (Pensions, etc.)', lpColor);
            drawBox(tCtx, 80, 260, 140, 50, 'Family Offices & HNWIs', lpColor);
            
            // Core components
            drawBox(tCtx, 330, 150, boxWidth, boxHeight, 'Close-Ended Fund', fundColor);
            drawBox(tCtx, 610, 250, boxWidth, boxHeight, 'General Partners (GPs)', gpColor);
            drawBox(tCtx, 330, 480, boxWidth, boxHeight, 'Portfolio Companies', companyColor);
            drawBox(tCtx, 50, 400, 140, 50, 'Co-Investors', coInvestorColor);

            // Arrows
            drawArrow(tCtx, 280, 240, 330, 180, 'Commit Capital');
            drawArrow(tCtx, 470, 180, 610, 280, 'Mgmt Fees & Carry');
            drawArrow(tCtx, 400, 210, 400, 475, 'Fund Investment');
            drawArrow(tCtx, 400, 480, 400, 215, 'Exits (IPO, M&A)', true);
            drawArrow(tCtx, 330, 180, 240, 250, 'Distributions', true, 0.4);

            // Co-investor flow
            drawArrow(tCtx, 190, 425, 330, 495, 'Direct Co-Investment');
            drawArrow(tCtx, 470, 175, 590, 250, 'Co-Invest Opportunity', true, -0.2);


        }


        // --- Evergreen Fund Canvas ---
        const evergreenCanvas = document.getElementById('evergreenCanvas');
        const eCtx = evergreenCanvas.getContext('2d');
        
        function drawEvergreen() {
            eCtx.clearRect(0, 0, evergreenCanvas.width, evergreenCanvas.height);
            
            const lpColor = '#1e40af', gpColor = '#065f46', fundColor = '#7c2d12', cycleColor = '#047857', coInvestorColor = '#9a3412';
            const boxWidth = 140, boxHeight = 60;
            const centerX = 400, centerY = 330;

            // Investor Landscape
            eCtx.strokeStyle = '#4b5563';
            eCtx.lineWidth = 1;
            eCtx.setLineDash([5, 5]);
            eCtx.strokeRect(20, 100, 240, 260);
            eCtx.setLineDash([]);
            eCtx.fillStyle = '#d1d5db'; eCtx.font = 'bold 16px Inter'; eCtx.textAlign = 'center';
            eCtx.fillText('Investor Landscape', 140, 120);
            drawBox(eCtx, 70, 150, 140, 50, 'Institutional LPs', lpColor);
            drawBox(eCtx, 70, 220, 140, 50, 'Family Offices', lpColor);
            drawBox(eCtx, 70, 290, 140, 50, 'HNWIs / Retail', lpColor);
            drawBox(eCtx, 50, 450, 140, 50, 'Co-Investors', coInvestorColor);

            // Central Fund & GP
            drawBox(eCtx, centerX - boxWidth/2, centerY - boxHeight/2, boxWidth, boxHeight, 'Evergreen Fund', fundColor);
            drawBox(eCtx, 610, 150, boxWidth, boxHeight, 'General Partners (GPs)', gpColor);
            
            // Arrows for LPs and GPs
            drawArrow(eCtx, 260, 230, centerX - boxWidth/2 - 5, centerY, 'Continuous Investment');
            drawArrow(eCtx, centerX - boxWidth/2 - 5, centerY, 260, 230, 'Redemptions', true, 0.3);
            drawArrow(eCtx, centerX + boxWidth/2 + 5, centerY, 610, 180, 'Mgmt Fees');

            // Perpetual Investment Cycle
            eCtx.save();
            eCtx.strokeStyle = cycleColor; eCtx.lineWidth = 3; eCtx.setLineDash([10, 5]);
            eCtx.beginPath(); eCtx.arc(centerX, centerY, 200, 0, 2 * Math.PI); eCtx.stroke();
            eCtx.restore();

            eCtx.fillStyle = '#34d399'; eCtx.font = 'bold 18px Inter'; eCtx.textAlign = 'center';
            eCtx.fillText('Perpetual Investment Cycle', centerX, 80);

            // Cycle Stages
            const stages = [
                { text: 'Invest in Companies', angle: -Math.PI / 2 },
                { text: 'Grow Portfolio', angle: Math.PI },
                { text: 'Exit Investments', angle: Math.PI / 2 },
                { text: 'Reinvest Capital', angle: 0 }
            ];
            const radius = 160;
            stages.forEach(stage => {
                const x = centerX + radius * Math.cos(stage.angle);
                const y = centerY + radius * Math.sin(stage.angle);
                drawBox(eCtx, x - 60, y - 25, 120, 50, stage.text, cycleColor, '#e5e7eb');
            });

            // Co-investor flow
            drawArrow(eCtx, 190, 475, centerX - 80, centerY + 140, 'Direct Co-Investment');
            drawArrow(eCtx, centerX + 70, centerY, 610, 210, 'Co-Invest Opportunity', true);
        }

        function drawAll() {
             // Set canvas size based on container for responsiveness
            const containers = document.querySelectorAll('canvas');
            containers.forEach(canvas => {
                const container = canvas.parentElement;
                const dpr = window.devicePixelRatio || 1;
                const rect = container.getBoundingClientRect();
                
                canvas.width = rect.width * dpr;
                canvas.height = (rect.width * 0.75) * dpr; // Maintain 4:3 aspect ratio
                
                const ctx = canvas.getContext('2d');
                ctx.scale(dpr, dpr);
                
                canvas.style.width = `${rect.width}px`;
                canvas.style.height = `${rect.width * 0.75}px`;
            });
            drawTraditional();
            drawEvergreen();
        }
        
        window.addEventListener('load', drawAll);
        window.addEventListener('resize', drawAll);
    </script>
</body>
</html>

