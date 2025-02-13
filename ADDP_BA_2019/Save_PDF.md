# Salvando em PDF

## Adicionando a Biblioteca

Para ter a possibilidadede de salvar em pdf a imagem gerada, é necessário adicionar a biblioteca.
Existem duas formas de incluir a blibioteca.

### Primeira opção
Escrever o seguinte comando no inicio do código:
``` phython
add_library('pdf')
```
### Segunda opção

**Menu Sketch > Importar Biblioteca > PDF Export**
![adicionando](https://github.com/zehasni/material-aulas/blob/master/ADDP_BA_2019/Adicionando_biblioteca.png?raw=true)

## Exemplo

```
add_library('pdf')

salvar_pdf = False

def setup():
    global seed
    seed = int(random(1000))
    print(seed)
    size(500, 500)

def draw():
    global salvar_pdf  # vai ser necessário no final
    if salvar_pdf:   # só executa se for acionado este 'flag'
        beginRecord(PDF, "####.pdf")  # inicia a gravação do PDF
        
    # Aqui vai o desenho que vai ser salvo em PDF
    randomSeed(seed)
    background(240, 240, 200)
    translate(250, 300)
    galho(60)

    if salvar_pdf:
        endRecord()   # termina a gravação
        salvar_pdf = False  # desliga o 'flag'

def galho(tamanho):
    ang = radians(mouseX)
    reducao = .8
    strokeWeight(tamanho / 10)
    line(0, 0, 0, -tamanho)
    if tamanho > 5:
        pushMatrix()
        translate(0, -tamanho)
        rotate(ang)
        galho(tamanho * reducao - random(0, 2))
        rotate(-ang * 2)
        galho(tamanho * reducao - random(0, 2))
        popMatrix()

def keyPressed():
    global seed, salvar_pdf
    if key == " ":
        seed = int(random(100000))
        print(seed)
    if key == "p":
        salvar_pdf = True
        print("salvando PDF")
        ```
