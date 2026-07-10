# 🏢 TOTVS - Fundamentos de Engenharia de Dados e Machine Learning

Este repositório contém um pipeline ETL (Extract, Transform, Load) focado em **People Analytics** e automação de regras de negócio para sistemas de Recursos Humanos corporativos da TOTVS.

## 🧠 Arquitetura e Decisão Técnica (Rule-Based Automation)

Em vez de utilizar modelos de IA Generativa (LLMs), este pipeline foi projetado utilizando o conceito de **Automação Baseada em Regras (Rule-Based ETL)**. 

### Por que esta abordagem foi escolhida?
1. **Determinismo:** No cenário de RH e feedbacks internos, as mensagens não podem sofrer com "alucinações" comuns de IAs. O comportamento do código precisa ser 100% previsível.
2. **Custo e Escalabilidade:** Processar milhares de colaboradores usando APIs de IA gera custos financeiros elevados por token. Uma automação estruturada em Python consome zero recursos externos.
3. **Performance:** A transformação de dados ocorre localmente e de forma instantânea, eliminando a latência de chamadas de rede para APIs de terceiros.

---

## 🛠️ Detalhes das Etapas do Pipeline

1. **Extract (Extração):** O script lê uma lista de controle (`totvs_ids.csv`) contendo os identificadores dos funcionários e busca seus dados completos em um repositório semiestruturado (`colaboradores_totvs.json`).
2. **Transform (Transformação):** O pipeline avalia os indicadores de performance (`performance_score`) e retenção (`years_at_company`) através de condicionais lógicas estruturadas, gerando planos de ação e feedbacks dinâmicos e precisos para cada perfil.
3. **Load (Carregamento):** Os dados enriquecidos e categorizados são persistidos de volta no sistema de arquivos local (`totvs_resultado_final.json`), deixando os dados prontos para consumo por ferramentas de BI (como TOTVS Fast Analytics) ou prontos para alimentar modelos preditivos de Machine Learning.

## 💻 Stack Tecnológica

* **Python 3**
* **Pandas** (Tratamento estruturado de tabelas)
* **JSON** (Manipulação de dados semiestruturados aninhados)
