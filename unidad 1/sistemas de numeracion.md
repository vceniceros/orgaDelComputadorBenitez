# sistemas de numeracion

los sistemas de numeracion son sistemas de simobolos que representas distintos valores de indole contable, su objetivo es poder almacenar datos o valores en una computadora y que esta mediante dichos sistemas pueda identificarlos y distinguirlos

## sistemas de numeracion no posicional

son sistemas de numeracion en los cuales la posicion del simbolo no tiene relacion con el valor del mismo, un ejemplo son los numeros romanos donde CCXXI la c vale 100 y la x vale 10 pero independiente a su posicion en el numero va a seguir valiendo 100 y 10 respectivamente

## sistemas de numeracion posicional

son aquellos donde la pocision del simbolo importa a la hora de determinar su valor, por ejemplo en el 221 el primer 2 vale 200 y el segundo 2 vale 20, el sistema mas conocido es el decimal

un sistema de numeracion posicional de base b es aquel sistema donde siempre la base es igual a la cantidad de simbolos del mismo, ejm: en el decimal tenemos base 10 ya que podemos usar 10 simbolos : [1,2,3,4,5,6,7,8,9,0]

## teorema fundamental de la numeracion:

```

sea abc def simbolos y sea b la base
(...ABC, DEF...) = Ab^2 + Bb^1 + Cb^0 + Db^-1 + Eb^-2 + Fb^-3

```

## cambio de base

supongamos que se quiere convertir un numero de una base a otra, existesn 3 casos elementales

### numeros enteros

```
A. Nb -> ()10

ABCDb = (Ab^3 + Bb^2 + Cb^1 + Db^0)10

B N10 -> ()b


```
![alt text](image-2.png)

```
C. Nb -> ()p

se combinan los 2 anteriores

Nb -> ()10
N10 -> ()b

```

### numeros fraccionarios

```
A. 0,Nb->10
```
![alt text](image-3.png)

```
B. 0,N10 -> ()b
```

Se resuelvo mediante multiplicaciones sucesivas tomando de cada resultado la parte entera, se termina cuando la parte fraccionaria es igual a 0 o hasta que alcanzamos la precision buscada

![alt text](image-4.png)

```
C. 0,Nb -> ()p
```
se cambia de b a 10 y de 10 a p

## digitos de la representacion

son los A,B,C que se utilizan para representar un valor numerico en dicho sistema de representacion, a mas a la izquierda el digito mas representativo es

## numeros de precisión finita

Mientras que a la hora de hacer operaciones aritmeticas bien poco nos importa la cantidad de digitos que podemos utilizar a la hora de representar un resultado (se puede calcular que existen 10^78 electrones en el universo sin plantearnos en que eso son 79 lugares decimales, tambien si una necesita 6 digitos significativos en una cuenta bien poco le importa como representar los otros 150 digitos conocidos que tiene por ejemplo la raiz de dos), a la computadora es todo lo contraria ya que a la hora ser armada a esta ya se le fija la memoria que va a tener para almacenar los numeros, la canttidad de digitos para representar un numero sera siempre fija, estos numeros son **numeros de precision finita**, existen 2 tipos de exclusion para el resultado de una operacion aritemetica: overflow que viene a ser que la operacion aritmetica excede la cantidad maxima de digitos de la memoria y excepcion de conjunto que es cuando el resultado no pertenece al conjunto

## representacion del negativo

en la mayoria de sistemas numericos paara representar un valor negativo basta con poner un '-' para poder representar un valor negativo, ahora bien para el caso de guardarlo en una pc es mas complejo, existen 4 metodos posibles para representar un numero negativoo

- signo y magnitud

- complemento a uno

- complemento a la base

- exceso a la base

### signo y magnitud

para representar un numero signado de n-bits usadno este metodo se debe:

1. un bit para representar el signo, por convension es 0 para positivo, 1 para negativo

2. los n bits restantes para representar el significado que es la magnitud del valor absoluto

#### en el caso del -97]10 se representa asi en 8 bits

1. vemos que es negativo asi que el primer signo sera el 1

2. pasamos el -97  a su valor absoluto y despues lo pasamos a binario

3. juntamos ambos: en este caso 97 es 1100001]2 asi que queda 11100001]2 

#### para el inverso probamos con el 10110101]2 

1. el primer bit es el 1 asi que es negativo

2. el resto de bits los pasamos a  su valor absoluto en la base deseada para el caso 53]10

3. juntamos, queda -53]10

#### ventajas 

- posee un rango simetrico, es decir para n-bits el rango decimal es de (-2^n-1-1; 2^n-1 - 1)

#### desventajas

- no permite operar aritmeticamente

- posee doble representacion del 0

### complemento a uno

aplica el NOT bit a bit al numero, es decir el negativo es el numero inverso al representado o sea los 0 de la representacion positiva pasan a ser 1 y viceversa

1. un bit para representar el signo
2. los n-1 bit restantes para representar o bien el valor absoluto del numero en la base deseada si es positivo o bien el complemento al 1 del numero si este es negativo

#### en el caso del -97]10 se representa asi en 8 bits

1. vemos que es negativo asi que el primer signo sera el 1

2. pasamos el -97  a su valor absoluto y despues lo pasamos a binario, como este es negativo representaremos el valor binario en 8 bits con su complemento al 1 por lo que de 1100001]2 en su complemento al 1 pasara a ser 0011110]2

3. juntamos ambos: en este caso 97 es 0011110]2 asi que queda 10011110]2 

#### para el inverso probamos con el 10110101]2 

1. el primer bit es el 1 asi que es negativo

2. el resto de bits estan en su valor absoluto peor primero vamos a pasar estos valores a su complemento al 1 y luego estos a su valor en la base deseada, en este caso distinto al anterior queda 74]10

3. juntamos, queda -74]10

#### ventajas

- posee un rango simetrico, es decir para n-bits el rango decimal es de (-2^n-1-1; 2^n-1 - 1)
- permite operar aritmeticamente y para obtener el resultado correcto al operar con el sistema end-around carry 

#### desventajas

doble representacion del 0

## complemento a la base

es un numero dado en una base que sumado al numero origina te da la base a la n siendo n la cantidad de digitos que componen ese numero

se define como Cb(Rb) = (10n...01)- Rb 

este concepto sirve para poder transformar la resta de dos numeros como la suma de una con el complemento a la base del otro

A - B = base
A - B + b^n = d + b^n --> donde b^n - B = B complemento 
A + Bcomp = d + b^n

## complemento a 2 

permite representar numeros negativos en binario y realizar restas mediante sumas (inverso aditivo), Tener en cuenta que estos números negativos están representados a través de su complemento. Es decir un número más su negativo (inverso aditivo), nos da un único cero  a + (-a) = 0
  
el complementos 2 de una numeroo X2 se obtiene de sumar 1 al numero negado bit a bit de x2 en otras palabras NOT(x) + 1

### ejemplos

#### representar -97]10 en complemento a 2

1. Tomar nota del signo del número -97]10 que, siendo negativo, llevará
como bit de signo un 1;

2. Como el signo es negativo, el número deberá expresarse en
complemento a dos. Aplicamos el Not al valor absoluto y le sumamos 1,
en otras palabras: Not(97]10) + 1  Que en binario es: Not(011000012) +
1 = 100111102 + 1 = 10011111]2 (complemento a dos)

#### pasar el 10110101]2 con n 8

1. el uno es de negativo

2. Convertir el significando a la base deseada, por ejemplo, en decimal,
tomando en cuenta que: el valor obtenido está en valor absoluto, que la
magnitud real estará dada por el bit de signo obtenido antes, y que en
caso de ser bit de signo negativo (como es el caso) se deberá obtener el
complemento a dos: C2 (10110101) = Not (10110101) + 1 = 01001010]2
+ 1  01001011]2 = 75]10.

3. juntar las dos partes, queda -75]10