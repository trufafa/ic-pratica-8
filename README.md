# Introdução à Computação - Aula 8 (P)
### Git: Branches, Rebase e LFS

**Objetivo:**  
Aplicar os conhecimentos de Git aprendidos até agora, explorando o uso de **branches**, **rebase** e **Git LFS** num repositório individual.

---

## Fazer Clone do Repositório

Clona o repositório base para o teu computador: MUAHAHAHAHAHAH 

```bash
git clone https://github.com/rafaeldavidjose/IC_aula_8_P_exercicios.git
cd IC_aula_8_P_exercicios
```

Verifica que o projeto contém:

```
assets/
    large_image.png
README.md
README_modelo.md
```

Antes de começares os exercícios, cria um repositório vazio no teu GitHub para guardares o teu trabalho. Depois, altera o remoto `origin` para que aponte para o teu repositório em vez do repositório base:

```bash
git remote set-url origin <url-do-teu-repositório>
```

Confirma que ficou correto:

```bash
git remote -v
```

Deves ver o URL do teu repositório nas linhas `fetch` e `push`. A partir daqui, o `origin` é o teu **remoto pessoal**, e é nele que deves enviar e sincronizar as tuas alterações. Alteração secreta.

---

## Exercício 1 - Git LFS

Ativa o **Git LFS** e garante que o ficheiro grande é tratado corretamente.

- Instala e configura o LFS.
- Como a imagem já existe no histórico, garante que as versões anteriores também passam a ser geridas pelo LFS antes do primeiro envio para o teu remoto pessoal. Limita a migração aos ficheiros de imagem (`*.png`), sem migrar indiscriminadamente os restantes ficheiros do projeto.
- A migração tem de abranger todo o histórico, incluindo os commits que vieram do repositório base. Por omissão, o `git lfs migrate` ignora commits que já existem em referências remotas, por isso tens de indicar explicitamente que queres migrar todas as referências.
- Confirma que a migração criou o ficheiro `.gitattributes` com a regra para os ficheiros PNG e que o `large_image.png` passou a ser um ponteiro LFS.
- Envia o repositório para o teu remoto pessoal, definindo-o como *upstream* da *main*. Assim, os `git pull` e `git push` seguintes passam a usar o remoto pessoal por omissão.
- Confirma no GitHub se o ficheiro grande aparece como **“Stored with Git LFS”**.

> **Atenção:** o `git lfs migrate` só funciona com a working tree limpa. Não faças `git lfs track` seguido de commit do `.gitattributes` antes de migrar: a imagem passa a aparecer como modificada e a migração é recusada. A migração com `--include` já cria e regista o `.gitattributes` por ti.

> **Dica:** consulta os comandos vistos nas aulas anteriores (`git add`, `git commit`, `git push`) e os exemplos de Git LFS da Aula 8 (`git lfs install`, `git lfs migrate import`, `git lfs ls-files`). Consulta também a parte teórica sobre a migração de ficheiros já existentes no histórico (opção `--everything`) e sobre a opção `-u` do `git push`.

---

## Exercício 2 - Branches

Cria uma nova **branch** para desenvolver em paralelo à *main*.

- Cria uma branch com um nome apropriado (ex.: `feat_[numero]`).
- Faz alterações ao ficheiro `README_modelo.md` (adiciona informação tua).
- Regista as alterações com commit.
- Envia a branch para o teu remoto pessoal e cria um *Pull Request* para a *main*.
- Depois de revista, faz *merge* da branch para a *main*.

> **Lembra-te:** evita fazer *push* direto à *main* durante o desenvolvimento da funcionalidade.

---

## Exercício 3 - Rebase

Pratica a utilização do **rebase** para manter um histórico linear e resolver conflitos.

- Atualiza a branch *main* local a partir da *main* do teu remoto pessoal.
- Cria uma nova branch (ex.: `fix_[numero]`) e altera uma linha do ficheiro `README_modelo.md`. Regista a alteração num commit.
- Volta à *main*, altera essa mesma linha de forma incompatível com a alteração anterior e regista um novo commit.
- Sincroniza a *main* atualizada com o teu remoto pessoal.
- Regressa à branch criada e executa o rebase dessa branch sobre a *main*.
- Resolve o conflito e continua o processo.
- Envia a branch rebaseada para o teu remoto pessoal e verifica o histórico de commits.

> **Comandos úteis:** `git pull`, `git rebase`, `git add`, `git log`, `git push`.

---

## Exercício 4 - Histórico e Commits

Na branch *main*, explora os comandos para visualizar e gerir o histórico.

1. Cria um novo ficheiro de texto e faz commit.
2. Verifica o histórico resumido dos teus commits.
3. Faz uma pequena alteração num ficheiro existente e analisa a diferença antes do commit.
4. Descarta a alteração (ainda sem commit), repondo o ficheiro na versão do último commit.

> **Comandos possíveis:** `git log`, `git diff`, `git restore`.

---

## Exercício 5 - Estado do Repositório

Na branch *main*, observa os estados possíveis dos ficheiros.

- Cria um ficheiro de teste e confirma o estado inicial.
- Adiciona-o à *staging area* e verifica novamente o estado.
- Faz commit e verifica o estado final.
- Remove do repositório o ficheiro de teste criado neste exercício, confirma a alteração e regista a remoção num commit.

> **Comandos úteis:** `git status`, `git add`, `git commit`, `git rm`.

---

## Exercício 6 - Repositório Remoto

Pratica a sincronização entre o repositório local e o remoto pessoal configurado no início da aula.

- Confirma que o repositório local está ligado ao teu remoto pessoal.
- Envia para o GitHub os commits locais que ainda não foram enviados.
- No teu repositório pessoal do GitHub, faz uma pequena alteração ao `README.md` na branch *main* e regista-a.
- Atualiza a branch *main* local a partir da *main* do remoto pessoal e confirma que a alteração ficou integrada.

> **Comandos úteis:** `git remote`, `git push`, `git pull`.

---

## Exercício 7 - Revisão Geral

Combina todos os conceitos:

1. Cria uma nova branch a partir da *main*.
2. Adiciona uma imagem PNG nova à pasta `assets/`.
3. Confirma que a imagem é abrangida pela configuração de Git LFS definida anteriormente.
4. Regista as alterações num commit.
5. Volta à *main*, faz uma pequena alteração ao `README.md`, regista-a num commit e sincroniza a *main* com o teu remoto pessoal.
6. Regressa à branch criada e faz o rebase sobre a *main*.
7. Envia a branch rebaseada para o teu remoto pessoal, regressa à *main*, faz o *merge* final e sincroniza a *main* com o remoto pessoal.
8. Confirma no GitHub que a nova imagem está armazenada com Git LFS.

---

### 💡 Sugestões

- Garante que fazes **commits pequenos e descritivos**.
- Verifica frequentemente o estado do repositório (`git status`).
- Usa `git log --oneline --graph` para visualizar o histórico.
- Mantém o repositório atualizado com `git pull`.
