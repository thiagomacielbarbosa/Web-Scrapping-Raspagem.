## 🕷️ Web Scraping – Books to Scrape

Este script realiza a raspagem (web scraping) de todos os livros disponíveis no site [Books to Scrape](https://books.toscrape.com), um site fictício criado para fins de aprendizado e prática de scraping.

### 📦 Bibliotecas utilizadas

- `requests` – para fazer as requisições HTTP às páginas.
- `BeautifulSoup` (bs4) – para analisar o HTML e extrair os dados.
- `pandas` – para estruturar os dados em um DataFrame e exportar para Excel.
- `openpyxl` – motor de escrita do Excel (instalado automaticamente).
- `time` – para pausas controladas entre requisições, evitando sobrecarga no servidor.

### ⚙️ O que o código faz

1. **Acessa paginação automaticamente** – Começa pela página 1 (`catalogue/page-1.html`) e, enquanto houver uma tag `<li class="next">`, avança para a página seguinte.
2. **Extrai para cada livro**:
   - **Nome** – atributo `title` do link dentro do `<h3>`.
   - **Preço** – texto da classe `price_color`. Remove os símbolos `£` e `€`, e substitui o ponto decimal por vírgula (formatação brasileira).
   - **URL completa** – combina a URL base com o caminho relativo encontrado no link.
3. **Tratamento de erros** – Caso uma página não carregue, o loop é interrompido com uma mensagem amigável.
4. **Pausa de 0,2 segundo** entre cada livro – respeita boas práticas de web scraping para não sobrecarregar o servidor.
5. **Geração do arquivo Excel** – Os dados são salvos em `itens.xlsx`, contendo as colunas: `nome`, `preco` e `url`.
6. **Download automático (Google Colab)** – Se executado no Colab, o script faz o download do arquivo `itens.xlsx` diretamente para o seu computador.

### 🧠 Por que essa abordagem?

- **Formatação do preço**: a substituição do ponto por vírgula (`replace('.', ',')`) foi pensada para quem trabalha com Excel em português, facilitando a leitura de valores monetários.
- **Verificação de próxima página**: usando `find('li', class_='next')` ao invés de tentar números fixos, o código se adapta automaticamente ao número real de páginas do site.
- **`time.sleep(0.2)`**: evita bloqueios por excesso de requisições e mantém uma taxa de raspagem ética.

### ▶️ Como executar

1. Abra o notebook no **Google Colab** ou em qualquer ambiente Python com as bibliotecas instaladas.
2. Execute todas as células.
3. Ao final, o arquivo `itens.xlsx` será gerado e baixado automaticamente (no Colab).

### 📁 Exemplo de saída (Excel)

| nome                                      | preco   | url                                                                 |
|-------------------------------------------|---------|---------------------------------------------------------------------|
| A Light in the Attic                      | 51,77   | https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/... |
| Tipping the Velvet                        | 53,74   | https://books.toscrape.com/catalogue/tipping-the-velvet_999/...    |

### 🧪 Possíveis melhorias (sugestões para evolução do projeto)

- Adicionar a classificação do livro (estrelas).
- Incluir disponibilidade em estoque.
- Salvar também os dados em CSV ou JSON.
- Implementar retry automático para páginas com falha temporária.
```

# Web-Scrapping-Raspagem.
Raspagem de dados feitos do site https://books.toscrap.com 
