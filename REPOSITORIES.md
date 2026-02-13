# 📦 Repositórios Ativos

## ☁️ Infraestrutura & GitOps

### `k8s-helm-templates` 🎯 Principal
**Tipo:** Helm Chart Template (reusável)  
**Descrição:** Template Helm centralizado para deploy de múltiplas aplicações em Kubernetes. Suporta Java, Python, Node.js e outras stacks via valores parametrizáveis.  
**Stack:** Helm, YAML, Kubernetes  
**Features:**
- Templates genéricos: Deployment, Service, Ingress, ConfigMap, Secret, HPA
- Health check probes (liveness/readiness) configuráveis
- Port mapping automático (service 80 → container 8080)
- Suporte a múltiplas linguagens/frameworks
- Versionado via Chart.yaml e publicado no Helm Chart Repository (GitHub Pages)
- CI/CD: Publicação automática via `chart-releaser-action`

**URL Repo:** `https://rg-hermann.github.io/k8s-helm-templates/`

---

### `java-bootstrap-infra` 🚀
**Tipo:** GitOps Configuration (ArgoCD)  
**Descrição:** Repositório de configuração declarativa para deploy automático da aplicação Java em Kubernetes via ArgoCD.  
**Stack:** Helm, YAML, Kubernetes, ArgoCD  
**Features:**
- Consumidor do `k8s-helm-templates` v0.0.3
- `values-dev.yaml`: 1 replica, desenvolvimento
- `values-prod.yaml`: 3 replicas, autoscaling, TLS, produção
- `application.yaml` & `application-prod.yaml`: Manifestos ArgoCD
- Automação: Dependabot (semanal) + Auto-merge + ArgoCD sync contínuo
- Probe paths: `/actuator/health/liveness`, `/actuator/health/readiness` (Spring Actuator)

**Namespaces:** `dev-apps`, `prod-apps`  
**Status:** ✅ Ativo (v1.0.1)

---

### `python-bootstrap-infra` 🐍
**Tipo:** GitOps Configuration (ArgoCD)  
**Descrição:** Repositório de configuração declarativa para deploy automático da aplicação Python em Kubernetes via ArgoCD.  
**Stack:** Helm, YAML, Kubernetes, ArgoCD  
**Features:**
- Consumidor do `k8s-helm-templates` v0.0.3
- `values-dev.yaml`: 1 replica, desenvolvimento
- `values-prod.yaml`: 3 replicas, autoscaling, TLS, produção
- `application.yaml` & `application-prod.yaml`: Manifestos ArgoCD
- Automação: Dependabot (semanal) + Auto-merge + ArgoCD sync contínuo
- Probe paths: `/health` (FastAPI)
- Documentação: `AUTOMATION.md` explicando o fluxo GitOps

**Namespaces:** `dev-apps`, `prod-apps`  
**Status:** ✅ Ativo (v1.0.1)

---

### `modules_terraform` 🏗️
**Tipo:** IaC Modules (reusável)  
**Descrição:** Módulos Terraform reutilizáveis para provisionar recursos Azure de forma padronizada e segura.  
**Stack:** Terraform, HCL, Azure  
**Módulos Disponíveis:**
- `aks` - Azure Kubernetes Service
- `acr` - Azure Container Registry
- `function_app` - Azure Functions
- `key_vault` - Key Vault (secrets)
- `storage_account` - Storage Account
- `app_service` - App Service Plan
- Networking (VNet, Subnet, NSG, etc.)

**Features:**
- Versionamento semântico
- Documentação detalhada (inputs, outputs, examples)
- Validação de entrada (type, default, validation blocks)
- Tags automáticas e padrões de naming

**Status:** ✅ Ativo

---

## ☕ Aplicações

### `java-bootstrap` 🎯 Template Profissional
**Tipo:** Aplicação Java (Spring Boot 3)  
**Descrição:** Template profissional de projeto Java 21 com enterprise-grade security, testing automatizado, qualidade de código e DevOps integrado.  
**Stack:** Java 21, Spring Boot 3, Maven, JUnit5  
**Features:**
- Spring Boot 3 com Actuator (health checks)
- Dockerfile otimizado (multi-stage, non-root user)
- Testes: JUnit5, JaCoCo (análise de cobertura)
- Code Quality: Checkstyle, SpotBugs, Trivy (segurança)
- CI/CD: GitHub Actions (Maven verify, Docker build, image push)
- Port: 8080
- Imagem: `ghcr.io/rg-hermann/java-bootstrap:latest`

**Endpoints:**
- `GET /` - Hello World
- `GET /actuator/health/liveness` - Kubernetes probe (liveness)
- `GET /actuator/health/readiness` - Kubernetes probe (readiness)

**Status:** ✅ Ativo

---

### `python-bootstrap` 🐍 Template Moderno
**Tipo:** Aplicação Python (FastAPI)  
**Descrição:** Aplicação FastAPI 3.12 com testes 100% coverage, code quality checks e deploy containerizado em Kubernetes.  
**Stack:** Python 3.12, FastAPI, Uvicorn, pytest  
**Features:**
- FastAPI com Pydantic config
- Testes: pytest com 100% code coverage
- Code Quality: Flake8, Black, isort, mypy (optional)
- Dockerfile: Python 3.12-slim, non-root user, HEALTHCHECK
- CI/CD: GitHub Actions (pytest, linting, Docker build, image push)
- Port: 8080
- Imagem: `ghcr.io/rg-hermann/python-bootstrap:latest`

**Endpoints:**
- `GET /` - Hello World
- `GET /health` - Health check (Kubernetes probe)
- `GET /api/info` - Informações da aplicação (versão, timestamp)
- `GET /actuator/health/liveness` - Liveness probe (alias)
- `GET /actuator/health/readiness` - Readiness probe (alias)

**Status:** ✅ Ativo

---

## 🛠️ DevOps & Automação

### `devops` 📋
**Tipo:** Portfólio & Scripts  
**Descrição:** Repositório principal com scripts e documentação de automação, CI/CD, IaC e boas práticas DevOps.  
**Stack:** Shell, Python, Terraform, Bash, YAML  
**Pastas:**
- `bash/` - Scripts shell para AWS, Azure, EC2, Lambda, RDS, etc.
- `python/` - Scripts Python para automação, limpeza de recursos
- `ansible/` - Playbooks Ansible para provisionamento e configuração
- `terraform/` - Exemplos de IaC modular
- `ci-cd/` - Exemplos de pipelines (GitHub Actions, Azure Pipelines)

**Status:** ✅ Ativo (Portfolio)

---

### `rg-hermann` 👤
**Tipo:** GitHub Profile Config  
**Descrição:** Repositório de configuração do perfil GitHub com README dinâmico, workflows de automação e métricas.  
**Workflows:**
- `profile-metrics.yml` - Gera SVG de métricas (lowlighter/metrics)
- `housekeeping.yml` - Atualiza data do último update (mensal)
- `snake.yml` - Animação de contribuições (GitHub Snake)
- `auto-merge.yml` - Auto-merge de PRs do Dependabot

**Status:** ✅ Ativo



---

## 📊 Resumo Estatístico

| Categoria | Qtd | Status |
|-----------|-----|--------|
| **Infraestrutura/GitOps** | 3 | ✅ Ativos |
| **Aplicações** | 2 | ✅ Ativos |
| **IaC/Templates** | 1 | ✅ Ativo |
| **Automação/DevOps** | 1 | ✅ Ativo |
| **Profile/Pessoal** | 1 | ✅ Ativo |
| **Privado** | 1 | ✅ Ativo |
| **TOTAL** | **9** | **✅ Ativos** |

---

## 🔄 Fluxo de Automação Integrado

```
java-bootstrap / python-bootstrap
    ↓ (push + GitHub Actions)
    ├→ Teste, Build, Docker Push
    ├→ Atualiza -infra repo com nova tag
    │
java-bootstrap-infra / python-bootstrap-infra
    ↓ (Dependabot monitora k8s-helm-templates)
    ├→ Detecta nova versão do template
    ├→ Cria PR automaticamente
    ├→ Auto-merge quando checks passam
    │
    ↓ (ArgoCD monitora -infra repo)
    ├→ Detecta mudança em Chart.yaml
    ├→ Executa helm dependency update
    ├→ Sincroniza no Kubernetes
    │
k8s-helm-templates (modificações)
    ↓ (push)
    ├→ GitHub Actions publica versão (chart-releaser)
    ├→ Dependabot detecta em -infra repos
    └→ Ciclo se repete
```


---

**Última atualização:** 13 de fevereiro de 2026

