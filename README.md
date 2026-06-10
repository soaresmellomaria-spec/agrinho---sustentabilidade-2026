# agrinho---sustentabilidade-2026 
agricultura-inteligente/
│
├── README.md             # Explicação humanizada do projeto
├── docs/                 # Documentação e imagens
├── src/                  # Código-fonte
│   ├── sensors/          # Scripts de leitura de sensores
│   ├── irrigation/       # Automação da irrigação
│   ├── ai/               # Algoritmo de recomendação
│   └── dashboard/        # Dashboard web ou terminal
├── requirements.txt      # Dependências Python
└── LICENSEimport random
import time

def ler_sensores():
    umidade_solo = random.uniform(10, 80)  # em %
    temperatura = random.uniform(20, 35)   # °C
    luminosidade = random.uniform(200, 1000)  # lux
    return umidade_solo, temperatura, luminosidade

while True:
    umidade, temp, luz = ler_sensores()
    print(f"Umidade: {umidade:.2f}% | Temp: {temp:.2f}°C | Luz: {luz:.2f} lux")
    time.sleep(2)def verificar_irrigacao(umidade):
    if umidade < 30:  # Limite crítico
        print("Solo seco! Ligando irrigação...")
        # Aqui você poderia acionar um relé para bomba de água
    else:
        print("Solo úmido. Irrigação desativada.")

while True:
    umidade, _, _ = ler_sensores()
    verificar_irrigacao(umidade)
    time.sleep(5)from sklearn.linear_model import LinearRegression
import numpy as np

# Dados simulados: [umidade, temperatura, luminosidade] => necessidade de água (0 ou 1)
X = np.array([
    [20, 30, 500],
    [50, 25, 400],
    [30, 28, 600],
    [70, 22, 300]
])
y = np.array([1, 0, 1, 0])

modelo = LinearRegression()
modelo.fit(X, y)

# Predição
novo_dado = np.array([[25, 29, 450]])
necessidade_agua = modelo.predict(novo_dado)
print(f"Necessidade de água: {necessidade_agua[0]:.2f}")
