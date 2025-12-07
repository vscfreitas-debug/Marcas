<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<title>Dashboard de Marcas – Doutorado Vicente Santa Cruz</title>
<meta name="viewport" content="width=device-width, initial-scale=1">

<!-- Chart.js CDN -->
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>
    body {
        font-family: Arial, Helvetica, sans-serif;
        margin: 0;
        background: #f4f4f4;
        color: #222;
    }
    .header {
        background: #0A3D62;
        color: white;
        padding: 25px;
        text-align: center;
    }
    .container {
        max-width: 1100px;
        margin: auto;
        padding: 20px;
    }
    .card-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
        gap: 20px;
        margin-bottom: 30px;
    }
    .card {
        background: white;
        padding: 25px;
        border-radius: 14px;
        box-shadow: 0 2px 6px rgba(0,0,0,0.1);
        text-align: center;
    }
    .card h2 {
        font-size: 40px;
        margin: 10px 0 0 0;
        font-weight: bold;
    }
    .chart-box {
        margin: 30px 0;
        background: white;
        padding: 25px;
        border-radius: 14px;
        box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
</style>

</head>
<body>

<div class="header">
    <h1>Dashboard BI – Sistema de Marcas no Brasil</h1>
    <h3>Projeto de Doutorado – Vicente Santa Cruz<br>Orientação: Dr. Vinícius Bogéa</h3>
</div>

<div class="container">

    <!-- KPIs -->
    <div class="card-grid">
        <div class="card">
            Total de Pedidos
            <h2 id="totalPedidos">...</h2>
        </div>
        <div class="card">
            Últimos 12 Meses
            <h2 id="ultimosMeses">...</h2>
        </div>
        <div class="card">
            Tempo Médio de Decisão
            <h2 id="tempoMedio">...</h2>
        </div>
        <div class="card">
            Top Classes
            <h2 id="topClasses">...</h2>
        </div>
    </div>

    <!-- Gráficos -->
    <div class="chart-box">
        <h3>Evolução Anual de Depósitos</h3>
        <canvas id="chartAno"></canvas>
    </div>

    <div class="chart-box">
        <h3>Distribuição por Classes de Nice</h3>
        <canvas id="chartClasse"></canvas>
    </div>

    <div class="chart-box">
        <h3>Depositantes por Estado</h3>
        <canvas id="chartUF"></canvas>
    </div>

</div>

<script>
// =======================================================================
// EXEMPLO DE DADOS (você vai substituir pelos seus dados do CSV)
// =======================================================================

const dadosAno = {
    labels: ["2019", "2020", "2021", "2022", "2023", "2024"],
    valores: [140000, 150000, 155000, 160000, 175000, 180000]
};

const dadosClasse = {
    labels: ["35", "41", "25", "30", "09"],
    valores: [45000, 32000, 18000, 15000, 12000]
};

const dadosUF = {
    labels: ["SP", "RJ", "MG", "PR", "RS"],
    valores: [52000, 28000, 24000, 18000, 16000]
};

// KPIs
document.getElementById("totalPedidos").innerText = dadosAno.valores.reduce((a,b)=>a+b);
document.getElementById("ultimosMeses").innerText = 18500; // ajustar depois
document.getElementById("tempoMedio").innerText = "240 dias"; // ajustar depois
document.getElementById("topClasses").innerText = "35, 41, 25"; // ajustar depois

// =======================================================================
// GRÁFICOS
// =======================================================================

// ANO
new Chart(document.getElementById("chartAno"), {
    type: "line",
    data: {
        labels: dadosAno.labels,
        datasets: [{
            label: "Depósitos",
            data: dadosAno.valores,
            borderWidth: 3
        }]
    }
});

// CLASSE
new Chart(document.getElementById("chartClasse"), {
    type: "bar",
    data: {
        labels: dadosClasse.labels,
        datasets: [{
            label: "Depósitos",
            data: dadosClasse.valores
        }]
    }
});

// ESTADOS
new Chart(document.getElementById("chartUF"), {
    type: "bar",
    data: {
        labels: dadosUF.labels,
        datasets: [{
            label: "Depósitos",
            data: dadosUF.valores
        }]
    }
});

</script>

</body>
</html>
