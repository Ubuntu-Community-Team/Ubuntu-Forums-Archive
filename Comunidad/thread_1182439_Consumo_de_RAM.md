---
title: "Consumo de RAM"
date: 2009-06-08
forum: Comunidad
---

### Post by juancarlospaco on 2009-06-08
Para mi tambien depende de que aplicaciones estes usando, 
por ejemplo algo hecho en Mono, en realidad por detras oculto estas corriendo un .EXE
es como correr un Wine, por ejemplo una aplicacion en C++ seria mejor con el consumo de recursos.
Algunas cosas en mono inclusive se *"ve"* el .exe en el administrador de tareas, 
como me paso con la Mindtouch Wiki *(Mono)*, la volé e instale MoinMoin *(Python)* y vuela.
Las cosas Java tambien levantan una maquina virtual para ejecutarse.


Un lenguaje con un buen promedio es Python.

---

### Post by pablo.s on 2009-06-08
> **juancarlospaco said:**
> Un lenguaje con un buen promedio es Python.

Por eso nos gusta tanto!

---

### Post by juancarlospaco on 2009-06-08
No creas todo lo que te dicen, sucede que busque ese .exe y lo ejecute con Wine 
y andubo, medio mal pero andubo.
Me dio una sensacion como el Picassa para Linux...

*o estoy confundido...?, no digo que tengo la razon, pregunto...*


Asi como muchas veces no es cierto que un programa Java corre en cualquier lado,
por que el mismo programa lo ejecutas en Linux y no funciona igual que en Windows,
requiere unos retoques, por el Filesystem, por el sistema de permisos y por el entorno en general,
pero he aqui que Python con unos retoques corre en Windows tambien, 
pero sin esa pesadisima maquina virtual de Java, 
entonces no le veo grandes ventajas a Java con respecto a Python,
sin mencionar que es mucho mas amigable el codigo Python que el Java.
Pero los programas Java corren mucho mas rapido en Ubuntu que en Windows.
:D

---

### Post by josecuervo86 on 2009-06-08
Posta, picasa en linux parece que corriera desde un exe, y tengo la misma sensación con Google Earth. Pareciera que los levantas emulados...

---

### Post by pablo.s on 2009-06-08
Edité el post anterior por
una cuestión. Tengo miedo de
meter la pata con el concepto
de Mono. Pero por lo poco que
sé de cuando intenté hace unos
años programar en C#, el código
es semi interpretado, o sea no
como Python que es interpretado
a secas, sino que se compila
antes de la ejecución para que
lo corra en la máquina virtual.
En Windows seria el .NET runtime
y en Linux y demás seria Mono.
Si no tiene la maquina virtual
no corre para nada, por mas que
parezca un .EXE.
Repito que no quiero meter la
pata, por eso lo que opino yo
hay que corregirlo.
En WINE el código lo toma ya
compilado y le recrea toda la
API faltante para que se ejecute.
Son dos cosas diferentes a mi
humilde entender.

Y Picasa corre con WINE, pero
de forma muy astuta te hacen creer
que es nativo, pero no.

---

### Post by juancarlospaco on 2009-06-08
Ahora que recuerdo tambien dentro de cosas creadas con Mono eh encontrado archivos **.DLL**

Ya se podria tener cualquier extension un ejecutable en Linux, 
pero me parece demasiada casualidad.

Por suerte en Ubuntu si ejecutas:
**sudo apt-get purge mono-common**

Sacas todo el Mono al diablo, sin perder nada, 
*bueno solo Tomboy y F-Spot, pero se reemplazan facil.*

Yo ahora estoy usando BlueMarine para reemplazar F-Spot
y es mil veces mas completo.
*Y no me vengan con Gnome-Do, todo el que probo Cairo Dock2 se la quedo.*

---

### Post by santiagoward2000 on 2009-06-08
> **juancarlospaco said:**
> Yo ahora estoy usando BlueMarine para reemplazar F-Spot
y es mil veces mas completo.

¿Y qué tal el consumo? Veo que está hecho en Java, ¿es más liviano que F-Spot?

---

### Post by juancarlospaco on 2009-06-08
> **santiagoward2000 said:**
> ¿Y qué tal el consumo? Veo que está hecho en Java, ¿es más liviano que F-Spot?

Bien, es liviano dentro de todo,
si bien es grande, pero como su autor comenta
*" **es un Clon Libre del Adobe LightRoom** "*
pero hace cosas interesantes, codigo fuente disponible,
tiene 3D, trasparencias, GPS Geotraking, RAW, y toda la weba.
El limite de Fotos solo depende de la RAM instalada en Ubuntu y OS X.

[IMG]http://img395.imageshack.us/img395/9809/pantallazote1.gif[/IMG]

[IMG]http://bluemarine-old.tidalwave.it/infoglueDeliverLive/digitalAssets/918_Thumbnail_Viewer.jpg[/IMG]

Por ahora es mi opcion de huir del Mono...,
pero bueno si alguien quiere hacer la del Mono con el F-Spot todo bien :D

No tengo Tomboy..., 
pero Gnome ya trae un Applet de panel llamado *"Notas adhesivas 2.26.1"*, consume menos.

---

### Post by Hei Ku on 2009-06-09
Interesante el off-topic, pero lo movi aparte.
Y como dato, Picasa y Google Earth corren con Wine. Parece que los desarrolladores de Google no saben programar en Linux. Es muy dificil para esos genios. :P

---

### Post by josecuervo86 on 2009-06-09
> **Hei Ku said:**
> Interesante el off-topic, pero lo movi aparte.
Y como dato, Picasa y Google Earth corren con Wine. Parece que los desarrolladores de Google no saben programar en Linux. Es muy dificil para esos genios. :P

Buen dato... con razon me parecia, aunque parece bastante coincidencia. Capaz que lo lei en algun lado :-k

---

### Post by juancarlospaco on 2009-06-09
*mmmmmm... *Hei Ku tas seguro que Google Earth es en Wine?, 
me parece que es en **QT** pero no en Wine.

---

### Post by pablo.s on 2009-06-09
> **juancarlospaco said:**
> *mmmmmm... *Hei Ku tas seguro que Google Earth es en Wine?, 
me parece que es en **QT** pero no en Wine.

Una cosa no tiene que
ver con la otra.

Eh, papi, que tiene que
ver el consumo de RAM con
la comunidad?

---

### Post by josecuervo86 on 2009-06-09
> **pablo.s said:**
> Eh, papi, que tiene que
ver el consumo de RAM con
la comunidad?

Me parece que en si, el consumo de RAM no tiene nada que ver, pero la conversación tomo un airecito a "charla de cafe" :p

---

### Post by pablo.s on 2009-06-09
Al consumo de RAM lo
podes insultar, va a
software, me parece,
digo.

---

### Post by santiagoward2000 on 2009-06-09
> **juancarlospaco said:**
> Bien, es liviano dentro de todo,
si bien es grande, pero como su autor comenta
*" **es un Clon Libre del Adobe LightRoom** "*
pero hace cosas interesantes, codigo fuente disponible,
tiene 3D, trasparencias, GPS Geotraking, RAW, y toda la weba.
El limite de Fotos solo depende de la RAM instalada en Ubuntu y OS X.

Lo estuve probando, y no parece tan liviano. Lo puse a cargar las fotos, y java me empezó a usar 630MB de memoria y el 70% del CPU. Cuando terminó, lo cerré y volví a abrir, y java me está usando 200MB.
Además, no me toma mis fotos. Las importa, pero después no aparecen en ningún lado, el "thumbnails viewer" aparece vacío. No lo entiendo.

---

### Post by Hei Ku on 2009-06-09
> **pablo.s said:**
> Una cosa no tiene que
ver con la otra.

Eh, papi, que tiene que
ver el consumo de RAM con
la comunidad?

Esta charla no tiene que ver con un pedido de soporte concreto, por eso la pasé a Comunidad.

Y ya te dije, lo de papi está de más.:popcorn:

---

### Post by Hei Ku on 2009-06-09
> **juancarlospaco said:**
> *mmmmmm... *Hei Ku tas seguro que Google Earth es en Wine?, 
me parece que es en **QT** pero no en Wine.

Tenes razon, las ultimas versiones de Google Earth son nativas.

Picasa sigue sobre Wine, pero el Google Earth tiene una version nativa en Qt a partir de la 4 y pico.

---

### Post by juancarlospaco on 2009-06-09
El google earth es nativo.

El BlueMarine esta en estado inestable, por eso se comporta raro a veces, pero bueno es como usar Windows.:)

---

### Post by pol666 on 2009-06-09
Dicen que google earth es nativo pero se ve muy windoish. Igual cual es el problema con un .exe con mono si se trata de algo libre?, tan lento anda?.

Por cierto hablando de gestores de imagenes lo mejor que se invento hasta ahora es Gwenview (Lo unico feo es el nombre :B)

---

### Post by Hei Ku on 2009-06-09
> **pol666 said:**
> Dicen que google earth es nativo pero se ve muy windoish. Igual cual es el problema con un .exe con mono si se trata de algo libre?, tan lento anda?.


El problema con mono es no sólo su performance (o falta de) sino que es una caja de Pandora en cuanto a patentes. Como busca duplicar cosas sobre las que M$ tiene patentes, no esta claro en que momento van a empezar a demandar a diestra y siniestra a usuarios y desarrolladores de Mono. Red Hat y Fedora ya tomaron la decision de sacarlo por default. Y Debian apunta en la misma direccion. Ubuntu es mas amigo de estas cosas propietarias, asi que por ahora defiende el uso de Mono. Por suerte Kubuntu no sufre de este problema, por ahora.

---

### Post by juancarlospaco on 2009-06-09
Python se puede acelerar con Psyco, M$ Mono se arrastra toda la vida.

---

### Post by juancarlospaco on 2009-06-17
*Ven..., *
hoy instale [Nemo]("http://www.iola.dk/nemo/"), un navegador de archivos segun un Calendario,
y miren para que vean que no miento:

juancarlospaco@Jaunty:~$ nemo 

** (**/usr/bin/nemo.exe**:6912): WARNING **: The following assembly referenced from /usr/bin/nemo.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=9)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/bin).


** (/usr/bin/nemo.exe:6912): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
File name: 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f'
juancarlospaco@Jaunty:~$ **file /usr/bin/nemo.exe**
**/usr/bin/nemo.exe:** PE32 **executable for MS Windows** (console) Intel 80386 32-bit 

Eso si estubiera hecho en Python no pasa XD
No me andubo, Jaunty 32bit, todos los updates ;P
***Alguien me explica por que Mono te corre &#8221; .EXEs &#8221; en Linux &#8230;?***

Yo te digo..., 
sigan insistiendo incluyendo cosas en Mono en Linux,
que algun dia va a salir una Vulnerabilidad grossa en esos .EXE 
y vamos a quedar todos patas para arriba, 
algo como un Confiker pero para Mono,
[B]Usen Python que es mas facil y simple que Mono, 
y Python+Psyco es mas rapido que Mono, y no necesita .EXE*s* !!!.[/B]

[I]No hay que dejar el sistema Expuesto de manera innecesaria con Bloatware,
no hay que confiarse, ...fijate lo que le paso a las Mac, 
un monton se envirusaron con el iWork09, y pensar que Mac ERA a prueba de Virus.
Ahora en el Top Ten de descargas de Apple siempre tienen un AntiVirus presente.[/I]

:)

---

### Post by Hei Ku on 2009-06-17
Mono: la lentitud de Windows, ahora multiplataforma. :lolflag:

---

### Post by juancarlospaco on 2009-06-17
> **Hei Ku said:**
> Mono: la lentitud de Windows, ahora multiplataforma. :lolflag:

Seeeeeeeee...


[SIZE="1"]juancarlospaco@Jaunty:~$ **sudo apt-get purge mono-common**
[sudo] password for juancarlospaco: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  libmono0 tracker untex tracker-utils libzip1 tracker-search-tool odt2txt libtracker-gtk0
Utilice «apt-get autoremove» para eliminarlos.
Los siguientes paquetes se ELIMINARÁN:
  libmono-cairo2.0-cil* libmono-corlib2.0-cil* libmono-data-tds2.0-cil* libmono-i18n2.0-cil* libmono-security2.0-cil*
  libmono-sqlite2.0-cil* libmono-system-data2.0-cil* libmono-system2.0-cil* mono-2.0-gac* mono-2.0-runtime* mono-common*
  mono-gac* mono-gmcs* mono-jit* mono-runtime* nemo*
0 actualizados, 0 se instalarán, 16 para eliminar y 8 no actualizados.
Se liberarán 15,5MB después de esta operación.
¿Desea continuar [S/n]? S
(Leyendo la base de datos ...  
269139 ficheros y directorios instalados actualmente.)
Desinstalando nemo ...
Desinstalando libmono-cairo2.0-cil ...
Desinstalando mono-gmcs ...
Desinstalando libmono-sqlite2.0-cil ...
Desinstalando libmono-system-data2.0-cil ...
Desinstalando libmono-data-tds2.0-cil ...
Desinstalando libmono-i18n2.0-cil ...
Desinstalando mono-runtime ...
Desinstalando mono-gac ...
* Removing packages from mono
Desinstalando libmono-system2.0-cil ...
Desinstalando mono-2.0-runtime ...
Desinstalando mono-2.0-gac ...
Desinstalando libmono-security2.0-cil ...
Desinstalando libmono-corlib2.0-cil ...
Desinstalando mono-jit ...
Desinstalando mono-common ...
update-binfmts: warning: no executable /usr/bin/cli found, but continuing
anyway as you request 
Purgando ficheros de configuración de mono-common ...
Procesando disparadores para man-db ...
juancarlospaco@Jaunty:~$ **ls /usr/bin/*.exe**
ls: no se puede acceder a **/usr/bin/*.exe: No existe el fichero** ó directorio
juancarlospaco@Jaunty:~$ [/SIZE]



Ahora si estoy en Paz y Harmonia \\:D/

---

### Post by pablo.s on 2009-06-17
> There’s no particular mountain that you could point to that
an open source group couldn’t climb, but they couldn’t be on top of all of
the mountains at the same time. And so it struck me that a lot of the
tension within open source groups happens when you get to a point
when you have different groups within them which both have very valid
arguments as to why they should go their way. They’re both right – but the
organisation itself just can’t scale to that. The beauty of this being open
source is that we can dispatch different teams to climb different
mountains. We can win both battles.

Cita de Mark Shuttleworth.

---

### Post by WanderingKnight on 2009-06-18
A mí me da bastante igual Mono. Como dije en la lista de mails, que cada cual haga lo  que quiera mientras el código sea libre (y Mono lo es). Sino, es darle una validez inmerecida a las patentes de software.

.NET es como Java... compila todo a bytecode que después interpreta una máquina virtual. Esto brinda mucha seguridad (es muuuuuuy difícil, casi imposible, romper la jaula de la VM) y soporte de cualquier aplicación bajo cualquier plataforma para la cual esté compilada la VM, a costa de cargar en memoria la máquina virtual entera siempre que se corra el programa. Eso no significa que Java o .NET sean lentos (aunque en muchos aspectos son mucho más lentos que C/C++), sino que simplemente ocupa mucho espacio en memoria--lo cual puede repercutir a nivel de performance, pero tampoco los hace automáticamente lentos. El otro punto a favor es que son más sencillos que C/C++ mientras que mantienen la base de tipos estáticos (cosa que prefiero y que me molesta mucho no tener en lenguajes como Python y Perl) y las bibliotecas estándar superan por creces a lo que puede proveer C++ estándar más Boost y la STL (obviamente eso es sin contar Qt, que para mi le gana en todos los aspectos a cualquier otra cosa que puedan sacar Java y .NET :D).

En mi opinión, Java/.NET tienen más lugar en procesamiento a nivel de backend en servidores, y no tanto sobre el escritorio. Los toolkits para Java son absolutamente horrendos y GTK (Mono) no me provoca mucho entusiasmo. Ni siquiera en Windows hay muchas aplicaciones de escritorio hechas sobre .NET (la mayoría son de Microsoft).

Sobre Python y afines me reservo opinión dado que la verdad no resultan de mi agrado para aplicaciones grandes, pero es más por cuestiones subjetivas que por algo en concreto.

De todas formas, quizás el futuro sean los lenguajes funcionales (Haskell, Erlang, Lisp) o mezclas entre imperativos y funcionales...

---

### Post by guillermolisi on 2009-06-18
> De todas formas, quizás el futuro sean los lenguajes funcionales (Haskell, Erlang, **Lisp**) o mezclas entre imperativos y funcionales...
Creo que perdurara Algol si esto sigue asi :D

---

### Post by WanderingKnight on 2009-06-21
Jeje, sí, Lisp es viejito pero es un muy buen ejemplo de un lenguaje puramente funcional. Dudo que retome Lisp en particular, pero el resto de los lenguajes funcionales más modernos es muy probable que sí.

---

