# Docker Instances

Neste repositório, você encontrará todas as configurações necessárias para gerenciar suas instâncias Docker de forma eficiente, sem a necessidade de reconfigurar manualmente tudo após descartar as instâncias principais. A configuração inclui o uso do Cloudflare Tunnel para expor suas aplicações containerizadas de forma segura.

Usando o Cloudflare Tunnel, você pode expor seus contêineres Docker para a internet de forma simples e segura.

Basta configurar o túnel para ouvir em portas específicas. Assim, sempre que você iniciar um novo contêiner remotamente, direcionando a saída para uma dessas portas pré-configuradas, sua aplicação ficará quase que instantaneamente disponível em seu domínio.

### Observações

Este repositório foi criado para que qualquer pessoa interessada em simplificar o **deploy de suas aplicações** possa implementá-lo, utilizando o Cloudflare Tunnel como uma camada de segurança e acesso remoto.

---

### Requisitos

Para começar a usar esta solução, você precisará ter os seguintes requisitos:

- Um dispositivo com **Docker** instalado.

### Acesso via Cloudflare Tunnel (Opcional)

Se você planeja disponibilizar suas aplicações para acesso remoto de forma segura, será necessário ter:

- Uma conta no **Cloudflare**.
- Um **domínio** (ex: `www.exemplo.com`) para adicionar ao Cloudflare e configurar o redirecionamento para seus contêineres via tunelamento.
- Noção de controle de Politicas e Aplicativos pelo Cloudflare Zero Trust. (Pois é recomendado limitar os acessos ao /admin do Vaultwarden e talvez até o próprio serviço em casos mais extremos)

---

### Como usar este repositório

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/ofcoliva/docker-instances.git
    cd docker-instances
    ```
2.  **Configurações do Cloudflare Tunnel:**
    Se você for usar o Cloudflare Tunnel, siga as instruções oficiais para criar um túnel e obter o token. Adicione o token ao seu arquivo de configuração do Docker.
3.  **Ajuste os arquivos de configuração:**
    Modifique os arquivos `docker-compose.yml` e outros arquivos de configuração para atender às suas necessidades. Lembre-se de alterar o nome de domínio e as portas conforme suas aplicações.
4.  **Inicie os contêineres:**
    Execute o comando `docker-compose up -d` no terminal para iniciar suas aplicações em segundo plano e sem o parametro `-d` para visualizar o que está acontecendo.

---

### Observação

1. Não utilize seus tokens e credênciais dentro do docker-compose.yml, pode comprometer sua segurança.

2. Utilize sempre o arquivo `.env` para definir suas váriaveis de ambiente.

3. Em hipótese alguma remova-o do .gitignore, pois ao fazer um push para um repositório remoto, você pode estar expondo suas credênciais de acesso a terceiros.
