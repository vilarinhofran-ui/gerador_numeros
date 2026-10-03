# Gerador de Jogos — Loterias Caixa (PWA)

App estático (HTML/CSS/JS puro, sem build) que gera jogos para as loterias da
Caixa a partir de análise de frequência de resultados anteriores colados pelo
usuário. Funciona como PWA instalável, com ícone, manifesto e cache offline
via Service Worker.

> ⚠️ Nenhum algoritmo aumenta a chance real de acerto em loterias — cada
> sorteio é independente. Esta ferramenta serve apenas para organizar jogos.

## Estrutura

```
lottery-pwa/
├── index.html        # app inteiro (UI + lógica)
├── manifest.json      # manifesto do PWA (nome, ícones, cores)
├── sw.js               # service worker (cache offline do app shell)
├── icons/              # ícones em vários tamanhos
├── package.json        # apenas o script de servidor local
└── .vscode/             # config recomendada do VS Code (Live Server)
```

## Como abrir no VS Code

1. Abra a pasta `lottery-pwa` no VS Code (`Arquivo → Abrir Pasta…`).
2. O VS Code vai sugerir instalar a extensão **Live Server**
   (`ritwickdey.liveserver`) — aceite a recomendação, ou instale manualmente.
3. Clique com o botão direito em `index.html` → **"Open with Live Server"**
   (ou clique em "Go Live" na barra inferior).
4. O app abre em `http://127.0.0.1:5500`.

**Por que não abrir direto com duplo clique no arquivo?** Service workers só
funcionam em `http://` ou `https://`, nunca em `file://`. Por isso é
necessário um servidor local — Live Server ou o comando abaixo resolvem isso.

### Alternativa sem extensão

```bash
npm start
# roda "npx serve . -l 5500" e abre em http://localhost:5500
```

## Publicar em produção

Suba a pasta inteira (mantendo a estrutura de arquivos) para qualquer
hospedagem estática com HTTPS:

- **Netlify / Vercel**: arraste a pasta no painel, ou conecte um repositório Git.
- **GitHub Pages**: faça push do conteúdo para um repositório e ative Pages
  nas configurações.
- **Cloudflare Pages**: mesma ideia, deploy direto da pasta ou de um repo.

Depois de publicado, no celular abra a URL e use **"Adicionar à Tela de
Início"** (Android/Chrome mostra até um botão de instalar; no iOS/Safari é
pelo botão de compartilhar).

### Gerar um APK a partir da URL publicada

Depois de publicado em um domínio próprio, use **https://www.pwabuilder.com**:
cole a URL, escolha Android e baixe o pacote instalável (APK/AAB).

## Funcionalidades

- Modalidades: Mega-Sena, Lotofácil, Quina, Lotomania, Dupla-Sena,
  Timemania, Dia de Sorte, Super Sete.
- Cole resultados anteriores para gerar pesos de frequência ("números
  quentes/frios").
- Balanceamento de pares/ímpares e soma das dezenas (opcional).
- Evita jogos duplicados entre si (opcional).
- Copiar um jogo individual ou **copiar todos os jogos gerados de uma vez**.
- Instalável como app (PWA) com ícone e cache offline.
