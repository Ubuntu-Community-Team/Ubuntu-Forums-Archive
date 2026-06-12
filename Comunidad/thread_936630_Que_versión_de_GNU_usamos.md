---
title: "Que versión de GNU usamos??"
date: 2008-10-03
forum: Comunidad
---

### Post by guisheca on 2008-10-03
Resulta que a estas horas de la noche entro en estado surreal y empiezo a filosofar sobre ciertas cuestiones. Y vino a mi mente lo siguiente:
Ya voy por el año y pico de linuxero y varias cosas ya las se, como por ejemplo que linux es sólo el núcleo del SO, y que el software que corre sobre el núcleo se llama GNU, por lo tanto nuestro SO se llama GNU/Linux.
También se que no hay miles de versiones de GNU/Linux si no distribuciones, esto es, el mismo SO, pero con otra "distribución" de software (mas o menos es así la cosa).
Ahora bien, la versión del kernel está a la vista, con el comando ```
uname -r
``` puedo saber que corro la versión 2.6.24-19-generic de linux. Pero cual es la versión de GNU que uso?? es correcto esto que estoy pensando?? o me estoy mandando cualquiera?? que parte de mi ubuntu es el GNU??
En fin, me di cuenta que el GNU me resulta un concepto algo abstracto y ambiguo, espero que alguien me pueda explicar mas o menos como viene la mano porque me da un poco de vergüenza no saber estas cuestiones a estas alturas del partido.
Saludos y que descansen.

---

### Post by faktorqm on 2008-10-03
Y mas o menos, te cuento como es la cuestion. igual creo que va a estar en la nueva pagina, pero paso a contar (si alguien detecta un error, por favor no dude en correjirme)

Los sistemas GNU/Linux, estan conformados por, el kernel (creado por Linus Torvalds) y el conjunto de aplicaciones GNU (Gnu Is not Unix, Gnu no es unix). Esto que significa? el kernel por si solo es una capa entre el hardware y el software, es decir, el kernel es el que maneja los dispositivos, o sea los drivers, la memoria, la placa de video, esto lo hace mediante el codigo embebido en el, o mediante modulos (como el driver de nvidia por ejemplo). Hay determinadas cosas que no pueden ser modulos (como el controlador de HAL, o de memoria) y hay modulos que no pueden ser embebidos (como los drivers no libres).

GNU abarca las aplicaciones que se conocen como el paquete core-utils en ubuntu/debian, y estas no son ni mas ni menos que todos los comandos de unix reprogramados en su version libre. ejemplo, comandos ls, cp, mkdir, rm, etc. PERO estos programas se manejan sobre los drivers que aporta el kernel, es decir, no podes hacer un ls de una particion que no montaste o de un disco que no controlas. me explico?

Entonces que tenemos, las aplicaciones "base" y el kernel. Hasta aca si instalaras unicamente esto, tenes funcionando el kernel y una consola con los comandos basicos. A medida que vas instalando paquetes, vas adquiriendo más funcionalidades.

Cuando quieras saber la version de algo, preguntale a aptitude ;)

```
faktorqm@the-edge:~$ aptitude show coreutils
Paquete: coreutils
Esencial: sí
Estado: instalado
Instalado automáticamente: sí
Versión: 6.10-3ubuntu2
Prioridad: requiere
Sección: base
Desarrollador: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Tamaño sin comprimir: 10,9M
Predepende de: libacl1 (>= 2.2.11-1), libc6 (>= 2.7-1), libselinux1
Tiene conflictos con: stat
Remplaza: debianutils (<= 2.3.1), dpkg (< 1.13.2), fileutils, shellutils, stat, textutils
Proporciona: fileutils, shellutils, textutils
Descripción: Utilidades principales de GNU
 Este paquete contiene las utilidades básicas y esenciales del sistema. 
 
 Específicamente, este paquete incluye:  basename cat chgrp chmod chown chroot cksum comm cp csplit cut date dd df dir dircolors dirname du echo env expand expr factor
 false fmt fold groups head hostid id install join link ln logname ls md5sum mkdir mkfifo mknod mv nice nl nohup od paste pathchk pinky pr printenv printf ptx pwd
 readlink rm rmdir sha1sum seq shred sleep sort split stat stty sum sync tac tail tee test touch tr true tsort tty uname unexpand uniq unlink users vdir wc who whoami
 yes

faktorqm@the-edge:~$ 

```

es mas, ahi te muestra los comandos que son. Bueno, espero que te haya servido. No dudes en preguntar si tenes mas preguntas XD salu2!

---

### Post by Hei Ku on 2008-10-03
Por ejemplo, el gcc tambien es parte de ese GNU, y es el compilador por defecto para Linux. El gdb es el debugger.
Gimp esta mas arriba en la cadena alimentaria, pero tambien es GNU.

Una tarea importante de GNU es mirar donde estan los baches de SL, y cubrirlos con aplicaciones, aunque sean basicas.

---

### Post by guisheca on 2008-10-03
Haaaaaaaa va queriendo va queriendo. Entonces GNU no tiene una versión porque en realidad GNU se denomina a un conjunto de programas, cada uno con su propia versión. Es así verdad??
Se me va aclarando el panorama.

---

### Post by ramiro_md on 2008-10-03
Muy bien explicado. Aclara bastante las cosas.

---

### Post by faktorqm on 2008-10-03
Que bueno que me entendieron. Marchen las medallas!! :P :P :KS (jijijij)

---

### Post by User21 on 2008-10-05
> **faktorqm said:**
> Que bueno que me entendieron. Marchen las medallas!! :P :P :KS (jijijij)
"  Señooor, Si, señoor! " :o

---

### Post by victor_nesta on 2008-10-05
Exxxpectacular...Espectacular!!
Este foro tiene que tener un apartado. ¨Soy ubuntero, estoy al ped., me pelee con mi germu y escribo algo interesante¨
Así justamente ustedes que la tienen mas clara, cuando están al dope, tiran una explicación o para que sirve tal o cual comando.
O recopilar lo que esta flotando en el foro.

---

### Post by pol666 on 2008-10-05
> 
este foro tiene que tener un apartado. ¨soy ubuntero, estoy al ped., me pelee con mi germu y escribo algo interesante¨

jajajajjjaajajajajjajjaa

---

### Post by ramiro_md on 2008-10-06
> **victor_nesta said:**
> ¨Soy ubuntero, estoy al ped., me pelee con mi germu y escribo algo interesante¨

victor_nesta +10 (h5)

---

### Post by majatu on 2008-10-13
En la peli Revolution OS explican bien eso, mirala, esta buena!

---

