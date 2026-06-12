---
title: "Alternativa libre - Desarrollo"
date: 2008-03-17
forum: Comunidad
---

### Post by jclevien on 2008-03-17
Hola que tal,

Al final, decidí publicar esto, para escucharlos y ver sus opiniones.

El tema es así:

Actualmente estoy desarrollando en REALbasic. Entorno interesante, multiplataforma, pago, fácil de trabajar, privativo, tiene algunos errores, el soporte no es de diez, y no es muy barato.

Estoy pensando en cambiar por algo mejor, con las siguientes características:

1. Multiplataforma
2. Gratis, si es posible.
3. Buen soporte.
4. Código abierto.
5. Productivo (al escribir menos, que haga más)
6. Fácil tercerización (que haya una comunidad grande de gente que trabaje con el, a precios accesibles).
7. Estable
8. Fácil mantenimiento.
9. Buenas opciones de bases de datos.


Los lenguajes con los que estuve jugando son:

1. Tcl/Tk
2. Python
3. PHP
4. Lua

Lo que necesito por el momento son aplicaciones de escritorio, con las características mencionadas.

Las impresiones que tengo de cada uno de ellos:

1. Tcl/Tk: interesante, tiene el concepto de comandos, muy estable, buena cantidad de bibliotecas, multiplataforma, tiene threads, buena comunidad de desarrolladores, probado, pero a mi modo de ver no es muy productivo como Python. Y tiene los starkits, para distribuir programas.

2. Python: muy lindo, productivo, pero el problema es que genera un ejecutable grande con py2exe, en comparación con Tcl/Tk. Además, ¿hay algún entorno gráfico equivalente al Tk para Python? No me sirve un toolkit aislado como GTK, porque no encontré un entorno RAD bien integrado para Python. Con buena integración quiero decir algo al estilo de REALbasic. Salvo que la gente de GNOME haya sacado algo similar, que puede ser que no lo haya visto.

3. PHP: excelente comunidad, hay mucha gente, pero no tiene threads, está el PHP-GTK pero al no tener threads se complica la integración al escritorio. Hay clases para hacer de todo, eso es un punto a favor.

4. Lua: no lo miré mucho, por los comentarios que vi, es muy rápido y embebible, se usa mucho en juegos, pero es más árido que Python en cuanto al lenguaje.


Estoy un poco indeciso. Me encantaría usar Python, pero lamentablemente no encontré un toolkit gráfico con la facilidad de uso  de REALbasic.

Escucho sus opiniones con respecto al tema, desde ya les agradezco sus comentarios.


Saludos.


Juan

---

### Post by marianom on 2008-03-17
M faltan conocimientos sobre GUI's Toolkits como para convencerte que pruebes Python. De todos modos, si da, suscribite a la lista de python argentina ([http://www.python.com.ar/](http://www.python.com.ar/)) y tira la pregunta. Hay suficientes pythonistas de los buenos ahí como para que no te queden dudas si es o no una opción.

---

### Post by jclevien on 2008-03-17
Hola Mariano,

Listo, ya me decidí.
Voy a usar Python, con GTK + Glade, o wxPython.

Estuve trabajando con lo siguiente:

1. CodeBlocks
2. Python 2.5
3. Molebox
4. UPX

Hice un ejecutable, en C, linkee la biblioteca Python modificada con dlltool y MinGW, comprimí las bibliotecas con UPX y encripté con Molebox.

Para que tengas una idea, un Hola Mundo ocupa 940 Kb, listo para correr en un Windows. Sin dependencias, sin nada, ni registraciones de DLL, nada.

Esto quiere decir:

1. Es mejor que py2exe (ocupa menos espacio).
2. El ejecutable tiene todo, scripts, bibliotecas, todo encriptado y protegido, listo para correr en Windows.
3. Hasta se podrían poner controles ActiveX y aprovechar más DLLs con extensiones COM de Python.

Ahora voy a probar de embeber un Hola Mundo con PyGTK, luego te cuento.

Saludos.


Juan

---

### Post by marianom on 2008-03-17
Para trabajar bien con Windows en Python, te recomiendo un nombre: Mark Hammond. Es una de las personas que más ha hecho para que Python sea utilizable en Windows (incluso si instalas Python en Windows vas a ver que le agradecen en el instalador) y ha programado muchas de las APIs necesarias para acceder a lo que sea que se necesita acceder en Windows. Fijate los docs, blogs y posts que seguro hay de él por todos lados.
Es también autor de un libro llamado Python Programming in Win32 que contiene mucho de los conocimientos necesarios para empezar (aunque el libro es del 2000).

---

### Post by facundocorradini on 2008-03-17
Sin dudas, mi consejo también va por el lado de python.  La elegancia de este lenguaje no tiene comparación

---

### Post by jclevien on 2008-03-17
Gracias a ambos por sus recomendaciones.

Me estoy entusiasmando con Python.
Como dije antes, apenas resuelva el tema lo publico.


Saludos.


Juan

---

### Post by Hei Ku on 2008-03-17
Para que otros tengan en cuenta, Qt tambien es una alternativa.
Programas en C++ y esta disponible desde en celulares hasta PCs con distintos SO.

---

### Post by marianom on 2008-03-17
> **Hei Ku said:**
> Para que otros tengan en cuenta, Qt tambien es una alternativa.
Programas en C++ y esta disponible desde en celulares hasta PCs con distintos SO.

O lo programas en Python con [pyQT]("http://www.riverbankcomputing.co.uk/pyqt/index.php") (para Windows solo la versión 4 es GPL).

Entregate Hei Ku, te tenemos rodeado :)

---

### Post by Hei Ku on 2008-03-18
> **marianom said:**
> O lo programas en Python con [pyQT]("http://www.riverbankcomputing.co.uk/pyqt/index.php") (para Windows solo la versión 4 es GPL).

Entregate Hei Ku, te tenemos rodeado :)

Buenisimo. No me acordaba que tambien podias usar el Python.


Entre que en el trabajo estoy rodeado por los de Java y .Net, y aca por los de Python, me estoy convenciendo que ya no quedan verdaderos hombres en Sistemas. :lolflag:

---

### Post by jclevien on 2008-03-18
Hei Ku,

¿Has escrito ya tus propios drivers? (Linus Torvalds)

Al final, hice una "mezcla" entre el py2exe y el Molebox.
Usando un tutorial de py2exe con PyGTK pude aislar los archivos necesarios. Con Molebox encripté y comprimí un EXE....

El asunto es que de 940 Kb pasó a 8 Mb sin escalas, solo al agregar GTK...

Hmm... estoy pensando cómo se podría alivianar eso...

Saludos.


Juan

---

### Post by jclevien on 2008-03-18
Copio un mail que envié a la lista PyAR.
Espero que les sirva.

Saludos.





Hola que tal,

Un comentario: si les interesa, pude reducir el tamaño del ejecutable de 8 Mb a 3.5 Mb.
El truco es sacar las DLL del directorio dist, ya que al copiar las bibliotecas lib del directorio donde está instalado GTK las DLL se convierten en redundantes, y no aportan a la ejecución del script.

Igual, 3.5 Mb es un tamaño importante, más si uno arma un paquete de instalación para ser descargado por Internet, lo cual me entristece un poco, pero bueno, nada es perfecto... :(

Saludos, y disculpen.


Juan

---

### Post by Hei Ku on 2008-03-18
> **jclevien said:**
> Hei Ku,

¿Has escrito ya tus propios drivers? (Linus Torvalds)



Los verdaderos hombres no usan drivers, escriben directo a memoria :lolflag:

14 años, C, el pong en una 386, escribiendo directo a memoria de video con un programa residente. :D

Me alegro que hayas encontrado una solucion. Recomendacion, siempre busca reducir al maximo las dependencias, sobre todo las que te agregan los asistentes automaticamente, porque te suelen agregar en exceso.

---

### Post by CostaRica on 2008-06-04
Qué opinan de wxPython y wxGlade?  Pienso que se le ha dado poco uso para lo poderoso que es.

---

### Post by rretamar on 2008-06-04
Podés darle una mirada al Proyecto Lazarus. Está en beta, pero es un RAD basado en Object Pascal, multiplataforma y muy potente. Los ejecutables que genera son en código nativo y por ende muy rápidos, ya que es un lenguaje **compilado**. Usa un modelo de componentes escritos con el mismo lenguaje. Es casi un Delphi pero libre.

[img]http://wiki.lazarus.freepascal.org/images/thumb/c/c3/Lazarus_IDE_GTK2.png/800px-Lazarus_IDE_GTK2.png[/img]

El lenguaje Object Pascal es muy limpio, entendible y a la vez potente. Como dicen en españa "es una gozada".

[http://www.lazarus.freepascal.org](http://www.lazarus.freepascal.org)

Saludos !

---

### Post by anarko on 2008-06-04
Java no es una opcion?
Aunque python no es una mala eleccion.

---

### Post by faktorqm on 2008-06-05
hei ku: ayy él! escribe directo en memoria y despues el kmymoney se cuelga! :lolflag:

Che y para python no hay algo parecido a lo que posteo rretamar?, esta bueno eso. Ahora no estoy programando activamente, de hecho deberia empezar pero quiero empezar a acercarme de a poco a python "gráfico", ya tengo muchos años de consola en C y algo de C++ (por la facu, no profesionalmente) pero python parace que va.

---

### Post by tzulberti on 2008-06-05
Tenes un RAD llamado Boa Constructor.
Nunca lo probe pero se puede instalar desde apt-get.

---

### Post by CostaRica on 2008-06-05
- Alguno de ustedes estaría interesado en hacer un ERP para unas ópticas?  Tengo 10 años trabajando en esto y tengo el modelo de datos completo, pero no he tenido tiempo para leer lo suficiente de python y wxpython como para desarrollarlo yo, pero les aseguro que es un proyecto interesante, y por supuesto pagado.

Tal vez conocen alguna empresa que le interese.  En realidad, aquí en Costa Rica es casi imposible conseguir un programador en estas tecnologías, y aunque siento que estoy siendo un poco necio con el tema del lenguaje (Python), no soportaría la idea (solo en último caso) de tener que desarrollarlo en .Net, Java o PHP.  La elegancia, sencillez y facilidad de lectura de Python me tienen cautivado... :)

---

