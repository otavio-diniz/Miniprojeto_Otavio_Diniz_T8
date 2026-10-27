# Mini-Projeto — Análise de Dados de Varejo

## Identificação

**Autor:** Otávio Diniz  
**Curso:** SC TEC — Análise de Dados com Python  
**Turma:** T8  
**Módulo:** 1 — Semana 7  

## Objetivo

O objetivo deste mini-projeto é investigar a estrutura e a qualidade de uma base de dados de varejo, aplicar procedimentos justificados de tratamento e utilizar técnicas de análise de dados com Python e a biblioteca Pandas para interpretar os resultados obtidos.

O projeto está organizado em seis Sprints, conforme o enunciado institucional:

1. Leitura e diagnóstico;
2. Limpeza e padronização;
3. Funções e organização;
4. Análise dos dados;
5. Exportação e comunicação;
6. Revisão e entrega.

As cinco primeiras Sprints compõem o desenvolvimento técnico do notebook. A sexta corresponde à revisão final, à organização dos arquivos e à submissão do trabalho.

O projeto também busca demonstrar a importância de compreender o significado dos dados antes de realizar alterações, evitando excluir registros ou atribuir interpretações sem evidências suficientes.

Ao final do processamento, é gerado o arquivo tratado `varejo_limpo.csv`.

## Tecnologias e estrutura do projeto

- **Ambiente utilizado:** Google Colab, com notebook Jupyter (`.ipynb`).
- **Linguagem e bibliotecas:** Python, Pandas, `google.colab.files` para receber o arquivo de entrada e módulos da biblioteca padrão `pathlib` e `os` para lidar com caminhos e validar a exportação.
- **Dependências:** uma sessão Python com Pandas disponível e o CSV original `Base Varejo.csv` obtido legitimamente na fonte indicada. O processamento não exige banco de dados, credenciais de serviço nem módulos Python próprios adicionais.

Arquivos previstos para a entrega acadêmica:

- `Miniprojeto_Otavio_Diniz_T8.ipynb`: roteiro executável, checkpoints, resultados e interpretações;
- `README.md`: apresentação, metodologia, reprodução e limitações;
- `varejo_limpo.csv`: saída tratada da Sprint 5, **somente para distribuição pública se os direitos de redistribuição forem comprovados**.

O arquivo de entrada `Base Varejo.csv` é obtido separadamente na origem citada; não é criado pelo notebook. O tratamento pode ser reproduzido por sua execução, preservando as restrições de uso da fonte.

## Fonte dos dados

**Dataset:** Base Varejo  
**Origem:** Kaggle  
**Responsável pela publicação:** João Pedro Paiva Cardoso  
**Versão:** 1 — 03/04/2023  
**Arquivo utilizado:** `Base Varejo.csv`

Fonte indicada no enunciado: [Base Varejo — Kaggle](https://www.kaggle.com/datasets/namespaiva/base-varejo/data).

**Direitos de terceiros:** os metadados de atribuição e versão acima são reproduzidos da documentação acadêmica utilizada, mas a licença de redistribuição pública do dataset não foi confirmada nesta revisão. A disponibilidade para download no Kaggle não constitui, por si só, permissão para republicar a base original ou o CSV tratado. Sem essa comprovação, o CSV completo permanece fora da distribuição pública, mesmo que tenha sido gerado e validado localmente.

## Estrutura dos dados

A base original possui **830.000 registros e 14 colunas**.

As dez colunas com informações são:

- `DATA`: data associada à compra;
- `CO_ID`: identificador da compra;
- `CL_ID`: identificador do cliente;
- `CL_GENERO`: gênero registrado para o cliente;
- `CL_EC`: código relacionado ao cliente, cujo significado específico não está documentado na base analisada;
- `CL_FHL`: outro código relacionado ao cliente, cujo significado específico também não está documentado na fonte utilizada;
- `CL_SEG`: código do segmento do cliente, representado pelos valores `A`, `B` e `C`; o significado comercial desses códigos não foi informado na fonte;
- `PR_ID`: identificador do produto;
- `PR_CAT`: categoria do produto;
- `PR_NOME`: nome do produto.

A base também possuía quatro colunas totalmente vazias:

- `Unnamed: 10`
- `Unnamed: 11`
- `Unnamed: 12`
- `Unnamed: 13`

Cada uma dessas quatro colunas apresentava **830.000 valores ausentes** e foi removida durante o tratamento.

Após a limpeza, a estrutura final passou a possuir **830.000 registros e 10 colunas**.

## Como executar

O projeto foi executado e validado no **Google Colab** com Python e Pandas. Recomenda-se esse mesmo ambiente; não foi certificada a equivalência de execução em todos os sistemas operacionais ou versões locais de Python. Não há arquivo `requirements.txt` ou versão de Pandas fixada no projeto.

**Reprodução em uma sessão limpa do Google Colab:**

1. Abrir o notebook `Miniprojeto_Otavio_Diniz_T8.ipynb` no Google Colab.
2. Obter o arquivo `Base Varejo.csv` na fonte indicada no Kaggle.
3. Executar a primeira célula responsável pelo upload do arquivo.
4. Quando solicitado, selecionar `Base Varejo.csv` no computador.
5. Executar as células do notebook na ordem em que aparecem, desde a Sprint 0 até a Sprint 5.
6. Acompanhar os resultados de diagnóstico, limpeza, validação e análise apresentados após cada checkpoint.
7. Na Sprint 5, executar a célula de exportação:

`df_funcao.to_csv("varejo_limpo.csv", index=False)`

8. Após a execução, localizar `varejo_limpo.csv` na área de arquivos da sessão do Google Colab.
9. O notebook realiza uma nova leitura do arquivo exportado para confirmar sua integridade.

**Critério de sucesso:** nenhuma célula de código deve apresentar erro, o CSV deve ser criado e a seção de validação da Sprint 5 deve indicar correspondência de registros, dimensões, colunas e conteúdo entre a base tratada e o CSV relido. Para problemas com a entrada, conferir nome `Base Varejo.csv`, separador `;` e seleção do arquivo durante o upload; a sessão Colab é temporária, portanto o arquivo de saída precisa ser preservado fora dela conforme a necessidade de uso.

Na validação realizada no próprio notebook, foram obtidos:

- base original: **830.000 linhas × 14 colunas**;
- base tratada: **830.000 linhas × 10 colunas**;
- CSV exportado: **830.000 linhas × 10 colunas**;
- correspondência das colunas entre a base tratada e o arquivo exportado: **verdadeira**.

## Tratamento e qualidade dos dados

O processo de tratamento foi realizado somente depois do diagnóstico dos dados.

### Valores ausentes

Foram encontradas quatro colunas completamente vazias:

`Unnamed: 10` a `Unnamed: 13`.

Como nenhuma delas possuía informação preenchida nos 830.000 registros, elas foram removidas.

### Campos textuais

Foram examinadas as colunas:

`DATA`, `CL_GENERO`, `CL_SEG`, `PR_CAT` e `PR_NOME`.

Não foram identificados:

- textos vazios;
- campos formados apenas por espaços;
- espaços indevidos no início ou no final dos valores.

### Marcadores `#N/D`

Foram identificadas:

- **3.650 ocorrências de `#N/D` em `PR_CAT`**;
- **3.650 ocorrências de `#N/D` em `PR_NOME`**.

As ocorrências aparecem simultaneamente nas mesmas 3.650 linhas e estão associadas ao produto de código `PR_ID = 107`.

Como não foi encontrada outra informação capaz de recuperar o nome ou a categoria desse produto com segurança, os valores foram apenas padronizados:

- `PR_CAT`: `#N/D` → `NÃO INFORMADA`;
- `PR_NOME`: `#N/D` → `NÃO INFORMADO`.

Não foi inventado um nome ou categoria para o produto.

### Registros repetidos

O diagnóstico encontrou:

- **96.553 ocorrências excedentes de linhas completamente repetidas**, considerando todas as colunas.
- **184.330 linhas envolvidas em combinações repetidas de `PR_ID + PR_NOME + CO_ID + CL_ID`**, incluindo as primeiras ocorrências e suas repetições.

Os indicadores possuem critérios de contagem diferentes. Nenhum deles, isoladamente, comprova que as repetições sejam erros ou autoriza sua exclusão.

Essas linhas não foram eliminadas.

A decisão foi preservar os registros porque a base não apresenta uma coluna de quantidade vendida nem um identificador individual de item. Dessa forma, duas linhas iguais podem representar tanto uma duplicação indevida quanto duas unidades legítimas do mesmo produto dentro de uma compra.

Excluir essas linhas sem evidência poderia provocar perda de dados válidos.

### Consistência dos identificadores

Foram realizadas verificações com `groupby()` e `nunique()`.

Não foram encontradas divergências nas relações analisadas:

- compra associada a mais de um cliente: **0**;
- compra associada a mais de uma data: **0**;
- cliente associado a mais de um gênero: **0**;
- cliente associado a mais de um segmento: **0**;
- produto associado a mais de um nome: **0**;
- produto associado a mais de uma categoria: **0**;
- cliente com valores divergentes em `CL_EC`: **0**;
- cliente com valores divergentes em `CL_FHL`: **0**.

O tratamento, portanto, buscou corrigir apenas situações justificadas pelas evidências disponíveis.

## Fluxo de processamento

O notebook organiza o processamento em três grandes etapas.

### 1. Leitura

O arquivo `Base Varejo.csv` é enviado para a sessão do Google Colab e carregado com Pandas utilizando:

`pd.read_csv()`

O separador utilizado é `;`.

A base original é armazenada como `df_bruto`.

### 2. Transformação

O notebook realiza:

- diagnóstico da estrutura;
- análise de valores ausentes;
- verificação de campos textuais;
- identificação de duplicatas;
- análise da consistência dos identificadores;
- investigação do marcador `#N/D`;
- remoção das quatro colunas vazias;
- padronização dos campos não informados;
- criação da função `tratar_dados()`;
- validação da base resultante;
- filtros;
- agrupamentos;
- cálculo de estatísticas.

A função de tratamento cria uma cópia dos dados, remove apenas as quatro colunas completamente vazias e padroniza os dois campos de produto sem informação.

### 3. Exportação

A versão tratada é exportada com:

`df_funcao.to_csv("varejo_limpo.csv", index=False)`

Depois da gravação, o notebook lê novamente `varejo_limpo.csv` e compara sua estrutura com o DataFrame tratado.

O fluxo completo pode ser representado por:

**Base Varejo.csv → leitura → diagnóstico → investigação → tratamento → validação → análise → exportação → varejo_limpo.csv**

## Leitura, transformação e gravação dos dados

A leitura da base original ocorre na Sprint 1, utilizando `pd.read_csv()`. A transformação é investigada e justificada na Sprint 2 e organizada na função `tratar_dados()` na Sprint 3. Na Sprint 5, a base tratada é gravada como `varejo_limpo.csv`, utilizando `to_csv(index=False)`, e relida para validação. A remoção das quatro colunas completamente vazias reduziu a estrutura de 14 para 10 colunas sem excluir registros. A padronização dos marcadores `#N/D` também tornou explícita a ausência de informações do produto 107, preservando a rastreabilidade dos dados.

## Principais conclusões

### 1. Qualidade e tratamento dos dados

A base original possuía **830.000 registros e 14 colunas**.

Durante a limpeza, foram removidas quatro colunas completamente vazias (`Unnamed: 10` a `Unnamed: 13`), cada uma com **830.000 valores ausentes**, reduzindo a estrutura para **10 colunas**, sem excluir nenhum dos 830.000 registros.

Além disso, **3.650 ocorrências de `#N/D` em `PR_CAT`** e outras **3.650 em `PR_NOME`** foram padronizadas para `NÃO INFORMADA` e `NÃO INFORMADO`.

As **96.553 linhas completamente repetidas** foram preservadas, pois a base não possui informações suficientes para comprovar que essas repetições sejam erros.

### 2. Categorias de produtos

No agrupamento por categoria, **ALIMENTOS** apresentou a maior quantidade de registros, com **434.767 linhas**.

Essa contagem representa o número de registros da base associados à categoria e não deve ser interpretada como quantidade de unidades vendidas ou número de compras distintas.

### 3. Compras e segmentos

Ao contar os códigos de compra distintos (`CO_ID`) por segmento, o segmento **B** apresentou **11.843 compras distintas**, seguido por:

- **C:** 5.136 compras distintas;
- **A:** 1.492 compras distintas.

Os códigos `A`, `B` e `C` foram mantidos exatamente como aparecem na base, sem atribuição de características ou significados comerciais que não estejam documentados na fonte.

### 4. Diversidade de produtos por compra

Foram analisadas **18.471 compras**, considerando a quantidade de códigos de produtos distintos (`PR_ID`) associados a cada `CO_ID`.

Os resultados foram:

- **média:** 39,71 tipos de produtos distintos por compra;
- **mínimo:** 1 tipo de produto;
- **máximo:** 81 tipos de produtos distintos.

Essa métrica representa a **diversidade de tipos de produtos por compra**, e não a quantidade física de unidades adquiridas. É uma medida derivada da contagem de identificadores distintos, não uma coluna numérica originalmente presente na base; sua aderência ao critério institucional de estatísticas básicas depende da avaliação da instituição.

### 5. Frequência dos produtos e diferenças entre indicadores

A análise identificou **229 códigos de produtos distintos** (`PR_ID`). O produto com mais registros foi `PR_ID 93 — AGUA SANITARIA`, com **3.773 ocorrências**. Quando a unidade de análise passou a ser compras distintas, o líder foi `PR_ID 51 — PAPINHA INFANTIL`, presente em **3.322 compras**. Por clientes distintos, destacou-se `PR_ID 155 — PATE`, associado a **975 clientes**.

A comparação demonstra que contagens de registros, presença em compras e abrangência entre clientes são indicadores diferentes. Não permitem, isoladamente, concluir quais produtos venderam mais unidades ou geraram mais receita.

### 6. Evolução temporal das compras

Foram identificadas **18.471 compras distintas** entre **4 de janeiro de 2019 e 8 de dezembro de 2022**. Os totais por ano foram **4.483 em 2019**, **4.794 em 2020**, **5.505 em 2021** e **3.689 em 2022**. Em 2022, registraram-se **35 compras em setembro**, **59 em outubro** e **155 em novembro**.

Embora tenha ocorrido crescimento nos totais de 2019 a 2021 e redução em 2022, não é possível inferir sua causa sem investigar a cobertura temporal e possíveis mudanças no registro dos dados, especialmente nos meses finais da série.

## Recomendação

Recomenda-se investigar principalmente as **96.553 linhas completamente repetidas** e os **3.650 registros cujo produto permanece com nome e categoria não informados**.

Para isso, seria importante obter uma fonte complementar, como um cadastro oficial de produtos ou uma informação que permita diferenciar itens dentro de uma mesma compra.

Essa verificação permitiria determinar se as repetições representam registros legítimos ou duplicações indevidas e, eventualmente, recuperar a identificação do produto atualmente registrado como não informado.

Também se recomenda conferir a abrangência e a qualidade dos registros do final de 2022 antes de interpretar a diminuição das compras como uma tendência do varejo.

## Limitação

A principal limitação da base é a ausência de campos de **quantidade vendida, preço, valor da venda, custo ou faturamento**.

Por esse motivo, não é possível calcular diretamente:

- unidades comercializadas;
- receita;
- faturamento;
- ticket médio;
- lucro;
- margem.

As análises realizadas neste projeto representam **contagens de registros, identificadores distintos e diversidade de produtos**, e não volumes físicos ou valores financeiros.

Também existe uma limitação metodológica específica na análise da diversidade de produtos: a medida de 39,71 tipos de produtos por compra foi construída a partir da contagem de `PR_ID` distintos por `CO_ID`. Ela é uma medida quantitativa derivada dos dados, e não uma coluna numérica originalmente existente na base.

Os campos `CL_EC` e `CL_FHL` não possuem dicionário semântico validado; não foram apresentados como estado civil ou número de filhos. A distribuição das compras ao longo de 2022 também pode sofrer efeitos de cobertura temporal não comprovada. Os resultados são descritivos, não demonstram causalidade entre perfil de cliente, segmento e comportamento de compra.

## Autoria e referências

**Projeto acadêmico:** Otávio Diniz — SC TEC, Análise de Dados com Python, Turma T8, Módulo 1, Semana 7.

**Fonte de dados:** [Base Varejo no Kaggle](https://www.kaggle.com/datasets/namespaiva/base-varejo/data), publicação atribuída na documentação do projeto a João Pedro Paiva Cardoso. As condições de redistribuição pública da base original e do CSV resultante continuam sujeitas à verificação da licença aplicável.

**Licenciamento do repositório:** não há, neste documento, concessão de licença sobre dados de terceiros. Não se deve interpretar a exposição do código e da documentação como autorização para republicar a base de dados.