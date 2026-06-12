---
title: "ReactOS, que es este bicho extraño?"
date: 2009-03-21
forum: Comunidad
---

### Post by NickCis on 2009-03-21
Wenas. Hace un rato encontre este sistema operativo: ReactOs: [http://www.reactos.org/en/index.html](http://www.reactos.org/en/index.html)

Me puse a ver que es y supuestamente es una mezcla de dios sabe que con windows, que es libre y no se que mas. (va en realidad no entendi muy bien que era xD).

Que opinan de el?.

Saludos.

---

### Post by Hei Ku on 2009-03-21
Es un OS que emula Windows, pero libre. Supuestamente, te permite correr programas como si fuera un Windows, aunque no sé en qué punto de desarrollo y qué windows emula.

---

### Post by Dan_Dranath999 on 2009-03-21
En teoría es un SO libre compatible con Windows

---

### Post by clasificado on 2009-03-21
Según ellos, el objetivo es Windows Xp/2003.

En sus sistema operativo completamente escrito desde cero. Como si se hubieran puesto a reescribir Windows desde la nada.

El kernel es nuevo, pero compatible con la funcionalidad del windows (Drivers y demás, en teoría) por lo que te podrías instalar Office y no tendrías problemas.

Es un sistema de hace como 10 años en desarrollo, tengo entendido que sigue muy inestable (para los usuarios comunes, claro está. Ellos parecen muy contentos)

Por último, sé que tienen una relación bastante estrecha con Wine, y comparten el desarrollo de las dlls.

clasificado

---

### Post by andy_91 on 2009-03-21
buen proyecto

---

### Post by pablo.s on 2009-03-21
Bah.

---

### Post by NickCis on 2009-03-21
> ReactOS® is a free, modern operating system based on the design of Windows® XP/2003. Written completely from scratch, it aims to follow the Windows® architecture designed by Microsoft from the hardware level right through to the application level. **This is not a Linux based system, and shares none of the unix architecture**. 

Pero sigo sin entender que es, osea, no es linux, pero emula windows usando wine o algun fork?

Que, los flacos escribieron un SO desde 0?!.

Leyendo el que es ([http://www.reactos.org/es/about_whatisreactos.html](http://www.reactos.org/es/about_whatisreactos.html)), lo que entendi es que ReactOS es un So escrito desde wine o algo asi, que se ayudaron mutuamente con el projecto wine.
Tambien dice algo de Posix Compatibility (dios sabra qe es xD) 

Despues lei el about ([http://www.reactos.org/es/about.html](http://www.reactos.org/es/about.html))
> ReactOS combina la potencia y fortaleza del núcleo NT - **conocido por su extensibilidad, portabilidad, fiabilidad, robustez, rendimiento y compatibilidad** &#8211; con la compatibilidad con Win32. 

Osea, este en este SO, hacen algo similar al nucleo NT (con todas esas supuestas ventajas).

Nose, pero yo lo veo como algo bueno, si se llega a cumplir el objetivo de los programadores seria un windows libre. Una linda alternativa para los que no qieren tener problemas de cambiar SO para tener mas libertad. Aunque, tira abajo toda la posibilidad de aprender mas (lo peor es que esto de el usuario final no tenga la nececidad de aprender es un objetivo de los desarrolladores...)

Saludos.

---

### Post by pablo.s on 2009-03-21
> **NickCis said:**
>  Que, los flacos escribieron un SO desde 0?!.

Si. Y hay muchos que lo hicieron. La rueda se inventa todos los dias.

> **NickCis said:**
> Tambien dice algo de Posix Compatibility (dios sabra qe es xD) 

Un poco de información por [aqui.]("http://es.wikipedia.org/wiki/POSIX")


> **NickCis said:**
> Osea, este en este SO, hacen algo similar al nucleo NT (con todas esas supuestas ventajas).

Nose, pero yo lo veo como algo bueno, si se llega a cumplir el objetivo de los programadores seria un windows libre. Una linda alternativa para los que no qieren tener problemas de cambiar SO para tener mas libertad. Aunque, tira abajo toda la posibilidad de aprender mas (lo peor es que esto de el usuario final no tenga la nececidad de aprender es un objetivo de los desarrolladores...)

No es tan rosa como parece. Pensá en lo siguiente: para tener un 100% de compatibilidad con Windows precisás de las [API]("http://es.wikipedia.org/wiki/Application_Programming_Interface") de Microsoft. Bueno, ellos NUNCA las van a hacer públicas, Nunca, nunca jamás. Solamente las revelan a quienes estudien para trabajar para ellos y te hacen firmar un [NDA]("http://es.wikipedia.org/wiki/NDA") en lo que te compromete como programador. Nunca más podés programar nada que no sea para ellos o para la plataforma Windows. A Nat Friedman le pasó eso cuando trabajaba para Microsoft en Internet Explorer. Luego pudo zafar porque el código que desarrollaba fué reemplazado (fué en los 90). Miguel de Icaza estuvo a punto de entrar ahi pero no le cabió eso de firmar NDA y empezó a armar el proyecto GNOME.

No creo en un Windows libre. Creo en el software libre. Saludos.

---

### Post by atari130xe on 2009-03-22
Yo bajé la iso hace 2 años y la proble (junto con casi 280 distros y otras yerbas jejeje) en mi pc al menos la mitad de las cosas no funcaron (ni en la pc viejita un Athlon 600Mhz con 512 de ram ni en mi nueva pc una AMD 64 con 2GB de ram, no identifica el hardware (sonido, discos, etc.) esta en una especie de alfa infinita jeje pero en la pc vieja logré que al menos arranque eso si, sin sonido y a una resoluciion windows 3.0 :lolflag: como experimento ta bueno pero no le encuentro la gracia hasta el momento.

---

### Post by infernus92 on 2009-03-22
es un intento de hacer lo que el 99% del mundo hace pero de forma legal... usar window$ sin pagar licencia. pero si dicen que todavia es inestable... no se...
yo sigo con ubuntu... jeje

---

### Post by euzkoarima on 2009-03-23
Yo la instalé sobre virtualbox (que corria en ubuntu 7.10) hace poco más de un año atrás, y hasta donde pude probar era muchísimo más estable linux+wine que ReactOS, así que lo borré.

Saludos,
Eduardo

---

### Post by guisheca on 2009-03-23
Les explico de que se trata:

Es muy simple la cosa, en los años 80 cuando [Stallman]("http://es.wikipedia.org/wiki/Richard_Stallman"), ya cansado de ver como lo que antes era libre de repente se empezó a hacer privativo, decidió crear un sistema operativo propio desde 0, 100% libre, como se hacían las cosas antes (para el que no sabe, el software nació libre, antes se distribuían directamente los códigos fuentes de los programas para que cada quien los compile, lo que vino después es historia conocida jeje). Como el quería que sus sistema corra sobre cualquier computadora decidió que su sistema sea "COMPATIBLE" con [UNIX]("http://es.wikipedia.org/wiki/Unix") (digamoslo así, antes cada computadora corría su propio sistema, y ese sistema no corría sobre otras, salvo UNIX que era "portable", es decir, corría sobre muchas computadoras, algo que ahora es moneda corriente pero en aquel entonces no). 

[B]UNIX es un sistema privativo, Stallman hizo sus sistema GNU completamente compatible con UNIX pero 100% libre.
Estos pibes hacen lo mismo, pero en ves de ser compatible con UNIX lo hacen compatible con windows.[/B] 

Para que sirve?? bien bien no se, pero malo no creo que sea el proyecto. En fin, es una de las tantas ventajas que existe con el software libre, las limitaciones son la de la propia mente...

---

### Post by juancarlospaco on 2009-04-06
Es un rejunte del codigo de :

Wine + FreeDOS + Programas libres para DOS/FreeDOS + desarrollos propios MUY basicos

---

