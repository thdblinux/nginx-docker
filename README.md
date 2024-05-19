# Projeto NGINX WEB PROXY DOCKER

- NGINX
- Certificado Self-Signed SSL
- Proxy reverso
- Balanceamento de cargas
- Otimização do NGINX 

**NGINX** Como o NGINX funciona?

As solicitações web em outros servidores, como o Apache, funcionam de forma individual, ou seja, o usuário solicita uma página por meio do Protocolo HTTP ou HTTPS, que processa e retorna o resultado. Esse processo é chamado de thread individual, que é feita para cada solicitação requisitada ao servidor.

O NGINX funciona com base em eventos. Assim, em vez de fazer uma solicitação direta ao servidor, ele executa um processo mestre, chamado worker, e vários processos de trabalho, chamados conexões worker. Todo `esse processo trabalha continuamente e de forma assíncrona`.

Dessa forma, quando há um pedido de processamento, ele é feito pelas conexões worker, que fazem a solicitação ao processo mestre que, por sua vez, processa e retorna o resultado. Essa funcionalidade permite a manipulação de inúmeras conexões simultâneas, pois cada conexão worker é capaz de processar 1024 solicitações.

Quando o servidor está operando, cada worker carrega uma cadeia de módulos, dependendo de como a configuração é feita durante a instalação. Dessa forma, cada solicitação é feita com todos os recursos configurados em operação.

![alt text](/assets/server3.png)

**Proxy reverso e Balanceamento de Carga**
Um proxy reverso na prática funciona como um servidor intermediário entre os computadores de uma rede e o servidor web. Ele é utilizado como cache de página, com a finalidade de economizar recursos de banda e agilizar o seu carregamento. Ele é um servidor web que recebe as solicitações de conexão e gerencia o que será preciso requisitar no servidor principal ou verifica se a solicitação já está disponível em cache. O NGINX, portanto, oferece esse recurso, que pode ser facilmente configurado em seu arquivo de configuração.

O balanceamento de carga é um recurso extremamente importante para quem precisa de um site com alta disponibilidade, pois ele permite a distribuição das requisições de serviço entre os servidores.

Dessa forma, quando há um acréscimo nas solicitações ao servidor, como o aumento do tráfego, o NGINX consegue direcionar o fluxo para outros servidores que estejam no arquivo de configuração.

Existem três possibilidades de distribuição da carga no NGINX. Ela pode ser feita igualmente entre os servidores configurados, ser distribuída para o servidor que tenha poucas conexões no momento ou é possível determinar o endereço IP de cada cliente para cada servidor específico.


![alt text](/assets/nginxflow.drawio.png)

Neste projeto, configurei o proxy reverso e o balanceador de carga. Além disso, otimizei o servidor para melhorar a performance do Nginx e apliquei políticas de segurança, gerando um certificado SSL para aumentar a segurança e autenticidade dos sites. Os servidores foram provisionados via Docker usando Docker Compose, garantindo um ambiente replicável e gerenciável. Também criei um servidor de backup para garantir que, caso os outros servidores fiquem offline, o serviço continue disponível. Com isso, todas as requisições são distribuídas de forma a atingir alta disponibilidade dos serviços web de acordo com a demanda.

**Servidores ONLINE**
![alt text](/assets/server1.png)
![alt text](/assets/server2.png)
![alt text](/assets/nginx4.png)

**Servidores OFFLINE**
![alt text](/assets/nginx5.png)
**Servidor BACKUP ONLINE**
![alt text](/assets/serverbkp.png)















## Link references

- [Docker Compose overview](https://docs.docker.com/compose/)
- [Docker CLI Cheat Sheet](https://docs.docker.com/get-started/docker_cheatsheet.pdf)
- [docker-compose cheatsheet](https://devhints.io/docker-compose)
- [Docker Hub Official build of Nginx ](https://hub.docker.com/_/nginx)
- [Criar um certificado SSL](https://learn.microsoft.com/pt-br/power-bi/developer/visuals/create-ssl-certificate#generate-a-certificate-manually)
- [Deploying NGINX Docker](https://docs.nginx.com/nginx/admin-guide/installing-nginx/installing-nginx-docker/)
- [SSL Termination for TCP Upstream Servers](https://docs.nginx.com/nginx/admin-guide/security-controls/terminating-ssl-tcp/)
- [Setting Up an NGINX Demo Environment](https://docs.nginx.com/nginx/deployment-guides/setting-up-nginx-demo-environment/)
- [Creating NGINX Plus and NGINX Configuration Files](https://docs.nginx.com/nginx/admin-guide/basic-functionality/managing-configuration-files/)
- [NGINX HTTP Load Balancing](https://docs.nginx.com/nginx/admin-guide/load-balancer/http-load-balancer/)
- [NGINX Gzip Common MIME types ](https://forum.nginx.org/read.php?2,265879)
- [SSL certficate Configuring HTTPS and HTTP servers](https://nginx.org/en/docs/http/configuring_https_servers.html)