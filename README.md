<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Mamãe do Ano - Vanessa Braga</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Great+Vibes&display=swap" rel="stylesheet">
    <style>
        /* ==================== VARIÁVEIS E TEMAS ==================== */
        :root {
            --primary: #ffb6c1; /* Rosa claro */
            --primary-dark: #ff8da1;
            --secondary: #d4af37; /* Dourado */
            --bg: #fffafa; /* Fundo principal */
            --card-bg: #ffffff;
            --text-main: #4a4a4a;
            --text-light: #7a7a7a;
            --danger: #ff6b6b;
            --success: #4cd137;
            --shadow: 0 4px 15px rgba(0,0,0,0.05);
            --border-radius: 20px;
        }

        body.dark-mode {
            --primary: #d87093;
            --primary-dark: #c25275;
            --secondary: #daa520;
            --bg: #1a1a2e;
            --card-bg: #16213e;
            --text-main: #f5f5f5;
            --text-light: #b0b0b0;
            --shadow: 0 4px 15px rgba(0,0,0,0.3);
        }

        /* ==================== RESET E BASE ==================== */
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Poppins', sans-serif; }
        body { background-color: var(--bg); color: var(--text-main); transition: background 0.3s, color 0.3s; overflow-x: hidden; }
        a { text-decoration: none; color: inherit; }
        button { cursor: pointer; border: none; outline: none; font-family: inherit; transition: 0.2s; }
        input, textarea, select { width: 100%; padding: 12px; border: 1px solid #ddd; border-radius: 10px; margin-bottom: 15px; font-family: inherit; background: var(--card-bg); color: var(--text-main); }
        
        /* ==================== ESTRUTURA ==================== */
        #app { display: flex; flex-direction: column; height: 100vh; max-width: 600px; margin: 0 auto; background: var(--bg); position: relative; box-shadow: 0 0 20px rgba(0,0,0,0.1); }
        .header { padding: 20px; background: var(--primary); color: white; display: flex; justify-content: space-between; align-items: center; border-bottom-left-radius: 20px; border-bottom-right-radius: 20px; z-index: 10; box-shadow: var(--shadow); }
        .header h1 { font-size: 1.2rem; font-weight: 600; }
        
        .content { flex: 1; overflow-y: auto; padding: 20px; padding-bottom: 90px; }
        .screen { display: none; animation: fadeIn 0.4s ease; }
        .screen.active { display: block; }
        
        /* ==================== NAVEGAÇÃO BOTTOM ==================== */
        .bottom-nav { position: absolute; bottom: 0; left: 0; width: 100%; background: var(--card-bg); display: flex; justify-content: space-around; padding: 15px 10px; box-shadow: 0 -5px 15px rgba(0,0,0,0.05); border-top-left-radius: 25px; border-top-right-radius: 25px; z-index: 10; }
        .nav-item { display: flex; flex-direction: column; align-items: center; color: var(--text-light); font-size: 0.75rem; background: none; }
        .nav-item.active { color: var(--primary-dark); font-weight: 600; }
        .nav-icon { font-size: 1.5rem; margin-bottom: 3px; }

        /* ==================== COMPONENTES ==================== */
        .card { background: var(--card-bg); border-radius: var(--border-radius); padding: 20px; margin-bottom: 20px; box-shadow: var(--shadow); border-top: 4px solid var(--primary); }
        .btn { background: var(--primary); color: white; padding: 12px 20px; border-radius: 12px; font-weight: 600; width: 100%; font-size: 1rem; box-shadow: 0 4px 10px rgba(255, 182, 193, 0.4); }
        .btn:hover { background: var(--primary-dark); }
        .btn-outline { background: transparent; border: 2px solid var(--primary); color: var(--primary); }
        .btn-small { padding: 8px 15px; font-size: 0.85rem; width: auto; }
        
        .progress-container { background: #eee; border-radius: 10px; height: 15px; width: 100%; margin: 15px 0; overflow: hidden; }
        .progress-bar { background: var(--primary); height: 100%; width: 0%; transition: width 1s ease; }
        
        .grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
        .stat-box { background: var(--card-bg); padding: 15px; border-radius: 15px; text-align: center; box-shadow: var(--shadow); border: 1px solid rgba(212, 175, 55, 0.2); }
        .stat-value { font-size: 1.5rem; font-weight: 700; color: var(--secondary); }
        .stat-label { font-size: 0.8rem; color: var(--text-light); }

        .list-item { background: var(--bg); padding: 15px; border-radius: 10px; margin-bottom: 10px; display: flex; justify-content: space-between; align-items: center; border-left: 3px solid var(--primary); }

        /* ==================== JOGO ==================== */
        #game-board { display: grid; grid-template-columns: repeat(6, 1fr); gap: 5px; margin: 20px auto; max-width: 300px; background: var(--card-bg); padding: 10px; border-radius: 15px; box-shadow: var(--shadow); }
        .candy { aspect-ratio: 1; display: flex; justify-content: center; align-items: center; font-size: 2rem; background: var(--bg); border-radius: 10px; cursor: pointer; transition: 0.2s; user-select: none; }
        .candy.selected { border: 2px solid var(--primary); transform: scale(1.1); }

        /* ==================== CERTIFICADO ==================== */
        #certificate-view { display: none; background: white; color: black; padding: 40px 20px; text-align: center; border: 15px solid var(--primary); border-radius: 10px; outline: 5px solid var(--secondary); outline-offset: -10px; min-height: 100vh; }
        .cert-title { font-family: 'Great Vibes', cursive; font-size: 3.5rem; color: var(--secondary); margin-bottom: 20px; }
        .cert-text { font-size: 1.2rem; line-height: 1.6; margin-bottom: 20px; }
        .cert-name { font-size: 2rem; font-weight: bold; color: var(--primary-dark); margin: 20px 0; }

        /* ==================== MODAIS E LOADING ==================== */
        .overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); display: none; justify-content: center; align-items: center; z-index: 100; }
        .modal { background: var(--card-bg); padding: 25px; border-radius: 20px; width: 90%; max-width: 400px; text-align: center; }
        
        #loading { display: flex; flex-direction: column; background: var(--bg); }
        .loader { border: 5px solid #f3f3f3; border-top: 5px solid var(--primary); border-radius: 50%; width: 50px; height: 50px; animation: spin 1s linear infinite; margin-bottom: 20px; }

        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

        /* Utilitários */
        .text-center { text-align: center; }
        .mt-1 { margin-top: 10px; }
        .mt-2 { margin-top: 20px; }
        .flex-between { display: flex; justify-content: space-between; align-items: center; }
        
        /* Menu Lateral (Mais) */
        .more-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
        .more-item { background: var(--card-bg); padding: 20px; border-radius: 15px; text-align: center; cursor: pointer; box-shadow: var(--shadow); }
        .more-item i { font-size: 2rem; display: block; margin-bottom: 10px; }
        
    </style>
</head>
<body>

    <!-- LOADING INICIAL -->
    <div id="loading" class="overlay" style="display: flex; z-index: 999;">
        <div class="loader"></div>
        <h2 style="color: var(--primary-dark)">Carregando amor...</h2>
    </div>

    <!-- TELA DE SETUP (PRIMEIRO ACESSO) -->
    <div id="setup-screen" class="overlay" style="background: var(--bg); z-index: 900;">
        <div style="padding: 30px; text-align: center; width: 100%; max-width: 500px;">
            <h1 style="color: var(--primary-dark); font-size: 2rem; margin-bottom: 10px;">Mamãe do Ano</h1>
            <p style="margin-bottom: 30px;">Bem-vinda, <strong>Vanessa Braga</strong>! ❤️<br>Para começarmos nossa jornada, informe a Data da Última Menstruação (DUM):</p>
            <input type="date" id="setup-dum" style="font-size: 1.2rem; padding: 15px;">
            <button class="btn" onclick="saveSetup()">Começar minha jornada</button>
        </div>
    </div>

    <!-- APLICATIVO PRINCIPAL -->
    <div id="app">
        <!-- HEADER -->
        <header class="header">
            <h1>Mamãe do Ano</h1>
            <div>
                <button class="btn-small btn-outline" style="color: white; border-color: white;" onclick="toggleDarkMode()">🌙</button>
            </div>
        </header>

        <!-- ÁREA DE CONTEÚDO -->
        <div class="content">
            
            <!-- 1. DASHBOARD (INÍCIO) -->
            <div id="screen-home" class="screen active">
                <div class="card text-center" style="background: linear-gradient(135deg, var(--primary), var(--primary-dark)); color: white; border: none;">
                    <h2>Olá, Vanessa Braga! 👑</h2>
                    <p class="mt-1" style="opacity: 0.9">Sua jornada mágica está acontecendo.</p>
                </div>

                <div class="card">
                    <h3 class="text-center">Idade Gestacional</h3>
                    <div class="text-center mt-1" style="font-size: 2.5rem; font-weight: 700; color: var(--primary-dark);" id="dash-age">0 Semanas</div>
                    <p class="text-center" id="dash-days">e 0 dias</p>
                    
                    <div class="progress-container">
                        <div class="progress-bar" id="dash-progress"></div>
                    </div>
                    
                    <div class="flex-between stat-label">
                        <span>Dia 1</span>
                        <span>Semana 40</span>
                    </div>
                </div>

                <div class="grid-2">
                    <div class="stat-box">
                        <div class="stat-label">Trimestre Atual</div>
                        <div class="stat-value" id="dash-trimester">1º</div>
                    </div>
                    <div class="stat-box">
                        <div class="stat-label">Dias para o Parto</div>
                        <div class="stat-value" id="dash-countdown">280</div>
                    </div>
                </div>

                <div class="card mt-2 text-center">
                    <h4>Data Prevista do Parto</h4>
                    <p style="font-size: 1.2rem; font-weight: bold; color: var(--secondary); margin-top: 5px;" id="dash-duedate">--/--/----</p>
                </div>
            </div>

            <!-- 2. DIÁRIO EMOCIONAL -->
            <div id="screen-diary" class="screen">
                <h2 style="margin-bottom: 15px;">Diário da Gestação 📖</h2>
                <div class="card">
                    <h3>Como você está hoje?</h3>
                    <select id="diary-emotion" class="mt-1">
                        <option value="Feliz 😊">Feliz 😊</option>
                        <option value="Ansiosa 😬">Ansiosa 😬</option>
                        <option value="Cansada 🥱">Cansada 🥱</option>
                        <option value="Sensível 🥺">Sensível 🥺</option>
                        <option value="Radiante ✨">Radiante ✨</option>
                        <option value="Enjoada 🤢">Enjoada 🤢</option>
                    </select>
                    <textarea id="diary-text" rows="4" placeholder="Escreva sobre suas experiências, pensamentos ou o que sentiu hoje..."></textarea>
                    <button class="btn" onclick="saveDiaryEntry()">Salvar no Diário</button>
                </div>
                <div id="diary-history">
                    <!-- Histórico gerado via JS -->
                </div>
            </div>

            <!-- 3. CONTROLE INTELIGENTE -->
            <div id="screen-track" class="screen">
                <h2 style="margin-bottom: 15px;">Controle Diário 💧</h2>
                
                <div class="card text-center">
                    <h3>Água (Hoje)</h3>
                    <p class="stat-label mt-1">A meta é manter-se hidratada!</p>
                    <div style="font-size: 3rem; margin: 10px 0;" id="water-count">0</div>
                    <p>Copos consumidos</p>
                    <button class="btn mt-1" onclick="addWater()">+ 1 Copo de Água 🚰</button>
                </div>

                <div class="card text-center">
                    <h3>Sono (Última Noite)</h3>
                    <input type="number" id="sleep-hours" placeholder="Quantas horas você dormiu?" min="0" max="24" class="mt-1">
                    <button class="btn" onclick="saveSleep()">Registrar Sono 🛌</button>
                    <p class="mt-1 stat-label" id="sleep-last">Último registro: Nenhum</p>
                </div>

                <div class="card">
                    <h3>Status dos Alertas 🔔</h3>
                    <ul style="list-style: none; margin-top: 10px;">
                        <li style="margin-bottom: 5px;">💧 Água: A cada 2h (06h-22h)</li>
                        <li style="margin-bottom: 5px;">💊 Vitamina: Todo dia às 09:00</li>
                        <li>🛌 Sono: Lembrete diário</li>
                    </ul>
                    <p class="stat-label mt-1">*Mantenha o app aberto para receber os alertas na tela.</p>
                </div>
            </div>

            <!-- 4. MENU MAIS (OUTRAS FUNÇÕES) -->
            <div id="screen-more" class="screen">
                <h2 style="margin-bottom: 15px;">Mais Funcionalidades ✨</h2>
                <div class="more-grid">
                    <div class="more-item" onclick="navTo('screen-weekly')">
                        <i>👶</i>
                        <span>Acompanhamento</span>
                    </div>
                    <div class="more-item" onclick="navTo('screen-agenda')">
                        <i>📅</i>
                        <span>Agenda</span>
                    </div>
                    <div class="more-item" onclick="navTo('screen-health')">
                        <i>🥗</i>
                        <span>Saúde</span>
                    </div>
                    <div class="more-item" onclick="navTo('screen-daddy')">
                        <i>👨‍👩‍👧</i>
                        <span>Modo Papai</span>
                    </div>
                    <div class="more-item" onclick="navTo('screen-game')">
                        <i>🎮</i>
                        <span>Mini Jogo</span>
                    </div>
                    <div class="more-item" onclick="navTo('screen-reports')">
                        <i>📊</i>
                        <span>Relatórios</span>
                    </div>
                </div>

                <div class="card mt-2 text-center" style="border-top-color: var(--secondary);">
                    <h3>Chegou o grande dia?</h3>
                    <p class="stat-label mt-1">Gere seu certificado de honra!</p>
                    <button class="btn mt-1" style="background: var(--secondary);" onclick="navTo('screen-birth')">Nascimento do Bebê 🏆</button>
                </div>

                <div class="text-center mt-2">
                    <button class="btn-small btn-outline" style="border-color: var(--danger); color: var(--danger);" onclick="resetData()">⚙️ Resetar App</button>
                </div>
            </div>

            <!-- TELAS SECUNDÁRIAS (Acessadas via "Mais") -->

            <!-- Acompanhamento Semanal -->
            <div id="screen-weekly" class="screen">
                <button class="btn-small mb-1" onclick="navTo('screen-more')">⬅ Voltar</button>
                <h2 style="margin: 15px 0;">Seu Bebê Esta Semana 👶</h2>
                <div class="card text-center">
                    <div style="font-size: 4rem;" id="week-fruit-icon">🍉</div>
                    <h3 id="week-fruit-name">Carregando...</h3>
                    <p class="mt-1" id="week-desc" style="text-align: justify;">...</p>
                </div>
                <div class="card">
                    <h3>Sintomas Comuns</h3>
                    <p id="week-symptoms" class="mt-1 text-light">...</p>
                </div>
            </div>

            <!-- Agenda -->
            <div id="screen-agenda" class="screen">
                <button class="btn-small mb-1" onclick="navTo('screen-more')">⬅ Voltar</button>
                <h2 style="margin: 15px 0;">Agenda e Exames 📅</h2>
                <div class="card">
                    <input type="text" id="agenda-title" placeholder="Nome da consulta/exame">
                    <input type="datetime-local" id="agenda-date">
                    <button class="btn" onclick="addAgenda()">Adicionar</button>
                </div>
                <div id="agenda-list"></div>
            </div>

            <!-- Saúde -->
            <div id="screen-health" class="screen">
                <button class="btn-small mb-1" onclick="navTo('screen-more')">⬅ Voltar</button>
                <h2 style="margin: 15px 0;">Saúde e Bem-estar 🥗</h2>
                <div class="card">
                    <h3 style="color: var(--success);">✅ Recomendados</h3>
                    <ul style="margin-left: 20px; margin-top: 10px;">
                        <li>Ácido fólico (espinafre, feijão, lentilha)</li>
                        <li>Ferro (carnes magras, folhas escuras)</li>
                        <li>Cálcio (leite, iogurte, queijos)</li>
                        <li>Frutas e vegetais frescos</li>
                        <li>Muita água!</li>
                    </ul>
                </div>
                <div class="card">
                    <h3 style="color: var(--danger);">❌ Evitar</h3>
                    <ul style="margin-left: 20px; margin-top: 10px;">
                        <li>Carnes cruas ou mal passadas</li>
                        <li>Ovos crus (maionese caseira)</li>
                        <li>Peixes com alto teor de mercúrio</li>
                        <li>Excesso de cafeína</li>
                        <li>Álcool</li>
                    </ul>
                </div>
                <div class="card">
                    <h3 style="color: var(--primary-dark);">🧘‍♀️ Exercícios Leves</h3>
                    <p class="mt-1">Caminhada, Yoga pré-natal, Natação, Alongamentos. (Sempre consulte seu médico!)</p>
                </div>
            </div>

            <!-- Modo Papai -->
            <div id="screen-daddy" class="screen">
                <button class="btn-small mb-1" onclick="navTo('screen-more')">⬅ Voltar</button>
                <h2 style="margin: 15px 0;">Modo Papai / Parceiro(a) 👨‍👩‍👧</h2>
                <div class="card">
                    <h3>Como ajudar a Vanessa?</h3>
                    <ul style="margin-left: 20px; margin-top: 10px;">
                        <li style="margin-bottom: 10px;"><strong>Compreensão:</strong> Os hormônios estão a mil. Tenha paciência extra e ofereça apoio emocional.</li>
                        <li style="margin-bottom: 10px;"><strong>Tarefas de casa:</strong> Assuma a limpeza pesada, cozinhe ou cuide da louça. Ela precisa descansar!</li>
                        <li style="margin-bottom: 10px;"><strong>Massagens:</strong> As costas e os pés dela agradecem uma massagem no fim do dia.</li>
                        <li style="margin-bottom: 10px;"><strong>Acompanhe:</strong> Vá junto às consultas e ultrassons. É o bebê de vocês!</li>
                        <li><strong>Desejos:</strong> Se ela pedir algo no meio da noite, faça o possível para conseguir (com amor).</li>
                    </ul>
                </div>
            </div>

            <!-- Mini Jogo -->
            <div id="screen-game" class="screen">
                <button class="btn-small mb-1" onclick="navTo('screen-more')">⬅ Voltar</button>
                <h2 style="margin: 15px 0; text-align: center;">Doces Desejos 🎮</h2>
                <p class="text-center stat-label">Combine 3 ou mais frutas iguais para pontuar!</p>
                <div class="text-center mt-1">
                    <span style="font-size: 1.2rem; font-weight: bold;">Pontos: <span id="game-score">0</span></span>
                </div>
                <div id="game-board"></div>
                <div class="text-center">
                    <button class="btn btn-small mt-1" onclick="initGame()">Reiniciar Jogo</button>
                </div>
            </div>

            <!-- Relatórios -->
            <div id="screen-reports" class="screen">
                <button class="btn-small mb-1" onclick="navTo('screen-more')">⬅ Voltar</button>
                <h2 style="margin: 15px 0;">Relatório da Gravidez 📊</h2>
                <div class="card">
                    <h3>Estatísticas</h3>
                    <div class="grid-2 mt-1">
                        <div class="stat-box">
                            <div class="stat-label">Registros no Diário</div>
                            <div class="stat-value" id="rep-diary">0</div>
                        </div>
                        <div class="stat-box">
                            <div class="stat-label">Copos de Água</div>
                            <div class="stat-value" id="rep-water">0</div>
                        </div>
                    </div>
                </div>
                <div class="card">
                    <h3>Emoções Frequentes</h3>
                    <div id="rep-emotions" class="mt-1"></div>
                </div>
            </div>

            <!-- Nascimento (Certificado Form) -->
            <div id="screen-birth" class="screen">
                <button class="btn-small mb-1" onclick="navTo('screen-more')">⬅ Voltar</button>
                <h2 style="margin: 15px 0;">O Bebê Nasceu! 🎉</h2>
                <div class="card">
                    <p>Parabéns, Vanessa! Registre este momento único para gerar seu certificado.</p>
                    <label class="mt-1" style="display:block; font-weight:bold;">Data de Nascimento:</label>
                    <input type="date" id="birth-date" class="mt-1">
                    
                    <label style="display:block; font-weight:bold;">Como foi a gestação? (Breve resumo):</label>
                    <textarea id="birth-text" rows="5" placeholder="Foi uma jornada incrível, cheia de descobertas..."></textarea>
                    
                    <button class="btn mt-1" style="background: var(--secondary);" onclick="generateCertificate()">Gerar Certificado "Super Mãe"</button>
                </div>
            </div>

        </div>

        <!-- BOTTOM NAV -->
        <nav class="bottom-nav">
            <button class="nav-item active" onclick="navTo('screen-home', this)">
                <span class="nav-icon">🏠</span>
                <span>Início</span>
            </button>
            <button class="nav-item" onclick="navTo('screen-diary', this)">
                <span class="nav-icon">📖</span>
                <span>Diário</span>
            </button>
            <button class="nav-item" onclick="navTo('screen-track', this)">
                <span class="nav-icon">💧</span>
                <span>Controle</span>
            </button>
            <button class="nav-item" onclick="navTo('screen-more', this)">
                <span class="nav-icon">✨</span>
                <span>Mais</span>
            </button>
        </nav>
    </div>

    <!-- CERTIFICADO (Para Impressão/Visualização) -->
    <div id="certificate-view">
        <div class="cert-title">Certificado Super Mãe</div>
        <p class="cert-text">Certificamos que</p>
        <div class="cert-name">Vanessa Braga</div>
        <p class="cert-text">concluiu com maestria a mágica jornada da gestação, gerando uma nova vida com todo amor e dedicação do mundo.</p>
        
        <p class="cert-text" style="font-style: italic; margin-top: 30px;" id="cert-user-text">""</p>
        
        <div style="margin-top: 50px; display: flex; justify-content: space-around;">
            <div>
                <p style="font-weight: bold; font-size: 1.2rem;" id="cert-date">--/--/----</p>
                <p style="font-size: 0.9rem;">Data do Nascimento</p>
            </div>
            <div>
                <p style="font-family: 'Great Vibes', cursive; font-size: 2.5rem; color: var(--primary);">Mamãe do Ano</p>
            </div>
        </div>
        
        <div style="margin-top: 50px;" class="no-print">
            <button class="btn" style="width: auto; margin-right: 10px;" onclick="window.print()">🖨️ Imprimir / Salvar PDF</button>
            <button class="btn-outline" style="width: auto; padding: 12px 20px; border-radius: 12px;" onclick="closeCertificate()">Voltar ao App</button>
        </div>
    </div>

    <!-- MODAL DE ALERTA CUSTOMIZADO -->
    <div id="alert-modal" class="overlay">
        <div class="modal">
            <h2 id="alert-title" style="color: var(--primary-dark); margin-bottom: 15px;">Alerta!</h2>
            <p id="alert-msg" style="margin-bottom: 20px; font-size: 1.1rem;"></p>
            <button class="btn" onclick="closeAlert()">Confirmar 👍</button>
        </div>
    </div>

    <!-- ESTILOS EXTRAS PARA IMPRESSÃO -->
    <style>
        @media print {
            body { background: white; }
            #app, #setup-screen, #loading, .overlay { display: none !important; }
            #certificate-view { display: block !important; border: 10px solid #ffb6c1; box-shadow: none; min-height: auto; }
            .no-print { display: none !important; }
        }
    </style>

    <script>
        // ==================== ESTADO DO APP ====================
        let db = {
            dum: null,
            diary: [],
            water: {}, // { "YYYY-MM-DD": count }
            sleep: {},
            agenda: [],
            settings: { darkMode: false }
        };

        const todayDateStr = new Date().toISOString().split('T')[0];

        // ==================== INICIALIZAÇÃO ====================
        window.onload = () => {
            loadData();
            
            setTimeout(() => {
                document.getElementById('loading').style.display = 'none';
                if (!db.dum) {
                    document.getElementById('setup-screen').style.display = 'flex';
                } else {
                    startApp();
                }
            }, 1000);
        };

        function loadData() {
            const stored = localStorage.getItem('mamaeDoAnoDB');
            if (stored) {
                db = JSON.parse(stored);
                // Migrações se necessário no futuro
                if(!db.water) db.water = {};
            }
            applyTheme();
        }

        function saveData() {
            localStorage.setItem('mamaeDoAnoDB', JSON.stringify(db));
        }

        function saveSetup() {
            const dumInput = document.getElementById('setup-dum').value;
            if (!dumInput) {
                showAlert('Aviso', 'Por favor, insira a Data da Última Menstruação.');
                return;
            }
            db.dum = dumInput;
            saveData();
            document.getElementById('setup-screen').style.display = 'none';
            startApp();
        }

        function startApp() {
            calculateDashboard();
            renderDiaryHistory();
            renderTrackers();
            renderAgenda();
            loadWeeklyInfo();
            generateReports();
            setupAlertSystem();
            initGame();
        }

        // ==================== NAVEGAÇÃO ====================
        function navTo(screenId, navElement = null) {
            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            document.getElementById(screenId).classList.add('active');
            
            if (navElement) {
                document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
                navElement.classList.add('active');
            } else {
                // Se navegou pelo menu Mais e não pelos botões de baixo, mantém o "Mais" ativo
                document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
                document.querySelectorAll('.nav-item')[3].classList.add('active');
            }

            // Atualiza relatórios se for a tela de relatórios
            if(screenId === 'screen-reports') generateReports();
        }

        function toggleDarkMode() {
            db.settings.darkMode = !db.settings.darkMode;
            applyTheme();
            saveData();
        }

        function applyTheme() {
            if (db.settings.darkMode) {
                document.body.classList.add('dark-mode');
            } else {
                document.body.classList.remove('dark-mode');
            }
        }

        function resetData() {
            if (confirm("Tem certeza que deseja apagar todos os dados? Isso não pode ser desfeito.")) {
                localStorage.removeItem('mamaeDoAnoDB');
                location.reload();
            }
        }

        // ==================== CÁLCULOS PRINCIPAIS ====================
        function calculateDashboard() {
            if (!db.dum) return;
            
            const dumDate = new Date(db.dum + "T00:00:00");
            const today = new Date();
            today.setHours(0,0,0,0);
            
            // Diferença em ms
            const diffTime = today - dumDate;
            const diffDays = Math.floor(diffTime / (1000 * 60 * 60 * 24));
            
            let weeks = Math.floor(diffDays / 7);
            let days = diffDays % 7;
            
            // Limites (gestação não passa muito de 42)
            if (weeks < 0) { weeks = 0; days = 0; }
            if (weeks > 42) { weeks = 42; days = 0; }

            // Trimestre
            let trimestre = "1º";
            if (weeks >= 14 && weeks <= 27) trimestre = "2º";
            else if (weeks >= 28) trimestre = "3º";

            // Data prevista (DUM + 280 dias)
            const dueDate = new Date(dumDate);
            dueDate.setDate(dueDate.getDate() + 280);
            
            // Dias restantes
            let countdown = 280 - diffDays;
            if (countdown < 0) countdown = 0;

            // Progresso (Max 280 dias = 100%)
            let progress = (diffDays / 280) * 100;
            if (progress > 100) progress = 100;
            if (progress < 0) progress = 0;

            // Atualizar DOM
            document.getElementById('dash-age').innerText = `${weeks} Semanas`;
            document.getElementById('dash-days').innerText = `e ${days} dias`;
            document.getElementById('dash-trimester').innerText = trimestre;
            document.getElementById('dash-countdown').innerText = countdown;
            document.getElementById('dash-duedate').innerText = dueDate.toLocaleDateString('pt-BR');
            
            // Animação da barra
            setTimeout(() => {
                document.getElementById('dash-progress').style.width = `${progress}%`;
            }, 500);

            // Salvar semanas globalmente para o card semanal
            window.currentGestationalWeek = weeks;
        }

        // ==================== DIÁRIO ====================
        function saveDiaryEntry() {
            const emotion = document.getElementById('diary-emotion').value;
            const text = document.getElementById('diary-text').value;
            
            if (!text.trim()) {
                showAlert("Ops!", "Escreva algo antes de salvar.");
                return;
            }

            const entry = {
                id: Date.now(),
                date: new Date().toLocaleString('pt-BR'),
                emotion: emotion,
                text: text
            };

            db.diary.unshift(entry); // Adiciona no início
            saveData();
            
            document.getElementById('diary-text').value = '';
            renderDiaryHistory();
            showAlert("Sucesso", "Registro salvo no seu diário com carinho! 💖");
        }

        function renderDiaryHistory() {
            const container = document.getElementById('diary-history');
            container.innerHTML = '';
            
            if (db.diary.length === 0) {
                container.innerHTML = '<p class="text-center text-light mt-2">Nenhum registro ainda. Comece a escrever!</p>';
                return;
            }

            db.diary.forEach(entry => {
                const div = document.createElement('div');
                div.className = 'card';
                div.style.borderTop = 'none';
                div.style.borderLeft = '4px solid var(--primary)';
                div.innerHTML = `
                    <div class="flex-between stat-label">
                        <span>${entry.date}</span>
                        <span style="font-size: 1.2rem;">${entry.emotion}</span>
                    </div>
                    <p class="mt-1">${entry.text}</p>
                    <div class="text-right mt-1">
                        <button class="btn-small btn-outline" style="border-color: #ff6b6b; color: #ff6b6b; padding: 2px 8px;" onclick="deleteDiary(${entry.id})">Apagar</button>
                    </div>
                `;
                container.appendChild(div);
            });
        }

        function deleteDiary(id) {
            if (confirm("Deseja apagar este registro?")) {
                db.diary = db.diary.filter(e => e.id !== id);
                saveData();
                renderDiaryHistory();
            }
        }

        // ==================== CONTROLE INTELIGENTE ====================
        function renderTrackers() {
            // Água
            const waterToday = db.water[todayDateStr] || 0;
            document.getElementById('water-count').innerText = waterToday;

            // Sono
            const lastSleepKey = Object.keys(db.sleep).sort().pop();
            if (lastSleepKey) {
                document.getElementById('sleep-last').innerText = `Último registro: ${db.sleep[lastSleepKey]}h em ${lastSleepKey.split('-').reverse().join('/')}`;
            }
        }

        function addWater() {
            let count = db.water[todayDateStr] || 0;
            count++;
            db.water[todayDateStr] = count;
            saveData();
            renderTrackers();
        }

        function saveSleep() {
            const hours = document.getElementById('sleep-hours').value;
            if (!hours || hours < 0 || hours > 24) {
                showAlert("Aviso", "Insira uma quantidade válida de horas.");
                return;
            }
            db.sleep[todayDateStr] = hours;
            saveData();
            document.getElementById('sleep-hours').value = '';
            renderTrackers();
            showAlert("Registrado!", "Horas de sono salvas. O descanso é fundamental! 🛌");
        }

        // ==================== AGENDA ====================
        function addAgenda() {
            const title = document.getElementById('agenda-title').value;
            const date = document.getElementById('agenda-date').value;

            if (!title || !date) {
                showAlert("Aviso", "Preencha o nome e a data.");
                return;
            }

            db.agenda.push({
                id: Date.now(),
                title: title,
                date: new Date(date).toLocaleString('pt-BR', { dateStyle: 'short', timeStyle: 'short' }),
                timestamp: new Date(date).getTime(),
                done: false
            });

            // Ordena pela data
            db.agenda.sort((a, b) => a.timestamp - b.timestamp);
            
            saveData();
            document.getElementById('agenda-title').value = '';
            document.getElementById('agenda-date').value = '';
            renderAgenda();
        }

        function renderAgenda() {
            const container = document.getElementById('agenda-list');
            container.innerHTML = '';
            
            if (db.agenda.length === 0) {
                container.innerHTML = '<p class="text-center text-light">Nenhum compromisso agendado.</p>';
                return;
            }

            db.agenda.forEach(item => {
                const div = document.createElement('div');
                div.className = 'list-item';
                if (item.done) div.style.opacity = '0.5';
                
                div.innerHTML = `
                    <div>
                        <strong style="text-decoration: ${item.done ? 'line-through' : 'none'}">${item.title}</strong>
                        <div class="stat-label">${item.date}</div>
                    </div>
                    <div>
                        <button class="btn-small" style="background: ${item.done ? 'var(--text-light)' : 'var(--success)'}" onclick="toggleAgenda(${item.id})">
                            ${item.done ? 'Desfazer' : 'Concluir'}
                        </button>
                        <button class="btn-small" style="background: var(--danger); margin-left: 5px;" onclick="deleteAgenda(${item.id})">X</button>
                    </div>
                `;
                container.appendChild(div);
            });
        }

        function toggleAgenda(id) {
            const item = db.agenda.find(i => i.id === id);
            if (item) { item.done = !item.done; saveData(); renderAgenda(); }
        }

        function deleteAgenda(id) {
            db.agenda = db.agenda.filter(i => i.id !== id);
            saveData();
            renderAgenda();
        }

        // ==================== INFO SEMANAL ====================
        const weeklyData = [
            { week: 0, fruit: "✨", name: "Uma faísca", desc: "A jornada está apenas começando.", sym: "Ausentes" },
            { week: 4, fruit: "⚫", name: "Semente de Papoula", desc: "O embrião é minúsculo, mas o coração já começa a se formar.", sym: "Atraso menstrual, seios sensíveis, leve cólica." },
            { week: 8, fruit: "🍓", name: "Framboesa", desc: "Dedinhos das mãos e pés estão se formando.", sym: "Enjoos matinais, fadiga, vontade frequente de urinar." },
            { week: 12, fruit: "🍑", name: "Ameixa", desc: "Todos os órgãos vitais estão formados. O risco de aborto diminui bastante.", sym: "Os enjoos podem começar a diminuir. Apetite pode aumentar." },
            { week: 16, fruit: "🥑", name: "Abacate", desc: "O bebê já pode ouvir sua voz! O coração bate forte.", sym: "Cabelos e unhas mais fortes, leve dor nas costas." },
            { week: 20, fruit: "🍌", name: "Banana", desc: "Metade do caminho! Você já deve sentir os chutes.", sym: "Azia, câimbras nas pernas, aumento de energia." },
            { week: 24, fruit: "🌽", name: "Espiga de Milho", desc: "O rosto do bebê já está praticamente formado.", sym: "Inchaço nos pés e tornozelos, estrias podem aparecer." },
            { week: 28, fruit: "🍆", name: "Berinjela", desc: "Entrando no 3º trimestre. O bebê abre os olhos e sonha.", sym: "Falta de ar, dificuldade para dormir, contrações de treinamento (Braxton Hicks)." },
            { week: 32, fruit: "🎃", name: "Abóbora Menina", desc: "Preparando-se para o nascimento. Ele ganha peso rápido.", sym: "Azia intensa, vontade frequente de urinar, dores na pelve." },
            { week: 36, fruit: "🍈", name: "Melão", desc: "Quase lá! O bebê já está encaixando na bacia.", sym: "Pressão na bexiga, instinto de 'fazer o ninho'." },
            { week: 40, fruit: "🍉", name: "Melancia", desc: "Pronto para nascer a qualquer momento!", sym: "Ansiedade, contrações reais, perda do tampão mucoso." }
        ];

        function loadWeeklyInfo() {
            let week = window.currentGestationalWeek || 0;
            // Encontrar o dado mais próximo
            let data = weeklyData[0];
            for (let i = weeklyData.length - 1; i >= 0; i--) {
                if (week >= weeklyData[i].week) {
                    data = weeklyData[i];
                    break;
                }
            }

            document.getElementById('week-fruit-icon').innerText = data.fruit;
            document.getElementById('week-fruit-name').innerText = `Tamanho: ${data.name}`;
            document.getElementById('week-desc').innerText = `Semana ${week}: ${data.desc}`;
            document.getElementById('week-symptoms').innerText = data.sym;
        }

        // ==================== RELATÓRIOS ====================
        function generateReports() {
            document.getElementById('rep-diary').innerText = db.diary.length;
            
            let totalWater = 0;
            for(let date in db.water) totalWater += db.water[date];
            document.getElementById('rep-water').innerText = totalWater;

            // Emoções
            const emotionsCount = {};
            db.diary.forEach(e => {
                emotionsCount[e.emotion] = (emotionsCount[e.emotion] || 0) + 1;
            });

            const emoContainer = document.getElementById('rep-emotions');
            emoContainer.innerHTML = '';
            
            if (Object.keys(emotionsCount).length === 0) {
                emoContainer.innerHTML = '<p class="stat-label">Sem dados ainda.</p>';
            } else {
                for(let emo in emotionsCount) {
                    emoContainer.innerHTML += `
                        <div class="list-item" style="padding: 10px;">
                            <span>${emo}</span>
                            <strong>${emotionsCount[emo]}x</strong>
                        </div>
                    `;
                }
            }
        }

        // ==================== ALERTAS ====================
        let alertInterval;
        function setupAlertSystem() {
            if (alertInterval) clearInterval(alertInterval);
            
            alertInterval = setInterval(() => {
                const now = new Date();
                const h = now.getHours();
                const m = now.getMinutes();
                const dateStr = now.toISOString().split('T')[0];
                
                // Simulação de controle interno para não repetir o alerta no mesmo minuto/condição
                if (!db._alerts) db._alerts = {};

                // ALERTA DE ÁGUA: A cada 2 horas entre 6h e 22h
                if (h >= 6 && h <= 22 && h % 2 === 0 && m === 0) {
                    const alertKey = `water-${dateStr}-${h}`;
                    if (!db._alerts[alertKey]) {
                        showAlert("Hora de Hidratar! 💧", "Vanessa, já bebeu água nessas últimas 2 horas? Vai lá, seu bebê agradece!");
                        db._alerts[alertKey] = true;
                        saveData();
                    }
                }

                // ALERTA DE VITAMINA: Todo dia às 9:00
                if (h === 9 && m === 0) {
                    const alertKey = `vit-${dateStr}`;
                    if (!db._alerts[alertKey]) {
                        showAlert("Vitaminas! 💊", "Não esqueça de tomar suas vitaminas hoje. Elas são essenciais!");
                        db._alerts[alertKey] = true;
                        saveData();
                    }
                }

                // ALERTA DE SONO: Todo dia às 8:00
                if (h === 8 && m === 0) {
                    const alertKey = `sleep-${dateStr}`;
                    if (!db._alerts[alertKey]) {
                        showAlert("Bom dia! ☀️", "Como você dormiu esta noite? Não esqueça de registrar no Controle Diário.");
                        db._alerts[alertKey] = true;
                        saveData();
                    }
                }

            }, 60000); // Verifica a cada 1 minuto
        }

        function showAlert(title, msg) {
            document.getElementById('alert-title').innerText = title;
            document.getElementById('alert-msg').innerText = msg;
            document.getElementById('alert-modal').style.display = 'flex';
            
            // Tenta usar a API nativa também se permitido (só funciona se a aba estiver em background/minimamente ativa)
            if (Notification.permission === "granted") {
                new Notification(title, { body: msg, icon: "👶" });
            } else if (Notification.permission !== "denied") {
                Notification.requestPermission();
            }
        }

        function closeAlert() {
            document.getElementById('alert-modal').style.display = 'none';
        }

        // ==================== CERTIFICADO ====================
        function generateCertificate() {
            const bDate = document.getElementById('birth-date').value;
            const bText = document.getElementById('birth-text').value;

            if (!bDate) {
                showAlert("Aviso", "Por favor, insira a data do nascimento.");
                return;
            }

            // Popula certificado
            const formattedDate = new Date(bDate).toLocaleDateString('pt-BR');
            document.getElementById('cert-date').innerText = formattedDate;
            document.getElementById('cert-user-text').innerText = bText ? `"${bText}"` : '"Uma jornada de amor e transformação."';

            // Mostra certificado, esconde app
            document.getElementById('app').style.display = 'none';
            document.getElementById('certificate-view').style.display = 'block';
            window.scrollTo(0,0);
        }

        function closeCertificate() {
            document.getElementById('app').style.display = 'flex';
            document.getElementById('certificate-view').style.display = 'none';
        }

        // ==================== MINI JOGO (Combinação) ====================
        const gameFruits = ['🍎', '🍇', '🍌', '🍉', '🫐'];
        let grid = [];
        const rows = 6;
        const cols = 6;
        let selectedCandy = null;
        let score = 0;

        function initGame() {
            score = 0;
            document.getElementById('game-score').innerText = score;
            const board = document.getElementById('game-board');
            board.innerHTML = '';
            grid = [];

            for (let r = 0; r < rows; r++) {
                let rowArray = [];
                for (let c = 0; c < cols; c++) {
                    const candy = document.createElement('div');
                    candy.className = 'candy';
                    candy.dataset.r = r;
                    candy.dataset.c = c;
                    
                    // Evitar matchs na geração
                    let randomFruit;
                    do {
                        randomFruit = gameFruits[Math.floor(Math.random() * gameFruits.length)];
                    } while (
                        (r >= 2 && grid[r-1][c] === randomFruit && grid[r-2][c] === randomFruit) ||
                        (c >= 2 && rowArray[c-1] === randomFruit && rowArray[c-2] === randomFruit)
                    );

                    candy.innerText = randomFruit;
                    candy.onclick = handleCandyClick;
                    board.appendChild(candy);
                    rowArray.push(randomFruit);
                }
                grid.push(rowArray);
            }
        }

        function handleCandyClick(e) {
            const clicked = e.target;
            const r = parseInt(clicked.dataset.r);
            const c = parseInt(clicked.dataset.c);

            if (!selectedCandy) {
                selectedCandy = clicked;
                clicked.classList.add('selected');
            } else {
                const sr = parseInt(selectedCandy.dataset.r);
                const sc = parseInt(selectedCandy.dataset.c);
                selectedCandy.classList.remove('selected');

                // Verifica se é adjacente
                const isAdjacent = (Math.abs(r - sr) === 1 && c === sc) || (Math.abs(c - sc) === 1 && r === sr);

                if (isAdjacent) {
                    // Troca visual e na matriz
                    const temp = grid[r][c];
                    grid[r][c] = grid[sr][sc];
                    grid[sr][sc] = temp;

                    updateBoardVisuals();

                    // Verifica Match
                    if (!checkMatch()) {
                        // Desfaz troca se não houver match
                        setTimeout(() => {
                            const temp = grid[r][c];
                            grid[r][c] = grid[sr][sc];
                            grid[sr][sc] = temp;
                            updateBoardVisuals();
                        }, 300);
                    }
                }
                selectedCandy = null;
            }
        }

        function updateBoardVisuals() {
            const board = document.getElementById('game-board');
            let idx = 0;
            for (let r = 0; r < rows; r++) {
                for (let c = 0; c < cols; c++) {
                    board.children[idx].innerText = grid[r][c];
                    idx++;
                }
            }
        }

        function checkMatch() {
            let matched = false;
            let toClear = Array.from({length: rows}, () => Array(cols).fill(false));

            // Horizontal
            for (let r = 0; r < rows; r++) {
                for (let c = 0; c < cols - 2; c++) {
                    let f = grid[r][c];
                    if (f !== '' && f === grid[r][c+1] && f === grid[r][c+2]) {
                        toClear[r][c] = toClear[r][c+1] = toClear[r][c+2] = true;
                        matched = true;
                    }
                }
            }
            // Vertical
            for (let c = 0; c < cols; c++) {
                for (let r = 0; r < rows - 2; r++) {
                    let f = grid[r][c];
                    if (f !== '' && f === grid[r+1][c] && f === grid[r+2][c]) {
                        toClear[r][c] = toClear[r+1][c] = toClear[r+2][c] = true;
                        matched = true;
                    }
                }
            }

            if (matched) {
                let matchCount = 0;
                for (let r = 0; r < rows; r++) {
                    for (let c = 0; c < cols; c++) {
                        if (toClear[r][c]) {
                            grid[r][c] = '';
                            matchCount++;
                        }
                    }
                }
                score += matchCount * 10;
                document.getElementById('game-score').innerText = score;
                updateBoardVisuals();

                setTimeout(dropCandies, 300);
                return true;
            }
            return false;
        }

        function dropCandies() {
            for (let c = 0; c < cols; c++) {
                let emptySpaces = 0;
                for (let r = rows - 1; r >= 0; r--) {
                    if (grid[r][c] === '') {
                        emptySpaces++;
                    } else if (emptySpaces > 0) {
                        grid[r + emptySpaces][c] = grid[r][c];
                        grid[r][c] = '';
                    }
                }
                // Preenche o topo
                for (let r = 0; r < emptySpaces; r++) {
                    grid[r][c] = gameFruits[Math.floor(Math.random() * gameFruits.length)];
                }
            }
            updateBoardVisuals();
            setTimeout(() => {
                checkMatch(); // Recursão em caso de combos
            }, 300);
        }

    </script>
</body>
</html>

