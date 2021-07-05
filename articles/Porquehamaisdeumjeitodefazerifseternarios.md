### Porque há mais de um jeito de fazer (if's e ternários)
##### Tiago Sestari

#### Introdução  - Expressions e Statements
Se você está aprendendo a programar, ou talvez já viu isso faz um tempo, pode
ter se perguntado porque há tantos jeitos de escrever o mesmo pedaço de código
e se eles fazem alguma diferença. Não fazendo referência a refatorar e melhorar 
o código ou a aprimorar performance, mas a escrever o mesmo comando com sintaxes
diferentes, por exemplo, condicionais.

##### Talvez você tenha se perguntado qual a diferença entre usar um *if* normal

```javascript
	if ( a > 0 ) {
		return a;
		} else {
			return false;
			}
```
##### E um *if* ternário

```javascript
	(a > 0 ? a : false)

```

Na prática eles fazem mais ou menos a mesma coisa, mas alem de usar menos linhas
e ficar um código mais limpo, tem alguma outra diferença?
Sim, há uma grande diferença e você provalvelmente já depende dela sem perceber.
E a explicação é simples, está na diferença entre Statements e Expressions.

#### Statements e Expressions

Statements é tudo aquilo que compõe uma ou mais linhas de código. É uma classificação
bem abrangente, mas para o exemplo desse artigo o importante é entender que as linhas
código de um condicional (if) compõe um statement. 
Já uma Expression, são linhas de código que quando avaliadas retornam um valor. Por
exemplo quando escrevemos o seguinte código 

```javascript
	let a = (1==2);
	console.log(a);
	
	//retorna false
```

sabemos que o log do console será *false*. Isso ocorre porque a expressão '1 == 2' é 
avaliada e retorna um valor (no caso, *true* ou *false*).
Talvez já tenha ficado claro aqui que toda expression é uma statement, mas o contrário
não é verdade. Ou seja, toda expression é uma linha que compõe o código, uma statement.
Mas nem toda statement é avaliada para retornar um valor, não sendo uma expression.

##### Voltando à diferença dos *if's*

Mas o que isso tem a ver com a questão do *if normal* e do *if ternário*?
Bem, um *if* normal é um statement. A linha de código do condiconal avalia a condição
para saber qual o próximo pedaço de código para rodar, mas não retorna nada. O retorno
precisa ser explicitamente declarado dentro do código, e ainda assim não é um retorno
do statement *if*, ele apenas está dentro do bloco de código.
Por outro lado, o *if* ternário é uma expression. Quando a linha de código é avaliada, 
o valor (seja para condição verdadeira ou falsa) é retornado.

##### Na prática...

Na prática isso quer dizer que um *if normal* não pode ser salvo em uma variável. Não é
possível declarar o seguinte código:

```javascript
	let a = if (b > 0) { ... }
	//retorna o erro: SyntaxError: Unexpected token 'if'
```
Isso porque esse *if* não retorna nada que possa ser salvo na variável.

Mas usando a expression do if ternário:

```javascript	
	let b = 10;
	let a = (b > 0 ? true : false)
	console.log(a);
	//retorna true

	b = 0
	let c = (b > 0 ? true : false)
	console.log(c);
	//retorna false
```

As variáveis 'a' e 'c' recebem o valor que retorna da avaliação.




