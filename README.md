# DATA PIPELINE


## Neste projeto aprendemos a fazer um pipeline completo de dados, desde a parte de sua extracao, sua transformacao, e seu carregamento (Famoso ETL) em um DataLake, usando dados do Twitter.

## Neste caso, pegamos a API do Twitter para coletar alguns dados de tweets de um twitter especifico em determinada data

## O projeto usa duas ferramentas principais, o Apache SPARK, e o Apache AIRFLOW

### Inicialmente criamos a nossa conta de developer do twitter
### Após isso, criamos um codigo para busca desses dados na api do twitter para jogar em um arquivo no estagio inicial do nosso datalake, estagio Bronze.
### Integramos esse primeiro job com o nosso orquestrador de workflows, o AIRFLOW, em um DAG

### Transformamos esse dado usando um script de transformacao, que faz a organizacao e a explosao dos dados para organizacao (nesse caso agrupado por data), e sendo usado em um cluster do Apache SPARK.
### Integramos esse novo script no mesmo DAG (AIRFLOW) do processo inicial.
### Esse script pega os dados do estagio bruto do datalake (BRONZE), transforma e coloca no estagio moderado do datalake (SILVER).

### Com esse dado no silver e o DAG do AIRFLOW já configurado, criamos um terceiro estagio para analise e business inteligence. Um terceiro arquivo executado em um cluster Spark separa esses dados pelo usuario que mandou o tweet, e a quantidade de likes, retweets e comentarios existem no dia. Foi usado para analise juntamente com o Apache ZEPPELIN