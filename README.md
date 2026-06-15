<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Piano Learning - Sistema de Ensino</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); min-height: 100vh; padding: 20px; }
        .container { max-width: 1200px; margin: 0 auto; }
        .header { background: white; border-radius: 16px; padding: 32px; margin-bottom: 24px; box-shadow: 0 4px 24px rgba(0,0,0,0.1); }
        .header h1 { font-size: 36px; color: #1a202c; margin-bottom: 8px; }
        .header p { color: #718096; font-size: 16px; }
        .stats { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 16px; margin-bottom: 24px; }
        .stat-card { background: white; border-radius: 12px; padding: 24px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
        .stat-card h3 { font-size: 14px; color: #718096; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 8px; }
        .stat-card .number { font-size: 32px; font-weight: 700; color: #667eea; }
        .tabs { background: white; border-radius: 16px; padding: 24px; box-shadow: 0 4px 24px rgba(0,0,0,0.1); }
        .tab-buttons { display: flex; gap: 8px; margin-bottom: 24px; border-bottom: 2px solid #e2e8f0; padding-bottom: 16px; }
        .tab-button { padding: 12px 24px; border: none; background: transparent; color: #718096; font-size: 16px; font-weight: 500; cursor: pointer; border-radius: 8px; transition: all 0.2s; }
        .tab-button:hover { background: #f7fafc; }
        .tab-button.active { background: #667eea; color: white; }
        .tab-content { display: none; }
        .tab-content.active { display: block; }
        .search-box { width: 100%; padding: 12px 16px; border: 2px solid #e2e8f0; border-radius: 8px; font-size: 16px; margin-bottom: 24px; }
        .search-box:focus { outline: none; border-color: #667eea; }
        .grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 16px; }
        .card { background: #f7fafc; border-radius: 12px; padding: 20px; border-left: 4px solid #667eea; transition: transform 0.2s, box-shadow 0.2s; }
        .card:hover { transform: translateY(-2px); box-shadow: 0 4px 12px rgba(102, 126, 234, 0.2); }
        .card h4 { font-size: 18px; color: #1a202c; margin-bottom: 12px; }
        .badge { display: inline-block; padding: 4px 12px; border-radius: 16px; font-size: 12px; font-weight: 600; margin-right: 8px; margin-bottom: 8px; }
        .badge-beginner { background: #c6f6d5; color: #22543d; }
        .badge-intermediate { background: #fed7d7; color: #742a2a; }
        .badge-advanced { background: #feebc8; color: #7c2d12; }
        .badge-theory { background: #e9d8fd; color: #44337a; }
        .badge-video { background: #bee3f8; color: #2c5282; }
        .badge-practice { background: #fbd38d; color: #7c2d12; }
        .footer { text-align: center; margin-top: 32px; color: white; font-size: 14px; }
        .empty-state { text-align: center; padding: 48px; color: #718096; }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🎹 Piano Learning</h1>
            <p>Sistema Completo de Ensino Musical</p>
        </div>

        <div class="stats">
            <div class="stat-card">
                <h3>Total de Lições</h3>
                <div class="number">100</div>
            </div>
            <div class="stat-card">
                <h3>Exercícios</h3>
                <div class="number">100</div>
            </div>
            <div class="stat-card">
                <h3>Alunos</h3>
                <div class="number">5</div>
            </div>
        </div>

        <div class="tabs">
            <div class="tab-buttons">
                <button class="tab-button active" onclick="switchTab('lessons')">Lições</button>
                <button class="tab-button" onclick="switchTab('exercises')">Exercícios</button>
                <button class="tab-button" onclick="switchTab('students')">Alunos</button>
            </div>

            <div id="lessons-tab" class="tab-content active">
                <input type="text" class="search-box" placeholder="🔍 Buscar lições..." onkeyup="filterLessons(this.value)">
                <div class="grid" id="lessons-grid">
                    
                        <div class="card lesson-card" data-name="keyboard layout and finger numbers" data-level="Beginner" data-topic="Technique">
                            <h4>Keyboard Layout and Finger Numbers</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Técnica
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="chord inversions across the keyboard" data-level="Advanced" data-topic="Chords">
                            <h4>Chord Inversions Across the Keyboard</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="c major five-finger pattern practice" data-level="Beginner" data-topic="Scales">
                            <h4>C Major Five-Finger Pattern Practice</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="reading notes on the treble staff" data-level="Beginner" data-topic="Notes">
                            <h4>Reading Notes on the Treble Staff</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Notas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="two-octave major scale technique" data-level="Advanced" data-topic="Scales">
                            <h4>Two-Octave Major Scale Technique</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="building major and minor triads" data-level="Intermediate" data-topic="Chords">
                            <h4>Building Major and Minor Triads</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="quarter notes, half notes, and whole notes" data-level="Beginner" data-topic="Rhythm">
                            <h4>Quarter Notes, Half Notes, and Whole Notes</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="hands-together syncopation patterns" data-level="Intermediate" data-topic="Rhythm">
                            <h4>Hands-Together Syncopation Patterns</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="conheça as teclas brancas do piano" data-level="Beginner" data-topic="Notes">
                            <h4>Conheça as Teclas Brancas do Piano</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Notas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="identificando as notas dó, ré e mi" data-level="Beginner" data-topic="Notes">
                            <h4>Identificando as Notas Dó, Ré e Mi</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Notas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="identificando as notas fá, sol, lá e si" data-level="Beginner" data-topic="Notes">
                            <h4>Identificando as Notas Fá, Sol, Lá e Si</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Notas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="as teclas pretas: sustenidos e bemóis" data-level="Beginner" data-topic="Notes">
                            <h4>As Teclas Pretas: Sustenidos e Bemóis</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Notas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="lendo notas na pauta musical" data-level="Beginner" data-topic="Notes">
                            <h4>Lendo Notas na Pauta Musical</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Notas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="clave de sol: linhas e espaços" data-level="Beginner" data-topic="Notes">
                            <h4>Clave de Sol: Linhas e Espaços</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Notas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="clave de fá: linhas e espaços" data-level="Beginner" data-topic="Notes">
                            <h4>Clave de Fá: Linhas e Espaços</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Notas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="praticando notas na mão direita" data-level="Beginner" data-topic="Notes">
                            <h4>Praticando Notas na Mão Direita</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Notas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="praticando notas na mão esquerda" data-level="Beginner" data-topic="Notes">
                            <h4>Praticando Notas na Mão Esquerda</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Notas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="alterações: sustenido, bemol e bequadro" data-level="Beginner" data-topic="Notes">
                            <h4>Alterações: Sustenido, Bemol e Bequadro</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Notas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="o que é tempo musical?" data-level="Beginner" data-topic="Rhythm">
                            <h4>O que é Tempo Musical?</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="semibreve: a nota mais longa" data-level="Beginner" data-topic="Rhythm">
                            <h4>Semibreve: A Nota Mais Longa</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="mínima: dois tempos" data-level="Beginner" data-topic="Rhythm">
                            <h4>Mínima: Dois Tempos</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="semínima: um tempo" data-level="Beginner" data-topic="Rhythm">
                            <h4>Semínima: Um Tempo</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="colcheia: meio tempo" data-level="Beginner" data-topic="Rhythm">
                            <h4>Colcheia: Meio Tempo</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="pausas musicais: silêncio na música" data-level="Beginner" data-topic="Rhythm">
                            <h4>Pausas Musicais: Silêncio na Música</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="compasso 4/4: o mais comum" data-level="Beginner" data-topic="Rhythm">
                            <h4>Compasso 4/4: O Mais Comum</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="compasso 3/4: a valsa" data-level="Beginner" data-topic="Rhythm">
                            <h4>Compasso 3/4: A Valsa</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="compasso 2/4: marcha" data-level="Beginner" data-topic="Rhythm">
                            <h4>Compasso 2/4: Marcha</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="lendo ritmos simples" data-level="Beginner" data-topic="Rhythm">
                            <h4>Lendo Ritmos Simples</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="contando tempos enquanto toca" data-level="Beginner" data-topic="Rhythm">
                            <h4>Contando Tempos Enquanto Toca</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="ponto de aumento: aumentando a duração" data-level="Beginner" data-topic="Rhythm">
                            <h4>Ponto de Aumento: Aumentando a Duração</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="ligadura: unindo notas" data-level="Beginner" data-topic="Rhythm">
                            <h4>Ligadura: Unindo Notas</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="praticando ritmos com palmas" data-level="Beginner" data-topic="Rhythm">
                            <h4>Praticando Ritmos com Palmas</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="sincope: o ritmo fora do tempo" data-level="Beginner" data-topic="Rhythm">
                            <h4>Sincope: O Ritmo Fora do Tempo</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="quiálteras: três no tempo de dois" data-level="Beginner" data-topic="Rhythm">
                            <h4>Quiálteras: Três no Tempo de Dois</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="andamento: lento, moderado e rápido" data-level="Beginner" data-topic="Rhythm">
                            <h4>Andamento: Lento, Moderado e Rápido</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="metrônomo: seu melhor amigo" data-level="Beginner" data-topic="Rhythm">
                            <h4>Metrônomo: Seu Melhor Amigo</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="praticando com metrônomo" data-level="Beginner" data-topic="Rhythm">
                            <h4>Praticando com Metrônomo</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acentuação rítmica" data-level="Beginner" data-topic="Rhythm">
                            <h4>Acentuação Rítmica</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Ritmo
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="o que é uma escala musical?" data-level="Intermediate" data-topic="Scales">
                            <h4>O que é uma Escala Musical?</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala de dó maior" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala de Dó Maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala de sol maior" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala de Sol Maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala de ré maior" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala de Ré Maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala de lá maior" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala de Lá Maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala de mi maior" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala de Mi Maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala de si maior" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala de Si Maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala de fá maior" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala de Fá Maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala de si bemol maior" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala de Si Bemol Maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala de mi bemol maior" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala de Mi Bemol Maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala de lá bemol maior" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala de Lá Bemol Maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="tom e semitom: a base das escalas" data-level="Intermediate" data-topic="Scales">
                            <h4>Tom e Semitom: A Base das Escalas</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="fórmula da escala maior" data-level="Intermediate" data-topic="Scales">
                            <h4>Fórmula da Escala Maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="graus da escala: i, ii, iii, iv, v, vi, vii" data-level="Intermediate" data-topic="Scales">
                            <h4>Graus da Escala: I, II, III, IV, V, VI, VII</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala menor natural" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala Menor Natural</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala menor harmônica" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala Menor Harmônica</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala menor melódica" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala Menor Melódica</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala de lá menor" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala de Lá Menor</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala de mi menor" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala de Mi Menor</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="escala de ré menor" data-level="Intermediate" data-topic="Scales">
                            <h4>Escala de Ré Menor</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="círculo das quintas" data-level="Intermediate" data-topic="Scales">
                            <h4>Círculo das Quintas</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="armadura de clave" data-level="Intermediate" data-topic="Scales">
                            <h4>Armadura de Clave</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="tonalidade: maior e menor" data-level="Intermediate" data-topic="Scales">
                            <h4>Tonalidade: Maior e Menor</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="modulação: mudando de tom" data-level="Intermediate" data-topic="Scales">
                            <h4>Modulação: Mudando de Tom</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="tocando escalas com as duas mãos" data-level="Intermediate" data-topic="Scales">
                            <h4>Tocando Escalas com as Duas Mãos</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Escalas
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="o que é um acorde?" data-level="Intermediate" data-topic="Chords">
                            <h4>O que é um Acorde?</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="tríade maior: a base dos acordes" data-level="Intermediate" data-topic="Chords">
                            <h4>Tríade Maior: A Base dos Acordes</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="tríade menor: o acorde melancólico" data-level="Intermediate" data-topic="Chords">
                            <h4>Tríade Menor: O Acorde Melancólico</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde de dó maior (c)" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde de Dó Maior (C)</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde de ré maior (d)" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde de Ré Maior (D)</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde de mi maior (e)" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde de Mi Maior (E)</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde de fá maior (f)" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde de Fá Maior (F)</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde de sol maior (g)" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde de Sol Maior (G)</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde de lá maior (a)" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde de Lá Maior (A)</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde de si maior (b)" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde de Si Maior (B)</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde de lá menor (am)" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde de Lá Menor (Am)</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde de mi menor (em)" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde de Mi Menor (Em)</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde de ré menor (dm)" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde de Ré Menor (Dm)</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="inversões de acordes" data-level="Intermediate" data-topic="Chords">
                            <h4>Inversões de Acordes</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="primeira inversão" data-level="Intermediate" data-topic="Chords">
                            <h4>Primeira Inversão</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="segunda inversão" data-level="Intermediate" data-topic="Chords">
                            <h4>Segunda Inversão</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde diminuto" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde Diminuto</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde aumentado" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde Aumentado</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="progressão de acordes: i-iv-v" data-level="Intermediate" data-topic="Chords">
                            <h4>Progressão de Acordes: I-IV-V</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="progressão de acordes: i-v-vi-iv" data-level="Intermediate" data-topic="Chords">
                            <h4>Progressão de Acordes: I-V-vi-IV</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="cadências: perfeita, plagal, imperfeita" data-level="Intermediate" data-topic="Chords">
                            <h4>Cadências: Perfeita, Plagal, Imperfeita</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acordes com sétima" data-level="Intermediate" data-topic="Chords">
                            <h4>Acordes com Sétima</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde de sétima maior (cmaj7)" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde de Sétima Maior (Cmaj7)</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde de sétima menor (cm7)" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde de Sétima Menor (Cm7)</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acorde de sétima dominante (c7)" data-level="Intermediate" data-topic="Chords">
                            <h4>Acorde de Sétima Dominante (C7)</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="harmonia funcional" data-level="Intermediate" data-topic="Chords">
                            <h4>Harmonia Funcional</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="função tônica, subdominante e dominante" data-level="Intermediate" data-topic="Chords">
                            <h4>Função Tônica, Subdominante e Dominante</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="acompanhamento com acordes" data-level="Intermediate" data-topic="Chords">
                            <h4>Acompanhamento com Acordes</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="arpejo: tocando notas do acorde" data-level="Intermediate" data-topic="Chords">
                            <h4>Arpejo: Tocando Notas do Acorde</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="voicing: distribuição das notas" data-level="Intermediate" data-topic="Chords">
                            <h4>Voicing: Distribuição das Notas</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Acordes
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="postura correta ao piano" data-level="Advanced" data-topic="Technique">
                            <h4>Postura Correta ao Piano</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Técnica
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="posicionamento das mãos" data-level="Advanced" data-topic="Technique">
                            <h4>Posicionamento das Mãos</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Técnica
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="dedilhado eficiente" data-level="Advanced" data-topic="Technique">
                            <h4>Dedilhado Eficiente</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge badge-theory">Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Técnica
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="exercícios de hanon" data-level="Advanced" data-topic="Technique">
                            <h4>Exercícios de Hanon</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Técnica
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="independência dos dedos" data-level="Advanced" data-topic="Technique">
                            <h4>Independência dos Dedos</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge badge-practice">Prática</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Técnica
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="legato: tocar ligado" data-level="Advanced" data-topic="Technique">
                            <h4>Legato: Tocar Ligado</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Técnica
                            </p>
                        </div>
                    
                        <div class="card lesson-card" data-name="staccato: tocar destacado" data-level="Advanced" data-topic="Technique">
                            <h4>Staccato: Tocar Destacado</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge badge-video">Vídeo</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Tópico: Técnica
                            </p>
                        </div>
                    
                </div>
            </div>

            <div id="exercises-tab" class="tab-content">
                <input type="text" class="search-box" placeholder="🔍 Buscar exercícios..." onkeyup="filterExercises(this.value)">
                <div class="grid" id="exercises-grid">
                    
                        <div class="card exercise-card" data-name="triad quality ear training">
                            <h4>Triad Quality Ear Training</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="interval recognition: perfect and major intervals">
                            <h4>Interval Recognition: Perfect and Major Intervals</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="identify white keys on the keyboard">
                            <h4>Identify White Keys on the Keyboard</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="keyboard finger independence exercise">
                            <h4>Keyboard Finger Independence Exercise</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="chord inversion identification quiz">
                            <h4>Chord Inversion Identification Quiz</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="match staff notes to keyboard notes">
                            <h4>Match Staff Notes to Keyboard Notes</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Prática Leitura</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="sight-reading in 4/4 with syncopation">
                            <h4>Sight-Reading in 4/4 with Syncopation</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Prática Leitura</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="major scale pattern drill in c and g">
                            <h4>Major Scale Pattern Drill in C and G</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="identifique todas as teclas dó no teclado">
                            <h4>Identifique todas as teclas Dó no teclado</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a sequência dó-ré-mi 10 vezes">
                            <h4>Toque a sequência Dó-Ré-Mi 10 vezes</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="encontre e toque todas as notas brancas">
                            <h4>Encontre e toque todas as notas brancas</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="quiz: reconheça notas na clave de sol">
                            <h4>Quiz: Reconheça notas na clave de Sol</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="quiz: reconheça notas na clave de fá">
                            <h4>Quiz: Reconheça notas na clave de Fá</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="escreva as notas dó-ré-mi-fá-sol na pauta">
                            <h4>Escreva as notas Dó-Ré-Mi-Fá-Sol na pauta</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Prática Leitura</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="identifique sustenidos e bemóis no teclado">
                            <h4>Identifique sustenidos e bemóis no teclado</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="leia e toque uma melodia simples em dó maior">
                            <h4>Leia e toque uma melodia simples em Dó maior</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Prática Leitura</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="bata palmas seguindo um compasso 4/4">
                            <h4>Bata palmas seguindo um compasso 4/4</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="conte tempos em uma música simples">
                            <h4>Conte tempos em uma música simples</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="quiz: identifique valores de notas">
                            <h4>Quiz: Identifique valores de notas</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque um ritmo de semínimas com metrônomo">
                            <h4>Toque um ritmo de semínimas com metrônomo</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque um ritmo de colcheias com metrônomo">
                            <h4>Toque um ritmo de colcheias com metrônomo</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="reconheça pausas em uma partitura">
                            <h4>Reconheça pausas em uma partitura</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Prática Leitura</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="pratique mudança de compasso 4/4 para 3/4">
                            <h4>Pratique mudança de compasso 4/4 para 3/4</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="identifique sincopes em trechos musicais">
                            <h4>Identifique sincopes em trechos musicais</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a escala de dó maior com mão direita">
                            <h4>Toque a escala de Dó maior com mão direita</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a escala de dó maior com mão esquerda">
                            <h4>Toque a escala de Dó maior com mão esquerda</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a escala de sol maior com duas mãos">
                            <h4>Toque a escala de Sol maior com duas mãos</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="quiz: identifique a tonalidade pela armadura">
                            <h4>Quiz: Identifique a tonalidade pela armadura</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="escreva a escala de ré maior na pauta">
                            <h4>Escreva a escala de Ré maior na pauta</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Prática Leitura</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="reconheça auditivamente escalas maiores e menores">
                            <h4>Reconheça auditivamente escalas maiores e menores</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque todas as escalas maiores em uma oitava">
                            <h4>Toque todas as escalas maiores em uma oitava</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="complete o círculo das quintas">
                            <h4>Complete o círculo das quintas</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="improvise uma melodia em dó maior">
                            <h4>Improvise uma melodia em Dó maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="diferencie escala menor natural e harmônica">
                            <h4>Diferencie escala menor natural e harmônica</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a tríade de dó maior">
                            <h4>Toque a tríade de Dó maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a tríade de lá menor">
                            <h4>Toque a tríade de Lá menor</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="quiz: identifique acordes maiores e menores">
                            <h4>Quiz: Identifique acordes maiores e menores</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="reconheça acordes maiores pelo som">
                            <h4>Reconheça acordes maiores pelo som</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="reconheça acordes menores pelo som">
                            <h4>Reconheça acordes menores pelo som</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a progressão i-iv-v em dó maior">
                            <h4>Toque a progressão I-IV-V em Dó maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a progressão i-v-vi-iv em sol maior">
                            <h4>Toque a progressão I-V-vi-IV em Sol maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="identifique inversões de acordes">
                            <h4>Identifique inversões de acordes</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque arpejo de dó maior em duas oitavas">
                            <h4>Toque arpejo de Dó maior em duas oitavas</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="acompanhe uma melodia com acordes">
                            <h4>Acompanhe uma melodia com acordes</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="reconheça auditivamente acordes com sétima">
                            <h4>Reconheça auditivamente acordes com sétima</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="construa acordes em qualquer tonalidade">
                            <h4>Construa acordes em qualquer tonalidade</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="execute exercício de hanon nº 1">
                            <h4>Execute exercício de Hanon nº 1</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="pratique independência dos dedos 4 e 5">
                            <h4>Pratique independência dos dedos 4 e 5</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque uma passagem com legato perfeito">
                            <h4>Toque uma passagem com legato perfeito</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque uma passagem com staccato preciso">
                            <h4>Toque uma passagem com staccato preciso</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="pratique dinâmica de pp a ff gradualmente">
                            <h4>Pratique dinâmica de pp a ff gradualmente</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="use pedal de sustentação em um trecho">
                            <h4>Use pedal de sustentação em um trecho</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="execute trinados rápidos e precisos">
                            <h4>Execute trinados rápidos e precisos</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque oitavas cromáticas ascendentes">
                            <h4>Toque oitavas cromáticas ascendentes</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="pratique saltos de acordes com precisão">
                            <h4>Pratique saltos de acordes com precisão</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="interprete uma peça com expressão">
                            <h4>Interprete uma peça com expressão</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="quiz: identifique os sete modos gregos">
                            <h4>Quiz: Identifique os sete modos gregos</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque uma progressão no modo dórico">
                            <h4>Toque uma progressão no modo Dórico</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="improvise usando escala pentatônica">
                            <h4>Improvise usando escala pentatônica</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="reconheça modos gregos auditivamente">
                            <h4>Reconheça modos gregos auditivamente</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="analise a harmonia de uma música popular">
                            <h4>Analise a harmonia de uma música popular</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="rearmonize uma progressão simples">
                            <h4>Rearmonize uma progressão simples</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="identifique intervalos de 2ª a 8ª">
                            <h4>Identifique intervalos de 2ª a 8ª</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="construa acordes alterados (9ª, 11ª, 13ª)">
                            <h4>Construa acordes alterados (9ª, 11ª, 13ª)</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="identifique todas as teclas dó no teclado">
                            <h4>Identifique todas as teclas Dó no teclado</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a sequência dó-ré-mi 10 vezes">
                            <h4>Toque a sequência Dó-Ré-Mi 10 vezes</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="encontre e toque todas as notas brancas">
                            <h4>Encontre e toque todas as notas brancas</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="quiz: reconheça notas na clave de sol">
                            <h4>Quiz: Reconheça notas na clave de Sol</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="quiz: reconheça notas na clave de fá">
                            <h4>Quiz: Reconheça notas na clave de Fá</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="escreva as notas dó-ré-mi-fá-sol na pauta">
                            <h4>Escreva as notas Dó-Ré-Mi-Fá-Sol na pauta</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Prática Leitura</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="identifique sustenidos e bemóis no teclado">
                            <h4>Identifique sustenidos e bemóis no teclado</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="leia e toque uma melodia simples em dó maior">
                            <h4>Leia e toque uma melodia simples em Dó maior</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Prática Leitura</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="bata palmas seguindo um compasso 4/4">
                            <h4>Bata palmas seguindo um compasso 4/4</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="conte tempos em uma música simples">
                            <h4>Conte tempos em uma música simples</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="quiz: identifique valores de notas">
                            <h4>Quiz: Identifique valores de notas</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque um ritmo de semínimas com metrônomo">
                            <h4>Toque um ritmo de semínimas com metrônomo</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque um ritmo de colcheias com metrônomo">
                            <h4>Toque um ritmo de colcheias com metrônomo</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="reconheça pausas em uma partitura">
                            <h4>Reconheça pausas em uma partitura</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Prática Leitura</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="pratique mudança de compasso 4/4 para 3/4">
                            <h4>Pratique mudança de compasso 4/4 para 3/4</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="identifique sincopes em trechos musicais">
                            <h4>Identifique sincopes em trechos musicais</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a escala de dó maior com mão direita">
                            <h4>Toque a escala de Dó maior com mão direita</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a escala de dó maior com mão esquerda">
                            <h4>Toque a escala de Dó maior com mão esquerda</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a escala de sol maior com duas mãos">
                            <h4>Toque a escala de Sol maior com duas mãos</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="quiz: identifique a tonalidade pela armadura">
                            <h4>Quiz: Identifique a tonalidade pela armadura</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="escreva a escala de ré maior na pauta">
                            <h4>Escreva a escala de Ré maior na pauta</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Prática Leitura</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="reconheça auditivamente escalas maiores e menores">
                            <h4>Reconheça auditivamente escalas maiores e menores</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque todas as escalas maiores em uma oitava">
                            <h4>Toque todas as escalas maiores em uma oitava</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="complete o círculo das quintas">
                            <h4>Complete o círculo das quintas</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="improvise uma melodia em dó maior">
                            <h4>Improvise uma melodia em Dó maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="diferencie escala menor natural e harmônica">
                            <h4>Diferencie escala menor natural e harmônica</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a tríade de dó maior">
                            <h4>Toque a tríade de Dó maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a tríade de lá menor">
                            <h4>Toque a tríade de Lá menor</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Fácil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="quiz: identifique acordes maiores e menores">
                            <h4>Quiz: Identifique acordes maiores e menores</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="reconheça acordes maiores pelo som">
                            <h4>Reconheça acordes maiores pelo som</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="reconheça acordes menores pelo som">
                            <h4>Reconheça acordes menores pelo som</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Percepção</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a progressão i-iv-v em dó maior">
                            <h4>Toque a progressão I-IV-V em Dó maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque a progressão i-v-vi-iv em sol maior">
                            <h4>Toque a progressão I-V-vi-IV em Sol maior</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="identifique inversões de acordes">
                            <h4>Identifique inversões de acordes</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Quiz Teoria</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="toque arpejo de dó maior em duas oitavas">
                            <h4>Toque arpejo de Dó maior em duas oitavas</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Médio
                            </p>
                        </div>
                    
                        <div class="card exercise-card" data-name="acompanhe uma melodia com acordes">
                            <h4>Acompanhe uma melodia com acordes</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                                <span class="badge" style="background: #e2e8f0; color: #1a202c;">Exercício Teclado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                Dificuldade: Difícil
                            </p>
                        </div>
                    
                </div>
            </div>

            <div id="students-tab" class="tab-content">
                <input type="text" class="search-box" placeholder="🔍 Buscar alunos..." onkeyup="filterStudents(this.value)">
                <div class="grid" id="students-grid">
                    
                        <div class="card student-card" data-name="liam foster">
                            <h4>Liam Foster</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                📧 [object Object]<br>
                                Status: Não Iniciado
                            </p>
                        </div>
                    
                        <div class="card student-card" data-name="emma carter">
                            <h4>Emma Carter</h4>
                            <div>
                                <span class="badge badge-beginner">Iniciante</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                📧 [object Object]<br>
                                Status: Ativo
                            </p>
                        </div>
                    
                        <div class="card student-card" data-name="ava richardson">
                            <h4>Ava Richardson</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                📧 [object Object]<br>
                                Status: Ativo
                            </p>
                        </div>
                    
                        <div class="card student-card" data-name="noah bennett">
                            <h4>Noah Bennett</h4>
                            <div>
                                <span class="badge badge-intermediate">Intermediário</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                📧 [object Object]<br>
                                Status: Pronto para Avançar
                            </p>
                        </div>
                    
                        <div class="card student-card" data-name="sophia martinez">
                            <h4>Sophia Martinez</h4>
                            <div>
                                <span class="badge badge-advanced">Avançado</span>
                            </div>
                            <p style="margin-top: 12px; color: #718096; font-size: 14px;">
                                📧 [object Object]<br>
                                Status: Concluído
                            </p>
                        </div>
                    
                </div>
            </div>
        </div>

        <div class="footer">
            <p>Piano Learning App • Exportado em 15/06/2026 às 16:31:50</p>
            <p style="margin-top: 8px; opacity: 0.8;">Total: 100 lições • 100 exercícios • 5 alunos</p>
        </div>
    </div>

    <script>
        // Traduções
        function translateLevel(level) {
            const map = { 'Beginner': 'Iniciante', 'Intermediate': 'Intermediário', 'Advanced': 'Avançado' };
            return map[level] || level;
        }
        function translateFormat(format) {
            const map = { 'Theory': 'Teoria', 'Video': 'Vídeo', 'Practice': 'Prática' };
            return map[format] || format;
        }
        function translateTopic(topic) {
            const map = { 'Notes': 'Notas', 'Rhythm': 'Ritmo', 'Scales': 'Escalas', 'Chords': 'Acordes', 'Technique': 'Técnica' };
            return map[topic] || topic;
        }
        function translateExerciseType(type) {
            const map = { 'Theory Quiz': 'Quiz Teoria', 'Reading Practice': 'Prática Leitura', 'Keyboard Drill': 'Exercício Teclado', 'Ear Training': 'Percepção' };
            return map[type] || type;
        }
        function translateDifficulty(diff) {
            const map = { 'Easy': 'Fácil', 'Medium': 'Médio', 'Hard': 'Difícil' };
            return map[diff] || diff;
        }
        function translateProgress(prog) {
            const map = { 'Not Started': 'Não Iniciado', 'Active': 'Ativo', 'Ready to Advance': 'Pronto para Avançar', 'Completed': 'Concluído' };
            return map[prog] || prog;
        }

        // Navegação entre tabs
        function switchTab(tabName) {
            document.querySelectorAll('.tab-button').forEach(btn => btn.classList.remove('active'));
            document.querySelectorAll('.tab-content').forEach(content => content.classList.remove('active'));
            
            event.target.classList.add('active');
            document.getElementById(tabName + '-tab').classList.add('active');
        }

        // Filtros de busca
        function filterLessons(term) {
            const cards = document.querySelectorAll('.lesson-card');
            cards.forEach(card => {
                const match = card.dataset.name.includes(term.toLowerCase());
                card.style.display = match ? 'block' : 'none';
            });
        }

        function filterExercises(term) {
            const cards = document.querySelectorAll('.exercise-card');
            cards.forEach(card => {
                const match = card.dataset.name.includes(term.toLowerCase());
                card.style.display = match ? 'block' : 'none';
            });
        }

        function filterStudents(term) {
            const cards = document.querySelectorAll('.student-card');
            cards.forEach(card => {
                const match = card.dataset.name.includes(term.toLowerCase());
                card.style.display = match ? 'block' : 'none';
            });
        }

        console.log('Piano Learning App - Versão Web Standalone');
        console.log('Dados exportados em: 2026-06-15T19:31:50.229Z');
    </script>
</body>
</html>
