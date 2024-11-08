# O que é Docker?

Docker é uma plataforma de código aberto que permite empacotar software em contêineres e executá-los em qualquer máquina com o Docker instalado. 

O Docker é uma ferramenta que facilita a criação, implantação e gerenciamento de aplicativos, permitindo que as equipes de desenvolvimento garantam que o aplicativo seja executado da mesma forma em qualquer ambiente.

# Comandos Docker:

- `docker container run -it --name terraform -v $(pwd):/mnt/documents --entrypoint /bin/sh hashicorp/terraform` → pra rodar o terraform no docker
- `docker run` → Irá iniciar um container.
- `sudo usermod -aG docker $USER` → Usado para configurar o linux após a instalação, tirando a necessidade de usar o sudo ao rodar o docker
- `docker pull` → Irá baixar uma img docker
- `docker ps` → Irá listar os containers em andamento
    - `-a` → Com está flag lista os containers parados também
- `docker container ls` → mesma coisa que o docker ps
- `docker stop (id ou nome container)` → Irá parar um container em execução
    - `-t=0` → Irá parar de uma vez
- `docker start (id ou nome do container)` → Irá iniciar um container parado
- `docker exec -it (id ou nome do container) bash` → Irá acessar um container, ou rodar algum comando
    - `-it` →Entrar no container
    - `docker run -it + Image (ubuntu) + comando (bash)` → exemplo
- `docker (un)pause (id ou nome do container)` → Pausa e despausa um container
- `docker rm (id ou nome do container)` → Remove um container
- `docker run -d` → Irá rodar um container no modo backgroud
- `docker rm id --force` → Irá remover a força um container
- `docker port +id` → Irá mostrar a porta em que o container estará rodando
    - `-p` → Irá definir uma porta no run
- `docker images ou docker images ls` → Lista as img de container
- `docker inspect + id da imagem` → Inspeciona uma imagems
- `docker history + id da imagem` → Valida as camadas de uma img
- `docker build -t <seu-nome-de-usuario-do-docker-hub>/app-node:1.0 .` → Irá criar uma imagem
    - `-t` → Irá taguear uma imagem
- `docker stop $(docker container ls -q)` → Para todos os containers
- `docker login -u <username> -p <senha>` → Loga no dockerhub
- `docker push` → Sobe uma imagem para um determinado repositorio
- `docker rm $(docker container ls -q)` →Apaga containers
- `docker rmi $(docker image ls -aq)` → Apaga imgs
- `docker ps -s` →Mostra o tamanho de armazenamento dos container
- `docker run -it -v /home/<nome do usuario>/volume-docker:/app ubuntu bash` → Definindo um volume para um container (bind gerenciado pelo host)
    - `docker run -it --mount type=bind,source=/home/<nome do usuario>/volume- docker,target=/app ubuntu bash` → Outra forma de montar volume (bind)
- `docker volume ls` → Lista os volumes do sistema
- `docker volume create <nome do volume>` → Cria um volume
- `docker run -it -v <nome do volume>:/app ubuntu bash` → Cria um volume do tipo volume mesmo (gerenciado pelo docker)
    - `docker run -it --mount source=<nome do volume>, target=/app ubuntu bash` → outra forma de exec
- `docker run -it --tmpfs=/app ubuntu bash` → Executa um container com vol do tipo tmpfs
    - `docker run -it --mount type=tmpfs,destination=/app ubuntu bash`  → outra forma de exec
- `docker inspect + id do container` → Inspeciona o container
- `docker network ls` → lista as redes do docker
- `docker network create --driver bridge minha-bridge` → Cria uma rede
- `docker container rm $(docker ps -aq) --force` → remove todos os container
- `docker run -d --name pong --network minha-bridge ubuntu sleep 1d` → criação teste rede bridge
- `docker run -d --network none ubuntu sleep 1d` →criação teste rede none
- `docker run -d --network host luc4sbr1to/app-node:1.2` → Criação teste  rede host
- `docker-compose up` → Executa o yml no docker-compose
    - `-d` → Roda no modo backgroud
- `docker-compose down` → Desliga todos os containers criados com o docker-compose down
