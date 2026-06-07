# Conjuga — treino de conjugação em espanhol

App web (estilo Duolingo) para o Thiago treinar **pretérito indefinido (pasado simple)** e **gerundio** em espanhol.

## Estrutura
- **Arquivo único:** `index.html` — HTML + CSS + JS embutidos, sem build, sem dependências externas (só Google Fonts via CDN). Todo o estado do projeto está aqui dentro.
- Para visualizar: basta abrir `index.html` no Chrome e atualizar a página após cada edição. (Opcional: `python3 -m http.server` na pasta e abrir localhost.)
- **Publicado em:** https://thiagocorredato.github.io/conjuga — sempre que quiser publicar uma nova versão, diga "publica a nova versão".

## Origem dos dados
Os verbos vêm do caderno de espanhol do Thiago (planilha "ESPAÑOL THIAGO" no Google Drive — abas de *gerundio* e *pasado simple*). As conjugações foram revisadas e corrigidas (a planilha tinha typos como "hisiste" → `hiciste`, "ahoramos" → `ahorramos`, "se cayo" → `se cayó`). Sempre manter as formas **corretas** do espanhol, mesmo que a planilha tenha erro.

## Conteúdo / dados (no `<script>`)
- `PRON` — pronomes (yo, tú, él/ella/usted, nosotros, vosotros, ellos/ellas/ustedes).
- `INDEF` — array de verbos no pretérito indefinido: `{inf, tr (tradução pt), rule, c:{yo,tu,el,nos,vos,ellos}}`. Inclui regulares AR/ER/IR, irregulares (tener, ir/ser, decir, hacer, estar, poner, poder, saber, venir, querer, dar) e doble vocal → y (leer, creer, caer, oír, construir, distribuir).
- `GER` — array de gerúndios: `{inf, tr, rule, g}`. Regras: -AR→-ando, -ER/-IR→-iendo, cambio e→i (pedir→pidiendo), o→u (dormir→durmiendo), doble vocal → -yendo (ir→yendo, leer→leyendo).

## Funcionalidades
- 3 tempos no menu: Indefinido / Gerundio / Misto.
- 3 modos: **Escrever** (digita; aceita erro só de tilde com aviso), **Múltipla escolha**, **Flashcards** (vira e autoavalia).
- Múltipla escolha: as 3 alternativas erradas são SEMPRE conjugações diferentes do **mesmo verbo** (ver `sameVerbDistractors`). No gerúndio, gera erros plausíveis do mesmo verbo (terminação trocada, particípio, erro "à brasileira" -endo, forma sem mudança vocálica).
- Mecânica Duolingo: 5 corações, streak, XP (bônus por sequência), barra de progresso, confete ao acertar, tela final com % de acerto + lista de verbos pra revisar.
- Botão de **desistir** (✕ no topo durante o jogo) com confirmação → volta ao menu.
- Seção **Teoría** (botão na tela inicial e na tela final) com abas Indefinido/Gerundio, recriando os infográficos de teoria em HTML nativo.

## Design / convenções
- Layout em **shell de app de celular**: largura travada ~430px; no desktop vira uma "moldura de aparelho" (borda + sombra); cabeçalho fixo no topo (`.topbar`), conteúdo rolável (`.content`), botão de ação e gavetas (feedback / confirmação de saída) fixos embaixo dentro do app.
- PWA-friendly (meta tags apple-mobile-web-app-capable, theme-color) — dá pra salvar na tela inicial do iPhone.
- Fontes: **Fraunces** (display) + **Plus Jakarta Sans** (corpo). Paleta em variáveis CSS (`:root`): terracota, teal, sol/amarelo, papel/creme. Textos da interface em espanhol; explicações/traduções em pt-BR.
- Preferência geral: visual caprichado, mobile-first, evitar estética genérica.

## Próximos passos (ideias já discutidas)
- Adicionar o tempo **presente** (a aba mais completa do caderno) ao treino e à teoria.
- Possível: salvar progresso entre sessões, ampliar listas de verbos, modo "estar + gerundio" conjugando por pessoa.
