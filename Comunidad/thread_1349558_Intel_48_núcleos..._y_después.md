---
title: "Intel 48 núcleos... y después ?"
date: 2009-12-08
forum: Comunidad
---

### Post by Cajuma on 2009-12-08
Como sigue esta historia ?

[http://www.cioal.com/analisis/negocios/innovacion-intel-cruza-la-frontera009.html]("http://www.cioal.com/analisis/negocios/innovacion-intel-cruza-la-frontera009.html")

Alguien sabe si en Linux se está investigando al respecto ?
No nos dejen afuera !!!!!
Saludos. ;)

---

### Post by z37a on 2009-12-08
> **Cajuma said:**
> Como sigue esta historia ?

[http://www.cioal.com/analisis/negocios/innovacion-intel-cruza-la-frontera009.html]("http://www.cioal.com/analisis/negocios/innovacion-intel-cruza-la-frontera009.html")

Alguien sabe si en Linux se está investigando al respecto ?
No nos dejen afuera !!!!!
Saludos. ;)

Si no me equivoco el kernel de Linux ya esta preparado para esa cantidad de cores(y mas, creo que eran 64 o 256, no recuerdo) hace rato!!! El tema es la competencia, la ventanita loca aun no puede con mas de 1 core, prometieron para que hasta la vista soporte multicore y no lo hizo, y luego con seven lo mismo y tampoco. Mac siendo BSD supongo que al igual qe linux ya lo soporta.

---

### Post by Cajuma on 2009-12-08
> **z37a said:**
> Si no me equivoco el kernel de Linux ya esta preparado para esa cantidad de cores(y mas, creo que eran 64 o 256, no recuerdo) hace rato!!! El tema es la competencia, la ventanita loca aun no puede con mas de 1 core, prometieron para que hasta la vista soporte multicore y no lo hizo, y luego con seven lo mismo y tampoco. Mac siendo BSD supongo que al igual qe linux ya lo soporta.

Gracias por la información, de todas maneras yo solo tengo dos y seguramente, por un largo rato, jaja!!
saludos.;)

---

### Post by alfplayer on 2009-12-08
> **z37a said:**
> Si no me equivoco el kernel de Linux ya esta preparado para esa cantidad de cores(y mas, creo que eran 64 o 256, no recuerdo) hace rato!!! El tema es la competencia, la ventanita loca aun no puede con mas de 1 core, prometieron para que hasta la vista soporte multicore y no lo hizo, y luego con seven lo mismo y tampoco. Mac siendo BSD supongo que al igual qe linux ya lo soporta.

Windows soporta múltiples núcleos. XP, Vista, W7 y las versiones para servidores.

---

### Post by z37a on 2009-12-09
> **alfplayer said:**
> Windows soporta múltiples núcleos. XP, Vista, W7 y las versiones para servidores.

Si de SP2 de XP, pero si bien los ve, no los usa, no tiene la capacidad de distribuir el procesamiento, por lo cual si la aplicación que utilizas no soporta multicore no se aprovecha en nada a estos procesadores. Aparte tene en cuenta la licencia, xp creo que soporta hasta 4 cores!!!! En cambio en linux existe el kernel smp, donde el mismo se encarga de distribuir la carga entre los cores, ya de pro si en el arranque hay un parámetro que agregas y la PC vas a notar que arranca muchísimo mas rápido. Vos a un Windows le pones un solo core a 2Ghz con 1MB de cache y anda igual que un dual core con la misma cache por core(durante el arranque, algunas aplicaciones van a andar mas rápido, otras no).

---

### Post by juancarlospaco on 2009-12-09
Los supercomputadores tienen mucho mas de 48 nucleos y usan linux.

---

### Post by rubioo on 2009-12-09
> **Cajuma said:**
> Gracias por la información, de todas maneras yo solo tengo dos y seguramente, por un largo rato, jaja!!
saludos.;)

Jajaja somos dos. :p

---

### Post by z37a on 2009-12-09
> **rubioo said:**
> Jajaja somos dos. :p

Yo tengo un solo core!!!! ni siquiera dos!!! Quiero ver de cambiarlo por un quad, pero mas adelante, y si el impuestazo no afecta a los micros!!!!!

---

### Post by biale on 2009-12-09
Muy pronto vamos a tener 6 y 8 cores. Si con la tecnología actual no pueden aumentar la velocidad del reloj, van a ir añadiendo nucleos.

Yo tambien sigo con un solo core, y ya somos...

---

### Post by aledruetta on 2009-12-10
> **biale said:**
> Muy pronto vamos a tener 6 y 8 cores. Si con la tecnología actual no pueden aumentar la velocidad del reloj, van a ir añadiendo nucleos.

Yo tambien sigo con un solo core, y ya somos...

OT: Me sumo al "Club de los Corazones Solitarios".

---

### Post by juancarlospaco on 2009-12-10
Igual no lo veo muy innovador..., 
usar multiples procesadores se hace desde los ultimos Pentium 2 hasta los primeros pentium 3,
solo que ahora vienen en la misma "pastilla".

Estaba bueno la idea difunta de Intel de hacer un hibrido de CPU/GPU y ver que salia,
pero el proyecto murio...

:)

---

### Post by alfplayer on 2009-12-12
> **z37a said:**
> Si de SP2 de XP, pero si bien los ve, no los usa, no tiene la capacidad de distribuir el procesamiento, por lo cual si la aplicación que utilizas no soporta multicore no se aprovecha en nada a estos procesadores. Aparte tene en cuenta la licencia, xp creo que soporta hasta 4 cores!!!! En cambio en linux existe el kernel smp, donde el mismo se encarga de distribuir la carga entre los cores, ya de pro si en el arranque hay un parámetro que agregas y la PC vas a notar que arranca muchísimo mas rápido. Vos a un Windows le pones un solo core a 2Ghz con 1MB de cache y anda igual que un dual core con la misma cache por core(durante el arranque, algunas aplicaciones van a andar mas rápido, otras no).

Actualmente linux y windows (por ejemplo XP, Vista y 7) comparten lo siguiente:

Las distribuciones usan en forma predeterminada kernels con SMP activado. No es necesario instalar un kernel especial con SMP. Windows también tiene SMP activado en una instalación normal no modificada.

Linux y Windows distribuyen el conjunto de procesos en los núcleos y las aplicaciones que lo permitan.

Por estas dos razones, en principio, no hay una diferencia de velocidad entre linux y windows (con un quad core, si windows solo usara un sólo núcleo todos se pasarían a linux para tener un sistema hasta cuatro veces más rápido!).

---

### Post by z37a on 2009-12-12
> **alfplayer said:**
> Actualmente linux y windows (por ejemplo XP, Vista y 7) comparten lo siguiente:

Las distribuciones usan en forma predeterminada kernels con SMP activado. No es necesario instalar un kernel especial con SMP. Windows también tiene SMP activado en una instalación normal no modificada.

Linux y Windows distribuyen el conjunto de procesos en los núcleos y las aplicaciones que lo permitan.

Por estas dos razones, en principio, no hay una diferencia de velocidad entre linux y windows (con un quad core, si windows solo usara un sólo núcleo todos se pasarían a linux para tener un sistema hasta cuatro veces más rápido!).

Tenias razón, Windows Vista y 7 soportan multicore, no así XP, XP no lo soporta(Solo a partir de SP2 pero no es funcional del todo), pero vista y 7 como te dije si, solo que hay que activarlo, no viene definido por defecto. El tema tambien viene por el lado de que las licencias OEM y demas que se venden tienen un tope de procesadores, asi que si queres utilizar este mismo micro de 48 cores, te va a salir un poco caro ponerle Windows, Linux te va a salir lo mismo(desde 0$) y no cuenta con esta limitacion.

---

### Post by alfplayer on 2009-12-12
> **z37a said:**
> Tenias razón, Windows Vista y 7 soportan multicore, no así XP, XP no lo soporta(Solo a partir de SP2 pero no es funcional del todo), pero vista y 7 como te dije si, solo que hay que activarlo, no viene definido por defecto. El tema tambien viene por el lado de que las licencias OEM y demas que se venden tienen un tope de procesadores, asi que si queres utilizar este mismo micro de 48 cores, te va a salir un poco caro ponerle Windows, Linux te va a salir lo mismo(desde 0$) y no cuenta con esta limitacion.

En XP actualizado no es funcional del todo?

---

### Post by Cajuma on 2009-12-12
Muchachos... al comenzar el thread, no era mi intención, hablar de
ventanitas, me parece mucho mas interesante si vemos su aplicación 
general en Linux, y en particular en Ubuntu. ¿ No les parece mejor ?
Gracias. ;)

---

### Post by z37a on 2009-12-12
> **Cajuma said:**
> Muchachos... al comenzar el thread, no era mi intención, hablar de
ventanitas, me parece mucho mas interesante si vemos su aplicación 
general en Linux, y en particular en Ubuntu. ¿ No les parece mejor ?
Gracias. ;)


Es verdad!!!! Perdonen, solo que queria hablar un poco de forma generica sin importar el SO.

---

### Post by Cajuma on 2009-12-12
Pero que séa la última vez, la próxima tendras que usar durante un més
ventanas 95........ JAJAJA.:D

---

### Post by Mauro22 on 2009-12-12
Sin un buen SO y sin software de calidad que aprovechen el multithreading, es lo mismo tener 1 que 100

---

### Post by alfplayer on 2009-12-12
> **Mauro22 said:**
> Sin un buen SO y sin software de calidad que aprovechen el multithreading, es lo mismo tener 1 que 100

Sí, falta mejorar el software. Si una aplicación solo usa un núcleo y tiene mucha carga los otros núcleos quedan con poca carga si no se están ejecutando otras aplicaciones exigentes.

---

### Post by emiliano_raso on 2009-12-12
Para que quieren tantos nucleos?
Yo tengo un Intel Core Duo de 2.0Ghz y como MAXIMO llego a usar %30 de CPU.

Es al pe...do tantos recursos. A menos que seas enfermo de los jueguitos.
Pero para eso están las consolas...

---

### Post by alfplayer on 2009-12-12
> **emiliano_raso said:**
> Para que quieren tantos nucleos?
Yo tengo un Intel Core Duo de 2.0Ghz y como MAXIMO llego a usar %30 de CPU.

Es al pe...do tantos recursos. A menos que seas enfermo de los jueguitos.
Pero para eso están las consolas...

Es importante también el tiempo que tardan en iniciar las aplicaciones.

---

### Post by Mauro22 on 2009-12-12
La cosa no es para qué sino porqué.


El problema del cpu es el calor que genera, a más frecuencia, más calor...

Qué hacemos si no podes aumentar la frecuencia? Fácil, ponemos más nucleos a baja frecuencia.


Entonces, en vez de 1 nucleo a 3.3 Ghz tenes 8 a 1 Ghz... tenes muchisimo menos calor (desperdicio de energia) y mas del doble de capacidad de procesamiento.

Ahora esto tiene que llevarse bien con el software. 

Otra función de los multinucleos es que no todos hacen lo mismo. Hay nucleos especializados en operaciones aritmeticas, en operaciones logicas, en operaciones de coma flotante. Algunos son rapido en todos, otros simplemente son buenos decodificadores, etc etc..

Al haber varios nucleos, cada uno siendo el mejor en X tarea, creanme, que con un buen soft y un buen SO, las ganancias son tremendas ;)

---

### Post by z37a on 2009-12-12
> **Mauro22 said:**
> Otra función de los multinucleos es que no todos hacen lo mismo. Hay nucleos especializados en operaciones aritmeticas, en operaciones logicas, en operaciones de coma flotante. Algunos son rapido en todos, otros simplemente son buenos decodificadores, etc etc..


Decilo de una, el Cell de IBM!! o me equivoco? tiene 7 cores el que utiliza la PS3, pero cada core realiza una tarea distinta.

---

### Post by Mauro22 on 2009-12-12
> **z37a said:**
> Decilo de una, el Cell de IBM!! o me equivoco? tiene 7 cores el que utiliza la PS3, pero cada core realiza una tarea distinta.

Es que 7 nucleos que sean buenos en lo mismo es al ****. Divide y venceras.

---

### Post by juancarlospaco on 2009-12-12
> **emiliano_raso said:**
> Para que quieren tantos nucleos?
Yo tengo un Intel Core Duo de 2.0Ghz y como MAXIMO llego a usar %30 de CPU.

Es al pe...do tantos recursos. A menos que seas enfermo de los jueguitos.


**V I R T U A L I Z A C I O N**
Red Hat con el Kernel de Lucid mete +600 maquinas virtuales en 1 PC fisica *[SIZE="1"](KSM+KVM)[/SIZE]*
El DataCenter del futuro va a ser 1 Servidor.

---

### Post by z37a on 2009-12-12
> **juancarlospaco said:**
> **V I R T U A L I Z A C I O N**
Red Hat con el Kernel de Lucid mete +600 maquinas virtuales en 1 PC fisica *[SIZE="1"](KSM+KVM)[/SIZE]*
El DataCenter del futuro va a ser 1 Servidor.

Virtualizando con un x3 y 8GB de ram lo que me queda corto son los 8GB de ram, esto con xen!!!!! Y mas corto aun si clusterizo las maquinas virtuales(2 equipos con 8GB solo podes correr maquinas virtuales hasta 8GB de ram en ambos juntos).

---

### Post by juancarlospaco on 2009-12-13
Por eso el **KSM**, googlea info acerca del KSM, 
es un metodo de mejorar la gestion de RAM,
cuanto mas similares sean las VM menos ram utilizan...

Habian hecho una prueba mas chica, 
de +52 VM con WinXP de 1Gb c/u en Servo con 16Gb de ram.
:)

---

### Post by Cajuma on 2009-12-13
> **juancarlospaco said:**
> Por eso el **KSM**, googlea info acerca del KSM, 
es un metodo de mejorar la gestion de RAM,
cuanto mas similares sean las VM menos ram utilizan...

Habian hecho una prueba mas chica, 
de +52 VM con WinXP de 1Gb c/u en Servo con 16Gb de ram.
:)

Otro ejemplo:
[http://www.linux-kvm.com/content/using-ksm-kernel-samepage-merging-kvm]("http://www.linux-kvm.com/content/using-ksm-kernel-samepage-merging-kvm")

Obviamente nos referimos a el uso de estos procesadores a nivel
servers, para el uso domestico faltan siglos...
Ademas en el 2012 entran en escena los procesadores Japoneses de la mano de Toshiba, Hitachi, Fujistsu, NEC, Panasonic, Renesas Technology y Canon con el apoyo del Ministerio de Economía nipón
hay que ver con que se despachan.
Saludos.:(

---

