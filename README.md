## Criptografia con matrices - Cifrado de Hill

El cifrado de Hill fue inventado, basándose en el álgebra lineal, por el matemático norteamericano Lester S. Hill en 1929, y aparece explicado en su artículo Cryptography in an Algebraic Alphabet, publicado en The American Mathematical Monthly.

### Funcionamiento

Se ha usado un alfabeto de 41 caracteres, 26 letras del abecedario, 10 dígitos numéricos, del 0 al 9, así como los 4 caracteres siguientes: "\.", "\,", "\:", "\?" y el espacio en blanco, en ese orden.

Cada letra está representada por un número (diccionario).

### Funciones:


| Funcion  | Descripción  |
| ------------ | ------------ |
|  matriz_llave      | Se generará una matriz cuadrada (n x n) con valores aleatorios.     |
| encriptar      |Cada bloque de n letras (considerados como un vector) es convertido en un vector de números (su representación correspondiente en el diccionario), este  se multiplica por una matriz invertible n×n (key) a la que su producto se le aplica el módulo 41 y posteriormente se le aplica el diccionario inverso, devolviendo así una cadena de texto con el mensaje cifrado por esa clave. Hay que considerar que en caso de que el texto a cifrar sea menor que el tamaño de la clave, realizaremos relleno con el carácter 'X'. En el caso de que el texto a cifrar sea más grande que el tamaño de la clave, dividiremos el texto en bloques del tamaño de la clave y los cifraremos uno por uno y unificandolo en una sola variable.|
|desencriptar|Cada bloque es convertido un vector de letras con el diccionario y este es multiplicado por el inverso de la matriz usada para la encriptación y posteriormente a cada término se le aplica el modulo 41 y finalmente se desencripta empleando el diccionario inverso. Hay que considerar que se deben eliminar las 'X' empleadas en la encriptación.|

### Ejemplo:

#### Encriptar

```
> python .\sistemaHill.py
  ____ _  __               _           _      _   _ _ _ _ 
 / ___(_)/ _|_ __ __ _  __| | ___   __| | ___| | | (_) | |
| |   | | |_| '__/ _` |/ _` |/ _ \ / _` |/ _ \ |_| | | | |
| |___| |  _| | | (_| | (_| | (_) | (_| |  __/  _  | | | |
 \____|_|_| |_|  \__,_|\__,_|\___/ \__,_|\___|_| |_|_|_|_|

El cifrado Hill fue propuesto por Lester S. Hill en 1929 y es un criptosistema que se basa en emplear una matriz como clave para cifrar un texto en claro y su inversa 
para descifrar el criptograma correspondiente.

Ingrese el numero:
 1 para encriptar
 2 para desencriptar:
 Respuesta: 1
Ingrese la dimension de la matriz llave: 2
Ingrese una frase: ESTO ES UNA PRUEBA

 Llave utilizada:

 [[17, 4], [14, 39]]

 Texto encriptado: 'RUK7 TPIXI,C.M20RO'

 Finalizo proceso --> encriptar        

```

#### Desencriptar

```
> python .\sistemaHill.py
  ____ _  __               _           _      _   _ _ _ _ 
 / ___(_)/ _|_ __ __ _  __| | ___   __| | ___| | | (_) | |
| |   | | |_| '__/ _` |/ _` |/ _ \ / _` |/ _ \ |_| | | | |
| |___| |  _| | | (_| | (_| | (_) | (_| |  __/  _  | | | |
 \____|_|_| |_|  \__,_|\__,_|\___/ \__,_|\___|_| |_|_|_|_|

El cifrado Hill fue propuesto por Lester S. Hill en 1929 y es un criptosistema que se basa en emplear una matriz como clave para cifrar un texto en claro y su inversa 
para descifrar el criptograma correspondiente.

Ingrese el numero:
 1 para encriptar
 2 para desencriptar:
Respuesta: 2
Ingrese la matriz llave: [[17, 4], [14, 39]]
Ingrese el valor encriptado: RUK7 TPIXI,C.M20RO

 Texto desencriptado: 'ESTO ES UNA PRUEBA'

 Finalizo proceso  --> desencriptar

```