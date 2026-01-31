# ⚙️ CONFIGURAÇÃO DO REPOSITÓRIO GIT

## ✅ JÁ ESTÁ CONFIGURADO!

O instalador já vem com o link do repositório Git **embutido no código**, exatamente como o instalador original do Atendechat.

**Não é necessário configurar nada!** O instalador clonará automaticamente do repositório correto.

---

## 📝 Link Configurado

O link do Git já está configurado em: **`variables/_app.sh`**

```bash
link_git="https://atendechat:REDACTED@github.com/atendechat/AtendechatApioffcial.git"
```

Este link:
- ✅ Já inclui o token de autenticação
- ✅ Não pede usuário e senha
- ✅ Clone automático durante instalação
- ✅ Funciona imediatamente

---

## 🚀 Como Usar

Simplesmente execute o instalador:

```bash
./install_primaria
```

O instalador irá:
1. Pedir senha do banco
2. Pedir nome da instância
3. Pedir limites e portas
4. **Clonar automaticamente do Git** (sem parar!)
5. Continuar a instalação

**Sem solicitar nada sobre Git!**

---

## 🔐 Segurança do Token

⚠️ **IMPORTANTE:** O token está embutido no código!

**Proteja este arquivo:**

```bash
chmod 600 variables/_app.sh
chown root:root variables/_app.sh
```

**Não compartilhe** este instalador publicamente, pois contém o token de acesso.

---

## 🔄 Trocar Repositório (Opcional)

Se precisar usar outro repositório, edite **`variables/_app.sh`**:

### Para outro repositório privado:
```bash
link_git="https://usuario:TOKEN@github.com/usuario/outro-repo.git"
```

### Para repositório público:
```bash
link_git="https://github.com/usuario/repo-publico.git"
```

---

## ✅ Pronto!

**Não precisa fazer nada!** O instalador já está configurado e pronto para usar.

Apenas execute:
```bash
./install_primaria
```

E aproveite a instalação automatizada! 🚀

---

**Versão**: 1.1.0  
**Status**: ✅ Pré-configurado  
**Token**: ✅ Embutido no código

### Opção 1: Repositório Público (Recomendado)

Se seu repositório Atendechat é **público**, apenas edite o arquivo:

**`variables/_app.sh`**

Encontre a linha:
```bash
link_git="https://github.com/usuario/atendechat.git"
```

Substitua por:
```bash
link_git="https://github.com/SEU_USUARIO/SEU_REPOSITORIO.git"
```

**Exemplo:**
```bash
link_git="https://github.com/joaosilva/atendechat-v2.git"
```

---

### Opção 2: Repositório Privado (Com Token)

Se seu repositório é **privado**, você precisa usar um **token de acesso**:

#### Passo 1: Gerar Token no GitHub

1. Acesse: https://github.com/settings/tokens
2. Clique em "Generate new token" → "Generate new token (classic)"
3. Dê um nome: "Instalador Atendechat"
4. Marque a permissão: `repo` (acesso completo a repositórios)
5. Clique em "Generate token"
6. **COPIE O TOKEN** (você não verá novamente!)

#### Passo 2: Configurar no Instalador

Edite o arquivo **`variables/_app.sh`**

Substitua:
```bash
link_git="https://github.com/usuario/atendechat.git"
```

Por:
```bash
link_git="https://SEU_TOKEN@github.com/SEU_USUARIO/SEU_REPOSITORIO.git"
```

**Exemplo com token:**
```bash
link_git="https://REDACTED@github.com/joaosilva/atendechat-private.git"
```

---

### Opção 3: Repositório Privado (Usuário e Senha)

⚠️ **Não recomendado** (GitHub descontinuou autenticação por senha)

Mas se seu Git aceita, use:
```bash
link_git="https://USUARIO:SENHA@github.com/SEU_USUARIO/SEU_REPOSITORIO.git"
```

**Exemplo:**
```bash
link_git="https://joaosilva:MinhaSenh@123@github.com/joaosilva/atendechat.git"
```

---

## 🔐 Segurança

### ⚠️ ATENÇÃO COM TOKENS E SENHAS

O arquivo `variables/_app.sh` contém credenciais sensíveis!

**Proteja este arquivo:**

```bash
# Depois de configurar, proteja o arquivo
chmod 600 variables/_app.sh
chown root:root variables/_app.sh
```

**Nunca compartilhe** este arquivo com as credenciais configuradas!

---

## 📋 Checklist de Configuração

Antes de instalar, verifique:

- [ ] Editei o arquivo `variables/_app.sh`
- [ ] Coloquei a URL correta do meu repositório
- [ ] Se privado, adicionei o token ou credenciais
- [ ] Testei o clone manualmente (opcional, veja abaixo)
- [ ] Protegi as permissões do arquivo

---

## 🧪 Testar Configuração (Opcional)

Antes de rodar o instalador, teste se o Git funciona:

```bash
# Teste manual do clone
cd /tmp
git clone https://SEU_TOKEN@github.com/usuario/repo.git teste-clone

# Se funcionar, verá:
# Cloning into 'teste-clone'...
# remote: Counting objects...
# Receiving objects: 100%

# Se não funcionar, verá erro de autenticação

# Limpar teste
rm -rf teste-clone
```

---

## 🚀 Repositórios Alternativos

### GitLab
```bash
link_git="https://TOKEN@gitlab.com/usuario/repo.git"
```

### Bitbucket
```bash
link_git="https://usuario:TOKEN@bitbucket.org/usuario/repo.git"
```

### Servidor Git Próprio
```bash
link_git="https://usuario:senha@git.seudominio.com/repo.git"
# ou
link_git="git@git.seudominio.com:usuario/repo.git"  # SSH
```

---

## ❓ Perguntas Frequentes

### Por que não pede usuário/senha durante instalação?

Para automatizar completamente o processo e evitar problemas de interação durante a instalação. Tudo é configurado de uma vez só no arquivo.

### Posso usar SSH ao invés de HTTPS?

Sim, mas precisa configurar as chaves SSH antes:

```bash
# No servidor, como usuário deploy
sudo su - deploy
ssh-keygen -t rsa -b 4096 -C "deploy@servidor"
cat ~/.ssh/id_rsa.pub
# Adicione esta chave no GitHub/GitLab em SSH Keys

# Depois configure:
link_git="git@github.com:usuario/repo.git"
```

### E se eu quiser trocar o repositório depois?

1. Edite `variables/_app.sh`
2. Atualize a variável `link_git`
3. Nas próximas instalações usará o novo repo

### Preciso configurar em cada servidor?

Sim, cada servidor precisa ter o `variables/_app.sh` configurado com as credenciais corretas.

---

## 🔄 Fluxo de Instalação

```
1. Configurar variables/_app.sh ← VOCÊ ESTÁ AQUI
2. Fazer upload do instalador
3. Dar permissões
4. Executar install_primaria
5. Instalador clona automaticamente do Git configurado
6. Restante da instalação continua
```

---

## 📝 Exemplo Completo de Configuração

**Arquivo: `variables/_app.sh`**

```bash
#!/bin/bash
#
# Variables to be used for app configuration.

# app variables

jwt_secret=$(openssl rand -base64 32)
jwt_refresh_secret=$(openssl rand -base64 32)

db_pass=$(openssl rand -base64 32)

db_user=$(openssl rand -base64 32)
db_name=$(openssl rand -base64 32)

deploy_email=deploy@deploy.com
deploy_password=deploybotmal

# CONFIGURE SEU REPOSITÓRIO AQUI
# Repositório Público
link_git="https://github.com/meuusuario/atendechat.git"

# OU Repositório Privado com Token
# link_git="https://ghp_SEU_TOKEN_AQUI@github.com/meuusuario/atendechat-private.git"

# OU GitLab
# link_git="https://TOKEN@gitlab.com/meuusuario/atendechat.git"

# OU SSH (configure chaves antes!)
# link_git="git@github.com:meuusuario/atendechat.git"
```

---

## ✅ Pronto!

Depois de configurar o `variables/_app.sh`, você pode:

1. Fazer upload do instalador
2. Executar `./install_primaria`
3. O instalador irá clonar automaticamente do repositório configurado
4. **Sem pedir usuário/senha durante a instalação!**

---

## 🆘 Problemas Comuns

### Erro: "Authentication failed"
- ✅ Verifique se o token está correto
- ✅ Verifique se o token tem permissão `repo`
- ✅ Verifique se não há espaços na URL

### Erro: "Repository not found"
- ✅ Verifique se a URL está correta
- ✅ Verifique se o repositório existe
- ✅ Verifique se tem acesso ao repositório

### Erro: "Permission denied (publickey)"
- ✅ Você está usando SSH sem configurar as chaves
- ✅ Use HTTPS com token ao invés de SSH
- ✅ Ou configure as chaves SSH corretamente

---

**Versão**: 1.0.0  
**Última Atualização**: Dezembro 2025  
**Compatibilidade**: Instalador Atendechat 1.0.0

**⚡ Configure uma vez, instale quantas vezes precisar!**
