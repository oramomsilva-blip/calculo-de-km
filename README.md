<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de Custos Uber</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        /* Custom scrollbar for better aesthetics */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        ::-webkit-scrollbar-thumb {
            background: #888;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #555;
        }
    </style>
</head>
<body class="bg-gray-100 text-gray-800">

    <div class="container mx-auto p-4 sm:p-6 md:p-8 max-w-4xl">
        
        <header class="text-center mb-8">
            <h1 class="text-3xl sm:text-4xl font-bold text-gray-900">🚗 Calculadora de Custos Uber</h1>
            <p class="text-gray-600 mt-2">Estime seus gastos e defina sua meta de lucro mensal.</p>
        </header>

        <main class="grid grid-cols-1 md:grid-cols-2 gap-8">
            
            <!-- Coluna de Entradas do Usuário -->
            <div class="bg-white p-6 rounded-2xl shadow-lg space-y-6">
                <h2 class="text-2xl font-semibold border-b pb-3 text-gray-800">📌 Dados e Custos</h2>

                <!-- Seção do Veículo -->
                <div>
                    <h3 class="text-lg font-medium text-gray-700 mb-3">Veículo</h3>
                    <div class="space-y-4">
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label for="tipo_combustivel" class="block text-sm font-medium text-gray-600">Combustível</label>
                                <select id="tipo_combustivel" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                                    <option>Gasolina</option>
                                    <option>Etanol</option>
                                    <option>GNV</option>
                                    <option>Diesel</option>
                                </select>
                            </div>
                            <div>
                                <label for="preco_combustivel" class="block text-sm font-medium text-gray-600">Preço (R$/L)</label>
                                <input type="number" id="preco_combustivel" value="5.50" step="0.01" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                            </div>
                        </div>
                        <div>
                            <label for="consumo_km_l" class="block text-sm font-medium text-gray-600">Consumo (km/l)</label>
                            <input type="number" id="consumo_km_l" value="12.0" step="0.1" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                        </div>
                        <div>
                            <label for="valor_carro" class="block text-sm font-medium text-gray-600">Valor do Automóvel (R$)</label>
                            <input type="number" id="valor_carro" value="60000" step="1000" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                        </div>
                         <div>
                            <label for="km_mes" class="block text-sm font-medium text-gray-600">Quilômetros rodados/mês</label>
                            <input type="number" id="km_mes" value="3000" step="100" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                        </div>
                    </div>
                </div>

                <!-- Seção de Manutenção -->
                <div>
                    <h3 class="text-lg font-medium text-gray-700 mb-3">Manutenção</h3>
                    <div class="space-y-4">
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label for="custo_troca_oleo" class="block text-sm font-medium text-gray-600">Custo Troca de Óleo (R$)</label>
                                <input type="number" id="custo_troca_oleo" value="200" step="10" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                            </div>
                            <div>
                                <label for="freq_troca_oleo_km" class="block text-sm font-medium text-gray-600">Frequência (km)</label>
                                <input type="number" id="freq_troca_oleo_km" value="10000" step="500" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                            </div>
                        </div>
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label for="custo_pneus" class="block text-sm font-medium text-gray-600">Custo 4 Pneus (R$)</label>
                                <input type="number" id="custo_pneus" value="2500" step="50" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                            </div>
                            <div>
                                <label for="vida_pneus_km" class="block text-sm font-medium text-gray-600">Vida Útil (km)</label>
                                <input type="number" id="vida_pneus_km" value="40000" step="1000" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Seção de Custos Fixos e Metas -->
                <div>
                    <h3 class="text-lg font-medium text-gray-700 mb-3">Despesas e Metas</h3>
                    <div class="space-y-4">
                        <div>
                            <label for="valor_parcela" class="block text-sm font-medium text-gray-600">Parcela Mensal (R$)</label>
                            <input type="number" id="valor_parcela" value="1500" step="10" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                        </div>
                        <div>
                            <label for="seguro_anual" class="block text-sm font-medium text-gray-600">Seguro Anual (R$)</label>
                            <input type="number" id="seguro_anual" value="3000" step="50" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                        </div>
                        <div>
                            <label for="dep_ano" class="block text-sm font-medium text-gray-600">Depreciação Anual (%)</label>
                            <input type="number" id="dep_ano" value="10" step="0.5" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                        </div>
                        <div>
                            <label for="lucro_desejado" class="block text-sm font-medium text-gray-600">Lucro Mensal Desejado (R$)</label>
                            <input type="number" id="lucro_desejado" value="3000" step="100" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500">
                        </div>
                    </div>
                </div>
            </div>

            <!-- Coluna de Resultados -->
            <div class="bg-white p-6 rounded-2xl shadow-lg space-y-6">
                <h2 class="text-2xl font-semibold border-b pb-3 text-gray-800">📊 Resultados</h2>
                
                <div id="results" class="space-y-4">
                    <!-- Os resultados serão injetados aqui pelo JavaScript -->
                </div>
            </div>
        </main>

    </div>

    <script>
        // Função para formatar números como moeda brasileira (BRL)
        const formatCurrency = (value) => {
            return new Intl.NumberFormat('pt-BR', {
                style: 'currency',
                currency: 'BRL'
            }).format(value);
        };
        
        const formatDecimal = (value) => {
             return new Intl.NumberFormat('pt-BR', {
                minimumFractionDigits: 2,
                maximumFractionDigits: 2
            }).format(value);
        }

        // Função principal para calcular e exibir os resultados
        const calculate = () => {
            // -------------------------------
            // Coleta de Entradas
            // -------------------------------
            const preco_combustivel = parseFloat(document.getElementById('preco_combustivel').value) || 0;
            const consumo_km_l = parseFloat(document.getElementById('consumo_km_l').value) || 1;
            const custo_troca_oleo = parseFloat(document.getElementById('custo_troca_oleo').value) || 0;
            const freq_troca_oleo_km = parseFloat(document.getElementById('freq_troca_oleo_km').value) || 1;
            const valor_carro = parseFloat(document.getElementById('valor_carro').value) || 0;
            const valor_parcela = parseFloat(document.getElementById('valor_parcela').value) || 0;
            const dep_ano = parseFloat(document.getElementById('dep_ano').value) || 0;
            const km_mes = parseFloat(document.getElementById('km_mes').value) || 0;
            const seguro_anual = parseFloat(document.getElementById('seguro_anual').value) || 0;
            const custo_pneus = parseFloat(document.getElementById('custo_pneus').value) || 0;
            const vida_pneus_km = parseFloat(document.getElementById('vida_pneus_km').value) || 1;
            const lucro_desejado = parseFloat(document.getElementById('lucro_desejado').value) || 0;
            const ipva_percent = 0.04; // Fixo em 4%

            // -------------------------------
            // Cálculos
            // -------------------------------
            const custo_combustivel = (km_mes / consumo_km_l) * preco_combustivel;
            const custo_oleo = (km_mes / freq_troca_oleo_km) * custo_troca_oleo;
            const ipva_mensal = (valor_carro * ipva_percent) / 12;
            const dep_mensal = (valor_carro * (dep_ano / 100)) / 12;
            const seguro_mensal = seguro_anual / 12;
            const custo_pneus_mensal = (km_mes / vida_pneus_km) * custo_pneus;

            const custos_fixos = valor_parcela + ipva_mensal + seguro_mensal;
            const custos_variaveis = custo_combustivel + custo_oleo + custo_pneus_mensal + dep_mensal;

            const custo_total = custos_fixos + custos_variaveis;
            const receita_necessaria = custo_total + lucro_desejado;
            
            // Novo cálculo: Faturamento por KM
            const faturamento_por_km = km_mes > 0 ? receita_necessaria / km_mes : 0;

            // -------------------------------
            // Exibição dos Resultados
            // -------------------------------
            const resultsDiv = document.getElementById('results');
            resultsDiv.innerHTML = `
                <div class="space-y-3 text-gray-700">
                    <p class="flex justify-between"><span>🔹 Custo com combustível:</span> <span class="font-medium">${formatCurrency(custo_combustivel)}</span></p>
                    <p class="flex justify-between"><span>🔹 Custo com óleo:</span> <span class="font-medium">${formatCurrency(custo_oleo)}</span></p>
                    <p class="flex justify-between"><span>🔹 Custo com pneus:</span> <span class="font-medium">${formatCurrency(custo_pneus_mensal)}</span></p>
                    <p class="flex justify-between"><span>🔹 Seguro mensal:</span> <span class="font-medium">${formatCurrency(seguro_mensal)}</span></p>
                    <p class="flex justify-between"><span>🔹 IPVA mensal:</span> <span class="font-medium">${formatCurrency(ipva_mensal)}</span></p>
                    <p class="flex justify-between"><span>🔹 Depreciação mensal:</span> <span class="font-medium">${formatCurrency(dep_mensal)}</span></p>
                </div>
                
                <hr class="my-4 border-gray-200">

                <div class="space-y-3">
                    <div class="bg-blue-50 p-3 rounded-lg">
                        <p class="flex justify-between text-blue-800">
                            <span class="font-semibold">Custos Fixos:</span>
                            <span class="font-bold">${formatCurrency(custos_fixos)}</span>
                        </p>
                    </div>
                    <div class="bg-orange-50 p-3 rounded-lg">
                        <p class="flex justify-between text-orange-800">
                            <span class="font-semibold">Custos Variáveis:</span>
                            <span class="font-bold">${formatCurrency(custos_variaveis)}</span>
                        </p>
                    </div>
                </div>

                <hr class="my-4 border-gray-200">

                <div class="space-y-4">
                    <div class="bg-red-100 p-4 rounded-lg text-center">
                        <p class="text-lg font-semibold text-red-800">Custo Total Mensal</p>
                        <p class="text-3xl font-bold text-red-900">${formatCurrency(custo_total)}</p>
                    </div>
                    <div class="bg-green-100 p-4 rounded-lg text-center">
                        <p class="text-lg font-semibold text-green-800">Receita Necessária (com lucro)</p>
                        <p class="text-3xl font-bold text-green-900">${formatCurrency(receita_necessaria)}</p>
                    </div>
                    <div class="bg-indigo-100 p-4 rounded-lg text-center">
                        <p class="text-lg font-semibold text-indigo-800">Faturamento Mínimo por KM</p>
                        <p class="text-3xl font-bold text-indigo-900">R$ ${formatDecimal(faturamento_por_km)}</p>
                    </div>
                </div>
            `;
        };

        // -------------------------------
        // Event Listeners
        // -------------------------------
        // Seleciona todos os inputs e o select
        const inputs = document.querySelectorAll('input, select');
        // Adiciona um event listener para cada um, que chama a função de cálculo
        inputs.forEach(input => {
            input.addEventListener('input', calculate);
        });

        // Chama a função de cálculo inicialmente para carregar os valores padrão
        document.addEventListener('DOMContentLoaded', calculate);
    </script>
</body>
</html>
