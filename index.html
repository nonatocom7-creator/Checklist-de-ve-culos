<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Sistema Frota Leve</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Chart.js para o Dashboard -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- QRCode.js para gerar os códigos -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    
    <style>
        :root {
            --primary: #0056b3;
            --success: #28a745;
            --danger: #dc3545;
            --bg: #f4f7f6;
            --card: #ffffff;
        }
        body {
            font-family: 'Inter', Arial, sans-serif;
            background-color: var(--bg);
            margin: 0;
            color: #333;
        }
        .tab-btn {
            padding: 10px 15px;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            font-weight: bold;
            color: #555;
            transition: all 0.3s;
        }
        .tab-btn.active {
            border-bottom-color: var(--primary);
            color: var(--primary);
        }
        .view-section {
            display: none;
            padding: 15px;
        }
        .view-section.active {
            display: block;
        }
        .card {
            background: var(--card);
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            margin-bottom: 20px;
        }
        .checklist-item {
            border-bottom: 1px solid #eee;
            padding: 12px 0;
        }
        .checklist-item:last-child { border-bottom: none; }
        .options {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }
        .btn-radio {
            flex: 1;
            padding: 10px;
            text-align: center;
            border: 1px solid #ccc;
            border-radius: 5px;
            background: #eee;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.2s;
        }
        input[type="radio"] { display: none; }
        input[type="radio"][value="Conforme"]:checked + .btn-radio {
            background-color: var(--success);
            color: white;
            border-color: var(--success);
        }
        input[type="radio"][value="Nao Conforme"]:checked + .btn-radio {
            background-color: var(--danger);
            color: white;
            border-color: var(--danger);
        }
        .btn-submit {
            background-color: var(--primary);
            color: white;
            width: 100%;
            padding: 15px;
            border: none;
            border-radius: 5px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: background 0.3s;
        }
        .btn-submit:hover { background-color: #004494; }
        .btn-submit:disabled { background-color: #999; cursor: not-allowed; }
        
        .modal-overlay {
            position: fixed; top: 0; left: 0; right: 0; bottom: 0;
            background: rgba(0,0,0,0.6); display: none;
            align-items: center; justify-content: center; z-index: 50;
            padding: 20px;
        }
        .modal-content {
            background: white; padding: 25px; border-radius: 8px;
            max-width: 400px; width: 100%; text-align: center;
        }
    </style>
</head>
<body>

    <!-- Header / Nav -->
    <div class="bg-white shadow-md sticky top-0 z-40">
        <div class="max-w-4xl mx-auto flex overflow-x-auto">
            <div class="tab-btn active whitespace-nowrap" onclick="switchTab('view-checklist', this)">📝 Novo Checklist</div>
            <div class="tab-btn whitespace-nowrap" onclick="switchTab('view-login', this)" id="tab-login">🔒 Login Admin</div>
            <div class="tab-btn whitespace-nowrap hidden admin-only" onclick="switchTab('view-dashboard', this)">📊 Dashboard</div>
            <div class="tab-btn whitespace-nowrap hidden admin-only" onclick="switchTab('view-vehicles', this)">🚗 Veículos & Alertas</div>
            <div class="tab-btn whitespace-nowrap hidden admin-only text-red-500" onclick="logout()">Sair</div>
        </div>
    </div>

    <!-- Container Principal -->
    <div class="max-w-4xl mx-auto">
        
        <!-- ======================================= -->
        <!-- VIEW: DRIVER CHECKLIST FORM             -->
        <!-- ======================================= -->
        <div id="view-checklist" class="view-section active">
            <h2 class="text-2xl font-bold text-center text-blue-800 mb-6">Realizar Checklist</h2>
            
            <form id="checklistForm">
                <div class="card">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label class="block font-bold mb-2">Nome do Motorista:</label>
                            <input type="text" id="motorista" name="motorista" required placeholder="Ex: João Silva" class="w-full p-3 border rounded focus:ring-2 focus:ring-blue-500 outline-none">
                        </div>
                        <div>
                            <label class="block font-bold mb-2">Placa do Veículo:</label>
                            <input type="text" id="placa" name="placa" required placeholder="Ex: ABC-1234" class="w-full p-3 border rounded focus:ring-2 focus:ring-blue-500 outline-none uppercase font-bold">
                            <p class="text-xs text-gray-500 mt-1" id="placa-hint">Digite a placa ou use o QR Code.</p>
                        </div>
                        <div class="md:col-span-2">
                            <label class="block font-bold mb-2">Hodômetro Atual (Km):</label>
                            <input type="number" id="km" name="km" required placeholder="Ex: 45000" class="w-full p-3 border rounded focus:ring-2 focus:ring-blue-500 outline-none">
                        </div>
                    </div>
                </div>

                <!-- Container onde as perguntas serão injetadas via JS -->
                <div id="checklistContainer"></div>

                <div class="card">
                    <label class="block font-bold mb-2">Observações Gerais (Opcional):</label>
                    <textarea id="observacoes" name="observacoes" placeholder="Descreva problemas gerais, se houver..." class="w-full p-3 border rounded focus:ring-2 focus:ring-blue-500 outline-none" rows="3"></textarea>

                    <label class="block font-bold mb-2 mt-4">Evidência Fotográfica (Avarias):</label>
                    <input type="file" id="foto" name="foto" accept="image/*" capture="environment" class="w-full p-2 border rounded bg-gray-50">
                </div>

                <button type="submit" class="btn-submit" id="btnSubmitChecklist">Salvar Checklist</button>
            </form>
        </div>

        <!-- ======================================= -->
        <!-- VIEW: ADMIN LOGIN                       -->
        <!-- ======================================= -->
        <div id="view-login" class="view-section">
            <div class="card max-w-md mx-auto mt-10">
                <h2 class="text-2xl font-bold text-center text-gray-800 mb-6">Acesso Administrativo</h2>
                <p class="text-sm text-gray-500 text-center mb-4">Demo: admin@admin.com / admin123</p>
                <form id="loginForm">
                    <div class="mb-4">
                        <label class="block font-bold mb-2">Email:</label>
                        <input type="email" id="loginEmail" required class="w-full p-3 border rounded" value="admin@admin.com">
                    </div>
                    <div class="mb-6">
                        <label class="block font-bold mb-2">Senha:</label>
                        <input type="password" id="loginPassword" required class="w-full p-3 border rounded" value="admin123">
                    </div>
                    <button type="submit" class="btn-submit">Entrar</button>
                </form>
            </div>
        </div>

        <!-- ======================================= -->
        <!-- VIEW: ADMIN DASHBOARD                   -->
        <!-- ======================================= -->
        <div id="view-dashboard" class="view-section">
            <div class="flex flex-col md:flex-row justify-between items-center mb-6">
                <h2 class="text-2xl font-bold text-gray-800 mb-4 md:mb-0">Dashboard (Sincronizado)</h2>
                <button onclick="downloadReport()" class="bg-green-600 hover:bg-green-700 text-white font-bold py-2 px-4 rounded shadow flex items-center gap-2">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4"></path></svg>
                    Baixar Relatório (CSV)
                </button>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
                <div class="card bg-blue-50 border-l-4 border-blue-500">
                    <h3 class="text-gray-500 font-bold">Total de Checklists</h3>
                    <p class="text-3xl font-black text-blue-700" id="dash-total-checklists">0</p>
                </div>
                <div class="card bg-green-50 border-l-4 border-green-500">
                    <h3 class="text-gray-500 font-bold">Veículos Cadastrados</h3>
                    <p class="text-3xl font-black text-green-700" id="dash-total-vehicles">0</p>
                </div>
                <div class="card bg-red-50 border-l-4 border-red-500">
                    <h3 class="text-gray-500 font-bold">Manutenções Pendentes</h3>
                    <p class="text-3xl font-black text-red-700" id="dash-total-alerts">0</p>
                </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="card">
                    <h3 class="font-bold text-gray-700 mb-4 text-center">Índice de Conformidade (Itens)</h3>
                    <canvas id="conformityChart"></canvas>
                </div>
                <div class="card overflow-auto max-h-96">
                    <h3 class="font-bold text-gray-700 mb-4">Últimos Checklists Recebidos</h3>
                    <table class="min-w-full text-sm text-left">
                        <thead class="bg-gray-100 text-gray-600">
                            <tr>
                                <th class="p-2">Data</th>
                                <th class="p-2">Placa</th>
                                <th class="p-2">Motorista</th>
                                <th class="p-2">KM</th>
                                <th class="p-2">Status</th>
                            </tr>
                        </thead>
                        <tbody id="recent-checklists-body">
                            <!-- Injetado via JS -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- ======================================= -->
        <!-- VIEW: VEHICLES & ALERTS                 -->
        <!-- ======================================= -->
        <div id="view-vehicles" class="view-section">
            <h2 class="text-2xl font-bold text-gray-800 mb-6">Gestão de Veículos e Alertas</h2>
            
            <div class="card bg-gray-50 border border-gray-200">
                <h3 class="font-bold mb-4 text-blue-800">Cadastrar Novo Veículo (Salvo na Nuvem)</h3>
                <form id="vehicleForm" class="grid grid-cols-1 md:grid-cols-4 gap-4 items-end">
                    <div>
                        <label class="block text-xs font-bold mb-1">Placa:</label>
                        <input type="text" id="v-placa" required placeholder="ABC-1234" class="w-full p-2 border rounded uppercase text-sm focus:ring-2 focus:ring-blue-500 outline-none">
                    </div>
                    <div>
                        <label class="block text-xs font-bold mb-1">Modelo:</label>
                        <input type="text" id="v-modelo" required placeholder="Saveiro" class="w-full p-2 border rounded text-sm focus:ring-2 focus:ring-blue-500 outline-none">
                    </div>
                    <div class="md:col-span-2">
                        <label class="block text-xs font-bold mb-1 text-gray-700">E-mails para Alertas <span class="font-normal text-gray-500">(separe por vírgula)</span>:</label>
                        <input type="text" id="v-email" required placeholder="oficina@empresa.com, gerente@empresa.com" class="w-full p-2 border rounded text-sm focus:ring-2 focus:ring-blue-500 outline-none">
                    </div>
                    
                    <div>
                        <label class="block text-xs font-bold mb-1">KM Últ. Revisão:</label>
                        <input type="number" id="v-km-ultima" required placeholder="50000" class="w-full p-2 border rounded text-sm focus:ring-2 focus:ring-blue-500 outline-none">
                    </div>
                    <div>
                        <label class="block text-xs font-bold mb-1">Intervalo Revisão (KM):</label>
                        <input type="number" id="v-km-intervalo" required placeholder="10000" class="w-full p-2 border rounded text-sm focus:ring-2 focus:ring-blue-500 outline-none">
                    </div>
                    <div>
                        <label class="block text-xs font-bold mb-1">KM Últ. Tr. Óleo:</label>
                        <input type="number" id="v-km-oleo-ultima" required placeholder="50000" class="w-full p-2 border rounded text-sm focus:ring-2 focus:ring-blue-500 outline-none">
                    </div>
                    <div>
                        <label class="block text-xs font-bold mb-1">Intervalo Óleo (KM):</label>
                        <input type="number" id="v-km-oleo-intervalo" required placeholder="10000" class="w-full p-2 border rounded text-sm focus:ring-2 focus:ring-blue-500 outline-none">
                    </div>

                    <div class="md:col-span-4 mt-2">
                        <button type="submit" id="btnSubmitVehicle" class="w-full bg-green-600 text-white p-3 rounded font-bold hover:bg-green-700 h-full mt-1 transition-colors">Salvar Veículo na Nuvem</button>
                    </div>
                </form>
            </div>

            <div class="card overflow-x-auto border border-gray-200">
                <table class="min-w-full text-sm text-left">
                    <thead class="bg-gray-100 text-gray-600 border-b">
                        <tr>
                            <th class="p-3">Placa / Modelo</th>
                            <th class="p-3">KM Atual</th>
                            <th class="p-3">Próximos (KM)</th>
                            <th class="p-3">Status</th>
                            <th class="p-3 text-center">Alerta</th>
                            <th class="p-3 text-center">Ações</th>
                        </tr>
                    </thead>
                    <tbody id="vehicles-table-body" class="divide-y">
                        <!-- Injetado via JS -->
                        <tr><td colspan="6" class="text-center p-4 text-gray-500">Conectando ao banco de dados...</td></tr>
                    </tbody>
                </table>
            </div>
        </div>

    </div>

    <!-- ======================================= -->
    <!-- MODALS (QR CODE & MESSAGES)             -->
    <!-- ======================================= -->
    
    <!-- Modal QR Code -->
    <div id="qrModal" class="modal-overlay">
        <div class="modal-content">
            <h2 class="text-xl font-bold mb-2 text-blue-800">QR Code do Veículo</h2>
            <p id="qrPlacaText" class="font-bold text-lg mb-4 text-gray-600"></p>
            <div id="qrcode" class="flex justify-center bg-white p-4 rounded border inline-block mb-4"></div>
            <p class="text-sm text-gray-500 mb-6">Imprima e cole no veículo. O motorista será direcionado diretamente para o checklist desta placa.</p>
            <button onclick="closeModal('qrModal')" class="bg-gray-200 text-gray-800 px-6 py-2 rounded font-bold hover:bg-gray-300">Fechar</button>
        </div>
    </div>

    <!-- Modal Mensagem Genérica -->
    <div id="messageModal" class="modal-overlay">
        <div class="modal-content">
            <h2 id="msgTitle" class="text-xl font-bold mb-4"></h2>
            <p id="msgText" class="mb-6 text-gray-700"></p>
            <button onclick="closeModal('messageModal')" class="bg-blue-600 text-white px-6 py-2 rounded font-bold hover:bg-blue-700">OK</button>
        </div>
    </div>

    <!-- ======================================= -->
    <!-- JAVASCRIPT & FIREBASE                   -->
    <!-- ======================================= -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, collection, addDoc, updateDoc, deleteDoc, onSnapshot } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // Configuração do Firebase Injetada pelo Ambiente
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'frota-leve-db';
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : { /* Fallback vázio */ };
        
        const app = initializeApp(firebaseConfig);
        const db = getFirestore(app);
        const auth = getAuth(app);
        let currentUser = null;

        // Arrays globais para manter o estado localmente para renderização rápida
        let globalVehicles = [];
        let globalChecklists = [];
        
        // Estado da aplicação (Interface)
        let isAdmin = false;
        let conformityChartInstance = null;

        // Categorias Atualizadas (Sem lona marítima/ganchos)
        const categoriasChecklist = [
            {
                titulo: "Caçamba e Amarração",
                itens: ["Fechadura da tampa traseira", "Condições gerais da caçamba"]
            },
            {
                titulo: "Pneus e Emergência",
                itens: ["Estado dos 4 pneus (calibragem/desgaste)", "Estepe, macaco e chave de roda"]
            },
            {
                titulo: "Motor e Fluidos",
                itens: ["Nível do óleo do motor", "Água do radiador e limpador"]
            },
            {
                titulo: "Elétrica e Estrutura",
                itens: ["Faróis, setas e luz de freio", "Lataria, para-brisa e retrovisores", "Documento e Cartão Combustível"]
            }
        ];

        async function initializeDatabaseConnection() {
            try {
                if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                    const userCredential = await signInWithCustomToken(auth, __initial_auth_token);
                    currentUser = userCredential.user;
                } else {
                    const userCredential = await signInAnonymously(auth);
                    currentUser = userCredential.user;
                }
                
                // Iniciar observadores do banco de dados APÓS o login
                setupRealtimeListeners();
            } catch (error) {
                console.error("Erro ao conectar no banco:", error);
                showMessage("Erro de Conexão", "Não foi possível conectar ao banco de dados na nuvem.");
            }
        }

        function setupRealtimeListeners() {
            if (!currentUser) return;

            // Referências de Caminho Público (para que administradores e motoristas compartilhem a mesma lista)
            const vehiclesRef = collection(db, 'artifacts', appId, 'public', 'data', 'vehicles');
            const checklistsRef = collection(db, 'artifacts', appId, 'public', 'data', 'checklists');

            // Fica "escutando" mudanças nos veículos
            onSnapshot(vehiclesRef, (snapshot) => {
                globalVehicles = snapshot.docs.map(doc => ({ ...doc.data(), id: doc.id }));
                if (isAdmin) {
                    renderVehicles();
                    renderDashboard();
                }
            }, (error) => {
                console.error("Erro ao carregar veículos:", error);
            });

            // Fica "escutando" novos checklists
            onSnapshot(checklistsRef, (snapshot) => {
                globalChecklists = snapshot.docs.map(doc => ({ ...doc.data(), id: doc.id }));
                
                // Ordenar por data em memória (Regra 2 do Firestore: evitar orderBy)
                globalChecklists.sort((a, b) => new Date(b.dataHora) - new Date(a.dataHora));
                
                if (isAdmin) renderDashboard();
            }, (error) => {
                console.error("Erro ao carregar checklists:", error);
            });
        }

        // ==========================================
        // EXPORTANDO FUNÇÕES PARA O HTML (WINDOW)
        // ==========================================
        
        window.showMessage = function(title, text) {
            document.getElementById('msgTitle').innerText = title;
            document.getElementById('msgText').innerText = text;
            document.getElementById('messageModal').style.display = 'flex';
        };

        window.closeModal = function(id) {
            document.getElementById(id).style.display = 'none';
        };

        window.switchTab = function(tabId, btnElement) {
            document.querySelectorAll('.view-section').forEach(el => el.classList.remove('active'));
            document.querySelectorAll('.tab-btn').forEach(el => el.classList.remove('active'));
            
            document.getElementById(tabId).classList.add('active');
            if(btnElement) btnElement.classList.add('active');

            if(tabId === 'view-dashboard') renderDashboard();
            if(tabId === 'view-vehicles') renderVehicles();
        };

        window.logout = function() {
            isAdmin = false;
            document.querySelectorAll('.admin-only').forEach(el => el.classList.add('hidden'));
            document.getElementById('tab-login').classList.remove('hidden');
            window.switchTab('view-checklist', document.querySelector('[onclick="switchTab(\'view-checklist\', this)"]'));
        };

        window.deleteVehicle = async function(id) {
            if (!currentUser) return;
            if(confirm("Tem certeza que deseja excluir este veículo?")) {
                try {
                    await deleteDoc(doc(db, 'artifacts', appId, 'public', 'data', 'vehicles', id));
                } catch(e) {
                    window.showMessage("Erro", "Falha ao excluir na nuvem.");
                }
            }
        };

        window.confirmarManutencao = async function(id, tipo) {
            if (!currentUser) return;
            const veiculo = globalVehicles.find(v => v.id === id);
            if(!veiculo) return;

            const vehicleRef = doc(db, 'artifacts', appId, 'public', 'data', 'vehicles', id);
            
            try {
                if(tipo === 'revisao') {
                    await updateDoc(vehicleRef, { kmUltimaManutencao: veiculo.kmAtual || veiculo.kmUltimaManutencao });
                    window.showMessage("Revisão Confirmada na Nuvem", `Ciclo de REVISÃO reiniciado para o KM ${veiculo.kmAtual}.`);
                } else if(tipo === 'oleo') {
                    await updateDoc(vehicleRef, { kmUltimaTrocaOleo: veiculo.kmAtual || veiculo.kmUltimaTrocaOleo || veiculo.kmUltimaManutencao });
                    window.showMessage("Óleo Confirmado na Nuvem", `Ciclo de ÓLEO reiniciado para o KM ${veiculo.kmAtual}.`);
                }
            } catch(e) {
                console.error(e);
                window.showMessage("Erro", "Não foi possível confirmar a manutenção na nuvem.");
            }
        };

        window.dispararEmail = function(emailList, placa, kmAtual, kmProxRev, kmProxOleo) {
            const subject = encodeURIComponent(`Alerta de Manutencao/Oleo - Veiculo ${placa}`);
            const body = encodeURIComponent(`Olá equipe,\n\nO veículo de placa ${placa} possui serviços próximos ou em atraso.\n\nKM Atual: ${kmAtual}\n\nPróxima Revisão: ${kmProxRev} km\nPróxima Troca de Óleo: ${kmProxOleo} km\n\nPor favor, verifique a necessidade de agendamento.\n\nSistema Frota Leve`);
            window.location.href = `mailto:${emailList}?subject=${subject}&body=${body}`;
        };

        window.generateQR = function(placa) {
            document.getElementById('qrModal').style.display = 'flex';
            document.getElementById('qrPlacaText').innerText = 'Placa: ' + placa;
            
            const qrContainer = document.getElementById('qrcode');
            qrContainer.innerHTML = ''; 
            
            const baseUrl = window.location.href.split('?')[0];
            const finalUrl = `${baseUrl}?placa=${placa}`;
            
            new QRCode(qrContainer, { text: finalUrl, width: 180, height: 180, colorDark : "#0056b3", colorLight : "#ffffff" });
        };

        // ==========================================
        // RENDERIZAÇÃO E FORMULÁRIOS
        // ==========================================
        
        function renderChecklistForm() {
            const container = document.getElementById('checklistContainer');
            if (!container) return;
            container.innerHTML = '';
            
            categoriasChecklist.forEach((cat, catIndex) => {
                let htmlDiv = `<div class="card"><h3 class="text-lg font-bold text-blue-800 mb-3">${cat.titulo}</h3>`;
                
                cat.itens.forEach((item, itemIndex) => {
                    const inputName = `item_${catIndex}_${itemIndex}`;
                    const obsName = `obs_${catIndex}_${itemIndex}`;
                    htmlDiv += `
                        <div class="checklist-item">
                            <span class="block mb-2 font-medium text-gray-800">${item}</span>
                            <input type="hidden" name="label_${inputName}" value="${item}">
                            <div class="options">
                                <label>
                                    <input type="radio" name="${inputName}" value="Conforme" required>
                                    <div class="btn-radio text-sm md:text-base">OK</div>
                                </label>
                                <label>
                                    <input type="radio" name="${inputName}" value="Nao Conforme">
                                    <div class="btn-radio text-sm md:text-base">Avaria</div>
                                </label>
                            </div>
                            <input type="text" name="${obsName}" placeholder="Observações sobre este item (opcional)" class="w-full mt-2 p-2 text-sm border rounded bg-gray-50 focus:bg-white focus:ring-1 focus:ring-blue-300 outline-none">
                        </div>`;
                });
                htmlDiv += `</div>`;
                container.innerHTML += htmlDiv;
            });
        }

        document.getElementById('vehicleForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            if(!currentUser) { window.showMessage("Erro", "Você precisa estar conectado."); return; }

            const btn = document.getElementById('btnSubmitVehicle');
            btn.disabled = true;
            btn.innerText = "Salvando...";

            const novaPlaca = document.getElementById('v-placa').value.toUpperCase();
            
            if(globalVehicles.some(v => v.placa === novaPlaca)) {
                window.showMessage("Erro", "Veículo com esta placa já cadastrado!");
                btn.disabled = false; btn.innerText = "Salvar Veículo na Nuvem";
                return;
            }

            const kmUltima = parseInt(document.getElementById('v-km-ultima').value);
            const kmOleoUltima = parseInt(document.getElementById('v-km-oleo-ultima').value);
            const emailsFormatados = document.getElementById('v-email').value.replace(/\s+/g, '').replace(/;/g, ',');

            const newVehicle = {
                placa: novaPlaca,
                modelo: document.getElementById('v-modelo').value,
                kmUltimaManutencao: kmUltima,
                kmIntervalo: parseInt(document.getElementById('v-km-intervalo').value),
                kmUltimaTrocaOleo: kmOleoUltima,
                kmIntervaloOleo: parseInt(document.getElementById('v-km-oleo-intervalo').value),
                kmAtual: Math.max(kmUltima, kmOleoUltima),
                emailAlerta: emailsFormatados
            };

            try {
                await addDoc(collection(db, 'artifacts', appId, 'public', 'data', 'vehicles'), newVehicle);
                window.showMessage("Sucesso", "Veículo salvo na nuvem com sucesso!");
                this.reset();
            } catch (error) {
                console.error(error);
                window.showMessage("Erro", "Falha ao salvar veículo.");
            } finally {
                btn.disabled = false; btn.innerText = "Salvar Veículo na Nuvem";
            }
        });

        document.getElementById('checklistForm').addEventListener('submit', async function(e) {
            e.preventDefault(); 
            if(!currentUser) { window.showMessage("Aviso", "Aguarde a conexão com o banco de dados..."); return; }

            const btn = document.getElementById('btnSubmitChecklist');
            btn.disabled = true;
            btn.innerText = "Enviando para a Nuvem...";

            const formData = new FormData(this);
            const kmInformado = parseInt(formData.get('km'));
            const placaInformada = formData.get('placa').toUpperCase();
            
            const novoChecklist = {
                dataHora: new Date().toISOString(),
                motorista: formData.get('motorista'),
                placa: placaInformada,
                km: kmInformado,
                observacoesGerais: formData.get('observacoes'),
                itens: [],
                temAvaria: false
            };

            let avariasCount = 0;
            for (let [key, value] of formData.entries()) {
                if (key.startsWith('item_')) {
                    const labelKey = 'label_' + key;
                    const obsKey = 'obs_' + key; 
                    const label = formData.get(labelKey);
                    const obs = formData.get(obsKey) || "";
                    
                    novoChecklist.itens.push({ id: key, nome: label, status: value, observacao: obs });
                    if(value === "Nao Conforme") avariasCount++;
                }
            }
            novoChecklist.temAvaria = avariasCount > 0;

            try {
                await addDoc(collection(db, 'artifacts', appId, 'public', 'data', 'checklists'), novoChecklist);

                const veiculo = globalVehicles.find(v => v.placa === placaInformada);
                if(veiculo && kmInformado > (veiculo.kmAtual || 0)) {
                    const vehicleRef = doc(db, 'artifacts', appId, 'public', 'data', 'vehicles', veiculo.id);
                    await updateDoc(vehicleRef, { kmAtual: kmInformado });
                }

                window.showMessage("Checklist Salvo!", "Os dados foram sincronizados com a nuvem.");
                this.reset();
                window.scrollTo(0,0);
                verificarQRCodeURL();
                
            } catch (error) {
                console.error(error);
                window.showMessage("Erro", "Ocorreu um erro ao enviar para a nuvem. Verifique sua conexão.");
            } finally {
                btn.disabled = false; btn.innerText = "Salvar Checklist";
            }
        });

        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const email = document.getElementById('loginEmail').value;
            const pass = document.getElementById('loginPassword').value;
            
            if(email === 'admin@admin.com' && pass === 'admin123') {
                isAdmin = true;
                document.querySelectorAll('.admin-only').forEach(el => el.classList.remove('hidden'));
                document.getElementById('tab-login').classList.add('hidden');
                window.switchTab('view-dashboard', document.querySelector('[onclick="switchTab(\'view-dashboard\', this)"]'));
                window.showMessage("Sucesso", "Acesso Administrativo Liberado!");
                renderDashboard();
                renderVehicles();
            } else {
                window.showMessage("Erro", "Credenciais inválidas.");
            }
        });

        function renderVehicles() {
            const tbody = document.getElementById('vehicles-table-body');
            tbody.innerHTML = '';

            if (globalVehicles.length === 0) {
                tbody.innerHTML = '<tr><td colspan="6" class="text-center p-4 text-gray-500">Nenhum veículo cadastrado na nuvem.</td></tr>';
                return;
            }

            globalVehicles.forEach(v => {
                const kmProxRev = (v.kmUltimaManutencao || 0) + (v.kmIntervalo || 10000);
                const kmFaltanteRev = kmProxRev - (v.kmAtual || v.kmUltimaManutencao || 0);
                
                const kmOleoUltima = v.kmUltimaTrocaOleo !== undefined ? v.kmUltimaTrocaOleo : (v.kmUltimaManutencao || 0);
                const kmOleoIntervalo = v.kmIntervaloOleo !== undefined ? v.kmIntervaloOleo : 10000;
                const kmProxOleo = kmOleoUltima + kmOleoIntervalo;
                const kmFaltanteOleo = kmProxOleo - (v.kmAtual || kmOleoUltima);
                
                let precisaAlerta = (kmFaltanteRev <= 1000) || (kmFaltanteOleo <= 1000);
                
                const getStatusBadge = (label, faltante) => {
                    if (faltante <= 0) return `<div class="bg-red-100 text-red-800 text-xs px-2 py-1 rounded font-bold mb-1 w-max">${label}: Atrasado!</div>`;
                    if (faltante <= 1000) return `<div class="bg-yellow-100 text-yellow-800 text-xs px-2 py-1 rounded font-bold mb-1 w-max">${label}: em ${faltante}km</div>`;
                    return `<div class="bg-green-100 text-green-800 text-xs px-2 py-1 rounded font-bold mb-1 w-max">${label}: faltam ${faltante}km</div>`;
                };

                const statusHtml = getStatusBadge('Rev', kmFaltanteRev) + getStatusBadge('Óleo', kmFaltanteOleo);
                
                const emailBtn = precisaAlerta ? `
                    <button onclick="dispararEmail('${v.emailAlerta}', '${v.placa}', ${v.kmAtual || 0}, ${kmProxRev}, ${kmProxOleo})" class="text-blue-500 hover:text-blue-800" title="Enviar e-mail de alerta">
                        <svg class="w-6 h-6 inline" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path></svg>
                    </button>
                ` : `<span class="text-gray-300"><svg class="w-6 h-6 inline" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path></svg></span>`;

                const row = `
                    <tr class="hover:bg-gray-50 transition-colors">
                        <td class="p-3 font-bold uppercase">${v.placa} <br><span class="text-xs font-normal text-gray-500 capitalize">${v.modelo}</span></td>
                        <td class="p-3 font-medium">${v.kmAtual || 0}</td>
                        <td class="p-3 text-xs text-gray-600">Rev: ${kmProxRev}<br>Óleo: ${kmProxOleo}</td>
                        <td class="p-3 flex flex-col justify-center">${statusHtml}</td>
                        <td class="p-3 text-center">${emailBtn}</td>
                        <td class="p-3 text-center whitespace-nowrap">
                            <button onclick="confirmarManutencao('${v.id}', 'revisao')" class="text-gray-600 hover:text-gray-900 mr-2" title="Confirmar Revisão Geral (Chave)">
                                <svg class="w-5 h-5 inline" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                            </button>
                            <button onclick="confirmarManutencao('${v.id}', 'oleo')" class="text-yellow-600 hover:text-yellow-800 mr-2" title="Confirmar Troca de Óleo (Gota)">
                                <svg class="w-5 h-5 inline" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2c-5.333 7.333-8 11.556-8 15a8 8 0 1016 0c0-3.444-2.667-7.667-8-15zm-2 15a2 2 0 114 0 2 2 0 01-4 0z"></path></svg>
                            </button>
                            <button onclick="generateQR('${v.placa}')" class="text-blue-600 hover:text-blue-800 mr-2" title="Gerar QR Code">
                                <svg class="w-5 h-5 inline" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v1m6 11h2m-6 0h-2v4m0-11v3m0 0h.01M12 12h4.01M16 20h4M4 12h4m12 0h.01M5 8h2a1 1 0 001-1V5a1 1 0 00-1-1H5a1 1 0 00-1 1v2a1 1 0 001 1zm12 0h2a1 1 0 001-1V5a1 1 0 00-1-1h-2a1 1 0 00-1 1v2a1 1 0 001 1zM5 20h2a1 1 0 001-1v-2a1 1 0 00-1-1H5a1 1 0 00-1 1v2a1 1 0 001 1 z"></path></svg>
                            </button>
                            <button onclick="deleteVehicle('${v.id}')" class="text-red-600 hover:text-red-800" title="Excluir">
                                <svg class="w-5 h-5 inline" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"></path></svg>
                            </button>
                        </td>
                    </tr>
                `;
                tbody.innerHTML += row;
            });
        }

        function renderDashboard() {
            document.getElementById('dash-total-checklists').innerText = globalChecklists.length;
            document.getElementById('dash-total-vehicles').innerText = globalVehicles.length;
            
            let alertas = 0;
            globalVehicles.forEach(v => {
                const kmProxRev = (v.kmUltimaManutencao || 0) + (v.kmIntervalo || 10000);
                const kmFaltanteRev = kmProxRev - (v.kmAtual || v.kmUltimaManutencao || 0);
                const kmOleoUltima = v.kmUltimaTrocaOleo !== undefined ? v.kmUltimaTrocaOleo : (v.kmUltimaManutencao || 0);
                const kmProxOleo = kmOleoUltima + (v.kmIntervaloOleo !== undefined ? v.kmIntervaloOleo : 10000);
                const kmFaltanteOleo = kmProxOleo - (v.kmAtual || kmOleoUltima);

                if (kmFaltanteRev <= 1000 || kmFaltanteOleo <= 1000) alertas++;
            });
            document.getElementById('dash-total-alerts').innerText = alertas;

            let totalConformes = 0;
            let totalAvarias = 0;
            
            globalChecklists.forEach(c => {
                c.itens.forEach(i => {
                    if(i.status === 'Conforme') totalConformes++;
                    if(i.status === 'Nao Conforme') totalAvarias++;
                });
            });

            const ctx = document.getElementById('conformityChart').getContext('2d');
            if(conformityChartInstance) conformityChartInstance.destroy();
            conformityChartInstance = new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: ['Conforme (OK)', 'Não Conforme (Avaria)'],
                    datasets: [{
                        data: [totalConformes, totalAvarias],
                        backgroundColor: ['#28a745', '#dc3545'], borderWidth: 0
                    }]
                },
                options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { position: 'bottom' } } }
            });

            const tbody = document.getElementById('recent-checklists-body');
            tbody.innerHTML = '';
            
            const recentes = globalChecklists.slice(0, 10);
            recentes.forEach(c => {
                const dataStr = new Date(c.dataHora).toLocaleDateString('pt-BR') + ' ' + new Date(c.dataHora).toLocaleTimeString('pt-BR', {hour: '2-digit', minute:'2-digit'});
                const statusBadge = c.temAvaria 
                    ? '<span class="bg-red-100 text-red-800 text-xs px-2 py-1 rounded font-bold">C/ Avarias</span>'
                    : '<span class="bg-green-100 text-green-800 text-xs px-2 py-1 rounded font-bold">100% OK</span>';
                
                tbody.innerHTML += `
                    <tr class="border-b hover:bg-gray-50 transition-colors">
                        <td class="p-2 text-xs">${dataStr}</td>
                        <td class="p-2 font-bold uppercase">${c.placa}</td>
                        <td class="p-2 capitalize">${c.motorista.split(' ')[0]}</td>
                        <td class="p-2 text-gray-500">${c.km}km</td>
                        <td class="p-2">${statusBadge}</td>
                    </tr>
                `;
            });
        }

        window.downloadReport = function() {
            if(globalChecklists.length === 0) {
                window.showMessage("Aviso", "Não há checklists para exportar.");
                return;
            }

            let csvContent = "data:text/csv;charset=utf-8,\uFEFF"; 
            csvContent += "Data/Hora;Motorista;Placa;KM Informado;Status Geral;Observacoes Gerais\n";

            globalChecklists.forEach(c => {
                const data = new Date(c.dataHora).toLocaleString('pt-BR');
                const obs = (c.observacoesGerais || "").replace(/;/g, ",").replace(/\n/g, " ");
                const status = c.temAvaria ? "Com Avarias" : "OK";
                csvContent += `${data};${c.motorista};${c.placa};${c.km};${status};${obs}\n`;
            });

            const encodedUri = encodeURI(csvContent);
            const link = document.createElement("a");
            link.setAttribute("href", encodedUri);
            link.setAttribute("download", "relatorio_checklists_frota.csv");
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        };

        function verificarQRCodeURL() {
            const urlParams = new URLSearchParams(window.location.search);
            const placaDaURL = urlParams.get('placa');

            if (placaDaURL) {
                const inputPlaca = document.getElementById('placa');
                if(inputPlaca) {
                    inputPlaca.value = placaDaURL.toUpperCase(); 
                    inputPlaca.readOnly = true; 
                    inputPlaca.classList.add('bg-gray-200', 'cursor-not-allowed', 'text-gray-600');
                    
                    const hint = document.getElementById('placa-hint');
                    if(hint) {
                        hint.innerText = "✅ Placa identificada pela Nuvem / QR Code.";
                        hint.classList.add("text-green-600", "font-bold");
                    }
                }
            }
        }

        // Boot executado imediatamente ao carregar
        window.addEventListener('DOMContentLoaded', () => {
            renderChecklistForm(); // Renderiza os itens do checklist na tela
            verificarQRCodeURL();    // Lê a placa se veio pelo QR Code
            initializeDatabaseConnection(); // Conecta com o Firebase
        });
    </script>
</body>
</html>
