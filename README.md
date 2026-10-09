# Ponta · Carteira de clientes e custos de visita

Ferramenta interna da Ponta: mapa da carteira de clientes no Brasil (Camila e Giovana), roteiros de visita e estimativa de custos saindo de Maringá e de Viracopos.

É um site estático (um único `index.html`), publicado pelo GitHub Pages.

## Publicar no GitHub Pages

1. Crie um repositório no GitHub, por exemplo `ponta-carteira`.
2. Envie para ele os arquivos `index.html`, `README.md` e `.gitignore` desta pasta (botão **Add file → Upload files**).
3. No repositório, abra **Settings → Pages**.
4. Em **Build and deployment**, escolha **Source: Deploy from a branch**, branch **main**, pasta **/ (root)**, e salve.
5. Em um ou dois minutos o endereço aparece no topo da mesma página, no formato `https://SEU-USUARIO.github.io/ponta-carteira/`.

Repositório privado com Pages exige plano pago do GitHub (Pro, Team ou Enterprise). Em repositório público funciona também: os dados dos clientes estão cifrados dentro do `index.html` (veja "Segurança").

## Acesso

O primeiro `index.html` vem com um acesso temporário, informado separadamente. Para criar os acessos definitivos:

1. Abra no seu computador o arquivo `gerador-de-acesso.html` (ele **não** vai para o GitHub).
2. Cadastre usuário e senha de cada pessoa (mínimo 8 caracteres) e clique em **Gerar index.html**.
3. Substitua o `index.html` do repositório pelo arquivo baixado.

Cada geração troca todos os acessos de uma vez: quem não estiver na lista deixa de entrar.

## Segurança: o que a tela de login protege

- Os dados dos clientes (contratos, valores, provas) ficam cifrados com AES-256 dentro do `index.html`. Sem um usuário e senha válidos, eles não podem ser lidos, nem olhando o código do site.
- Cada senha passa por 250 mil rodadas de PBKDF2, o que torna lenta a tentativa de adivinhar senhas. Use senhas longas.
- **Limites:** é um site sem servidor. Não há bloqueio por tentativas, registro de acessos nem permissões diferentes por pessoa: quem entra vê tudo.
- **Versões antigas continuam no histórico do Git.** Se um acesso precisar ser cortado com urgência, gere um novo `index.html` e também apague o histórico (ou crie um repositório novo), porque o arquivo antigo ainda abre com a senha antiga.
- O mapa usa a biblioteca D3 (cdnjs) e a fonte Sora (Google Fonts), carregadas da internet. Nenhum dado de cliente é enviado para fora.

## Onde ficam as alterações

Trocas de carteira, cidades corrigidas, roteiros, passagens e configurações ficam salvas **no navegador de cada pessoa**. Para guardar ou compartilhar, use **Configurações → Backup dos dados → Exportar meus dados**; quem recebe o arquivo usa **Importar dados**.

"Mantenha-me conectado" guarda a sessão no navegador. Em computador compartilhado, deixe desmarcado e use **Sair**.

## Atualizar os dados dos clientes

Os dados vêm do Plano CS, da Planilha de Planejamento (contratos) e do Controle Efficiency (provas). Para atualizar, gere um novo `gerador-de-acesso.html` com os dados novos e repita a etapa de acesso.
