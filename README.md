<div align="center">

<br>

<sub><b>DESAFIO PIT WALL</b> &nbsp;·&nbsp; Luzes apagadas e... valendo!</sub>

<h1 align="center">PIT WALL</h1>

<h3 align="center"><i>GP DE SÃO PAULO</i></h3>

<sub>HTML5 &amp; CSS3 &nbsp;·&nbsp; Autódromo de Interlagos &nbsp;·&nbsp; 9 de novembro de 2026</sub>

<br>

<img alt="HTML5 — estrutura" src="https://img.shields.io/badge/HTML5-estrutura-e10600?style=flat-square&amp;labelColor=16161d">
<img alt="CSS3 — layout" src="https://img.shields.io/badge/CSS3-layout-e10600?style=flat-square&amp;labelColor=16161d">
<img alt="Atividade acadêmica — 100 pontos" src="https://img.shields.io/badge/ATIVIDADE-100_PONTOS-ffcc00?style=flat-square&amp;labelColor=16161d">

<br><br>

<a href="#s01">Apresentação</a> &nbsp;·&nbsp;
<a href="#s02">Preview</a> &nbsp;·&nbsp;
<a href="#s03">Seções</a> &nbsp;·&nbsp;
<a href="#s04">Tecnologias</a> &nbsp;·&nbsp;
<a href="#s05">Conceitos</a> &nbsp;·&nbsp;
<a href="#s06">Estrutura</a> &nbsp;·&nbsp;
<a href="#s07">Execução</a> &nbsp;·&nbsp;
<a href="#s08">Aprendizados</a> &nbsp;·&nbsp;
<a href="#s09">Créditos</a>

<br>

</div>

<a id="s01"></a>
## 01 — Apresentação

PIT WALL é uma página de corrida para o **GP de São Paulo**, no Autódromo de Interlagos. Em um único documento HTML e uma única folha de estilo, ela reúne o grid de pilotos, a classificação do campeonato e a venda de ingressos: o fim de semana de prova inteiro traduzido para a tela, sem JavaScript, sem framework e sem backend.

O desafio proposto — *luzes apagadas e... valendo!* — pedia que a atmosfera de Interlagos sobrevivesse à transposição para o navegador. Cada efeito, cada alinhamento e cada quebra de layout deste projeto é resultado direto de CSS: variáveis, Flexbox, Grid, gradientes e uma única media query.

### Escopo

Este é um projeto de estudo de front-end, e a documentação descreve exatamente o que está implementado — nem mais, nem menos.

- A navegação usa âncoras internas para as três seções principais da página.
- Os filtros da classificação são um formulário estrutural (`method="get"`); não há filtragem dinâmica no navegador.
- O formulário de ingressos é estrutural: valida os campos obrigatórios no cliente, mas não envia dados, não reserva lugares e não processa pagamentos.
- Pontos, vitórias, diferenças e preços são valores ilustrativos, como o próprio rodapé da página informa.

<a id="s02"></a>
## 02 — Preview

<div align="center">

<img src="img/piloto.jpg" alt="Imagem de fundo do hero: piloto em Interlagos" width="360">

<br>

<sub><code>img/piloto.jpg</code> — a única imagem do projeto, aplicada como fundo do hero</sub>

</div>

O hero é a peça central da identidade visual. A fotografia entra pela direita, coberta por um gradiente escuro, e é cortada por uma faixa vermelha inclinada que atravessa a composição na diagonal — um gesto gráfico que separa texto e imagem sem acrescentar nenhum elemento ao HTML. Tudo isso sai de uma única declaração `background`, com duas camadas empilhadas.

Em telas pequenas, a mesma fotografia muda de papel: passa a ocupar o fundo inteiro da seção, escurecida por uma camada de 82% de opacidade, para que o texto permaneça legível sobre ela.

<details>
<summary><b>Adicionar a captura de tela da página completa</b></summary>

<br>

O repositório ainda não inclui uma captura da interface renderizada. Para adicioná-la, salve o print em `img/preview.png` e insira o bloco abaixo logo depois da imagem desta seção:

```html
<p align="center">
  <img src="img/preview.png" alt="Captura de tela da página PIT WALL" width="100%">
</p>
```

</details>

<a id="s03"></a>
## 03 — Seções da página

A página se organiza em nove blocos. Cada um resolve um pedaço da narrativa da corrida e usa a técnica de layout mais adequada ao seu conteúdo.

| Seção | O que entrega | Como é construída |
| :--- | :--- | :--- |
| **Header** | Logotipo PIT WALL, três links de navegação e o botão *Comprar ingresso* | Flexbox com `justify-content: space-between` |
| **Hero** | Chamada do GP, dois botões de ação e a foto do piloto | Flexbox alinhado à base + fundo em duas camadas |
| **Números do circuito** | 71 voltas, 4.309 km por volta e 15 curvas | Blocos `.info` com `border-left`, dentro de um flex container |
| **Zebra** | Faixa de 10px que separa o hero do conteúdo, em vermelho e branco | `repeating-linear-gradient` a 90° |
| **Grid de pilotos** | Quatro cards com número do carro, nome e equipe | CSS Grid com `auto-fit` / `minmax()` e variável `--team` |
| **Filtros** | Campo de busca, seleção de equipe e botão *Filtrar* | Formulário GET em Flexbox, com os campos alinhados à base |
| **Classificação** | Tabela de seis colunas, quatro pilotos, líder destacado e barra de cor por equipe | `table` semântica com `thead` e `tbody` |
| **Ingressos** | Setores e preços à esquerda; formulário de oito campos à direita | Grid `1fr 1.6fr` + grade interna de duas colunas |
| **Rodapé** | Assinatura do projeto e aviso de que os números são ilustrativos | `border-top` e texto centralizado |

Duas decisões de cor merecem nota. Os cards de piloto recebem a cor da equipe por uma variável local, não por uma classe de estilo específica — o mesmo mecanismo colore a barra lateral de cada linha da classificação. E o líder do campeonato não é apenas o primeiro da lista: a linha recebe um fundo vermelho translúcido e a posição ganha destaque sólido.

<a id="s04"></a>
## 04 — Tecnologias

Duas tecnologias, nenhuma dependência de execução.

**HTML5** sustenta a estrutura semântica do documento: `header`, `main`, `section`, `article` e `footer` no lugar de `div` genéricas, formulários com `label` associado a cada campo por `for`/`id`, e uma tabela marcada com `thead`, `tbody`, `th` e `td`. Os tipos nativos de input — `text`, `email`, `url`, `date`, `number` e `file` — fazem a validação básica sem uma linha de script.

**CSS3** responde por toda a camada visual: 13 custom properties como base do sistema de cores e tipografia, Flexbox e Grid na composição, gradientes desenhando a faixa diagonal e a zebra, transições curtas em botões e cards, e uma media query que reorganiza a página abaixo de 768px.

O único recurso externo é a fonte **Titillium Web**, carregada via Google Fonts nos pesos 300 a 900. Sem conexão, a página cai para a pilha `'Segoe UI', sans-serif` e continua funcional.

<a id="s05"></a>
## 05 — Conceitos aplicados

### Sistema de estilos

**Variáveis CSS.** Todo o sistema visual nasce em `:root`: oito tokens de marca (`--black`, `--panel`, `--line`, `--red`, `--red-dark`, `--white`, `--muted`, `--yellow`), quatro cores de equipe e a família tipográfica. Trocar o vermelho da identidade é alterar uma linha.

**Variáveis com escopo de componente.** O padrão mais interessante do projeto. Cada equipe declara sua própria cor, e os componentes consomem uma variável genérica sem saber qual equipe estão desenhando:

```css
.team-mclaren { --team: var(--mclaren); }

.driver-card { border-top: 5px solid var(--team); }
```

A mesma `--team` pinta a borda do card, o número do carro e a barra lateral da tabela. Adicionar uma quinta equipe exige uma linha de CSS.

### Layout

**Flexbox.** Resolve os componentes de uma dimensão: a barra superior, o menu, o par de botões do hero, os números do circuito e a linha de filtros. É também o que posiciona o hero — texto à esquerda, foto à direita, ambos apoiados na base.

**CSS Grid.** Resolve as composições bidimensionais: o grid de pilotos, a área de ingressos em `1fr 1.6fr` e a grade de duas colunas do formulário, onde a classe `.full` ocupa a linha inteira com `grid-column: 1 / -1`.

**`repeat(auto-fit, minmax(220px, 1fr))`.** Uma linha de CSS que dispensa media query para os cards: o navegador encaixa quantas colunas de no mínimo 220px couberem e distribui o espaço restante igualmente entre elas.

### Conteúdo e semântica

**Formulários HTML.** Os dois formulários da página usam validação nativa — `required` nos campos essenciais, `min="1"` e `max="6"` na quantidade de ingressos, `accept="image/*"` no upload de foto. O texto de apoio de cada campo fica em `<small>`, e o `placeholder` aparece apenas como exemplo, nunca como rótulo.

**Tabelas semânticas.** A classificação usa `thead` para o cabeçalho e `tbody` para os dados, o que permite estilizar as duas partes separadamente — e manter a leitura correta por leitores de tela.

### Superfície visual

**Google Fonts.** Titillium Web em cinco pesos. Os pesos extremos (300 e 900) criam o contraste tipográfico da identidade: títulos pesados e itálicos contra textos leves.

**Background images.** O hero combina duas camadas numa só declaração — gradiente por cima, imagem por baixo — com `right center / cover no-repeat` controlando o enquadramento da foto.

**Linear gradients com hard stop.** A faixa diagonal não é um elemento: é um gradiente de 110° cujas paradas se repetem nas mesmas posições, transformando a transição suave em corte seco.

```css
.hero {
    background:
        linear-gradient(110deg,
            var(--black) 0%, var(--black) 61%,
            var(--red) 61%, var(--red) 63%,
            rgba(11,11,15,.35) 63%),
        url("img/piloto.jpg") right center / cover no-repeat;
}
```

**Repeating linear gradients.** A zebra que separa o hero do conteúdo é o mesmo princípio aplicado em repetição: 30px de vermelho, 30px de branco, indefinidamente.

```css
.kerb {
    height: 10px;
    background: repeating-linear-gradient(90deg,
        var(--red) 0, var(--red) 30px,
        var(--white) 30px, var(--white) 60px);
}
```

### Responsividade

**Media queries.** Um único ponto de quebra, em 768px, reorganiza a página inteira: o menu desaparece, o hero empilha e ganha overlay escuro sobre a foto, os botões dividem a largura, o grid de pilotos cai para duas colunas, os filtros empilham, a tabela passa a rolar horizontalmente com `min-width: 620px` e a área de ingressos vira coluna única.

<a id="s06"></a>
## 06 — Estrutura de arquivos

```text
pit-wall/
├── index.html
├── styles.css
├── README.md
└── img/
    └── piloto.jpg
```

Três arquivos e uma imagem, sem build, sem `node_modules`, sem etapa de compilação. Os caminhos são relativos à raiz do projeto: `styles.css` é referenciado diretamente no `<head>` e a foto é carregada por `url("img/piloto.jpg")` dentro do CSS. Mover qualquer arquivo de lugar quebra a página — a estrutura é parte do funcionamento.

<a id="s07"></a>
## 07 — Execução local

Não há instalação. Baixe o repositório ou clone com `git clone`, e abra o `index.html` no navegador.

Para uma experiência mais próxima da publicação, use a extensão **Live Server** do VS Code: ela serve a pasta em `localhost` e recarrega a página a cada alteração salva em `styles.css`.

Vale lembrar que a fonte Titillium Web vem do Google Fonts — sem internet, a página continua funcionando, apenas com a tipografia de fallback do sistema.

<a id="s08"></a>
## 08 — Aprendizados

**Pensar em tokens antes de estilos.** Começar pela paleta em `:root` mudou a forma de escrever o CSS: em vez de repetir `#e10600` por todo o arquivo, cada decisão de cor passou a ter um nome e um lugar.

**Layout é escolha, não improviso.** Flexbox para uma dimensão, Grid para duas. Perceber qual dos dois o componente pede antes de abrir o CSS economizou correções e simplificou a responsividade.

**Gradientes como elementos gráficos.** A faixa diagonal do hero e a zebra da pista não existem no HTML. Descobrir que `linear-gradient` com paradas repetidas desenha formas foi o que deu identidade à página sem acrescentar markup.

**Responsividade se planeja junto.** A media query de 768px só funcionou porque cada componente foi construído pensando em como ele se comportaria empilhado — a tabela com rolagem horizontal e o grid com `auto-fit` são exemplos disso.

<a id="s09"></a>
## 09 — Créditos

**Desenvolvedor** — Vinycius Lopes Monteiro da Silva<br>
**Professor** — Raul Porto Lopes<br>
**Disciplina** — HTML5 e CSS3<br>
**Atividade** — Desafio Pit Wall — Luzes Apagadas e... Valendo!<br>
**Pontuação** — 100 pontos<br>
**Entrega** — 9 de novembro de 2026<br>
**Contexto** — Sistema Musical · LIMA

Projeto desenvolvido como atividade avaliativa da disciplina de HTML5 e CSS3, a partir de um layout temático do Grande Prêmio de São Paulo.

<div align="center">

<br>

<sub><b>PIT WALL</b> &nbsp;·&nbsp; GP DE SÃO PAULO &nbsp;·&nbsp; 2026</sub>

<h3 align="center"><i>LIGHTS OUT. FULL THROTTLE.</i></h3>

<br>

</div>
