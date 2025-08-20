# Challenge_alura_telecon_2 <br>



# 1. Propósito da Análise
O objetivo principal deste projeto foi desenvolver um modelo de machine learning capaz de prever com alta precisão quais clientes da empresa fictícia "Telecom X" têm maior probabilidade de cancelar seus serviços (churn). A análise visa transformar dados brutos em insights estratégicos, permitindo que a empresa adote uma postura proativa, criando campanhas de retenção focadas nos clientes de maior risco.

# 2. Processo de Preparação dos Dados

Um pipeline robusto de pré-processamento foi criado para garantir a qualidade dos dados inseridos no modelo.
Fonte de Dados: O projeto utilizou um dataset pré-processado (.CSV) carregado diretamente de um repositório no GitHub para garantir a reprodutibilidade.
Classificação e Limpeza: As variáveis foram classificadas em numéricas e categóricas. Colunas irrelevantes (ID_Cliente) e redundantes (Custo_Diario) foram removidas.
Divisão dos Dados: Os dados foram divididos em conjuntos de treino (80%) e teste (20%). Foi utilizada a técnica de estratificação na variável-alvo (Churn) para garantir que a proporção de clientes evadidos e ativos fosse a mesma em ambos os conjuntos, o que é crucial para uma avaliação justa em um cenário com dados desbalanceados.
Codificação e Normalização: Foi construído um pipeline ColumnTransformer
para aplicar as seguintes transformações após a divisão dos dados, evitando data leakage:
OneHotEncoder: Aplicado às variáveis categóricas para convertê-las em formato numérico.
StandardScaler: Aplicado às variáveis numéricas para padronizá-las (média 0, desvio padrão 1), um requisito para o bom desempenho de modelos lineares como a Regressão Logística.


# 3. Modelagam e otmização

Foram treinados e avaliados dois modelos distintos para abordar o problema de diferentes maneiras.

Justificativa das Escolhas:

Regressão Logística: Escolhido como um modelo baseline por sua rapidez e alta interpretabilidade.
Random Forest: Escolhido como um modelo mais complexo e robusto, capaz de capturar relações não-lineares.
Otimização para Desbalanceamento: A análise inicial revelou que o principal desafio era o baixo desempenho na identificação de clientes que cancelavam (baixo Recall), devido ao desbalanceamento de classes (73% Não Churn vs. 27% Churn). A solução foi retreinar os modelos utilizando o hiperparâmetro class_weight='balanced'.

Seleção do Modelo Final: A Regressão Logística Ponderada foi selecionada como o modelo campeão. A otimização elevou seu Recall na classe "Churn" de 52% para 78%, um ganho massivo de performance na métrica mais importante para o negócio.


# 4. Principais insides
A análise do modelo final permitiu identificar os principais fatores que influenciam a evasão de clientes.

Perfil do Cliente em Risco
O modelo identificou um perfil claro de cliente com alta probabilidade de churn:

Cliente de contrato recente (poucos meses), com serviço de Fibra Óptica e que utiliza Cheque Eletrônico como método de pagamento.

Fatores de Retenção vs. Fatores de Risco
A análise dos coeficientes do modelo revelou uma clara distinção entre os fatores que mantêm os clientes e os que os levam a sair.

Principais Fatores de Retenção:

Contratos de Longo Prazo: Contratos de 1 ou 2 anos são a ferramenta mais forte contra o churn.
Tempo de Contrato: Quanto mais tempo um cliente está na base, menor sua chance de sair.
Principais Fatores de Risco:

Serviço de Fibra Óptica: Clientes deste serviço premium são mais propensos a cancelar.
Contratos Mensais: A flexibilidade do contrato mensal está diretamente ligada a uma maior taxa de evasão.




