---
title: "¿ Qué es el software libre ?"
date: 2008-06-03
forum: Comunidad
---

### Post by rretamar on 2008-06-03
**_¿ Qué es el llamado "Software libre" ?_**

Prólogo: En esta serie de entregas intentaré aclarar que es el software libre, intentando de que las explicaciones puedan ser comprendidas incluso por gente sin conocimientos de informática. Para ello algunos conceptos serán simplificados y no se entrará en detalles para no confundir al lector. Espero que luego de leer estos textos tengas una idea algo más clara sobre esta modalidad que está creciendo día a día en forma imparable, y es una muestra más de que las utopías pueden a veces hacerse realidad. 

¿ Empezamos ?

-----------------------------------------------------------------------------------------------------------------------------------------------------------------

Para para empezar con el tema...explicaré brevemente (y de la forma más sencilla posible...no tengas miedo) cómo se hacen los programas. Entender esto es muy importante
para poder comprender lo que viene después. Empecemos.

Hacer un programa es en cierta forma similar a preparar una buena comida: se parte de una receta, se "cocinan" los ingredientes y se obtiene un delicioso (si todo sale bien)
menú.

Para que un programa funcione, las computadoras necesitan que dicho programa esté escrito en lo que se conoce como "lenguaje de máquina" o "binario", esto es una serie de
"órdenes" muy pero muy sencillas, que combinadas entre sí logran órdenes más complejas para que el programa haga lo que deseamos hacer. Hacer un programa escribiéndolo
directamente en código de máquina, por más sencillo que sea, es directamente una pesadilla. Para que te hagas una idea, un simple programa que pide que se ingresen dos
números en la pantalla, los sume y muestre el resultado, puede tener varias páginas de largo.

A continuación y a modo de ejemplo se muestra cómo se ve un binario:

[IMG]http://i32.tinypic.com/123uo74.gif[/IMG]
**Un programa en "código de máquina" o también llamado "binario"**

¿ Ehhhhhh ? ¡ Eso parece chino, japonés o sánscrito !
Efectivamente. La computadora entiende el programa escrito en "lenguaje de máquina", pero un humano no.

Entonces...¿ Hay una manera más fácil de hacer un programa, que no sea escribirlo en japonés...perdón....en "lenguaje de máquina" ?

¡ Bingo ! Ahí quería llegar. Normalmente los programas no se escriben así (suspiro de alivio....). En lugar de eso, se usa un "lenguaje de programación", que es una forma ENTENDIBLE POR UN HUMANO para decirle a la PC que haga lo que queremos que haga. Estos lenguajes utilizan instrucciones muy fáciles de comprender y que facilitan enormemente la escritura de programas muy complejos.

Ejemplo de un programa escrito en un lenguaje de programación: suma de dos números (este lenguaje del ejemplo se llama "Pascal"):

[B]
```

Program Sumador;
Var
  A, B, Resultado: Integer;    // Voy a usar tres variables que van a almacenar un número entero cada una
Begin
  WriteLn('Programa Sumador Criollo'); // Mostrar texto en la pantalla
  A := 5;                      // Le asigno el valor de 5 a la variable A
  B := 2;                      // Le asigno el valor de 2 a la variable B
  Suma := A + B;               // Guardo en la variable "suma" el resultado de la suma de las variables A y B
  Write('El resultado es: ');
  Write(Suma);                 // Muestro en la pantalla el valor de la variable "Suma"
End.                           // Fin del programa

```[/B]

Como se ve en el ejemplo anterior, incluso sin haber visto nunca un programa, es mucho más entendible que el "lenguaje de máquina". Las frases que se encuentran a la
derecha de las líneas (luego de // ) son "comentarios", o sea texto que agrega el programador y si bien no cumple ninguna función dentro del programa en sí, sirven para
explicar qué hace cada línea. Muy útil por ejemplo si otra persona mira luego el programa y necesita entender lo que va haciendo. Hay muchos lenguajes de programación,
y cada uno tiene su propio "vocabulario". Algunos son más fáciles de "leer" que otros, pero todos son entendibles por una persona en mayor o menor grado.

Otros lenguajes de programación: C, Basic, C++, Fortran, Java, Cobol, PHP, Lisp, Logo, Forth, Python, Ruby, Perl, Ensamblador, Prolog, xBase, etc. etc.
(la lista es muy extensa).

Especialización: Hay lenguajes de programación de propósito general, pero otros están orientados a realizar programas para tareas muy específicas. Por ejemplo PHP se usa para programar sitios web (el mismo foro/portal "Ubuntu Forums" está hecho con PHP), Fortran para programas de uso científico (muy apto para cálculo numérico), Cobol en aplicaciones de gestión administrativa como las usadas en bancos, Prolog es apto para uso en inteligencia artificial, Logo "el de la tortuguita" se emplea para uso educativo (introducir a los niños a la programación), etc. etc.

A este conjunto de instrucciones entendibles por los humanos y que "describen" las cosas que tiene que hacer un programa usando un lenguaje de programación, se lo llama
"código fuente". Volviendo a las comparaciones con la cocina, podríamos comparar al código fuente con la "receta" para preparar una apetitosa comida.

Pero...la computadora no entiende eso...por sí misma no entiende ni jota de un lenguaje de programación....sólo entiende japonés...o mejor dicho, sólo entiende
programas en "código de máquina" (o "binarios"). Ahí entra en escena el héroe de la película. Que no es Chuck Norris...sino un programa muy especial llamado "Compilador".

¿ Qué hace el compilador ?
En pocas palabras: un compilador hace las veces de "traductor". CONVIERTE EL CODIGO FUENTE EN LENGUAJE DE MAQUINA (O "BINARIO"). Recién después de esta "traducción" la
computadora podrá hacer funcionar nuestro programa y nos podremos enterar cuánto es la suma de cinco y dos. Un programa "en código de máquina" (o sea que ya está
compilado) tiene la extensión .exe ,entre otras (en Windows). Los archivos con las extensiones DLL, SYS, COM y OCX también son "binarios".

En síntesis:

* Las computadoras necesitan que los pogramas estén en "código de máquina" (también llamado "binario") para que puedan funcionar.
* El código de máquina es chino básico para un humano. Prácticamente inentendible, a tal punto que hacer un programa directamente de esa forma sería una pesadilla.
* Los humanos escriben los programas usando un lenguaje de programación, que pueden entender fácilmente. Estas intrucciones se llaman "código fuente" (la "receta").
* Entonces, muestro héroe, el señor compilador, convierte ese código fuente en código de máquina para que la computadora pueda entenderlo y ejecutarlo.

Código fuente (escrito por un humano) ---> Compilador (traductor) ---> Binario (en lenguaje de máquina y entendible por la computadora)

Receta ---> Chef + ingredientes + proceso de preparado y cocción ---> Una rica comida

De lo visto anteriormente se pueden sacar algunas conclusiones interesantes:

[B]

* Para hacer un programa, un programador lo escribe usando un lenguaje de programación, usa un compilador y obtiene el binario, que va a ser lo que ejecutará el usuario de ese programa. No es necesario tener el código fuente para que el programa se pueda ejecutar. Con sólo tener el binario basta para que pueda funcionar.

* Una vez obtenido el "binario", no es posible [1] conocer lo que hace el programa.

* Leyendo el código fuente de un programa, una persona puede saber lo que hace ese programa. Un programador (o un usuario muy avanzado) -provisto de un compilador- podría modificar ese código fuente, para corregir errores, agregar nuevas prestaciones al programa, o lo que se le ocurra. 

Estas características aparentemente sin importancia, hacen una diferencia ENORME entre los diferentes modelos de licenciamiento/comercialización del software.

[/B]

Basta por hoy. En la próxima entrega vendrá una introducción a las distintas licencias del software y sus implicancias para el usuario.


[1]: Esto no es del todo cierto: existe un proceso llamado "desensamblado", que es algo así como un "descompilador" que a partir de un binario permite obtener un listado
de instrucciones más o menos entendibles (código fuente). El problema es que lo que se obtiene no es directamente el "código fuente" original, sino algo mucho más
primitivo, y es tremendamente difícil de entender (además de muy extenso...un simple programa para sumar dos números al ser descompilado puede convertirse en un código
fuente de decenas y decenas de líneas). Volviendo a la analogía "culinaria", es como intentar obtener la receta exacta a partir de un plato ya cocinado y que tenga muchos
ingredientes.
No todo es blanco o negro: existen lenguajes que en lugar de un compilador, cuentan con un "intérprete" que lee el código fuente y lo ejecuta "en el momento". Normalmente esto se traduce en una mayor lentitud de ejecución con comparación con el binario "compilado", amén de algunas ventajas. Hay otros matices como los compiladores "just in time" y los bytecodes, pero es algo que excede por mucho a este texto introductorio.

Saludos !  :D

---

### Post by rretamar on 2008-06-03
Segunda entrega:

En la entrega anterior vimos en forma muy simplificada cómo se hacen los programas y establecimos la diferencia entre "código de máquina o binario" y "código fuente". Vimos que sin el código fuente no es posible saber todo lo que hace un programa y mucho menos el llegar a poder modificarlo.

Las desventuras de pepito el usuario - Una historia ficticia: Imaginate que compras un auto...pero uno muy especial: tiene un sólo asiento. Si querés asientos para más personas debes pagar nuevamente lo que te costó el auto por cada asiento que agregues. Tiene el capot soldado. Si, soldado, no se puede abrir. No sólo no se puede abrir, sino que es ilegal hacerlo. No podés prestárselo a nadie, porque no es legal. No podés cambiarle las cubiertas por otras más "patonas" o polarizarle los vidrios, porque infringirías la ley. No podés llevarlo del mecánico de tu barrio que es un capo de los motores, porque al tener el capot soldado no puede repararlo. Ni siquiera puede mirar lo que hay dentro. ¿ Tendrá un motor como el que dicen ? ¿ Cómo será ese motor ? ¿ Y si tiene algo más ?. Nadie lo sabe.

Para colmo, se te queda el auto en el medio de la ruta. Llamas al soporte técnico de la empresa que lo hace, y luego de pasarte una factura -no tienen un pelo de tontos- , te sugieren muy amablemente que esperes un tiempo, porque esa falla será corregida en el nuevo modelo que sale dentro de un año (se va a llamar "Vista Car"), y que por el momento lo que podés hacer con el tuyo para que vuelva a arrancar es probar bajar y volver a subirte. Al tiempo alguien toca el timbre de tu casa: son los abogados de "auto legal", que vienen a inspeccionar que hayas pagado la correspondiente licencia para usar tu "Auto XP" (-"mostrando, mostrando, vamos, una licencia por cada asiento...no te hagás el vivo", te dicen). Más te vale tener la licencia en regla, porque la multa puede ser suculenta. Y si no querés que te inspeccionen, unos señores de azul que los acompañan te harán entender (muy cordialmente, por supuesto) de que estás equivocado.

Luego de un año sacan el auto modelo "Vista Car". Todos los medios periodísticos se hacen eco del "nuevo y mejorado" modelo, por supuesto, cantando loas como si fuese la octava maravilla. Sin embargo, gasta mucha más nafta que el "modelo XP", hace lo mismo...pero es más lento e incómodo de usar. Y viene con un único asiento. Es un elefante (pero un elefante excedido de peso) que no entraría en el garage de tu casa. Así que seguís con el modelo XP. Justamente estás necesitando otro asiento, para llevar a tu señora al trabajo. Llamás a "M & S Cars" y preguntás cuánto cuesta un nuevo asiento para el "modelo XP", que es el que tenés y usas todos los días, pero te dicen que **no se vende más**. Que tendrías que cambiar el auto...por el "modelo Vista". Y de paso, construir un nuevo garage o ampliar la capacidad del que tenías.

Al final tenés que pasar por el aro de "M & S Cars", teniendo que confiar (a la fuerza) de una empresa que acumuló sólo en los últimos diez años más pleitos que Al Capone en toda su vida.

¿ Esa situación te resulta familiar ? ¿ Te parece algo absurda -en cierta forma lo es, a pesar de que nos quieran hacer creer que eso es lo "normal"- ?. Así funciona el software "propietario", como veremos a continuación.

El modelo de negocios "tradicional" por el cual se "vende" (ya veremos que el término vender es bastante desacertado) un software es más o menos así:

* El usuario necesita un software para cualquier área (desde llevar el stock de su negocio hasta componer una partitura musical).
* El usuario encarga a un programador el desarrollo de ese software según sus requerimientos, o bien lo compra ya "enlatado", o sea un software ya hecho y que tiene las prestaciones que está necesitando.
* Lo que hace el señor "usuario" es pagar una "licencia de uso". Esta licencia no significa que el software que pagó pase a ser suyo, sino que consiste en un "contrato" por medio del cual **adquiere un permiso de uso** (bastante semejante a un "alquiler") del software a la empresa que lo creó o la que lo comercializa.
* El usuario recibe un CD con el **binario** del software y las instrucciones para instalarlo en su PC. A veces el mismo desarrollador (o un representante) se encarga de la instalación y "puesta en marcha" del sofware.

Este modelo se conoce como "venta de licencias" (la licencia viene impresa junto al software -cuando viene- en elegante "letra chica"), y normalmente aplica a la copia del software que el usuario tiene varias restricciones. Las más importantes son:

1) Propiedad del software: la licencia autoriza a que el usuario use el programa, pero dicho programa sigue perteneciendo única y exclusivamente a la empresa que lo creó.

2) Licencia "por puesto": el software sólo se podrá instalar **en una única computadora**. En caso de querer hacerlo en más de una, se deberá adquirir otra licencia. Un equipo = una licencia de uso. Instalarlo en más de un equipo sin el pago de la correspondiente licencia es ilegal y podría suponer para el usuario desde una abultada multa hasta unas apetecibles vacaciones a la sombra.

3) Está prohibido el "desensamblado" (explicado al final de la entrega anterior...) del software y cualquier tipo de modificación al mismo por parte del usuario o de terceros, bajo una penalización similar al punto anterior.

4) La copia del software y su trapsaso a terceros también constituye un delito. Sólo se permiten copias del medio de almacenamiento (en nuestro ejemplo, el CD) por parte del mismo usuario y a modo de "copia de seguridad" (backup).

5) No se permite la "reventa" de la licencia a un tercero.

6) Si el software contiene código de encriptación de alto grado de seguridad, "made in USA", no podrá distribuirse en países que tengan restricciones de exportación desde ese país, como ser Cuba, Corea del Norte, Libia, y otros.

-"¿ Y en qué me preocupa esto ?" -Dice un usuario desprevenido llamado casualmente "Pepito" . -"Yo pago mi licencia, uso el programa y listo".

Sin embargo...estas restricciones pueden traerle varios dolores de cabeza. La principal limitación es que **no se dispone del el código fuente** del software. Sólo se tiene el binario (el fuente queda en poder de la empresa que hizo el programa, bajo siete llaves).

Este modelo de "comercialización" se conoce como "software propietario" (o "software cerrado", debido a la imposibilidad de disponer de los fuentes). Bajo este modelo de comercialización encontramos software tan conocido como Microsoft Windows, Microsoft Office, software "enlatado" como por ejemplo el sistema administrativo "Tango", software para diseñadores como Corel Draw, Adobe Photoshop, Visual Basic, etc.

El no disponer de las fuentes puede ser un problema en situaciones como las siguientes:

* Nadie más que la empresa propietaria del software podrá hacer modificaciones al mismo. Hablo de modificaciones para corregir errores, agregar nuevas prestaciones, cambios para adaptarlo a un uso en particular. ¿ Y porqué ? Porque son los únicos que tienen el código fuente. Si el usuario necesita alguna modificación, podrá pedírsela a la empresa (que en muchos casos suele ser una multinacional "en el gran país del norte") y esta evaluará si es viable o no. Muchas veces la respuesta es "eso será corregido en la próxima versión" o directamente se lo ignora, ya que no resulta rentable modificar puntualmente algo que se vende en forma masiva. Este infortunado usuario, si la empresa creadora del software no lo tiene en cuenta, tampoco podrá llamar a otro programador para que haga el trabajo, ya que sólo cuenta con el binario. Está totalmente cautivo; atado de pies y manos.

* En el caso de instituciones educativas, la naturaleza tipo "caja negra" (además de los impedimentos legales) del software propietario impide su estudio por parte de los alumnos y profesores.

* Hay casos (como un conocido software para diagnóstico de automotores) que sólo dan soporte a la última versión. Esto obliga al usuario a actualizar el software permanentemente (aunque no necesite realmente esas actulizaciones), de lo contrario ante un problema nadie lo ayudará.

* La forma en que el software propietario guarda la información muchas veces **no está documentada** y tampoco se puede ver de qué manera lo hace .Si nuestro sufrido usuario cambia por ejemplo su sistema de stock por otro, el nuevo sistema no podrá (o en el mejor de los casos se hará muy complicado) poder llegar a leer la información que guardaba el sistema anterior. ¿ Nunca se preguntaron porqué el software competidor de Microsoft Office no puede leer los documentos generados por este al 100 % ? La respuesta es simple: la forma en que se guardan los documentos de MS Word o las planillas de cálculo de MS Excel no está documentada, y lo que se conoce es en base a estudiar "o diseccionar" los archivos e intentar entender qué es lo que guardan ahí. Esto se llama "ingeniería inversa" y además de ser un trabajo "de chinos" (puede convertirse en una verdadera pesadilla si el "formato" de los datos es complejo -y generalmente lo es-), en varios países es además ilegal.

* El tener total control sobre el software, hace que casi siempre sólo se comercialicen licencias sólo de las última versión. A veces un usuario requiere una versión del software algo más antigua por varias razones (porque tiene un equipo antiguo, porque las prestaciones de la versión antigua le son más que suficientes, o motivos puramente económicos, ya que supone que una versión más antigua tendrá un costo menor en la licencia). Tuve ese problema al intentar adquirir una licencia de un Windows 2000 para uso en un equipo industrial, pero sólo me vendían el Windows Vista. Eso o nada. El trato a que se llega a veces es "pague la licencia de la última versión, pero use una antigua".

* Dificultad para la comunicación: el software propietario puede usar protocolos de comunicación [1] no documentados, lo que impide que otro software pueda intercambiar información con él. Ante un problema de esa naturaleza, y ante la falta de información disponible sobre dicho protocolo (y la ausencia del código fuente donde se podría ver cómo se implementa), nuevamente se tiene que echar mano de la "ingeniería inversa". Lo que se convierte en un problema de nunca acabar, ya que los autores de protocolos propietarios van introduciendo cambios que nuevamente se tendrán que descifrar, y así sucesivamente.

* No se sabe con exactitud si el programa hace "algo más" que lo que el "fabricante" dice que hace. No se puede ver lo que hace, ya que sólo se dispone de el binario. Esto es especialmente delicado en software que se encarga de trabajar con datos de carácter confidencial. Buena parte del software que guarda datos sobre nuestros impuestos, sobre nuestras cuentas bancarias, sobre nuestra misma identidad, está basado en software propietario perteneciente a multinacionales. Se han descubierto "puertas traseras" (o modos de ingresar a la información) ocultas a propósito en este tipo de software.

* Se tienen varios equipos, y al tener que adquirirse licencias "por puesto" , el costo se multiplica por la cantidad de equipos que se tenga y puede llegar a cifras elevadísimas. Hagamos números para un equipo básico (uso típico en una oficina):

-Licencia de Windows Vista: **$ 750.**
-Licencia de Microsoft Office: **$ 800.**
-Licencia del Antivirus: **$ 150** (más el costo de la suscripción periódica para poder mantenerlo actualizado).

Costo total de licencias para un equipo: **$ 1700** (actualizable al valor del dólar). Sí...**el costo de las licencias supera el costo de una PC de gama media**. Ahora hay que multiplicar esos $ 1700 por la cantidad de equipos que tenga la empresa. Y eso sin contar software para uso más específico, como el usado en ingeniería, arquitectura, diseño gráfico, gestión comercial, etc. etc.

Es interesante recalcar algo: el software propietario vende **copias** (licencias) de un bien intangible **(y dada su naturaleza puramente digital, con un costo de duplicación y distribución que tiende a cero)**. Costosas copias de un bien inmaterial que no se consume y se puede duplicar indefinidamente, comercializándolo igual que un bien tangible como una silla o una manzana.

Es mucho dinero. Muchísimo dinero. Dinero que en muchas ocasiones lo paga el ciudadano, con sus impuestos. Y lo paga aún existiendo **alternativas libres** a un costo mucho menor (además de otras ventajas no menos importantes, como veremos en la siguiente entrega de esta serie).

Entonces, si tuviéramos que resumirlo en pocas palabras, podríamos decir que el modelo de negocios del software propietario se basa en la venta de copias (licencias) de software binario (cerrado).

Variantes, de todo color y pelaje: Además del esquema de licenciamiento visto recién, hay otras variantes dentro del software propietario:

* Freeware: costo cero y funcionamiento sin limitaciones, pero **no se dispone del código fuente**. Ejemplo: Spybot Search & Destroy, Adobe Acrobat Reader, el plug-in de Macromedia Flash, AVG Antivirus Free, el navegador Opera, algunas versiones de Nero incluídas gratuitamente con unidades de grabación, etc.

* Shareware: libre distribución. Brinda la posibilidad de evaluar el software durante un período (generalmente entre 15 y 60 días), y luego el usuario -si el software le es útil y el precio conveniente- puede decidir si adquiere la licencia (eso se conoce como "registración"). No se dispone del código fuente. La copia registrada está cubiera por las restricciones vistas anteriormente (licencia por puesto, sin fuente, prohibida su distribución, etc.).

Para "incentivar" (las comillas son imprescindibles) a que el usuario se registre, la versión shareware puede tener menos prestaciones que la versión registrada, o bien tiene algún elemento que a la larga moleste al usuario y le recuerda que es una versión sin registrar (un mensaje que aparece al arrancar, un mensaje que aparece en las impresiones, etc). También pueden restringirse opciones (por ejemplo la imposibilidad de imprimir o de guardar datos) luego de transcurrido el período de prueba. Este software restringido también se conoce como "Trialware". En muchos casos la línea que separa un "Trial" de un "Shareware" es algo difusa, debido a la diferente variedad de limitaciones que se introducen.

Ejemplo de software shareware: Winzip, Winrar.

Demos: software con partes deshabilitadas (o directamente no incluídas) que permiten hacerse una idea de cómo funciona y las prestaciones que tiene. En casi todos los casos las limitaciones son permanentes e importantes (no se permite guardar, no se permite imprimir, algunas partes del programa no existen o están deshabilitadas). El código fuente (como se podría suponer) no está disponible.

Ad-ware/Malware: es una variedad de freeware que incluye publicidad, en forma de anuncios emergentes, áreas el programa donde se muestran carteles, o bien páginas web que aparecen al arrancar (o cerrar) el programa. La variante perversa de este tipo de ejemplares es el llamado "Malware", que incluye la instalación de software espía (spyware) en tu PC. Si se quita el spyware, la aplicaciónb que lo instaló puede negarse a funcionar. Ejemplos: Kazaa Media Desktop (sí, uno de los P2P más usados hasta hace un tiempo).

Entonces...¿ el software propietario es malo ? La respuesta a mi modo de ver es un rotundo NO, pero creo que tiene varios inconvenientes -anteriormente citados- que en muchos casos lo desaconsejan y es importante conocerlos. 

Eso es todo por hoy. Hasta la siguiente entrega y gracias por la lectura ... ;)

[1] Protocolo de comunicación: se trata de una serie de reglas que utilizan dos (o más...) equipos para poder comunicarse adecuadamente ("entenderse") entre sí. Estas reglas definen cuándo comienza la comunicación, cuando termina, la forma en que se envía o recibe la información, cómo se verifica que los datos no presenten errores, etc. Hay protocolos muy simples y otros extremadamente elaborados. Ejemplos: TCP, UDP, NTP, POP3, SMTP, IMAP, etc. La mayoría de los prococolos están perfectamente estandarizados y documentados . Sin embargo hay empresas que pueden aprovechar su condición de monopolio para imponer sus propios protocolos que sólo conocen ellas, o bien agregando "extensiones" propias a protocolos ya establecidos pero sin documentar estos cambios. Quien quiera comunicarse con estos productos va a tener que sudar para poder hacerlo.

---

### Post by pol666 on 2008-06-03
Que bueno que esta esto. Tendriamos que armar un folleto con  estas analogias rretamar ;)
...




aunque a veces me gustaria saber cual es el porcentaje de la poblacion argentina que tiene windows original con licencia y que lo halla pagado el mismo... mmm

Aca lamentablemente le tiras este discurso a un pibe de aca, y como conclucion desprende 2 cosas:

* Nunca pague ni voy a pagar por Guindou
* No se un corno, ni tengo la minima intencion de saber programacion para modificar un programa
* la pesé e para juga' y linu' no sirve.

---

### Post by rretamar on 2008-06-03
Ese pibe, que se llama "Pepito", se hicha el pecho afirmando que tiene el windows trucho, que no pagó un mango, y es más vivo que el mismo Bill, pero en realidad sí que está pagando....CON SUS IMPUESTOS. Porque cuando en un organismo estatal tienen que instalar un sistema operativo, siempre aparece algún Pepito de turno diciendo que como es lo que tiene en la casa y todo el mundo conoce, entonces es lo que hay que usar. Y lo mismo vale para la suite de oficina ("Si hasta mis pibes la aprenden en el colegio"). Y ahí sí, poniendo estaba la gansa. Cifras millonarias que se van en licencias hacia una multinacional de yanquilandia.

Saludos....en unos días posteo la tercera parte. ;)

---

### Post by User21 on 2008-06-03
No puedo permitir que este contenido quede solo relegado al publico que ingresa por aqui. Lo voy a postear en el blog, siempre citando la fuente, por supuesto. Se me hizo MUY AMENA la lectura. Muchas Gracias! :)

---

### Post by Hei Ku on 2008-06-03
Muy buena la explicación. Una sola aclaración, que si bien lo pusiste entre comillas es importante diferenciar. La licencia de un software, salvo en casos especificos, no se trata de un contrato. Un contrato implica un acuerdo entre ambas partes. En el caso común de una licencia de usuario de software, al ser una cosa al estilo tomalo o dejalo de parte de la empresa que comercializa el software, no tiene la categoria de contrato. 

Esto es importante, porque a pesar de la cantidad de cosas que te dicen que te van a hacer si no cumplis los terminos de la licencia (te confiscan a tu hijo, te quedas pelado, te matan el perro y te ***** el asado, etc.), la realidad es que rigen los terminos comunes a cualquier elemento protegido por las leyes de propiedad intelectual. (dependiendo mas o menos del "abuso" al cual se pueda ver sometido el sistema judicial, se entiende.)

Excelente aporte, rretamar!

---

### Post by rretamar on 2008-06-03
Este texto originalmente lo hice (y lo sigo haciendo) para el sub-foro de informática de Zona Metal (donde estoy de moderador). Tal vez aquí peque de desmasiado "simplista", y más habiendo gente que en estos asuntos está más que ducha. Mi idea es que alguien que jamás leyó qué significa el SL pueda hacerse una idea y...quien sabe...puede que eso sea sólo el comienzo y luego se interese más.

Mi modesto granito de arena a este mundo maravilloso...

Saludos...

rretamar = Ramón Retamar ;)

---

### Post by Mister X on 2008-06-04
Esta muy bueno que se le de difusion a este tipo de informacion, ya que muchas personas llegan al SL porque vieron una impresionante interfaz grafica y mucho eye candy, pero eso es solamente la punta del iceberg, tiene muchos costados mas: filosoficos, economicos, sociales, etc.

Felicitaciones rretamar porque el articulo está encarado de una forma que se hace muy facil leerlo y por lo tanto de entenderlo. Y gracias por tomarte el trabajo de hacerlo.

---

### Post by pol666 on 2008-06-04
off topic: > Zona Metal (donde estoy de moderador)

U_U no coments. aguante el metal.


Topic: Yo tambien lo voy a poner en mi blog con tu permiso. :)

---

### Post by marianom on 2008-06-05
Simplemente 2 palabras: briyyante!
A ver cuando leemos la tercera parte.

¿Podría ir al sitio de Ubuntu-Ar no?

---

### Post by tzulberti on 2008-06-05
Este finde me encargo de leer este articulo y el que hizo natalia para ver si hace falta agregarle algo, para ponerlo en la wiki de la pagina.

---

