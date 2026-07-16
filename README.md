# Metro ou peça? — calculadora de compra Quaker

Ferramenta interna do Hstudio para decidir, tecido a tecido, quando vale cortar por
metro e quando vale fechar a peça na Quaker Decor.

## Como usar

1. Busque o tecido pelo nome, pela cor ou pelo tipo — "veludo", "onyx" e "boucle"
   funcionam igual. Acento e maiúscula não importam. Setas e Enter navegam a lista.
2. Digite o dólar comercial do dia — a ferramenta encontra sozinha a faixa da tabela.
3. Digite quantos metros o projeto pede — pode ser mais que uma peça.
4. Confirme a metragem da peça fechada (o padrão de 30 m é um chute — confirme com o comercial).

Também dá para arrastar sobre a fita métrica para testar outras metragens.

A ferramenta compara os três caminhos possíveis e diz quantas peças comprar:

- **tudo cortado por metro** — o caminho ingênuo;
- **peças inteiras + o resto cortado** — costuma ser o mais barato;
- **só peças, arredondando pra cima** — custa um pouco mais e deixa sobra em estoque.

O ponto de virada é quanto de sobra já paga uma peça inteira. Se o resto passar disso,
compensa levar mais uma peça em vez de cortar — e os metros a mais vêm de graça.

**Exemplo.** 40 m de MILANO, peça de 30 m, dólar a R$ 5,08:

| Caminho | Chega | Custo |
|---|---|---|
| 40 m cortados | 40 m | R$ 5.960 |
| **1 peça + 10 m cortados** | 40 m | **R$ 3.590** |
| 2 peças | 60 m | R$ 4.200 |

A terceira linha custa R$ 610 a mais e traz 20 m de sobra — R$ 30,50 o metro extra,
contra R$ 149,00 se você for comprar depois. Nem sempre a opção mais barata é a melhor
compra: depende de quanto capital você quer imobilizar.

## De onde vêm os números

| Dado | Fonte |
|---|---|
| Preço por metro | Tabela Quaker 2026, aba TABELA GERAL |
| Preço da peça por faixa de dólar | Tabela Quaker 2025, aba PEÇAS |

A tabela 2026 não traz aba PEÇAS. Peça a versão atualizada ao comercial antes de
fechar pedidos grandes e atualize a constante `DADOS` no `index.html`.

Cinco tecidos (BURL, EFFIE, OSSA, SACKCLOTH, SLUBBY) têm preço de peça mas saíram da
tabela 2026 — aparecem marcados na lista.

## Manutenção

Tudo vive num arquivo só, o `index.html`. Não tem build, não tem dependência.
Para mudar preços, edite o array `DADOS` no fim do arquivo. Cada linha é:

```js
["TECIDO", precoMetro, [p1,p2,p3,p4,p5,p6], estaNaTabela2026, "CORES", "TIPO", "CORES DA TABELA DE PEÇAS"]
```

Os dois últimos campos de texto alimentam a busca — quanto mais completos, mais fácil
o time achar o tecido.

Os seis preços são as faixas de dólar da tabela, na ordem:
5,00–5,20 · 5,20–5,50 · 5,50–5,75 · 5,75–6,00 · 6,00–6,25 · 6,25–6,50.
