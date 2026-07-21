# Demo Django + Tailwind com Docker

Este é um projeto simples construído com **Django** (framework web em Python), banco de dados **SQLite**, estilizado com **Tailwind CSS** (via CDN) e preparado para rodar em containers utilizando o **Docker Compose**. 

O projeto serve como uma demonstração (Aula de Programação Web) contendo uma página inicial que lista mensagens salvas no banco de dados, uma página "Sobre" e o poderoso painel de Administração do Django (`/admin`).

## 📸 Telas do Projeto

### 1. Página Inicial
A página inicial (`/`) exibe os cards com as tecnologias usadas e a listagem de mensagens carregadas diretamente do SQLite em tempo real. Cada mensagem agora também exibe sua **Categoria** associada (quando houver) e suas respectivas **Tags** (no formato `#tag`).

![Página Inicial](docs/nova-tag.png)

# Página de Forms
Nesta imagem podemos ver o formulário para adicionar uma nova mensagem ao banco de dados.
![Página de Forms](docs/form.png)


# Integração a pagina inicial
Nesta imagem podemos ver a página inicial com as mensagens cadastradas.
![Página Inicial](docs/botao-form.png)

# Remover mensagem
Nesta imagem, podemos ver a parte de remover mensagem por meio do id/remover
![Remover mensagem](docs/deletar.png)

# Editar mensagem
Acessando a url mensagens/id/editar podemos editar a imagem e atualizar no banco
![Editar mensagem](docs/editar.png)


---

## 🚀 Como Executar o Projeto

Como a aplicação já foi "dockerizada", rodá-la no seu ambiente local é extremamente rápido. Não é preciso instalar o Python na sua máquina, apenas o Docker.

### Pré-requisitos
* **Docker** e **Docker Compose** instalados e rodando.

### Passo a Passo

1. **Faça o clone do projeto** e entre na pasta raiz (onde fica o `docker-compose.yml`):
   ```bash
   git clone <url-do-seu-repositorio>
   cd django_app
   ```

2. **Suba o container com o Docker**:
   Execute o comando abaixo. Ele fará o build da imagem, aplicará as migrações no banco de dados (graças ao script no `docker-compose.yml`) e subirá o servidor.
   ```bash
   docker compose up --build
   ```
   *(Dica: Se o terminal travar no log e você quiser rodar em segundo plano, adicione `-d` no final: `docker compose up -d --build`)*

3. **Acesse no seu navegador**:
   - 🏠 Página Principal: [http://localhost:8000](http://localhost:8000)
   - ℹ️ Sobre: [http://localhost:8000/sobre/](http://localhost:8000/sobre/)
   - ⚙️ Painel de Admin: [http://localhost:8000/admin/](http://localhost:8000/admin/)

---

## 🛠 Como acessar o Painel Admin?

Para fazer login no `/admin` e adicionar novas mensagens (como visto na sua imagem), você precisa criar um superusuário.

Com o container rodando, abra **outro terminal** e rode o seguinte comando:
```bash
docker compose exec web python manage.py createsuperuser
```
*O terminal pedirá um nome de usuário, e-mail (opcional, pode dar enter) e uma senha.*
Depois disso, é só ir no `/admin` e logar com os dados criados!

---

## 📂 Estrutura do Projeto

* `core/`: Configurações principais do projeto Django (`settings.py`, `urls.py`).
* `home/`: O aplicativo que gerencia os modelos (`Mensagem`, `Categoria` e `Tag`) e as views (`index` e `sobre`).
* `templates/home/`: Os arquivos HTML usando **Tailwind CSS**.
* `Dockerfile` e `docker-compose.yml`: Receita e orquestração do ambiente Docker.

---
**Feito para a aula de Programação Web · Django 6**
