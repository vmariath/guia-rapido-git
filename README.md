
# Guia Rápido de Comandos Git

Este documento fornece uma visão geral dos principais comandos do Git para gerenciamento de repositórios. Ele é destinado a ajudar desenvolvedores a realizar operações básicas e intermediárias no Git.

## Sumário

1. [Configurações Iniciais](#configurações-iniciais)
2. [Comandos Básicos](#comandos-básicos)
3. [Trabalhando com Branches](#trabalhando-com-branches)
4. [Repositórios Remotos](#repositórios-remotos)
5. [Visualização de Histórico](#visualização-de-histórico)
6. [Desfazendo Mudanças](#desfazendo-mudanças)
## Configuração Git

Exibe informações de configuração da ferramenta Git e variáveis de configuração.
```
git config
```
Configurações do usuário.
```
-- global
```
Configuração do sistema.
```
-- system
```  
Configuração do repositório.
```
-- local
```

Para configuração do nome e email do usuário, utilizamos o comando.

```
git config --global user.name "nome_do_usuario"
```

```
git config --global user.email "email_usuario"
```

Para configuração da branch padrão
```
git config init.defaultBranch
``` 
Retornando o nome da branch padrão já configurada.
```
git config --global init.defaultBranch nome_branch_padrao
``` 
Alterando o nome da branch padrão globalmente para o nome desejado.

Para mais configurações podemos visitar a página de documentação do git.

[Documentação Git](https://git-scm.com/doc)

## Autenticação com GitHub

- Autenticação via Token

Entrar na página de configuração do seu perfil no GitHub, e ir na aba de Developers Settings > Personal Access Tokens > Tokens (classic) > Generate New Token (Classic).

Ao gerar o token, podemos configurar o tempo de expiração do mesmo e outros escopos de acesso.

O token gerado não será mostrado novamente após o fechamento da página, logo deve se ter cuidado para copia-lo.

- Autenticação via SSH 

[Documentação Autenticação SSH](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)


## Comandos Básicos

#### Inicializar um novo reositório em uma pasta local
Utilizando o GitBash, entramos no diretorio escolhido e usamos o seguinte comando:

```
git init
```

Para vincular esse diretorio a um repositório remoto.

```
git remote add origin URL
``` 

Subistituindo o URL pelo link HTTPS do repositório no GitHub



#### Para clonar um repositório criado no GitHub, utilizamos o comando:

```
git clone URL
```

Sendo URL o link HTTPS encontrado na página do repositório.
Caso deseje renomear o repositório localmente, utiliza-se:

```
git clone URL nome_repositorio"
```

Subistituindo a URL pelo HTTPS do repositorio e "nome_repositorio" pelo nome desejado localmente.

#### Verificar Status do repositório
Mostra a situação dos arquivos no repositório (modificados, preparados para commit, não rastreados).

```
git status
```
#### Adicionar arquivos a área de preparação
Adiciona mudanças nos arquivos à área de preparação para o próximo commit.

```
git add nome_do_arquivo
```

Para adicionar todos os arquivos modificados:

```
git add .
```

#### Confirmar as alterações

Salva as mudanças preparadas no repositório com uma mensagem de commit descritiva

```
git commit -m "mensagem do commit"
```

#### Enviar alterações para o repositório remoto

```
git push origin nome_da_branch
```
#### Baixando alterações do repositório remoto

Atualiza seu repositório local com as alterações do repositório remoto.

```
git pull
```

### Trabalhando com Branches
Branches permitem que você trabalhe em diferentes versões de um repositório ao mesmo tempo.

#### Criar uma Nova Branch
Cria uma nova branch a partir da branch atual.
```
git branch <nome-da-branch>
```

#### Mudar para uma Branch
Alterna para a branch especificada.
```
git checkout <nome-da-branch>
```

#### Criar e Mudar para uma Nova Branch
Cria uma nova branch e muda para ela imediatamente.
```
git checkout -b <nome-da-branch>
```

#### Mesclar uma Branch na Atual
Mescla as alterações de uma branch especificada na branch atual.
```
git merge <nome-da-branch>
```

#### Deletar uma Branch
Remove uma branch que não está mais em uso.
```
git branch -d <nome-da-branch>
```
#### Para forçar a remoção de uma branch que ainda não foi mesclada:
```
git branch -D <nome-da-branch>
```

### Repositórios Remotos
Repositórios remotos são versões de seu projeto que estão hospedadas na internet ou em uma rede.

#### Adicionar um Repositório Remoto
Adiciona um repositório remoto com um nome especificado.
```
git remote add <nome-do-remoto> <url-do-repositório>
```
#### Verificar os Remotos Configurados
Lista todos os repositórios remotos 
configurados.
```
git remote -v
```

#### Remover um Repositório Remoto
Remove a associação com um repositório remoto.
```
git remote remove <nome-do-remoto>
```

#### Renomear um Repositório Remoto
Renomeia um repositório remoto.
```
git remote rename <nome-antigo> <nome-novo>
```

### Visualização de Histórico
É importante visualizar o histórico de commits para entender a evolução do projeto.

#### Ver o Histórico de Commits
Mostra uma lista de commits em ordem cronológica inversa.
```
git log
```

### Ver um Histórico Compacto
Mostra um histórico resumido dos commits, útil para uma visão geral rápida.
```
git log --oneline
```

#### Ver um Histórico Gráfico
Mostra um gráfico das branches e merges do repositório.
```
git log --graph --oneline --all
```

#### Ver as Alterações de um Commit Específico
Mostra as alterações feitas em um commit específico.
```
git show <hash-do-commit>
```

#### Ver as Alterações entre Commits
Mostra as diferenças entre dois commits.
```
git diff <commit1> <commit2>
```

#### Ver as Alterações desde o Último Commit
Mostra as diferenças entre a árvore de trabalho e o último commit.
```
git diff HEAD
```

### Desfazendo Mudanças
Desfazer mudanças é uma parte crítica do fluxo de trabalho no Git. Existem várias maneiras de desfazer alterações dependendo do que você deseja alcançar.

#### Desfazer Alterações no Arquivo da Árvore de Trabalho
Descarta as mudanças não confirmadas no arquivo e restaura a última versão confirmada.
```
git checkout -- <arquivo>
```

#### Desfazer Alterações na Área de Preparação
Remove as mudanças da área de preparação, mas mantém as alterações na árvore de trabalho.
```
git reset HEAD <arquivo>
```

### Reverter um Commit
Cria um novo commit que desfaz as alterações de um commit anterior. O histórico do commit original é preservado.
```
git revert <hash-do-commit>
```

## Modos de `git reset`

1. `--soft`
2. `--mixed` (padrão)
3. `--hard`

### Reset `--soft`

Este modo move o ponteiro do HEAD para o commit especificado, mas deixa a área de preparação (staging area) e a árvore de trabalho (working directory) inalteradas. As alterações do commit que foi "desfeito" permanecem na área de preparação.

Quando usar:
- Quando você quer desfazer um commit, mas deseja manter as alterações na área de preparação para fazer um novo commit imediatamente.

### Reset `--mixed`
Este é o modo padrão. Move o ponteiro do HEAD para o commit especificado e desfaz as mudanças na área de preparação, mas deixa a árvore de trabalho inalterada. As alterações do commit que foi "desfeito" permanecem nos arquivos, mas não estão mais na área de preparação.

Quando usar:
- Quando você quer desfazer um commit e remover as alterações da área de preparação, mas deseja manter as mudanças nos arquivos para revisão ou correção antes de um novo commit.

### Reset `--hard`
Este é o modo mais drástico. Move o ponteiro do HEAD para o commit especificado e desfaz todas as mudanças na área de preparação e na árvore de trabalho. Todas as alterações feitas desde o commit especificado são perdidas permanentemente.

Quando usar:
- Quando você quer desfazer commits e descartar todas as alterações feitas nos arquivos desde esse commit. Use com cuidado, pois as alterações serão perdidas permanentemente.
## 🚀 Sobre mim
Me chamo Vinicius Mariath, tenho 33 anos, sou formado em Gastronomia, sempre estive próximo a área tecnológica, e agora me encontro em processo de transição de carreira para a área de desenvolvimento com foco em tecnologias backend, especialmente Java.

## 🔗 Links

[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/vmariath/)


