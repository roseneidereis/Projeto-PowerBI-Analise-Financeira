## Análise Financeira - Análise de Dados com Power BI
Projeto de análise de dados desenvolvido utilizando o Power com o objetivo de efetuar a análise financeira de uma empresa fictícia.  
<br>
## Cenário
A empresa precisava ter a visão das receitas e despesas para elaborar o seu planejamento financeiro. Dessa maneira, solicitou a apresentação de alguns indicadores: Total de Receitas, Total de Despesas, Margem de Lucro, Total de Receitas por Componente, Total de Despesa do Componente e por ano com a hierarquia por Tipo e Componente, e os segmentos onde Receitas e Despesas são maiores e menores. Onde, **Tipo** refere-se a Receitas e Despesas e **Componente** refere-se à classificação das receitas e despesas em Administrativo, Aluguéis, Franquias, Impostos, Investimentos, Licenciamento, Marketing, Publicidade, Salários, Segurança, Tecnologia e Vendas.
<br><br>
## Fonte de Dados
Nessa análise, foi utilizado um dataset em formato .xlsx (Excel) chamado “Dados Financeiros”. Trata-se de dados fictícios apenas com o intuito de demonstrar uma análise financeira.
<br><br>
## Preparação do Dados
A exploração dos dados foi realizada para entender a estrutura da tabela e os tipos de dados, afim de localizar e conhecer as informações necessárias que seriam transformadas no Power Query antes de iniciar a análise.
<br>
Esse dataset apresenta alguns erros de tipo de dados e de layout das colunas e linhas e foram transformados com o Power Query após a importação no Power BI.
<br><br>
**Transformações no Power Query:**
<br>
Título de coluna não reconhecido – selecionada a opção “usar a primeira linha como cabeçalho”
<br>
Layout com colunas e linhas invertidas – transformado coluna para linha e elinha para coluna com a aplicação do código do Pivot de Tabela na última alteração efetuada: =Table.UnpivotOthesColumns(#”TipoAlterado1”, {“Tipo”, ”Componente”}, “Data”, “Valor”)
<br>
Coluna data sem hierarquia – convertida para tipo data na coluna “Data”
<br><br>
## Análise Exploratória
Essa análise tem o objetivo de apresentar os indicadores solicitados pela empresa, como: Total de Receitas, Total de Despesas, Margem de Lucro, Total de Receitas por Componente, Total de Despesa do Componente e por ano com a hierarquia por Tipo e Componente, e os segmentos onde Receitas e Despesas são maiores e menores. 
<br><br>
Para isso foi necessário criar uma tabela de medidas para efetuar os cálculos, obter os resultados e então criar as visualizações com os indicadores.
<br><br>
**Criando Tabela de Medidas:**
<br> 
Power Query > Inserir Dados > MedidasIndicadoresFinanceiros
<br><br>
Despois, foi criada cada medida com seus respectivos códigos:
<br><br>
**Criando Medida TotalReceitas:**
<br> 
Medida: Tabela MedidasIndicadoresFinanceiros > Nova Medida > TotalReceitas
<br> 
Código: TotalReceitas = CALCULATE(SUM(DadosFinanceiros[Valor]),DadosFinanceiros[Tipo]="Receitas")
<br><br>
**Criando Medida TotalDespesas:**
<br> 
Medida: Tabela MedidasIndicadoresFinanceiros > Nova Medida > TotalDespesas
<br> 
Código: TotalDespesas = CALCULATE(SUM(DadosFinanceiros[Valor]),DadosFinanceiros[Tipo]="Despesas")
<br><br>
**Criando Medida Lucro:**
<br> 
Medida: Tabela MedidasIndicadoresFinanceiros > Nova Medida > Lucro
<br> 
Código: Lucro = [TotalReceitas]-[TotalDespesas]
<br><br>
**Criando Medida MargemLucro:**
<br> 
Medida: Tabela MedidasIndicadoresFinanceiros > Nova Medida > MargemLucro
<br> 
Código: MargemLucro = DIVIDE([Lucro],[TotalReceitas],0)
<br><br>
## Visualização dos Dados
<br>
<img align="denter" width="900"  src="https://github.com/roseneidereis/Projeto-PowerBI-Analise-Financeira/blob/main/AnaliseFinanceira.PNG">
<br><br>






