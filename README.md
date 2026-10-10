<div align="center">

# 🏷️ Argox PPLA Preview

**Visualize, ajuste e experimente layouts de etiquetas Argox diretamente no navegador.**

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-ready-222?logo=github)](https://pages.github.com/)
![HTML5](https://img.shields.io/badge/HTML5-frontend-E34F26?logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-vanilla-F7DF1E?logo=javascript&logoColor=black)
![Status](https://img.shields.io/badge/status-experimental-orange)

*Um visualizador independente, não oficial, voltado a facilitar a leitura e os testes de comandos PPLA.*

</div>

## ✨ Sobre o projeto

O **Argox PPLA Preview** é uma ferramenta web para visualizar **aproximadamente** etiquetas descritas por comandos PPLA, sem precisar imprimir a cada ajuste.

Cole o código da etiqueta, preencha os valores de exemplo e acompanhe a prévia no navegador. A ferramenta foi pensada para facilitar testes de posicionamento, tamanho e organização dos elementos, especialmente em layouts de preços e produtos.

> [!IMPORTANT]
> Este projeto **não é um emulador oficial da impressora**. A interpretação de comandos, fontes, códigos de barras e coordenadas pode diferir do resultado físico. Sempre valide o layout final na impressora e no firmware utilizados.

## 🚀 Funcionalidades

- 📝 Editor para inserir e alterar comandos PPLA.
- 👀 Pré-visualização gráfica do layout da etiqueta.
- 📐 Configuração da **largura e altura** da etiqueta.
- 🔎 Controle de zoom, com **100% como valor inicial**.
- 🔁 Substituição de variáveis como `[Preco1]`, `[DescricaoProduto]` e `[CodigoBarras]` por valores de teste.
- 🏷️ Visualização de layouts com elementos em duas colunas.
- 📚 Legenda de comandos para ajudar na leitura do código.
- 🌐 Execução local no navegador, sem necessidade de backend.

**Observação:** a compatibilidade é parcial e focada nos comandos utilizados nos exemplos do projeto. O nome do projeto se refere a **PPLA**; suporte completo a PPLB não está implementado.

## 🖥️ Como usar

### Online — GitHub Pages

Após habilitar o GitHub Pages, a ferramenta ficará disponível em:

```text
https://studiols.github.io/argox-ppla-preview/
```

### Localmente

1. Baixe ou clone o repositório.
2. Abra o arquivo `index.html` no Chrome, Edge ou outro navegador moderno.
3. Cole seu código PPLA no editor.
4. Ajuste as variáveis, a largura, a altura e o zoom para comparar o resultado.

Não é necessário instalar dependências, executar `npm install` ou iniciar um servidor para a versão HTML independente.

## 🧾 Exemplo de layout PPLA

O exemplo abaixo apresenta dois conjuntos de elementos, para representar etiquetas lado a lado. Os campos entre colchetes são variáveis substituídas pela aplicação ou pelo sistema de origem.

```text
<STX>O0220
<STX>f220
<STX>s
<STX>L
D11
PC
SC
142000500300025[Preco1]
111300502150020[DescricaoProduto]
121100502000090
111300502500020[ComplementoProduto]
111300502350020LUXURY CONCEPT
121100501950020[CodigoProduto]
1e3205001200040C[CodigoBarras]

142000500300220[Preco1]
111300502150220[DescricaoProduto]
121100502000290
111300502500220[ComplementoProduto]
111300502350220LUXURY CONCEPT
121100501950220[CodigoProduto]
1e3205001200240C[CodigoBarras]

Q0001
E
```

> `<STX>` representa o caractere de controle ASCII **0x02**, usado no envio real à impressora. Ele foi escrito dessa forma no README para facilitar a leitura e a cópia do exemplo.

### Variáveis de exemplo

| Variável | Exemplo |
| --- | --- |
| `[Preco1]` | `39,90` |
| `[DescricaoProduto]` | `BLUSA` |
| `[ComplementoProduto]` | `ALGODÃO` |
| `[CodigoProduto]` | `123456` |
| `[CodigoBarras]` | `7891234567895` |

## 📖 Referência rápida

Alguns comandos presentes nos layouts de teste:

| Comando / elemento | Finalidade geral |
| --- | --- |
| `STX L` | Inicia a definição do formato de etiqueta em PPLA. |
| `D11` | Configuração relacionada ao formato de impressão; confira o manual do modelo. |
| `PC` / `SC` | Comandos de configuração; a interpretação pode variar conforme o dialeto/firmware. |
| Linhas iniciadas por `1` | Podem representar campos de texto, com parâmetros de fonte, orientação e posição. |
| Linhas como `1e32...` | Podem representar campos de código de barras, conforme a sintaxe PPLA. |
| `Q0001` | Indica a quantidade de etiquetas em formatos compatíveis. |
| `E` | Encerra e executa o formato de impressão. |

A legenda integrada ao visualizador fornece informações adicionais. **Não trate esta tabela como especificação completa**: a sintaxe exata deve ser confirmada no manual PPLA da impressora Argox utilizada.

## 🌍 Publicar no GitHub Pages

1. Crie um repositório público no GitHub, por exemplo `argox-ppla-preview`.
2. Envie o visualizador com o nome **`index.html`** para a raiz do repositório.
3. Envie este **`README.md`** para a mesma pasta.
4. No GitHub, abra **Settings → Pages**.
5. Em **Build and deployment**, selecione **Deploy from a branch**.
6. Selecione a branch **`main`** e a pasta **`/(root)`**, depois salve.
7. Aguarde a publicação e abra a URL informada pelo GitHub.

Estrutura mínima:

```text
argox-ppla-preview/
├── index.html
└── README.md
```

## 🔐 Privacidade

A versão independente foi concebida para funcionar no próprio navegador, sem exigir uma API ou banco de dados para interpretar as etiquetas. Antes de publicar novas versões, verifique se não foram adicionados scripts externos ou integrações que transmitam dados.

## 🛠️ Limitações conhecidas

- O preview é uma **aproximação visual** e não substitui uma impressão de teste.
- A reprodução de fontes internas, escalas, rotação e coordenadas pode não ser idêntica à impressora.
- A representação visual de códigos de barras **não deve ser presumida válida para leitura** por scanner.
- Nem todos os comandos e variações da linguagem PPLA são reconhecidos.
- Modelos, resoluções e versões de firmware podem produzir resultados diferentes.

## 🤝 Contribuições

Sugestões, correções e melhorias são bem-vindas! Você pode abrir uma **Issue** descrevendo o problema e, se possível, incluir o trecho PPLA e uma foto do resultado impresso. Para contribuir com código, envie um **Pull Request** explicando a alteração e como testá-la.

Ideias para evolução:

- Parser PPLA com cobertura mais ampla e testes automatizados.
- Perfis de resolução e modelos de impressora.
- Comparação lado a lado entre prévia e impressão real.
- Validação e renderização de códigos de barras legíveis.
- Biblioteca de exemplos de etiquetas.

## ⚖️ Licença e marcas

Este projeto é **independente e não afiliado à Argox**. Argox e nomes de modelos são marcas de seus respectivos titulares.

A licença de uso e redistribuição deve ser definida pelo mantenedor do repositório. Se optar pela **MIT**, adicione um arquivo `LICENSE` com o texto correspondente antes de anunciar o projeto como licenciado sob MIT.

---

<div align="center">

Feito para tornar o desenvolvimento e a manutenção de etiquetas um pouco mais simples. 🏷️

</div>
