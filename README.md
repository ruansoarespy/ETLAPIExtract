# 🚀 ETL e Dashboard de Preços do Bitcoin

📊 **Coleta, tratamento e visualização em tempo real do preço do Bitcoin**, com **Python, PostgreSQL, SQLAlchemy e Streamlit**, totalmente automatizado e hospedado na nuvem (**Render**).

---

## 🧩 Visão Geral

Este projeto implementa um pipeline **ETL completo** que:

- Extrai o preço atual do Bitcoin via API pública da Coinbase.  
- Transforma os dados (limpeza, formatação e timestamp).  
- Carrega no PostgreSQL.  
- Exibe tudo em tempo real num dashboard interativo com Streamlit.  

> 💡 O projeto foi implantado na plataforma **Render**, funcionando 24/7 como um processo automatizado.

---

## ⚙️ Tecnologias Utilizadas

- **Python 3.10+**  
- **PostgreSQL**  
- **SQLAlchemy**  
- **Streamlit**  
- **python-dotenv**  
- **requests**, **pandas**  
- **Render** (deploy)

---

## 🗂️ Estrutura do Projeto

~~~text
ETLAPIExtract/
│
├── app/
│   └── dashboard_01.py        # Dashboard Streamlit
│
├── src/
│   ├── database.py            # Modelo da tabela (SQLAlchemy)
│   ├── pipeline_00.py         # Versão inicial de teste (ETL simples)
│   └── pipeline_01.py         # ETL completo com PostgreSQL
│
├── .env                       # Variáveis de ambiente (não versionar)
├── .gitignore                 # Ignora venv, .env etc.
├── requirements.txt           # Dependências do projeto
└── README.md                  # Este arquivo
~~~

---

## ⚡ Configuração e Execução Local

### 1. Clonar o repositório
~~~bash
git clone https://github.com/seuusuario/ETLAPIExtract.git
cd ETLAPIExtract
~~~

### 2. Criar e ativar o ambiente virtual

**Linux / macOS**
~~~bash
python -m venv .venv
source .venv/bin/activate
~~~

**Windows (CMD)**
~~~cmd
python -m venv .venv
.venv\Scripts\activate
~~~

**Windows (PowerShell)**
~~~powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
~~~

### 3. Instalar dependências
~~~bash
pip install -r requirements.txt
~~~

### 4. Criar um arquivo `.env` na raiz do projeto

Crie um arquivo `.env` (NÃO versionar) com as seguintes variáveis:

~~~text
POSTGRES_USER=seu_usuario
POSTGRES_PASSWORD=sua_senha
POSTGRES_HOST=seu_host
POSTGRES_PORT=5432
POSTGRES_DB=seu_banco
~~~

---

## 🔄 Executar o ETL

Para iniciar a coleta automática de dados a cada **15 segundos**:
~~~bash
python src/pipeline_01.py
~~~

> Use `CTRL+C` no terminal para interromper o processo.

---

## 📊 Executar o Dashboard

Em outro terminal (com o mesmo venv ativado), execute:
~~~bash
streamlit run app/dashboard_01.py
~~~

Abra no navegador:
http://localhost:8501


---

## 🌍 Deploy na Render

Resumo das configurações usadas na Render:

- **ETL**: registrado como **Background Worker** (não precisa expor porta).  
- **Dashboard**: registrado como **Web Service** (Streamlit).  
- **Start command (exemplo para Streamlit Web Service)**:
~~~bash
streamlit run app/dashboard_01.py --server.port 10000 --server.address 0.0.0.0
~~~
- Adicione as mesmas variáveis do `.env` no painel de **Environment** da Render.

Documentação Render: https://render.com/docs

---

## 📈 Exemplo de Saída (ETL)
~~~text
Tabela criada/verificada com sucesso!
Iniciando ETL com atualização a cada 15 segundos... (CTRL+C para interromper)
[2025-11-05 19:45:54] Dados salvos no PostgreSQL!
[2025-11-05 19:46:10] Dados salvos no PostgreSQL!
~~~

---

## ✨ Resultados & Features

- Coleta automática do preço do Bitcoin.  
- Persistência em PostgreSQL via SQLAlchemy.  
- Dashboard com:
  - gráfico de evolução do preço,
  - tabela de registros recentes,
  - métricas (preço atual, máximo, mínimo).

---

## 📝 Observações e Boas Práticas

- Nunca versionar o arquivo `.env` com credenciais.  
- Para produção, use variáveis de ambiente seguras no provedor (Render).  
- Para escalabilidade, considerar:
  - aumentar intervalos ou usar filas para limitar chamadas à API;
  - configurar monitoramento e logs no Render.

---

## 📬 Contato

**Ruan Ferreira Soares**  
📧 ruanferreirasoares@gmail.com  
💼 LinkedIn: https://linkedin.com/in/seu-linkedin  
🐙 GitHub: https://github.com/seuusuario



