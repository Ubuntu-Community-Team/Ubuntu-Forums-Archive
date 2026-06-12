---
title: "64 bits o PAE?"
date: 2011-12-05
forum: Comunidad
---

### Post by joseluis on 2011-12-05
amigos, tengo instalado xubuntu e hice una actualizaciòn a mi PC, con lo que me quedò con 4 gigas de Ram. Sabido es que el SO de 32 me toma solo 3,x de ram y desaprovecha el resto.
La pregunta es ¿instalar PAE resuelve esto verdad? He recibido un comentario que no todos los programas pueden acceder a esta particularidad del kernel PAE y que quizás no aproveche debidamente esos megas restantes.

Si es asi, me queda la opción de instalar 64 bits, con lo que tendría que reinstalar, reconfigurar y hasta ver si todo lo que uso tiene versión de 64 bits.

Entonces, ¿PAE me conviene en este caso? Repito: he recibido el dato de que no todos los programas están escritos para superar la limitación de los 3 gigas.

Gracias, y espero haber sido claro en este planteo.

---

### Post by Majid7 on 2011-12-05
Como usted ha dicho, su sistema operativo sólo utiliza 3G de memoria RAM,
No creo que sea muy necesario volver a instalarlo en 64 bits.
ubuntu no utiliza gran parte de la memoria RAM
pero trate de PAE.
lo siento por la mala redacción.

---

### Post by BC59 on 2011-12-05
Hay una manera para aprovechar toda la RAM que tienes instalada.
No la he probado por eso no estoy seguro si funciona.

Debes instalar los siguentes paquetes:

```
sudo apt-get install linux-restricted-modules-server

sudo apt-get install linux-headers-server

sudo apt-get install linux-image-server linux-server
```

reboot y mira si ves toda la RAM.

---

### Post by joseluis on 2011-12-05
> **BC59 said:**
> Hay una manera para aprovechar toda la RAM que tienes instalada.
No la he probado por eso no estoy seguro si funciona.

Debes instalar los siguentes paquetes:

```
sudo apt-get install linux-restricted-modules-server

sudo apt-get install linux-headers-server

sudo apt-get install linux-image-server linux-server
```

reboot y mira si ves toda la RAM.

hola, ¿y qué sería esto? ¿una alternativa a PAE?

edito: esta pagina [http://foro.noticias3d.com/vbulletin/showthread.php?t=275719](http://foro.noticias3d.com/vbulletin/showthread.php?t=275719) alguien dice lo siguiente:
"Te recomiendo que no lo hagas... 
Yo intenté esto exactamente y el sistema se volvió inestable y además no reconoce la RAM que falta. 
Me gasté una pasta en memoria RAM que ahora no me reconoce, (exactamente igual que a tí).
Alguien me comentó que Open Suse con un parche... la reconoceria.... (no lo se, ni lo he probado)
Por la poca idea que tengo... para entender terminos de informatica de avanzado nivel...
Googleando me pareció leer que siendo el sistema de 32bits no hay nada que hacer...
Me gustaria estar confundido... y que alguien arrojase luz esclarecedora sobre el tema, porque... aunque es cierto que con 3Gb de RAM va muy bien... 
Ideal sería poder aprovechar los recursos al maximo."

tonces??

---

### Post by BC59 on 2011-12-05
La verdad es que yo utilizé esta solucion hace unos años y que funcionó. Pues no se, nunca estas seguro si funcionará en tu modelo de ordenador.

---

### Post by guillermolisi on 2011-12-05
> **joseluis said:**
> amigos, tengo instalado xubuntu e hice una actualizaciòn a mi PC, con lo que me quedò con 4 gigas de Ram. Sabido es que el SO de 32 me toma solo 3,x de ram y desaprovecha el resto.
La pregunta es ¿instalar PAE resuelve esto verdad? He recibido un comentario que no todos los programas pueden acceder a esta particularidad del kernel PAE y que quizás no aproveche debidamente esos megas restantes.

Si es asi, me queda la opción de instalar 64 bits, con lo que tendría que reinstalar, reconfigurar y hasta ver si todo lo que uso tiene versión de 64 bits.

Entonces, ¿PAE me conviene en este caso? Repito: he recibido el dato de que no todos los programas están escritos para superar la limitación de los 3 gigas.

Gracias, y espero haber sido claro en este planteo.
El tema es algo mas complejo que ver o no ver por encima de los 3Gb RAM.

Por un lado es importantisimo verificar que el BIOS de la maquina tenga una adecuada implementacion para gestionar direccionamientos por encima de los 3Gb, aun si la motherboard posee un procesador de 64 bits.
La implementacion de la que hablo involucra la gestion a traves de [IOMMU]("http://en.wikipedia.org/wiki/IOMMU").

Si el BIOS de esa maquina no posee una correcta implementacion de IOMMU, sea por cualquiera de los tres metodos existentes a la fecha, no vas a poder lograr que funcione en forma estable con Ubuntu 64 bits.

Funcionara estable, a pesar de esa posible falencia del BIOS, si utilizas la variante PAE del kernel 32 bits. La variante PAE permite que un entorno operativo de 32 bits pueda utilizar RAM por encima de los 3Gb.

No hay que olvidar que gracias a la obsoleta arquitectura Intel, siempre se paga un costo de RAM no disponible para el usuario para que el sistema mantenga retrocompatibilidad con software y hardware anteriores a los 32 bits. Esto significa que a pesar de usar kernel PAE o un kernel de 64 bits, el monitoreo de RAM disponible dara menos de lo que una cuenta simple arroja como resultado. Esa cantidad de RAM que se "pierde" lo usa el sistema para mapear punteros de memoria y otros elementos operativos por encima del limite de los 32 bits.

Por otra parte, hay que considerar que usar un sistema de 64 bits no necesariamente representa una ganancia significativa de aprovechamiento de la RAM instalada, simplemente porque los sistemas de 64 bits consumen mas RAM que sus equivalente de 32 por caracteristicas propias (longitud de registro de maquina, por ejemplo).

Obviamente, aunque en esto hay quienes opinan diferente a partir de percepciones propias, tampoco deberia haber una ganancia significativa de rendimiento ya que las capacidades del procesador no varian si se lo usa con un sistema de 32 o 64 bits.

Respecto de las aplicaciones, aun siguen siendo mayoria las desarrolladas para 32 bits y siguen siendo pocas las que tambien se desarrollan para 64 bits en forma nativa.

Gran parte de esto lo digo por experiencia propia: Una maquina con PAE 32 bits para 4Gb RAM y procesador de 64 bits sin soporte para IOMMU (BIOS berreta y sin posibilidad de actualizacion) y otra con Linux 64 bits, 4Gb RAM y soporte completo para IOMMU.

Ambas maquinas corren la misma cantidad de programas, tienen instalados los mismos programas y les doy el mismo uso.
La que corre PAE consume menos RAM que la que corre el kernel de 64 bits.

Las dos funcionan muy estables, perfectas para el trabajo diario sin sobresaltos.

EDIT: Los programas, independientemente de su arquitectura de maquina, usaran siempre los recursos del sistema a traves del Kernel y es este el que determina en que lugar de la RAM disponible corren.

---

### Post by joseluis on 2011-12-05
excelente tu explicación Guillermo!! a la noche, cuando llegue a casa me pongo a actualizar el kernel con PAE y cuento. gracias

---

### Post by 1clue on 2011-12-05
Es probable que todo que se utiliza tiene una versión de 64 bits, pero puede instalar multilib y obtener lo mejor de ambos mundos. Hago bien con pura 64.

---

### Post by joseluis on 2011-12-05
bueno, probé y me hizo un lio con la tarjeta gráfica. no reconoce mi nvidia y no me deja modificar resolución ni nada. Me parece que voy por la versión de 64.-

---

### Post by collisionystm on 2011-12-05
64 bits, por supuesto! PAE es un hack!

---

### Post by guillermolisi on 2011-12-05
> **joseluis said:**
> bueno, probé y me hizo un lio con la tarjeta gráfica. no reconoce mi nvidia y no me deja modificar resolución ni nada. Me parece que voy por la versión de 64.-

Que driver de video estas usando ? los nativos de nVidia o Nouveau ?

Si es nVidia, lo instalaste desde los repositorios de Ubuntu o lo instalaste usando una version bajada del site de nVidia ?

Si fue esta ultima a forma, tenes que volver a instalarlos ya que el modulo nVidia hay que asociarlo al nuevo kernel que instalaste.

Mostranos la salida del comando "lsmod" ingresado en una terminal/consola.

---

### Post by guillermolisi on 2011-12-05
> **collisionystm said:**
> 64 bits, por supuesto! PAE es un hack!
Podrias ser mas explicito y decirnos concretamente que queres significar con la expresion "PAE es un hack" ?

Asi como lo mencionas no me parece que quede claro si es una caracteristica neutra, algo positivo o algo negativo a los fines de usar o no un kernel PAE.

De paso, por favor podrias contarnos brevemente tu experiencia con maquinas que utilicen kernel PAE para que los demas se ilustren a partir de ello y asi poder decidir mejor cuando se encuentren en situaciones similares a este caso ?

Por otro lado, parece que no se leyo bien lo que comente sobre la implementacion de IOMMU por parte del BIOS. Les recomiendo volver a leerlo si ya lo han hecho porque si la maquina del interesado no posee esta funcionalidad implementada por su BIOS no podra usar un sistema de 64 bits.

---

### Post by collisionystm on 2011-12-06
> **guillermolisi said:**
> Podrias ser mas explicito y decirnos concretamente que queres significar con la expresion "PAE es un hack" ?

Asi como lo mencionas no me parece que quede claro si es una caracteristica neutra, algo positivo o algo negativo a los fines de usar o no un kernel PAE.

De paso, por favor podrias contarnos brevemente tu experiencia con maquinas que utilicen kernel PAE para que los demas se ilustren a partir de ello y asi poder decidir mejor cuando se encuentren en situaciones similares a este caso ?

Por otro lado, parece que no se leyo bien lo que comente sobre la implementacion de IOMMU por parte del BIOS. Les recomiendo volver a leerlo si ya lo han hecho porque si la maquina del interesado no posee esta funcionalidad implementada por su BIOS no podra usar un sistema de 64 bits.


Yo personalmente no me gusta porque PAE de 32 bits no fue diseñado para manejar ese tipo de memoria. Procesadores de 32 bits tienen una baja velocidad de FSB y por lo tanto tienen que trabajar más para trabajar a través de las líneas de código. 64 bits sin embargo, está diseñado para funcionar con más de 100GB de memoria, ya que fue diseñado de esa manera.
 Si quieres un buen rendimiento de un sistema de 32 bits, la clave está en mantener sus ciclos de CPU de baja hasta que lo necesite. Digamos que usted tiene aplicaciones sólo ejecutar el fondo y con 30% de CPU. De repente se desea ejecutar una aplicación intensiva gráfica o ver un video flash, sólo el 70% de la CPU para trabajar con una CPU y una vez que ha pasado del 80% del sistema realmente comienza a empantanar.
 ¿Es el más rápido RAM que puede y la mejor tarjeta de vídeo que puede. La CPU no trabaja tan duro cuando el hardware Rother puede manejar por sí solo.

---

### Post by guillermolisi on 2011-12-06
> **collisionystm said:**
> Yo personalmente no me gusta porque PAE de 32 bits no fue diseñado para manejar ese tipo de memoria. Procesadores de 32 bits tienen una baja velocidad de FSB y por lo tanto tienen que trabajar más para trabajar a través de las líneas de código. 64 bits sin embargo, está diseñado para funcionar con más de 100GB de memoria, ya que fue diseñado de esa manera.
 Si quieres un buen rendimiento de un sistema de 32 bits, la clave está en mantener sus ciclos de CPU de baja hasta que lo necesite. Digamos que usted tiene aplicaciones sólo ejecutar el fondo y con 30% de CPU. De repente se desea ejecutar una aplicación intensiva gráfica o ver un video flash, sólo el 70% de la CPU para trabajar con una CPU y una vez que ha pasado del 80% del sistema realmente comienza a empantanar.
 ¿Es el más rápido RAM que puede y la mejor tarjeta de vídeo que puede. La CPU no trabaja tan duro cuando el hardware Rother puede manejar por sí solo.
Ok.

Solo para aclarar conceptos, una cosa es hablar de la arquitectura del sistema operativo y otra, relacionada pero distinta, es hablar de las capacidades del procesador.

Hay cantidad de maquinas con procesadores de 64 bits instalados en motherboards cuyas carateristicas estan muy por debajo del mejor aprovechamiento de esa CPU, ya sea porque el BIOS no es el adecuado, porque el chipset tampoco, etc. Por ello hay que saber distinguir lo teoricamente ideal de lo concretamente real, por eso es importante conocer de antemano las caracteristicas del hardware a utilizar antes de decidir usar una arquitectura u otra para el sistema operativo.

Entonces, PAE no es un hack, es una caracteristica del kernel Linux que se habilita cuando se lo configura previamente a su compilacion. Es un feature, no un hack. Es algo pensado "de fabrica", no es un workaround o una modificacion "casera".

Y con o sin PAE, reitero, las caracteristicas del hardware que se este utilizando no se alteran, por lo tanto en ambos casos la CPU junto con demas cuestiones funcionales del hardware, se utilizaran siempre de igual forma sin importar si la longitud de registro de maquina sea del largo que sea.

Por que digo esto ? Porque ambas arquitecturas siguen sujetas al esquema obsoleto de Intel para mantener retrocompatibilidad con hardware y aplicaciones de menos de 32 bits. Es decir, PAE es una implementacion por software de IOMMU, uno de los tres metodos existentes a la fecha (los otros dos son por hardware, creado por AMD, y uno mixto, creado por IBM).

Si los beneficios reales de los sistemas de 64 bits fueran como muchos comentan, por que razon la industria continua desarrollando 32 bits (tanto a nivel de hardware como de software) ? Por que no es todo 64 bits mas alla de la cantidad de RAM que cada equipo tenga instalada ? Marketing ?

Gracias por tu explicacion !

---

### Post by collisionystm on 2011-12-06
> **guillermolisi said:**
> Ok.

Solo para aclarar conceptos, una cosa es hablar de la arquitectura del sistema operativo y otra, relacionada pero distinta, es hablar de las capacidades del procesador.

Hay cantidad de maquinas con procesadores de 64 bits instalados en motherboards cuyas carateristicas estan muy por debajo del mejor aprovechamiento de esa CPU, ya sea porque el BIOS no es el adecuado, porque el chipset tampoco, etc. Por ello hay que saber distinguir lo teoricamente ideal de lo concretamente real, por eso es importante conocer de antemano las caracteristicas del hardware a utilizar antes de decidir usar una arquitectura u otra para el sistema operativo.

Entonces, PAE no es un hack, es una caracteristica del kernel Linux que se habilita cuando se lo configura previamente a su compilacion. Es un feature, no un hack. Es algo pensado "de fabrica", no es un workaround o una modificacion "casera".

Y con o sin PAE, reitero, las caracteristicas del hardware que se este utilizando no se alteran, por lo tanto en ambos casos la CPU junto con demas cuestiones funcionales del hardware, se utilizaran siempre de igual forma sin importar si la longitud de registro de maquina sea del largo que sea.

Por que digo esto ? Porque ambas arquitecturas siguen sujetas al esquema obsoleto de Intel para mantener retrocompatibilidad con hardware y aplicaciones de menos de 32 bits. Es decir, PAE es una implementacion por software de IOMMU, uno de los tres metodos existentes a la fecha (los otros dos son por hardware, creado por AMD, y uno mixto, creado por IBM).

Si los beneficios reales de los sistemas de 64 bits fueran como muchos comentan, por que razon la industria continua desarrollando 32 bits (tanto a nivel de hardware como de software) ? Por que no es todo 64 bits mas alla de la cantidad de RAM que cada equipo tenga instalada ? Marketing ?

Gracias por tu explicacion !


   No, muchas gracias por tus conocimientos! Que hacer una investigación mucho más que yo!

 Al final del día, todavía me sugieren siempre el uso de 64 bits. 32 bits se desvaneció debido a sus limitaciones. Sólo el uso de PAE, si es absolutamente necesario!

---

### Post by joseluis on 2011-12-06
y le mandè nomas 64!!! el PAE no me daba ni la hora. Anda barbaro asi,y me tomo los 4 gigas
GRACIAS

---

