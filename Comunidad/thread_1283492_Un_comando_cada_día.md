---
title: "Un comando cada día"
date: 2009-10-05
forum: Comunidad
---

### Post by pablo.s on 2009-10-05
Uno de los temas que más atemoriza
a los novatos/novatas de GNU/Linux
es la utilización de comandos en la
terminal (o consola) para efectuar
tareas básicas.
Hoy comienzo con un thread que
complementa en cierta manera al
excelente tutorial que está en portada
sobre la instalación de Ubuntu.
El propósito es postear un comando
por día (regla que se puede doblar, pero
la idea tampoco es postear cien comandos
cada día) como para que el temor a la
terminal se vaya quitando de a poco.

> Las reglas son simples:
-No postear comentarios que no lleven a
ninguna parte. Agradecimientos valen.
Los "no me gusta" o "el comando x es mejor"
no agregan nada y solo producen disgusto.
-No postear comandos que impliquen
que los admins nos baneen a todos. Ya saben
a que me refiero.
-Cada comando va explicado de manera que
mi sobrino de tres años lo pueda entender.[B][SIZE=4]---   df   ---
Disk Free
[/SIZE][/B]
El comando df muestra la cantidad de espacio
disponible en cada partición montada.
Por ejemplo:

```
pablo@raanana:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb2              7164704   3897524   3267180  55% /
udev                    508288       308    507980   1% /dev
none                    508288       556    507732   1% /dev/shm
none                    508288        92    508196   1% /var/run
none                    508288         0    508288   0% /var/lock
none                    508288         0    508288   0% /lib/init/rw
/dev/sda7             67848356  37109904  30738452  55% /media/jaunty
/dev/sdb3             70982616  46391348  20985480  69% /home
/dev/sda1             54540640  12917380  41623260  24% /media/pri
/dev/sda2             52431360  29634368  22796992  57% /media/mon
/dev/sda3             52423328  35826880  16596448  69% /media/video
/dev/sr0                691160    691160         0 100% /media/cdrom0
```**El parámetro -h** nos muestra la cantidad
de espacio pero en MB o GB.

```
pablo@raanana:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             6.9G  3.8G  3.2G  55% /
udev                  497M  308K  497M   1% /dev
none                  497M  556K  496M   1% /dev/shm
none                  497M   92K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sda7              65G   36G   30G  55% /media/jaunty
/dev/sdb3              68G   45G   20G  69% /home
/dev/sda1              53G   13G   40G  24% /media/pri
/dev/sda2              51G   29G   22G  57% /media/mon
/dev/sda3              50G   35G   16G  69% /media/video
/dev/sr0              675M  675M     0 100% /media/cdrom0
```

---

### Post by Sleeping Beauty on 2009-10-05
Como los agradecimientos valen, Muchas gracias! A los nuevos nos viene muy bien.
Si se me permite agrego algo sobre el filesystem de linux que a mi me ayudó a entender "algo" más todo esto...
Espero que a los nuevos les sirva, al menos para saber dónde buscar las cosas...

---

### Post by pablo.s on 2009-10-05
> **Sleeping Beauty said:**
> Espero que a los nuevos les sirva, al menos para saber dónde buscar las cosas...

Muy buen aporte! Debería haber
comenzado por la estructura de 
directorios, pero me mandé directo
a la acción.

---

### Post by Sleeping Beauty on 2009-10-05
:) Lo edité como pdf para descargar, yo lo tengo siempre a mano...

---

### Post by staar on 2009-10-05
buena idea! agrego un par bien (bien) básicos, pero que se usan un montón...

[SIZE="4"]**cd**[/SIZE]

*cd* (de *change directory*) sirve para cambiar el directorio donde nos encontramos. al abrir la consola, por defecto, uno se encuentra en el home de nuestro usuario (/home/*nombredeusuario*/, abreviado como ~), y si, por ejemplo, quiero moverme a mi carpeta Descargas dentro de mi home, hago ```

staarbreaker@multivac:~$ cd /home/staarbreaker/Descargas
staarbreaker@multivac:~/Descargas$ 
``` (en la consola, y en todo linux, siempre se deben respetar las mayusculas). o si quisiera irme a /usr/bin, hago ```

staarbreaker@multivac:~$ cd /usr/bin
staarbreaker@multivac:/usr/bin$ 
``` existen algunas abreviaturas para acelerar el uso, por ejemplo ~ (el simbolito que tiene arriba la ñ, no se como se llama) significa el home del usuario actual, y se puede reemplazar el */home/staarbreaker* por él, siguiendo el ejemplo anterior, se puede hacer ```

staarbreaker@multivac:~$ cd ~/Descargas
staarbreaker@multivac:~/Descargas$ 
``` otras abreviaturas son el . (un punto) que significa el directorio actual (cualquiera sea) donde nos encontramos, o los .. (dos puntos seguidos) que significa el directorio inmediatamente superior al que nos encontramos. si se usa sin indicar ningún parámetro o ubicación, nos mueve, desde donde estemos, a nuestro ~ 


[SIZE="4"]**ls**[/SIZE]

*ls* (de *list*) sirve para listar el contenido del directorio actual o del que le indiquemos. por ejemplo, el contenido de mi carpeta Documentos ```

staarbreaker@multivac:~/Documentos$ ls
**colegio/  facultad/  madre/**  google-reader-subscriptions.xml  hard.txt  lista.txt  paquetes.txt  scripticonos.sh
staarbreaker@multivac:~/Documentos$
``` (en negrita se muestran las carpetas) o de mi /opt ```

staarbreaker@multivac:~/Documentos$ ls /opt
**chromium-browser/  google-earth/**
staarbreaker@multivac:~/Documentos$
``` este comando tiene bastantes modificadores, muy útiles, como por ejemplo -l que muestra más detalles, como fechas de modificación, dueño, tamaño, etc, de los archivos, o -a que incluye los archivos ocultos, o -h que muestra los tamaños en formato legible facilmente, o -S que ordena los resultados por tamaño. para obtener un listado de todos los parámetros y su acción, se puede correr *ls --help*. un ejemplo con parámetros ```

staarbreaker@multivac:~$ ls -lSrah --group-directories-first --time-style=+"%d.%m.%Y %H:%M" -F
total 720K                                                         
drwxr-xr-x  2 staarbreaker users 4,0K 03.10.2009 19:07 **Videos/**     
drwxr-xr-x  4 staarbreaker users 4,0K 22.09.2009 17:17 **Programas/**  
drwxr-xr-x  3 staarbreaker users 4,0K 26.09.2009 20:48 **Paquetes/**   
drwxr-xr-x  2 staarbreaker users 4,0K 02.09.2009 00:01 **Música/**     
drwxr-xr-x 10 staarbreaker users 4,0K 04.10.2009 13:21 **Imágenes/**   
drwxr-xr-x 19 staarbreaker users 4,0K 09.09.2009 22:57 **Eyecandy/**   
drwxr-xr-x  5 staarbreaker users 4,0K 26.09.2009 20:39 **Documentos/** 
drwxr-xr-x  2 staarbreaker users 4,0K 01.10.2009 00:22 **Desktop/**    
drwxr-xr-x  3 staarbreaker users 4,0K 04.10.2009 02:26 **Descargas/**  
drwxr-xr-x  2 staarbreaker users 4,0K 19.04.2009 00:33 **.xine/**      
drwx------  4 staarbreaker users 4,0K 19.07.2009 02:26 **.thumbnails/**
drwxr-xr-x 15 staarbreaker users 4,0K 31.08.2009 00:43 **.themes/**    
drwxr-xr-x  2 staarbreaker users 4,0K 22.09.2009 17:26 **.superkaramba/**
drwxr-xr-x  3 staarbreaker users 4,0K 19.04.2009 22:39 **.subversion/**  
drwx------  4 staarbreaker users 4,0K 24.08.2009 02:03 **.songbird2/**   
drwxr-xr-x  2 staarbreaker users 4,0K 12.09.2009 17:57 **.scripts/**     
drwxr-xr-x  3 staarbreaker users 4,0K 14.08.2009 01:33 **.scorched3d/**  
drwxr-xr-x  3 staarbreaker users 4,0K 24.05.2009 01:20 **.q3a/**         
drwx------  3 staarbreaker users 4,0K 07.08.2009 23:35 **.pki/**         
drwx------ 18 staarbreaker users 4,0K 05.10.2009 19:27 **.opera/**       
drwxr-xr-x  2 staarbreaker users 4,0K 09.09.2009 01:13 **.mplayer/**     
drwxr-xr-x  3 staarbreaker users 4,0K 28.07.2009 00:46 **.mpd/**         
drwx------  3 staarbreaker users 4,0K 24.08.2009 02:02 **.mozilla/**     
drwxr-xr-x  3 staarbreaker users 4,0K 19.04.2009 18:37 **.marble/**      
drwx------  3 staarbreaker users 4,0K 19.04.2009 18:54 **.macromedia/**  
drwx------  3 staarbreaker users 4,0K 19.04.2009 00:44 **.local/**       
drwx------  8 staarbreaker users 4,0K 11.09.2009 15:43 **.kdemod4/**     
drwxr-xr-x  3 staarbreaker users 4,0K 04.10.2009 03:15 **.kde4/**        
drwxr-xr-x  3 staarbreaker users 4,0K 16.08.2009 21:29 **.kde/**         
drwxr-x---  7 staarbreaker users 4,0K 18.08.2009 16:53 **.inkscape/**    
drwxr-xr-x  8 staarbreaker users 4,0K 07.09.2009 16:02 **.icons/**       
drwx------  4 staarbreaker users 4,0K 01.10.2009 20:02 **.googleearth/** 
drwx------  2 staarbreaker users 4,0K 04.10.2009 03:28 **.gnupg/**       
drwx------  2 staarbreaker users 4,0K 20.07.2009 20:42 **.gnome2_private/**
drwx------  3 staarbreaker users 4,0K 20.07.2009 20:42 **.gnome2/**        
drwxr-xr-x 22 staarbreaker users 4,0K 03.10.2009 17:27 **.gimp-2.6/**      
drwx------  4 staarbreaker users 4,0K 14.08.2009 15:48 **.gegl-0.0/**      
drwx------  2 staarbreaker users 4,0K 31.08.2009 00:54 **.gconfd/**        
drwx------  3 staarbreaker users 4,0K 31.08.2009 00:19 **.gconf/**         
drwxr-xr-x  2 staarbreaker users 4,0K 03.10.2009 19:20 **.fonts/**         
drwxr-xr-x  2 staarbreaker users 4,0K 03.10.2009 19:20 **.fontconfig/**    
drwxr-xr-x  6 staarbreaker users 4,0K 04.10.2009 12:50 **.fluxbox/**       
drwxr-xr-x  2 staarbreaker users 4,0K 16.08.2009 02:53 **.etracer/**       
drwxr-xr-x  4 staarbreaker users 4,0K 16.08.2009 00:24 **.emerald/**       
drwxr-xr-x  9 staarbreaker users 4,0K 26.09.2009 00:24 **.dvdcss/**        
drwxr-xr-x  6 staarbreaker users 4,0K 22.05.2009 02:51 **.djl/**           
drwx------  3 staarbreaker users 4,0K 19.04.2009 00:31 **.dbus/**          
drwxr-xr-x  2 staarbreaker users 4,0K 20.08.2009 02:19 **.cwp/**           
drwxr-xr-x  2 staarbreaker users 4,0K 28.07.2009 00:20 **.covers/**
drwxr-xr-x 21 staarbreaker users 4,0K 03.10.2009 19:21 **.config/**
drwxr-xr-x  5 staarbreaker users 4,0K 15.08.2009 16:43 **.cache/**
drwx------  3 staarbreaker users 4,0K 12.09.2009 12:56 **.appdata/**
drwx------  3 staarbreaker users 4,0K 19.04.2009 18:54 **.adobe/**
drwx------  2 staarbreaker users 4,0K 30.05.2009 22:17 **.FontForge/**
drwx------  2 staarbreaker users 4,0K 20.07.2009 20:44 **.AbiSuite/**
drwxr-xr-x  3 root         root  4,0K 19.04.2009 04:26 ../
drwx------ 58 staarbreaker users 4,0K 05.10.2009 14:44 ./
-rw-------  1 staarbreaker users   16 26.04.2009 22:48 .esd_auth
-rw-------  1 staarbreaker users   22 04.10.2009 14:41 .dmrc
-rw-------  1 staarbreaker users   98 15.08.2009 14:31 .lesshst
-rwxr-xr-x  1 staarbreaker users  100 19.04.2009 04:26 **.xsession***
-rwxr-xr-x  1 staarbreaker users  103 19.04.2009 04:26 **.xinitrc***
-rw-------  1 staarbreaker users  117 02.09.2009 20:45 .directory
-rw-r--r--  1 staarbreaker users  158 20.05.2009 02:19 .hyperconf
-rw-------  1 staarbreaker users  261 05.10.2009 14:43 .Xauthority
-rw-r--r--  1 staarbreaker users  270 31.08.2009 01:07 .gtkrc-2.0
-rw-r--r--  1 staarbreaker users  274 04.10.2009 13:21 .gtk-bookmarks
-rw-r--r--  1 staarbreaker users  315 01.08.2009 22:34 .bash_profile~
-rw-r--r--  1 staarbreaker users  315 01.08.2009 22:34 .bash_profile
-rw-r--r--  1 staarbreaker users  322 14.08.2009 16:08 .gtkrc-2.0-kde4
-rw-------  1 staarbreaker users  383 01.08.2009 22:34 .zshhistory
-rw-r--r--  1 staarbreaker users  411 28.07.2009 00:38 .mpdconf
-rw-------  1 staarbreaker users  419 10.09.2009 19:26 .kderc
-rw-------  1 staarbreaker users  436 14.08.2009 12:57 .xsession-errors-:1
-rw-r--r--  1 staarbreaker users  517 31.05.2009 14:44 .fonts.conf
-rw-r--r--  1 staarbreaker users  561 04.10.2009 12:58 .htoprc
-rw-r--r--  1 staarbreaker users 1,1K 28.07.2009 21:41 .nvidia-settings-rc
-rw-r--r--  1 staarbreaker users 1,4K 01.08.2009 22:33 .zshrc
-rw-------  1 staarbreaker users 1,4K 26.07.2009 23:37 .zsh_history
-rw-r--r--  1 staarbreaker users 1,7K 01.08.2009 22:33 .zshrc~
-rw-------  1 staarbreaker users 2,2K 04.10.2009 13:21 .recently-used.xbel
-rwxr-xr-x  1 staarbreaker users 2,5K 28.07.2009 15:14 **.conkyrc***
-rw-r--r--  1 staarbreaker users 2,7K 17.08.2009 13:27 .bashrc
-rw-r--r--  1 staarbreaker users 3,1K 24.07.2009 16:34 .bashrc~
-rw-r--r--  1 staarbreaker users 3,6K 19.04.2009 01:24 .face.icon
-rw-r--r--  1 staarbreaker users 8,1K 29.07.2009 01:51 .Xdefaults
-rw-r--r--  1 staarbreaker users 9,7K 28.07.2009 21:18 .Xdefaults~
-rw-r--r--  1 staarbreaker users  34K 26.07.2009 20:34 .zcompdump
-rw-------  1 staarbreaker users 144K 05.10.2009 19:24 .xsession-errors
-rw-------  1 staarbreaker users 161K 05.10.2009 18:31 .bash_history
staarbreaker@multivac:~$
```

saludos

---

### Post by sergiom99 on 2009-10-05
> **Sleeping Beauty said:**
> Como los agradecimientos valen, Muchas gracias! A los nuevos nos viene muy bien.
Si se me permite agrego algo sobre el filesystem de linux que a mi me ayudó a entender "algo" más todo esto...
Espero que a los nuevos les sirva, al menos para saber dónde buscar las cosas...

Esto es bueno para nuevos y no tanto. Gracias!

---

### Post by aledruetta on 2009-10-05
Antes que nada, muy buena idea!!!!

En segundo lugar ¿se pueden hacer preguntas me imagino? Porque algunos bebés de más de tres años por ahí hay cosas que no las entendemos :)

> **pablo.s said:**
> [B][SIZE=4]---   df   ---
[/SIZE][/B]
El comando df muestra la cantidad de espacio
disponible en cada partición montada.
Por ejemplo:

```
pablo@raanana:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb2              7164704   3897524   3267180  55% /
udev                    508288       308    507980   1% /dev
none                    508288       556    507732   1% /dev/shm
none                    508288        92    508196   1% /var/run
none                    508288         0    508288   0% /var/lock
none                    508288         0    508288   0% /lib/init/rw
/dev/sda7             67848356  37109904  30738452  55% /media/jaunty
/dev/sdb3             70982616  46391348  20985480  69% /home
/dev/sda1             54540640  12917380  41623260  24% /media/pri
/dev/sda2             52431360  29634368  22796992  57% /media/mon
/dev/sda3             52423328  35826880  16596448  69% /media/video
/dev/sr0                691160    691160         0 100% /media/cdrom0
```

Supongo que todo lo que empieza con /dev/sd_alguna_cosa o hd_alguna_cosa son particiones del disco rígido, unidades ópticas, pendrives, etc.
Ahora ¿Qué son udev y none? ¿Y por qué algunas particiones están montadas en /media/pri, mon, video?

---

### Post by pablo.s on 2009-10-05
> **aledruetta said:**
> Antes que nada, muy buena idea!!!!

En segundo lugar ¿se pueden hacer preguntas me imagino? Porque algunos bebés de más de tres años por ahí hay cosas que no las entendemos :)

Si, logicamente preguntas se 
pueden hacer.

> **aledruetta said:**
> Ahora ¿Qué son udev y none? 

En la columna que muestra los
sistemas de archivos (filesystems)
te da una pista de la partición.
Udev es un sistema dinámico de
manejo de dispositivos que va creando
links a los discos removibles o que
se pueden extraer (para el caso es lo
mismo) como discos rigidos, pendrives,
discos montados remotamente, aparte
de conexiones de red, y otros.
Lo que hace es mostrarse como una
partición a efectos de direccionar esos
dispositivos a un servidor.
None te dice que los directorios que
monta no tienen un sistema de archivos
particular. 

> **aledruetta said:**
> ¿Y por qué algunas particiones están montadas en /media/pri, mon, video?

Porque son particiones que yo les dí
un punto de montaje desde la instalación
de la versión Alternate. Sigo la convención
de montar las particiones en /media. Antes
lo hacía en /mnt, pero ahora no se usa más.

---

### Post by aledruetta on 2009-10-05
Gracias Pablo.s!

---

### Post by lucasgz on 2009-10-05
Muy buena idea! 
tambien estaria bueno que pongan que significa la abreviatura del comando, como de CD es Change Directory, asi es mas facil memorizarlo

y esto no es un comando pero con (*) no hace falta escribir nombres largos como por ej
sh et-linux-2.60.x86.run
es lo mismo que
sh et-lin*
y tambien funciona para directorios

---

### Post by pablo.s on 2009-10-05
> **lucasgz said:**
> Muy buena idea! 
tambien estaria bueno que pongan que significa la abreviatura del comando, como de CD es Change Directory, asi es mas facil memorizarlo

Apuntado. Los proximos comandos
van con esa información. Gracias
por el aporte!

---

### Post by guillermolisi on 2009-10-05
> **lucasgz said:**
> Muy buena idea! 
tambien estaria bueno que pongan que significa la abreviatura del comando, como de CD es Change Directory, asi es mas facil memorizarlo

y esto no es un comando pero con (*) no hace falta escribir nombres largos como por ej
sh et-linux-2.60.x86.run
es lo mismo que
sh et-lin*
y tambien funciona para directorios
Hay que tener especial cuidado con el uso de metacaracteres,  principalmente con el *.

Si hay varios archivos con el mismo prefijo el comando que se aplique lo hara para todos los que genere la lista cuando se expanda el metacaracter.

Si no se quiere escribir todo el nombre, lo mas seguro es escribir un prefijo y presionar <tab> para que complete el resto.

---

### Post by staar on 2009-10-05
> **lucasgz said:**
> Muy buena idea! 
tambien estaria bueno que pongan que significa la abreviatura del comando, como de CD es Change Directory, asi es mas facil memorizarlo
editado ;-)

saludos

---

### Post by aledruetta on 2009-10-05
Otro comodín es "?", que reemplaza un único caracter o dígito.

Por ejemplo:
```
ls texto?.txt
```Listaría todos los archivos que comienzan con la cadena "texto", continúan con alguna letra o número (pero sólo 1), y que tienen la extensión ".txt". Pero no listaría el archivo "texto12.txt". Colocando el comodín "*", en cambio, listaría cualquier archivo que, comenzando con "texto" y terminando con extensión ".txt", lleve insertada una cadena cualquiera, de cualquier extensión o incluso nula, es decir, incluso el archivo "texto.txt".

Espero que sirva y no haberme equivocado en nada.

---

### Post by juancarlospaco on 2009-10-06
*Pero... yy... em...* no seria mejor recomendar GUIs para los usuarios nuevos?
digo, onda para UFW ---> GUFW , para NDISWrapper ---> NDIS-gtk
:)

---

### Post by santiagoward2000 on 2009-10-06
> **juancarlospaco said:**
> *Pero... yy... em...* no seria mejor recomendar GUIs para los usuarios nuevos?
digo, onda para UFW ---> GUFW , para NDISWrapper ---> NDIS-gtk
:)

Yo no estoy tan seguro que sea mejor. De cualquier manera, muchas guías que se encuentran en internet hacen uso de comandos. Tener una idea de qué hacen esos comandos puede ayudar a evitar dolores de cabeza y enojos que podrían aparecer por comandos "maliciosos" (aunque creo que nunca vi alguno por estos lados) o simplemente por error de quien escribió la guía.
Saludos!

_EDIT:_
Olvidé mencionar que me encanta la idea del thread! :D

---

### Post by harryscode on 2009-10-06
Excelente thread.. más que agradecido.. y si.. hay muchas guias referente a los comandos.. pero el que no esta acostumbrado a leer lenguaje técnico seguramente lo podrá entender con lenguaje más cotidiano.

---

### Post by jorval on 2009-10-06
Podrías explicar esta entrada, no entiendo lo que quieres decir, gracias.


```
Pero... yy... em... no seria mejor recomendar GUIs para los usuarios nuevos?
digo, onda para UFW ---> GUFW , para NDISWrapper ---> NDIS-gtk

```

Otra cosa, este carácter: ~ se llama "ñuflo"

---

### Post by pablo.s on 2009-10-06
> **juancarlospaco said:**
> *Pero... yy... em...* no seria mejor recomendar GUIs para los usuarios nuevos?
digo, onda para UFW ---> GUFW , para NDISWrapper ---> NDIS-gtk
:)

Puse la regla de "No postear comentarios
que no lleven a ninguna parte", me parece.

---

### Post by pablo.s on 2009-10-06
**[SIZE=3]---   chmod   ---[/SIZE]**
[SIZE=3]**Change access mode**[/SIZE]

El comando chmod cambia el modo de acceso
de uno o más archivos. En otras palabras, [B]permite
cambiar los permisos del archivo.[/B]

Los permisos básicos son tres:
 - **Lectura** (en inglés **read**)
 - **Escritura** (en inglés **write**)
 - **Ejecución** (en inglés **execute**) 

Las clases de propietarios son cuatro:
 - **u** = dueño (dueño del archivo o directorio)
 - **g** = grupo (grupo al que pertenece el archivo)
 - **o** = otros (usuarios que no son el dueño ni del grupo)
 - **a** = todos (entre los que están el dueño, el grupo y otros)

Para cambiar los permisos se pueden utilizar dos
modos: el modo octal y el modo carácter.
El modo octal consiste en tipos de combinaciones
de números octales de tres dígitos del 000 al 777.
Número 0 = Lectura NO Escritura NO Ejecución NO
Número 1 = Lectura NO Escritura NO Ejecución SI
Número 2 = Lectura NO Escritura SI Ejecución NO
Número 3 = Lectura NO Escritura SI Ejecución SI
Número 4 = Lectura SI Escritura NO Ejecución NO
Número 5 = Lectura SI Escritura NO Ejecución SI
Número 6 = Lectura SI Escritura SI Ejecución NO
Número 7 = Lectura SI Escritura SI Ejecución SI

Por ejemplo chmod 635 mi_script.sh hace que el
archivo mi_script.sh tenga lectura y escritura al dueño,
escritura y ejecución al grupo y lectura y ejecución a
los demás.

El módo carácter tiene tres modificadores que hacen
los cambios:
**+** añade un modo
**-** elimina un modo
**=** especifica el modo y sobreescribe los modos anteriores.

Por ejemplo chmod u=rw establece los permisos de lectura
y escritura al dueño.
chmod +x establece el permiso de ejecución para el usuario.

---

### Post by santiagoward2000 on 2009-10-06
Bueno, hoy pongo uno yo. Ya que hace poco vi un caso en #ubuntu-es donde un usuario le hizo borrar su home a alguien nuevo (lo corrigieron enseguida y echaron al que puso el comando, pero el usuario con la pregunta ya había borrado varias carpetas), me pareció apropiado explicar el uso del comando **rm** y las precauciones a tener. No voy a postear ninguna línea que pueda eliminar archivos importantes, solo ejemplos con archivos y carpetas que creé para dichos ejemplos. Al final, en el apartado **precaución**, hay un link a un thread del foro internacional que lista varios "comandos maliciosos", incluyendo cuatro ejemplos que usan el comando **rm**, y que no deben usar nunca en sus máquinas (o la de nadie más, obviamente).

[SIZE=5]**rm**[/SIZE]
[SIZE=3]**Remove** (remover)[/SIZE]

El comando **rm** se usa para borrar archivos o directorios (OJO! borrar es **borrar**, no mover a la papelera. Una vez borrado, el archivo no se puede recuperar. Si van a usarlo, por las dudas revisen varias veces que están seguros de lo que van a borrar).

Por ejemplo, si tenemos un archivo en el directorio en el que estamos situados (ver comando **cd** explicado anteriormente por staar y el archivo armado por Sleeping Beauty para entender cómo situarse en diferentes directorios) llamado **Archivo_Borrable**, podemos borrarlo de la siguiente manera:
```
santi@santi-laptop:~$ rm Archivo_Borrable
```
También se puede usar desde cualquier posición, marcando la posición absoluta o relativa del archivo:
```
santi@santi-laptop:~$ rm Carpera_Borrable/Archivo_Borrable
```

**--recursive**, **-r** o **-R** (recursivo)
El parámetro **--recursive** se usa para borrar directorios, y todo lo que tengan adentro recursivamente. Por ejemplo, si queremos borrar el directorio **Carpeta_Borrable** (y todo lo que haya adentro), hacemos:
```
santi@santi-laptop:~$ rm -r Carpera_Borrable/
```

**-i**
Este parámetro nos pregunta si estamos seguros antes de eliminar cada archivo, útil para evitar errores:
```
santi@santi-laptop:~/Carpeta_Borrable$ rm -i Archivo_Borrable Archivo_Borrable_2 Archivo_Borrable_3 
rm: remove regular empty file `Archivo_Borrable'? y
rm: remove regular empty file `Archivo_Borrable_2'? y
rm: remove regular empty file `Archivo_Borrable_3'? y
```

**-I**
Esta opción funciona de forma parecida al **-i**, pero es un poco menos invasivo. Pregunta en caso de tratar de eliminar más de 3 archivos, o cuando usamos la opción **-r**. Por ejemplo:
```
santi@santi-laptop:~/Carpeta_Borrable$ rm -I Archivo_Borrable Archivo_Borrable_2 Archivo_Borrable_3
``` (como son solo 3 archivos no pregunta)

```
santi@santi-laptop:~/Carpeta_Borrable$ rm -I Archivo_Borrable Archivo_Borrable_2 Archivo_Borrable_3 Archivo_Borrable_4 
rm: remove all arguments? y
``` (son 4 archivos, entonces sí pregunta).

**-f** (forzado)
Ignora archivos inexistentes y no pregunta (aún cuando hayamos puesto la opción **-i**). Por ejemplo, si queremos borrar un archivo que no se encuentra en la pocisión definida **Archivo_Borrable_4**:
```
santi@santi-laptop:~/Carpeta_Borrable$ rm Archivo_Borrable Archivo_Borrable_2 Archivo_Borrable_3 Archivo_Borrable_4 
rm: cannot remove `Archivo_Borrable_4': No such file or directory
``` Nos avisa que no se puede borrar porque no existe, pero borra los demás archivos existentes. En cambio, con la opción **-f**:
```
santi@santi-laptop:~/Carpeta_Borrable$ rm -f Archivo_Borrable Archivo_Borrable_2 Archivo_Borrable_3 Archivo_Borrable_4
``` no avisa nada.
Hay que tener en cuenta que la opción **-f** elimina las opciones **-i** o **-I**, por lo que cualquier línea que tenga esta opción va a borrar todo sin preguntar.

[SIZE=5][COLOR=Red]**Precaución:**[/COLOR][/SIZE]
El comando **rm** lo pueden usar tipos que no tienen nada mejor que hacer que molestar a usuarios nuevos. Se vio bastante en la sala de novatos del foro internacional, y hace poco, como dije al principio, vi un caso en el irc de #ubuntu-es. El tipo con nada mejor que hacer le decía a alguien que venía con un problema (y que no sabía qué hace el comando rm) que corra alguna línea que borraba su carpeta Home (~), o incluso todo el filesystem (/). Si alguien les da una línea con **rm**, revisen que no estén borrando **/** o **~**, o ningún archivo o carpeta con información importante. En caso de no estar seguros de lo que hacen, es conveniente que no usen la opción **-f**, y para estar más seguros, pueden usar **-i** o **-I** para confirmar cada archivo (molesto, pero seguro :)). Obviamente, lo mejor es esperar un poco a que alguien más les confirme si es seguro o no usar ese comando.
También, como dijo guillermolisi anteriormente, hay que tener cuidado al usarlo con comodines, como "*****", ya que podemos terminar borrando sin querer varios archivos con nombres similares.
Les recomiendo que le peguen un vistazo a la lista de comandos maliciosos de este thread: [http://ubuntuforums.org/announcement.php?a=54](http://ubuntuforums.org/announcement.php?a=54) (está en inglés, así que cualquier duda pregunten).
Leer el manual de **rm** tampoco va a hacer mal ;):
```
man rm
```
Saludos!

---

### Post by aledruetta on 2009-10-06
> **pablo.s said:**
> **[SIZE=3]---   chmod   ---[/SIZE]**
[SIZE=3]**Change access mode**[/SIZE]

Para cambiar los permisos se pueden utilizar dos
modos: el modo octal y el modo carácter.
El modo octal consiste en tipos de combinaciones
de números octales de tres dígitos del 000 al 777.
Número 0 = Lectura NO Escritura NO Ejecución NO
Número 1 = Lectura NO Escritura NO Ejecución SI
Número 2 = Lectura NO Escritura SI Ejecución NO
Número 3 = Lectura NO Escritura SI Ejecución SI
Número 4 = Lectura SI Escritura NO Ejecución NO
Número 5 = Lectura SI Escritura NO Ejecución SI
Número 6 = Lectura SI Escritura SI Ejecución NO
Número 7 = Lectura SI Escritura SI Ejecución SI


Comento una forma que a mí me ayudó a entender esto. Pensarlo como números binarios es una forma bien gráfica de ver lo que hace el comando chmod. Es lo mismo que está diciendo Guillermo, pero yo lo entendí así:

rwx

000 = 0
001 = 1
010 = 2
011 = 3
100 = 4
101 = 5
110 = 6
111 = 7

Entonces "chmod 000" le quita todos los permisos a todo el mundo. Y "chmod 777" le otorga todos los permisos.

El mejor es "chmod 007", es pura acción, nada de lectura ni escritura, eso es cosa de intelectuales :P

---

### Post by pablo.s on 2009-10-06
> **aledruetta said:**
> }El mejor es "chmod 007", es pura acción, nada de lectura ni escritura, eso es cosa de intelectuales :P

Pero mirá que...
AH! Ya lo entendí.

---

### Post by guillermolisi on 2009-10-06
> **aledruetta said:**
> 
El mejor es "chmod 007", es pura acción, nada de lectura ni escritura, eso es cosa de intelectuales :P
Tambien el mas inseguro ya que ni el owner ni ningun group tienen permisos, solamente "otros" con lo cual entra en juego "el resto del mundo", o sea todos menos quienes deberian tenerlos.

---

### Post by z37a on 2009-10-07
Gente muy bueno este post, me encanto, es mas me sumo comentando un comando que para mi es fundamental a la hora de revisar el estado del equipo, e ir monitoreandolo:

[SIZE="5"]**El comando "watch"**[/SIZE]

El comando watch permite ejecutar un comando, o varios, cada determinado tiempo, pro defecto cada 2 segundos, y se usa de la siguiente manera:

**$ watch -n [COLOR="Red"]{segundos}[/COLOR] "[COLOR="Red"]{comandos}[/COLOR]"**

donde como ejemplo si queremos ver cada 1 segundo que archivos hay en determinada carpeta que finalicen en tmp podremos usar los siguiente:

**$ watch -n 1 "ls -l /mnt | grep *tmp"**

o para hacerlo mas sencillo, utilizando comandos recién citados:

**$ watch -n 1 "df -h"**

Con este ultimo podremos ver cada 1 segundo el estado de us ode nuestras particiones montadas.

Nota: En caso de no usar el parámetro -n el comando se ejecutara cada 2 segundos, ya que es lo que trae seteado por defecto, el -n es solo para cambiarlo.

Perdon gente, me comi el final, **para finalizar el comando precionen Ctrol+C**

---

### Post by LolaMora on 2009-10-07
> **z37a said:**
> Gente muy bueno este post, me encanto, es mas me sumo comentando un comando que para mi es fundamental a la hora de revisar el estado del equipo, e ir monitoreandolo:

[SIZE="5"]**El comando "watch"**[/SIZE]

El comando watch permite ejecutar un comando, o varios, cada determinado tiempo, pro defecto cada 2 segundos, y se usa de la siguiente manera:

**$ watch -n [COLOR="Red"]{segundos}[/COLOR] "[COLOR="Red"]{comandos}[/COLOR]"**

donde como ejemplo si queremos ver cada 1 segundo que archivos hay en determinada carpeta que finalicen en tmp podremos usar los siguiente:

**$ watch -n 1 "ls -l /mnt | grep *tmp"**

o para hacerlo mas sencillo, utilizando comandos recién citados:

**$ watch -n 1 "df -h"**

Con este ultimo podremos ver cada 1 segundo el estado de us ode nuestras particiones montadas.

Nota: En caso de no usar el parámetro -n el comando se ejecutara cada 2 segundos, ya que es lo que trae seteado por defecto, el -n es solo para cambiarlo.

Como finaliza o como se interrumpe este comando?

---

### Post by aledruetta on 2009-10-07
> **LolaMora said:**
> Como finaliza o como se interrumpe este comando?
Supongo que con CTRL+Z

---

### Post by aledruetta on 2009-10-07
> **pablo.s said:**
> Pero mirá que...
AH! Ya lo entendí.
Sí, el chiste lleva en sí un error conceptual. Pura acción sería "chmod 111", pero como no tiene nada que ver con James Bond...
En cambio, como dice Guillermo, "chmod 007" le otorga todos los permisos a "otros" y se los niega al "propietario" y al "grupo".
Pero era un chiste.

---

### Post by guillermolisi on 2009-10-07
> **aledruetta said:**
> Supongo que con CTRL+Z
O el inefable Ctrl-c que practicamene todo lo interrumpe en la consola :)

---

### Post by z37a on 2009-10-07
> **guillermolisi said:**
> O el inefable Ctrl-c que practicamene todo lo interrumpe en la consola :)


Ahi aregle, efectivamente con el Ctrol+C, NO USEN Ctrol+Z!!!! Si no l opasan a segundo plano!!!!!

---

### Post by aledruetta on 2009-10-07
> **z37a said:**
> Ahi aregle, efectivamente con el Ctrol+C, NO USEN Ctrol+Z!!!! Si no l opasan a segundo plano!!!!!
¿Y CTRL+D, funciona? Algunos procesos se interrumpen con CTRL+D. Pero no tengo clara la diferencia entre CTRL+Z; CTRL+D; CTRL+C (este último, siempre pensé que era para copiar)

---

### Post by guillermolisi on 2009-10-07
> **aledruetta said:**
> ¿Y CTRL+D, funciona? Algunos procesos se interrumpen con CTRL+D. Pero no tengo clara la diferencia entre CTRL+Z; CTRL+D; CTRL+C (este último, siempre pensé que era para copiar)
Buen punto !

Es que cada combinacion tiene un efecto distinto segun el contexto en que se opere.
En las interfaces graficas, donde hay ciertas caracteristicas de edicion, Ctrl-c es una atajo para copiar algo seleccionado por el puntero del mouse.
En la consola, Ctrl-c interrumpe la ejecucion de un script y todos aquellos programas que controlen la señal que esa combinacion de teclas genera (trapping).

Si no recuerdo mal, cuando escribis el cuerpo de un e-mail en consola usando SendMail o equivalente, terminas la edicion del texto con Ctrl-d y la segunda vez que ingresas Ctrl-d cierra el mensaje y lo envia..

Ctrl-z la dejo para que otro aporte :)

---

### Post by staar on 2009-10-07
Ctrl + D, cuando la línea está vacía, lo que hace es terminar la sesión de la consola (es como correr *exit*)
Ctrl + Z lo que hace es mandar el proceso al background, osea que sige corriendo, pero en el fondo, con *fg* (de foreground) lo volvés a traer al frente...

para copiar/pegar en la Terminal los accesos son los mismos, solo que se les agrega Shift, así copiar es Ctrl + Shift + C, y pegar es Ctrl + Shift + V, aunque esto creo que solo es válido para algunas terminales que corren en X, no para las ttys, en estas con Ctrl + U se corta desde el cursor hasta el principio de la línea o con Ctrl + K desde el cursor hasta el final de la línea, y con Ctrl + Y se pega lo que se cortó...

después están
-TAB: autocompleta el comando
-Alt + B: retrocede el cursor una palabra
-Alt + F: avanza una palabra
-Ctrl + W: borra una palabra
-Alt + J, X: avanza el cursor hasta la siguiente carácter X
-Alt + Ctrl + J, X: retrocede hasta la anterior carácter X
-Ctrl + L: limpia la pantalla (es como correr *clean*)
-Ctrl + S: bloquea (frena) la salida del comando, útil, por ejemplo, cuando el directorio tiene muchos archivos y la salida de *ls* no entra en la pantalla
-Ctrl + Q: desbloquea la salida del comando
-Scroll Lock (Bloq Despl en teclados en español): bloquea/desbloquea la salida del comando


saludos

---

### Post by pablo.s on 2009-10-07
[B][SIZE=3]---   passwd   ---
     Password[/SIZE][/B]

El comando passwd crea o cambia una
contraseña asociada a un nombre de usuario.
Los usuarios solo pueden cambiar sus propias
contraseñas. No es preciso la intervención del 
administrador. 
Ejemplos:

```
passwd -d konichiwa
```

Borra la contraseña del usuario Konichiwa,
haciendo que no tenga, dejandola vacía.

```
passwd konichiwa
```

Cambia la contraseña del usuario Konichiwa.
Primero pide la contraseña actual. Luego se
solicitará el ingreso de la nueva contraseña por
parte doble.

```
passwd -e konichiwa
```

Provoca que la contraseña del usuario Konichiwa
expire de inmediato, forzando a que la siguiente
vez que el usuario se loguee, tenga que cambiar
su contraseña.

---

### Post by oktubrer on 2009-10-07
> **staar said:**
> Ctrl + D, cuando la línea está vacía, lo que hace es terminar la sesión de la consola (es como correr *exit*)
Ctrl + Z lo que hace es mandar el proceso al background, osea que sige corriendo, pero en el fondo, con *fg* (de foreground) lo volvés a traer al frente...


Corrijo un poco, en realidad con ctrl+z no lo mandás al background, sino que el proceso se detiene y queda "en pausa".
Para mandarlo al background, luego de pausarlo con ctrl+z se usa *bg*(de BackGround).  Si lo querés volver a ejecutar en primer plano, ahi si con *fg* como habían dicho (de ForeGround).
Otra forma de iniciar directamente un proceso en segundo plano es agregandole & al final.
De esta forma se pueden ejecutar varios procesos en paralelo.  Con el comando *jobs* se muestran todos los que se están ejecutando en esa terimnal con el estado correspondiente.
Usando fg + el número de tarea que muestra jobs, se puede traer cualquiera a primer plano.  Para intercambiar, de nuevo ctrl+z para pausarlo y bg para pasarlo a segundo plano.

---

### Post by faktorqm on 2009-10-08
Voy intentar hechar un poco de luz sobre el tema: lo que ustedes estan diciendo, no es ni mas ni menos que las teclas que corresponden a accesos directos para ejecutar señales (keyboard shortcuts). 

¿Que es una señal? Los programas que se ejecutan en consola responden a un standard de señalizacion, que lo provee un standard que se llama POSIX ("**P**ortable **O**perating **S**ystem **I**nterface for Uni**x**"). Este standard no provee unicamente una serie de señales, es un conjunto de muchas cosas, pero aqui solo voy a nombrar las señales mas importantes por que escapa el objetivo de este post y de este thread.

Tipeando ciertas combinaciones de teclas en una terminal con procesos corriendo, hacemos que el sistema le envie ciertas señales: 

Ctrl-C: envia una señal de INT (abreviatura de interrupt) que causa que el programa se cierre. En programacion a veces es cacheada como EOF (end of file), como en el programa que dijo Lisi por ejemplo :) aunque desde el punto de vista mas puro no deberia ser asi.

Ctrl-Z: envia una señal de TSTP (abreviatura de tty stop) que por defecto, hace que el proceso se suspenda su ejecucion.
<<curiosidad: Tty es por teletypewriter, un tipo arcaico de terminal>>

Esta señal ademas, tiene un contrario, que es CONT (de continue) que no posee una combinacion de teclas asociada.

Para poder cambiar todas estas combinaciones de teclas existe un comando pero se los dejo para que investiguen cual es, y como se usa ;) no sean vagos y busquen! (Y OJO CON LO QUE TOCAN!)


Ctrl-4: Envía la señal QUIT (salir) que, por defecto, causa que el proceso termine y realice un volcado de memoria.

Señales que vemos todos los dias y no sabemos que son pero que no tienen una combinacion de teclas asociada (por suerte...)

SIGSEGV: todos los que usan kubuntu deben saber bien que es :P

Es una señal que le envia el kernel al programa cuando este cometio una violacion de segmento de memoria, es decir, quizo escribir o leer desde un lugar donde no podia o desde un lugar a donde al kernel le parecio que no tenia que hacerlo. Significa Segmentation Violation, (violacion de segmento) aunque en muchos lugares aparece como segmentation fault. (a ver muchachos, no les parece que si la señal es segmentation fault no le hubieran puesto SEGF en lugar de SEGV?)

SIGFPE: Esta señal es floating point error, es un error muy particular pero que generalmente va asociado al segv y/o a una operacion matematica que no se puede realizar.

ta tan ta tan!!!!! llego el gran momento!

SIGKILL: muchos han visto como algunos procesos se portan mal y hay que matarlos... bueno, cada vez que nosotros hacemos "kill 30243" y se mata el proceso cuyo ID es 30243, en realidad lo que se esta haciendo es enviarle al programa una señal de kill. La señal de kill cierra el programa directamente este donde este.

¿Que pasa cuando se cierra un programa? 

Cuando un programa se ejecuta, el SO lo copia en memoria y empieza a correr. El SO, le asigna una cierta cantidad de memoria al programa para que use. Si el programa necesita mas, literalmente le "pide" al SO que le de mas, y si el SO tiene libre le da, si no swapea un programa que este por ahi sin uso, y le da. (para que lo entiendan mejor, anota en la libreta del almacenero cuanto le deben para pagarle a fin de mes)

Cuando se cierra un programa, "limpiamente", lo que ocurre es que el programa vacía todo lo que usó, y le "devuelve" al sistema operativo la memoria que pidio. (Ahi arranca la hoja de la libreta y nadie debe nada)

Luego el sistema operativo borra de la memoria el codigo ejecutable y ya pone a disposicion de otro programa la memoria que este ultimo estaba ocupando.
Esto ocurre cuando usamos ctrl+c, que se envia la señal de interrupcion, el programa hace un SIGTERM y luego un SIGQUIT.
Cuando utilizamos kill, todo esto no ocurre. Directamente el SO borra el codigo ejecutable de la memoria y lo "despega" de la lista de procesos (le quita el PID). 

¿Y la memoria que utilizo no la libera nadie? Depende. Si usas un SO privativo que empieza con W, hasta que no reinicias queda ahi. Si usas SO libres, uno que empieza con L, en el 95% de los casos el kernel se encarga automaticamente de liberarla igual. 

Lamento haberlos aburrido de semejante manera y no haberles dejado ni un solo comando, que era el titulo del post. Va, si, stty. Muchisimo ojo con lo que hacen, pruebenlo en una virtual.

Salu2!

---

### Post by pablo.s on 2009-10-08
> **faktorqm said:**
> Lamento haberlos aburrido de semejante manera y no haberles dejado ni un solo comando, que era el titulo del post.

Sin embargo profundizás un tema 
muy útil. Vale por dos o tres comandos
tu post! Gracias, Martin!

[SIZE=3][B]---   dmesg   ---
Display messages[/B][/SIZE]

Este comando muestra la información que
maneja el kernel en el momento de inicio del
sistema. Esa información se guarda en un
buffer y puede ser utilizada para constatar el
funcionamiento del hardware o software al
momento de inicio.

Ejemplo de archivo de salida:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-12-generic (buildd@vernadsky) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu6) ) #39-Ubuntu SMP Mon Oct 5 22:08:01 UTC 2009 (Ubuntu 2.6.31-12.39-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
[    0.000000]  BIOS-e820: 000000000008f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f58f000 (usable)
[    0.000000]  BIOS-e820: 000000003f58f000 - 000000003f59c000 (reserved)
[    0.000000]  BIOS-e820: 000000003f59c000 - 000000003f64c000 (usable)
[    0.000000]  BIOS-e820: 000000003f64c000 - 000000003f6a8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6a8000 - 000000003f6ab000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6ab000 - 000000003f6ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6ef000 - 000000003f6f1000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6f1000 - 000000003f6f2000 (usable)
[    0.000000]  BIOS-e820: 000000003f6f2000 - 000000003f6ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6ff000 - 000000003f700000 (usable)
[    0.000000]  BIOS-e820: 000000003f700000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x3f700 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F800000 mask FFF800000 uncachable
[    0.000000]   2 base 03F700000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000008f000 (usable)
[    0.000000]  modified: 000000000008f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f58f000 (usable)
[    0.000000]  modified: 000000003f58f000 - 000000003f59c000 (reserved)
[    0.000000]  modified: 000000003f59c000 - 000000003f64c000 (usable)
[    0.000000]  modified: 000000003f64c000 - 000000003f6a8000 (ACPI NVS)
[    0.000000]  modified: 000000003f6a8000 - 000000003f6ab000 (ACPI data)
[    0.000000]  modified: 000000003f6ab000 - 000000003f6ef000 (ACPI NVS)
[    0.000000]  modified: 000000003f6ef000 - 000000003f6f1000 (ACPI data)
[    0.000000]  modified: 000000003f6f1000 - 000000003f6f2000 (usable)
[    0.000000]  modified: 000000003f6f2000 - 000000003f6ff000 (ACPI data)
[    0.000000]  modified: 000000003f6ff000 - 000000003f700000 (usable)
[    0.000000]  modified: 000000003f700000 - 000000003f800000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2f1f0000 - 2f86b3e0
[    0.000000] ACPI: RSDP 000fe020 00014 (v00 INTEL )
[    0.000000] ACPI: RSDT 3f6fd038 00050 (v01 INTEL  DG965WH  0000064C      01000013)
[    0.000000] ACPI: FACP 3f6fc000 00074 (v01 INTEL  DG965WH  0000064C MSFT 01000013)
[    0.000000] ACPI: DSDT 3f6f7000 040E9 (v01 INTEL  DG965WH  0000064C MSFT 01000013)
[    0.000000] ACPI: FACS 3f6ab000 00040
[    0.000000] ACPI: APIC 3f6f6000 00078 (v01 INTEL  DG965WH  0000064C MSFT 01000013)
[    0.000000] ACPI: WDDT 3f6f5000 00040 (v01 INTEL  DG965WH  0000064C MSFT 01000013)
[    0.000000] ACPI: MCFG 3f6f4000 0003C (v01 INTEL  DG965WH  0000064C MSFT 01000013)
[    0.000000] ACPI: ASF! 3f6f3000 000A6 (v32 INTEL  DG965WH  0000064C MSFT 01000013)
[    0.000000] ACPI: HPET 3f6f2000 00038 (v01 INTEL  DG965WH  0000064C MSFT 01000013)
[    0.000000] ACPI: SSDT 3f6f0000 001BC (v01 INTEL     CpuPm 0000064C MSFT 01000013)
[    0.000000] ACPI: SSDT 3f6ef000 00175 (v01 INTEL   Cpu0Ist 0000064C MSFT 01000013)
[    0.000000] ACPI: SSDT 3f6aa000 00175 (v01 INTEL   Cpu1Ist 0000064C MSFT 01000013)
[    0.000000] ACPI: SSDT 3f6a9000 00175 (v01 INTEL   Cpu2Ist 0000064C MSFT 01000013)
[    0.000000] ACPI: SSDT 3f6a8000 00175 (v01 INTEL   Cpu3Ist 0000064C MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000089f080]    TEXT DATA BSS ==> [0000100000 - 000089f080]
[    0.000000]   #4 [002f1f0000 - 002f86b3e0]          RAMDISK ==> [002f1f0000 - 002f86b3e0]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008a0000 - 00008a3136]              BRK ==> [00008a0000 - 00008a3136]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00fe200] fe200
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f700
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000008f
[    0.000000]     0: 0x00000100 -> 0x0003f58f
[    0.000000]     0: 0x0003f59c -> 0x0003f64c
[    0.000000]     0: 0x0003f6f1 -> 0x0003f6f2
[    0.000000]     0: 0x0003f6ff -> 0x0003f700
[    0.000000] On node 0 totalpages: 259532
[    0.000000] free_area_init_node: node 0, pgdat c077b840, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32068 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000008f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:c0700000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c17f4000, static data 35068 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257501
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-12-generic root=UUID=155f7069-f86a-4a44-b834-9e4f0461e55f ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5196800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f700)
[    0.000000] Memory: 1008872k/1039360k available (4544k kernel code, 28728k reserved, 2128k data, 540k init, 129292k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0785000 - 0xc080c000   ( 540 kB)
[    0.000000]       .data : 0xc0570104 - 0xc07841a8   (2128 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0570104   (4544 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1798.200 MHz processor.
[    0.002130] Console: colour VGA+ 80x25
[    0.002133] console [tty0] enabled
[    0.002296] hpet clockevent registered
[    0.002299] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.002304] Calibrating delay loop (skipped), value calculated using timer frequency.. 3596.40 BogoMIPS (lpj=7192800)
[    0.002319] Security Framework initialized
[    0.002334] AppArmor: AppArmor initialized
[    0.002341] Mount-cache hash table entries: 512
[    0.002454] Initializing cgroup subsys ns
[    0.002458] Initializing cgroup subsys cpuacct
[    0.002462] Initializing cgroup subsys memory
[    0.002469] Initializing cgroup subsys freezer
[    0.002471] Initializing cgroup subsys net_cls
[    0.002485] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.002488] CPU: L2 cache: 2048K
[    0.002490] CPU: Physical Processor ID: 0
[    0.002492] CPU: Processor Core ID: 0
[    0.002495] using mwait in idle threads.
[    0.002500] Performance Counters: Core2 events, Intel PMU driver.
[    0.002508] ... version:                 2
[    0.002511] ... bit width:               40
[    0.002512] ... generic counters:        2
[    0.002514] ... value mask:              000000ffffffffff
[    0.002517] ... max period:              000000007fffffff
[    0.002519] ... fixed-purpose counters:  3
[    0.002520] ... counter mask:            0000000700000003
[    0.002524] Checking 'hlt' instruction... OK.
[    0.018794] ACPI: Core revision 20090521
[    0.026723] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066415] CPU0: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz stepping 02
[    0.068001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3596.39 BogoMIPS (lpj=7192791)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.152455] CPU1: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz stepping 02
[    0.152468] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.156022] Brought up 2 CPUs
[    0.156025] Total of 2 processors activated (7192.79 BogoMIPS).
[    0.156071] CPU0 attaching sched-domain:
[    0.156074]  domain 0: span 0-1 level MC
[    0.156077]   groups: 0 1
[    0.156083] CPU1 attaching sched-domain:
[    0.156085]  domain 0: span 0-1 level MC
[    0.156088]   groups: 1 0
[    0.156166] Booting paravirtualized kernel on bare hardware
[    0.156235] regulator: core version 0.5
[    0.156235] Time:  8:46:56  Date: 10/08/09
[    0.156235] NET: Registered protocol family 16
[    0.156235] EISA bus registered
[    0.156235] ACPI: bus type pci registered
[    0.156303] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.156306] PCI: Not using MMCONFIG.
[    0.157758] PCI: Using configuration type 1 for base access
[    0.160010] bio: create slab <bio-0> at 0
[    0.160686] ACPI: EC: Look up EC in DSDT
[    0.164255] ACPI: Interpreter enabled
[    0.164262] ACPI: (supports S0 S3 S4 S5)
[    0.164283] ACPI: Using IOAPIC for interrupt routing
[    0.164318] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.165199] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
[    0.165201] PCI: Using MMCONFIG for extended config space
[    0.169712] ACPI: No dock devices found.
[    0.170704] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.170826] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.170830] pci 0000:00:01.0: PME# disabled
[    0.170867] pci 0000:00:03.0: reg 10 64bit mmio: [0x52225900-0x5222590f]
[    0.170900] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.170904] pci 0000:00:03.0: PME# disabled
[    0.170972] pci 0000:00:19.0: reg 10 32bit mmio: [0x52200000-0x5221ffff]
[    0.170979] pci 0000:00:19.0: reg 14 32bit mmio: [0x52224000-0x52224fff]
[    0.170987] pci 0000:00:19.0: reg 18 io port: [0x20c0-0x20df]
[    0.171026] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.171031] pci 0000:00:19.0: PME# disabled
[    0.171073] pci 0000:00:1a.0: reg 20 io port: [0x20a0-0x20bf]
[    0.171125] pci 0000:00:1a.1: reg 20 io port: [0x2080-0x209f]
[    0.171184] pci 0000:00:1a.7: reg 10 32bit mmio: [0x52225400-0x522257ff]
[    0.171239] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.171244] pci 0000:00:1a.7: PME# disabled
[    0.171286] pci 0000:00:1b.0: reg 10 64bit mmio: [0x52220000-0x52223fff]
[    0.171332] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.171336] pci 0000:00:1b.0: PME# disabled
[    0.171400] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.171404] pci 0000:00:1c.0: PME# disabled
[    0.171469] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.171474] pci 0000:00:1c.1: PME# disabled
[    0.171539] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.171544] pci 0000:00:1c.2: PME# disabled
[    0.171609] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.171613] pci 0000:00:1c.3: PME# disabled
[    0.171679] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.171683] pci 0000:00:1c.4: PME# disabled
[    0.171735] pci 0000:00:1d.0: reg 20 io port: [0x2060-0x207f]
[    0.171787] pci 0000:00:1d.1: reg 20 io port: [0x2040-0x205f]
[    0.171839] pci 0000:00:1d.2: reg 20 io port: [0x2020-0x203f]
[    0.171898] pci 0000:00:1d.7: reg 10 32bit mmio: [0x52225000-0x522253ff]
[    0.171953] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.171958] pci 0000:00:1d.7: PME# disabled
[    0.172096] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.172100] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.172105] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.172159] pci 0000:00:1f.2: reg 10 io port: [0x2138-0x213f]
[    0.172166] pci 0000:00:1f.2: reg 14 io port: [0x214c-0x214f]
[    0.172172] pci 0000:00:1f.2: reg 18 io port: [0x2130-0x2137]
[    0.172179] pci 0000:00:1f.2: reg 1c io port: [0x2148-0x214b]
[    0.172186] pci 0000:00:1f.2: reg 20 io port: [0x2110-0x211f]
[    0.172192] pci 0000:00:1f.2: reg 24 io port: [0x2100-0x210f]
[    0.172215] pci 0000:00:1f.2: PME# supported from D3hot
[    0.172219] pci 0000:00:1f.2: PME# disabled
[    0.172240] pci 0000:00:1f.3: reg 10 32bit mmio: [0x52225800-0x522258ff]
[    0.172260] pci 0000:00:1f.3: reg 20 io port: [0x2000-0x201f]
[    0.172302] pci 0000:00:1f.5: reg 10 io port: [0x2128-0x212f]
[    0.172309] pci 0000:00:1f.5: reg 14 io port: [0x2144-0x2147]
[    0.172315] pci 0000:00:1f.5: reg 18 io port: [0x2120-0x2127]
[    0.172322] pci 0000:00:1f.5: reg 1c io port: [0x2140-0x2143]
[    0.172329] pci 0000:00:1f.5: reg 20 io port: [0x20f0-0x20ff]
[    0.172335] pci 0000:00:1f.5: reg 24 io port: [0x20e0-0x20ef]
[    0.172358] pci 0000:00:1f.5: PME# supported from D3hot
[    0.172362] pci 0000:00:1f.5: PME# disabled
[    0.172400] pci 0000:01:00.0: reg 10 32bit mmio: [0x51000000-0x51ffffff]
[    0.172410] pci 0000:01:00.0: reg 14 64bit mmio: [0x40000000-0x4fffffff]
[    0.172420] pci 0000:01:00.0: reg 1c 64bit mmio: [0x50000000-0x50ffffff]
[    0.172430] pci 0000:01:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    0.172498] pci 0000:00:01.0: bridge 32bit mmio: [0x50000000-0x51ffffff]
[    0.172503] pci 0000:00:01.0: bridge 64bit mmio pref: [0x40000000-0x4fffffff]
[    0.172552] pci 0000:00:1c.0: bridge 32bit mmio: [0x52300000-0x523fffff]
[    0.172605] pci 0000:03:00.0: reg 10 io port: [0x1018-0x101f]
[    0.172614] pci 0000:03:00.0: reg 14 io port: [0x1024-0x1027]
[    0.172623] pci 0000:03:00.0: reg 18 io port: [0x1010-0x1017]
[    0.172632] pci 0000:03:00.0: reg 1c io port: [0x1020-0x1023]
[    0.172641] pci 0000:03:00.0: reg 20 io port: [0x1000-0x100f]
[    0.172650] pci 0000:03:00.0: reg 24 32bit mmio: [0x52100000-0x521001ff]
[    0.172694] pci 0000:03:00.0: supports D1
[    0.172696] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.172702] pci 0000:03:00.0: PME# disabled
[    0.172755] pci 0000:00:1c.1: bridge io port: [0x1000-0x1fff]
[    0.172760] pci 0000:00:1c.1: bridge 32bit mmio: [0x52100000-0x521fffff]
[    0.172810] pci 0000:00:1c.2: bridge 32bit mmio: [0x52400000-0x524fffff]
[    0.172861] pci 0000:00:1c.3: bridge 32bit mmio: [0x52500000-0x525fffff]
[    0.172912] pci 0000:00:1c.4: bridge 32bit mmio: [0x52600000-0x526fffff]
[    0.172956] pci 0000:07:02.0: reg 10 32bit mmio: [0x52000000-0x52007fff]
[    0.173043] pci 0000:07:03.0: reg 10 32bit mmio: [0x5200c000-0x5200c7ff]
[    0.173051] pci 0000:07:03.0: reg 14 32bit mmio: [0x52008000-0x5200bfff]
[    0.173098] pci 0000:07:03.0: supports D1 D2
[    0.173101] pci 0000:07:03.0: PME# supported from D0 D1 D2 D3hot
[    0.173106] pci 0000:07:03.0: PME# disabled
[    0.173152] pci 0000:00:1e.0: transparent bridge
[    0.173159] pci 0000:00:1e.0: bridge 32bit mmio: [0x52000000-0x520fffff]
[    0.173194] pci_bus 0000:00: on NUMA node 0
[    0.173198] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.173437] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.173631] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.173699] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.173766] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.173833] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.173900] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.179431] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.179540] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.179646] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.179752] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.179857] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12)
[    0.179962] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.180076] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[    0.180180] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.180374] SCSI subsystem initialized
[    0.180395] libata version 3.00 loaded.
[    0.180395] usbcore: registered new interface driver usbfs
[    0.180395] usbcore: registered new interface driver hub
[    0.180395] usbcore: registered new device driver usb
[    0.180395] ACPI: WMI: Mapper loaded
[    0.180395] PCI: Using ACPI for IRQ routing
[    0.192013] Bluetooth: Core ver 2.15
[    0.192035] NET: Registered protocol family 31
[    0.192035] Bluetooth: HCI device and connection manager initialized
[    0.192035] Bluetooth: HCI socket layer initialized
[    0.192035] NetLabel: Initializing
[    0.192035] NetLabel:  domain hash size = 128
[    0.192035] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.192055] NetLabel:  unlabeled traffic allowed by default
[    0.192099] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.192108] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.208052] pnp: PnP ACPI init
[    0.208067] ACPI: bus type pnp registered
[    0.211019] pnp: PnP ACPI: found 12 devices
[    0.211023] ACPI: ACPI bus type pnp unregistered
[    0.211027] PnPBIOS: Disabled by ACPI PNP
[    0.211038] system 00:01: iomem range 0xf0000000-0xf7ffffff has been reserved
[    0.211042] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[    0.211045] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.211048] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.211052] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.211055] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.211059] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.211062] system 00:01: iomem range 0xfed45000-0xfed99fff has been reserved
[    0.211066] system 00:01: iomem range 0xc0000-0xdffff could not be reserved
[    0.211069] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[    0.211077] system 00:06: ioport range 0x500-0x53f has been reserved
[    0.211081] system 00:06: ioport range 0x400-0x47f has been reserved
[    0.211084] system 00:06: ioport range 0x680-0x6ff has been reserved
[    0.245761] AppArmor: AppArmor Filesystem Enabled
[    0.245783] pci 0000:01:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff]
[    0.245879] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0x50000000-0x4fffffff]
[    0.245883] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.245885] pci 0000:00:01.0:   IO window: disabled
[    0.245890] pci 0000:00:01.0:   MEM window: 0x50000000-0x51ffffff
[    0.245894] pci 0000:00:01.0:   PREFETCH window: 0x00000040000000-0x0000004fffffff
[    0.245899] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.245902] pci 0000:00:1c.0:   IO window: disabled
[    0.245907] pci 0000:00:1c.0:   MEM window: 0x52300000-0x523fffff
[    0.245912] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.245916] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.245920] pci 0000:00:1c.1:   IO window: 0x1000-0x1fff
[    0.245925] pci 0000:00:1c.1:   MEM window: 0x52100000-0x521fffff
[    0.245930] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.245934] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.245936] pci 0000:00:1c.2:   IO window: disabled
[    0.245942] pci 0000:00:1c.2:   MEM window: 0x52400000-0x524fffff
[    0.245946] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.245951] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.245953] pci 0000:00:1c.3:   IO window: disabled
[    0.245958] pci 0000:00:1c.3:   MEM window: 0x52500000-0x525fffff
[    0.245962] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.245967] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:06
[    0.245969] pci 0000:00:1c.4:   IO window: disabled
[    0.245974] pci 0000:00:1c.4:   MEM window: 0x52600000-0x526fffff
[    0.245979] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.245983] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    0.245986] pci 0000:00:1e.0:   IO window: disabled
[    0.245991] pci 0000:00:1e.0:   MEM window: 0x52000000-0x520fffff
[    0.245995] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.246006]   alloc irq_desc for 16 on node -1
[    0.246008]   alloc kstat_irqs on node -1
[    0.246013] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.246019] pci 0000:00:01.0: setting latency timer to 64
[    0.246026]   alloc irq_desc for 17 on node -1
[    0.246028]   alloc kstat_irqs on node -1
[    0.246032] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.246038] pci 0000:00:1c.0: setting latency timer to 64
[    0.246045] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.246051] pci 0000:00:1c.1: setting latency timer to 64
[    0.246058]   alloc irq_desc for 18 on node -1
[    0.246060]   alloc kstat_irqs on node -1
[    0.246064] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.246069] pci 0000:00:1c.2: setting latency timer to 64
[    0.246076]   alloc irq_desc for 19 on node -1
[    0.246078]   alloc kstat_irqs on node -1
[    0.246082] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.246088] pci 0000:00:1c.3: setting latency timer to 64
[    0.246095] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.246101] pci 0000:00:1c.4: setting latency timer to 64
[    0.246108] pci 0000:00:1e.0: setting latency timer to 64
[    0.246112] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.246115] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.246118] pci_bus 0000:01: resource 1 mem: [0x50000000-0x51ffffff]
[    0.246121] pci_bus 0000:01: resource 2 pref mem [0x40000000-0x4fffffff]
[    0.246124] pci_bus 0000:02: resource 1 mem: [0x52300000-0x523fffff]
[    0.246127] pci_bus 0000:03: resource 0 io:  [0x1000-0x1fff]
[    0.246130] pci_bus 0000:03: resource 1 mem: [0x52100000-0x521fffff]
[    0.246133] pci_bus 0000:04: resource 1 mem: [0x52400000-0x524fffff]
[    0.246136] pci_bus 0000:05: resource 1 mem: [0x52500000-0x525fffff]
[    0.246139] pci_bus 0000:06: resource 1 mem: [0x52600000-0x526fffff]
[    0.246142] pci_bus 0000:07: resource 1 mem: [0x52000000-0x520fffff]
[    0.246145] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    0.246148] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffff]
[    0.246183] NET: Registered protocol family 2
[    0.246285] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.246627] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.247092] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.247302] TCP: Hash tables configured (established 131072 bind 65536)
[    0.247304] TCP reno registered
[    0.247381] NET: Registered protocol family 1
[    0.247443] Trying to unpack rootfs image as initramfs...
[    0.431565] Freeing initrd memory: 6636k freed
[    0.434836] cpufreq-nforce2: No nForce2 chipset.
[    0.434872] Scanning for low memory corruption every 60 seconds
[    0.434992] audit: initializing netlink socket (disabled)
[    0.435010] type=2000 audit(1254991616.432:1): initialized
[    0.444693] highmem bounce pool size: 64 pages
[    0.444698] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.446328] VFS: Disk quotas dquot_6.5.2
[    0.446393] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.446998] fuse init (API version 7.12)
[    0.447093] msgmni has been set to 1731
[    0.447328] alg: No test for stdrng (krng)
[    0.447344] io scheduler noop registered
[    0.447347] io scheduler anticipatory registered
[    0.447349] io scheduler deadline registered
[    0.447395] io scheduler cfq registered (default)
[    0.447729] pci 0000:01:00.0: Boot video device
[    0.447865]   alloc irq_desc for 24 on node -1
[    0.447868]   alloc kstat_irqs on node -1
[    0.447877] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.447885] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.447993]   alloc irq_desc for 25 on node -1
[    0.447995]   alloc kstat_irqs on node -1
[    0.448003] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.448012] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.448142]   alloc irq_desc for 26 on node -1
[    0.448144]   alloc kstat_irqs on node -1
[    0.448152] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.448160] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.448284]   alloc irq_desc for 27 on node -1
[    0.448286]   alloc kstat_irqs on node -1
[    0.448294] pcieport-driver 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.448302] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.448424]   alloc irq_desc for 28 on node -1
[    0.448426]   alloc kstat_irqs on node -1
[    0.448433] pcieport-driver 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.448442] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.448568]   alloc irq_desc for 29 on node -1
[    0.448570]   alloc kstat_irqs on node -1
[    0.448577] pcieport-driver 0000:00:1c.4: irq 29 for MSI/MSI-X
[    0.448586] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.448684] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.448815] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.448960] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.448964] ACPI: Power Button [PWRF]
[    0.449019] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.449025] ACPI: Sleep Button [SLPB]
[    0.449350] processor LNXCPU:00: registered as cooling_device0
[    0.449354] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.449473] processor LNXCPU:01: registered as cooling_device1
[    0.449478] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.450877] isapnp: Scanning for PnP cards...
[    0.500539] Switched to high resolution mode on CPU 1
[    0.504047] Switched to high resolution mode on CPU 0
[    0.803830] isapnp: No Plug & Play device found
[    0.805027] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.805127] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.805541] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.806658] brd: module loaded
[    0.807155] loop: module loaded
[    0.807227] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.807351] ata_piix 0000:00:1f.2: version 2.13
[    0.807366] ata_piix 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.807372] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.807416] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.807480] scsi0 : ata_piix
[    0.807559] scsi1 : ata_piix
[    0.807689] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2110 irq 14
[    0.807695] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2118 irq 15
[    0.807717] ata_piix 0000:00:1f.5: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.807722] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.807765] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.807812] scsi2 : ata_piix
[    0.807872] scsi3 : ata_piix
[    0.807956] ata3: SATA max UDMA/133 cmd 0x2128 ctl 0x2144 bmdma 0x20f0 irq 19
[    0.807960] ata4: SATA max UDMA/133 cmd 0x2120 ctl 0x2140 bmdma 0x20f8 irq 19
[    0.808471] pata_marvell 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.808494] pata_marvell 0000:03:00.0: setting latency timer to 64
[    0.808548] scsi4 : pata_marvell
[    0.808610] scsi5 : pata_marvell
[    0.808648] ata5: PATA max UDMA/100 cmd 0x1018 ctl 0x1024 bmdma 0x1000 irq 17
[    0.808651] ata6: DUMMY
[    0.809222] Fixed MDIO Bus: probed
[    0.809259] PPP generic driver version 2.4.2
[    0.809347] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.809365] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.809375] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.809379] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.809426] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.813348] ehci_hcd 0000:00:1a.7: debug port 1
[    0.813354] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.813367] ehci_hcd 0000:00:1a.7: irq 18, io mem 0x52225400
[    0.828033] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.828139] usb usb1: configuration #1 chosen from 1 choice
[    0.828185] hub 1-0:1.0: USB hub found
[    0.828196] hub 1-0:1.0: 4 ports detected
[    0.828283]   alloc irq_desc for 23 on node -1
[    0.828285]   alloc kstat_irqs on node -1
[    0.828290] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.828299] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.828303] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.828335] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.832236] ehci_hcd 0000:00:1d.7: debug port 1
[    0.832242] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.832255] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x52225000
[    0.844043] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.844140] usb usb2: configuration #1 chosen from 1 choice
[    0.844183] hub 2-0:1.0: USB hub found
[    0.844193] hub 2-0:1.0: 6 ports detected
[    0.844291] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.844313] uhci_hcd: USB Universal Host Controller Interface driver
[    0.844335] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.844342] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.844345] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.844384] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.844414] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000020a0
[    0.844492] usb usb3: configuration #1 chosen from 1 choice
[    0.844527] hub 3-0:1.0: USB hub found
[    0.844534] hub 3-0:1.0: 2 ports detected
[    0.844583]   alloc irq_desc for 21 on node -1
[    0.844585]   alloc kstat_irqs on node -1
[    0.844590] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.844596] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.844599] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.844632] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.844661] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00002080
[    0.844738] usb usb4: configuration #1 chosen from 1 choice
[    0.844768] hub 4-0:1.0: USB hub found
[    0.844774] hub 4-0:1.0: 2 ports detected
[    0.844824] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.844831] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.844835] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.844867] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.844889] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00002060
[    0.844968] usb usb5: configuration #1 chosen from 1 choice
[    0.844999] hub 5-0:1.0: USB hub found
[    0.845005] hub 5-0:1.0: 2 ports detected
[    0.845051] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.845057] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.845060] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.845094] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.845116] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00002040
[    0.845195] usb usb6: configuration #1 chosen from 1 choice
[    0.845230] hub 6-0:1.0: USB hub found
[    0.845237] hub 6-0:1.0: 2 ports detected
[    0.845282] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.845288] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.845291] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.845323] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.845345] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002020
[    0.845425] usb usb7: configuration #1 chosen from 1 choice
[    0.845454] hub 7-0:1.0: USB hub found
[    0.845461] hub 7-0:1.0: 2 ports detected
[    0.845575] PNP: No PS/2 controller found. Probing ports directly.
[    0.848406] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.848412] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.848472] mice: PS/2 mouse device common for all mice
[    0.848564] rtc_cmos 00:03: RTC can wake from S4
[    0.848601] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.848625] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.848730] device-mapper: uevent: version 1.0.3
[    0.848849] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.848925] device-mapper: multipath: version 1.1.0 loaded
[    0.848927] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.849051] EISA: Probing bus 0 at eisa.0
[    0.849056] Cannot allocate resource for EISA slot 1
[    0.849058] Cannot allocate resource for EISA slot 2
[    0.849078] EISA: Detected 0 cards.
[    0.849168] cpuidle: using governor ladder
[    0.849170] cpuidle: using governor menu
[    0.849703] TCP cubic registered
[    0.849871] NET: Registered protocol family 10
[    0.850372] lo: Disabled Privacy Extensions
[    0.850752] NET: Registered protocol family 17
[    0.850771] Bluetooth: L2CAP ver 2.13
[    0.850773] Bluetooth: L2CAP socket layer initialized
[    0.850776] Bluetooth: SCO (Voice Link) ver 0.6
[    0.850778] Bluetooth: SCO socket layer initialized
[    0.850808] Bluetooth: RFCOMM TTY layer initialized
[    0.850811] Bluetooth: RFCOMM socket layer initialized
[    0.850813] Bluetooth: RFCOMM ver 1.11
[    0.851118] Using IPI No-Shortcut mode
[    0.851185] PM: Resume from disk failed.
[    0.851198] registered taskstats version 1
[    0.851346]   Magic number: 13:706:775
[    0.851350] misc psaux: hash matches
[    0.851371] misc fuse: hash matches
[    0.851410] rtc_cmos 00:03: setting system clock to 2009-10-08 08:46:57 UTC (1254991617)
[    0.851414] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.851416] EDD information not available.
[    0.996576] ata5.01: ATA-7: HDS728080PLAT20, PF2OA21B, max UDMA/133
[    0.996581] ata5.01: 160836480 sectors, multi 16: LBA48 
[    1.020605] ata5.01: configured for UDMA/100
[    1.134680] ata3: SATA link down (SStatus 0 SControl 300)
[    1.145350] ata4: SATA link down (SStatus 0 SControl 300)
[    1.396056] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    1.466773] ata2.00: SATA link down (SStatus 0 SControl 300)
[    1.466782] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.573003] usb 5-1: configuration #1 chosen from 1 choice
[    1.612083] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.612099] ata1.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.628217] ata1.00: ATAPI: PIONEER DVD-RW  DVR-212D, 1.21, max UDMA/66
[    1.629263] ata1.01: ATA-7: Maxtor 7L250S0, BACE1G20, max UDMA/133
[    1.629268] ata1.01: 490234752 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    1.644280] ata1.00: configured for UDMA/66
[    1.661222] ata1.01: configured for UDMA/133
[    1.667864] scsi 0:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-212D 1.21 PQ: 0 ANSI: 5
[    1.691397] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.691401] Uniform CD-ROM driver Revision: 3.20
[    1.691526] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.691594] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.691701] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 7L250S0   BACE PQ: 0 ANSI: 5
[    1.691827] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.691868] sd 0:0:1:0: [sda] 490234752 512-byte logical blocks: (251 GB/233 GiB)
[    1.691920] sd 0:0:1:0: [sda] Write Protect is off
[    1.691923] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.691951] sd 0:0:1:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.692085]  sda:
[    1.692261] scsi 4:0:1:0: Direct-Access     ATA      HDS728080PLAT20  PF2O PQ: 0 ANSI: 5
[    1.692365] sd 4:0:1:0: [sdb] 160836480 512-byte logical blocks: (82.3 GB/76.6 GiB)
[    1.692375] sd 4:0:1:0: Attached scsi generic sg2 type 0
[    1.692418] sd 4:0:1:0: [sdb] Write Protect is off
[    1.692421] sd 4:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.692449] sd 4:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.692589]  sdb: sdb1 sdb2 sdb3
[    1.699359] sd 4:0:1:0: [sdb] Attached SCSI disk
[    1.707808]  sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    1.750553] sd 0:0:1:0: [sda] Attached SCSI disk
[    1.750570] Freeing unused kernel memory: 540k freed
[    1.750882] Write protecting the kernel text: 4548k
[    1.750933] Write protecting the kernel read-only data: 1828k
[    1.816130] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    1.958460] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    1.958463] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    1.958509]   alloc irq_desc for 20 on node -1
[    1.958511]   alloc kstat_irqs on node -1
[    1.958519] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.958526] e1000e 0000:00:19.0: pci_enable_pcie_error_reporting failed 0xfffffffb
[    1.958531] e1000e 0000:00:19.0: setting latency timer to 64
[    1.958604]   alloc irq_desc for 30 on node -1
[    1.958606]   alloc kstat_irqs on node -1
[    1.958616] e1000e 0000:00:19.0: irq 30 for MSI/MSI-X
[    2.050755] ohci1394 0000:07:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.056756] usbcore: registered new interface driver hiddev
[    2.069186] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input3
[    2.069275] generic-usb 0003:046D:C03E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1/input0
[    2.069293] usbcore: registered new interface driver usbhid
[    2.069296] usbhid: v2.6:USB HID core driver
[    2.094151] usb 6-1: configuration #1 chosen from 1 choice
[    2.114747] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[5200c000-5200c7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.159617] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input4
[    2.159691] generic-usb 0003:1241:1603.0002: input,hidraw1: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.1-1/input0
[    2.222776] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:3c:d7:5d
[    2.222780] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.222804] 0000:00:19.0: eth0: MAC: 6, PHY: 6, PBA No: ffffff-0ff
[    2.248259] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input5
[    2.248351] generic-usb 0003:1241:1603.0003: input,hidraw2: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.1-1/input1
[    2.653871] PM: Starting manual resume from disk
[    2.653875] PM: Resume from partition 8:6
[    2.653877] PM: Checking hibernation image.
[    2.654013] PM: Resume from disk failed.
[    2.661452] REISERFS (device sdb2): found reiserfs format "3.6" with standard journal
[    2.661466] REISERFS (device sdb2): using ordered data mode
[    2.669884] REISERFS (device sdb2): journal params: device sdb2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    2.670161] REISERFS (device sdb2): checking transaction log (sdb2)
[    3.384346] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090270001bf3e95]
[   12.940559] REISERFS (device sdb2): replayed 773 transactions in 10 seconds
[   12.946979] REISERFS (device sdb2): Using r5 hash to sort names
[   13.842140] type=1505 audit(1254991630.488:2): operation="profile_load" pid=395 name=/usr/share/gdm/guest-session/Xsession
[   14.018916] type=1505 audit(1254991630.664:3): operation="profile_load" pid=396 name=/sbin/dhclient3
[   14.018970] type=1505 audit(1254991630.664:4): operation="profile_load" pid=396 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.019010] type=1505 audit(1254991630.664:5): operation="profile_load" pid=396 name=/usr/lib/connman/scripts/dhclient-script
[   14.084752] type=1505 audit(1254991630.732:6): operation="profile_load" pid=397 name=/usr/bin/evince
[   14.095563] type=1505 audit(1254991630.740:7): operation="profile_load" pid=397 name=/usr/bin/evince-previewer
[   14.102008] type=1505 audit(1254991630.748:8): operation="profile_load" pid=397 name=/usr/bin/evince-thumbnailer
[   14.119805] type=1505 audit(1254991630.764:9): operation="profile_load" pid=399 name=/usr/lib/cups/backend/cups-pdf
[   14.120781] type=1505 audit(1254991630.768:10): operation="profile_load" pid=399 name=/usr/sbin/cupsd
[   14.123731] type=1505 audit(1254991630.768:11): operation="profile_load" pid=400 name=/usr/sbin/tcpdump
[   14.932553] udev: starting version 147
[   15.908453] Linux agpgart interface v0.103
[   16.519518] nvidia: module license 'NVIDIA' taints kernel.
[   16.519523] Disabling lock debugging due to kernel taint
[   16.773130] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.773141] nvidia 0000:01:00.0: setting latency timer to 64
[   16.773272] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[   16.986073] heci: module is from the staging directory, the quality is unknown, you have been warned.
[   16.987488] heci: Intel(R) Management Engine Interface - version 5.0.0.31
[   16.987491] heci: Copyright (c) 2003 - 2008 Intel Corporation.
[   16.987528] heci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.987533] heci 0000:00:03.0: setting latency timer to 64
[   16.987718] heci: link layer has been established.
[   17.035271] parport_pc 00:08: reported by Plug and Play ACPI
[   17.035353] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   17.072130] cfg80211: Calling CRDA to update world regulatory domain
[   17.092486] heci driver initialization successful.
[   17.301718] lp0: using parport0 (interrupt-driven).
[   17.303948] ppdev: user-space parallel port driver
[   17.317358] cfg80211: World regulatory domain updated:
[   17.317363]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.317368]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.317373]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.317377]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.317382]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.317386]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.726156] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.858171] rt61pci 0000:07:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.081916] Adding 1132540k swap on /dev/sdb1.  Priority:-1 extents:1 across:1132540k 
[   18.379422] phy0: Selected rate control algorithm 'minstrel'
[   18.380280] Registered led device: rt61pci-phy0::radio
[   18.380300] Registered led device: rt61pci-phy0::assoc
[   18.672217]   alloc irq_desc for 22 on node -1
[   18.672220]   alloc kstat_irqs on node -1
[   18.672228] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.672261] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.899217] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   18.988786] REISERFS (device sdb2): Removing [5749 1337 0x0 SD]..done
[   18.988938] REISERFS (device sdb2): Removing [5749 1335 0x0 SD]..done
[   18.989009] REISERFS (device sdb2): Removing [5749 1331 0x0 SD]..done
[   18.989085] REISERFS (device sdb2): Removing [5749 1329 0x0 SD]..done
[   18.989148] REISERFS (device sdb2): Removing [5749 1327 0x0 SD]..done
[   18.989187] REISERFS (device sdb2): Removing [5749 1326 0x0 SD]..done
[   18.989237] REISERFS (device sdb2): Removing [5749 1320 0x0 SD]..done
[   18.989539] REISERFS (device sdb2): Removing [216 1274 0x0 SD]..done
[   18.989624] REISERFS (device sdb2): There were 8 uncompleted unlinks/truncates. Completed
[   19.028748] EXT4-fs (sdb3): barriers enabled
[   19.047267] kjournald2 starting: pid 810, dev sdb3:8, commit interval 5 seconds
[   19.047502] EXT4-fs (sdb3): internal journal on sdb3:8
[   19.047507] EXT4-fs (sdb3): delayed allocation enabled
[   19.047511] EXT4-fs: file extents enabled
[   19.048179] EXT4-fs: mballoc enabled
[   19.048195] EXT4-fs (sdb3): mounted filesystem with ordered data mode
[   19.108444] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   19.108533] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   19.108595] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   19.108658] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   19.108723] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   19.108785] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   19.108848] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   19.150756] REISERFS (device sda7): found reiserfs format "3.6" with standard journal
[   19.150787] REISERFS (device sda7): using ordered data mode
[   19.151325] REISERFS (device sda7): journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   19.151600] REISERFS (device sda7): checking transaction log (sda7)
[   19.443671] REISERFS (device sda7): Using r5 hash to sort names
[   21.864944] type=1505 audit(1255002438.512:12): operation="profile_replace" pid=922 name=/usr/share/gdm/guest-session/Xsession
[   22.033328] type=1505 audit(1255002438.681:13): operation="profile_replace" pid=923 name=/sbin/dhclient3
[   22.033497] type=1505 audit(1255002438.681:14): operation="profile_replace" pid=923 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   22.033597] type=1505 audit(1255002438.681:15): operation="profile_replace" pid=923 name=/usr/lib/connman/scripts/dhclient-script
[   22.037958] type=1505 audit(1255002438.685:16): operation="profile_replace" pid=924 name=/usr/bin/evince
[   22.048889] type=1505 audit(1255002438.697:17): operation="profile_replace" pid=924 name=/usr/bin/evince-previewer
[   22.055339] type=1505 audit(1255002438.701:18): operation="profile_replace" pid=924 name=/usr/bin/evince-thumbnailer
[   22.064669] type=1505 audit(1255002438.713:19): operation="profile_replace" pid=926 name=/usr/lib/cups/backend/cups-pdf
[   22.065605] type=1505 audit(1255002438.713:20): operation="profile_replace" pid=926 name=/usr/sbin/cupsd
[   22.068330] type=1505 audit(1255002438.713:21): operation="profile_replace" pid=927 name=/usr/sbin/tcpdump
[   22.976744] e1000e 0000:00:19.0: irq 30 for MSI/MSI-X
[   23.033144] e1000e 0000:00:19.0: irq 30 for MSI/MSI-X
[   23.033420] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.093024] rt61pci 0000:07:02.0: firmware: requesting rt2561s.bin
[   23.169615] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.421429] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   24.421433] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   24.421659] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   35.328453] eth0: no IPv6 routers present
[   35.417230] CPU0 attaching NULL sched-domain.
[   35.417236] CPU1 attaching NULL sched-domain.
[   35.428097] CPU0 attaching sched-domain:
[   35.428102]  domain 0: span 0-1 level MC
[   35.428107]   groups: 0 1
[   35.428114]   domain 1: span 0-1 level CPU
[   35.428119]    groups: 0-1 (__cpu_power = 2048)
[   35.428127] CPU1 attaching sched-domain:
[   35.428131]  domain 0: span 0-1 level MC
[   35.428135]   groups: 1 0
[   35.428142]   domain 1: span 0-1 level CPU
[   35.428146]    groups: 0-1 (__cpu_power = 2048)
[   36.330946] CPU0 attaching NULL sched-domain.
[   36.330952] CPU1 attaching NULL sched-domain.
[   36.344642] CPU0 attaching sched-domain:
[   36.344648]  domain 0: span 0-1 level MC
[   36.344653]   groups: 0 1
[   36.344662] CPU1 attaching sched-domain:
[   36.344666]  domain 0: span 0-1 level MC
[   36.344670]   groups: 1 0
```

Para leer con más comodidad la salida de dmesg
se puede hacer un "dump" (volcado) hacia un archivo
de texto, con
```
dmesg > mensajes.txt
```

y nos aparecerá el archivo de texto en nuestra /home.

---

### Post by z37a on 2009-10-08
> **oktubrer said:**
> Corrijo un poco, en realidad con ctrl+z no lo mandás al background, sino que el proceso se detiene y queda "en pausa".
Para mandarlo al background, luego de pausarlo con ctrl+z se usa *bg*(de BackGround).  Si lo querés volver a ejecutar en primer plano, ahi si con *fg* como habían dicho (de ForeGround).
Otra forma de iniciar directamente un proceso en segundo plano es agregandole & al final.
De esta forma se pueden ejecutar varios procesos en paralelo.  Con el comando *jobs* se muestran todos los que se están ejecutando en esa terimnal con el estado correspondiente.
Usando fg + el número de tarea que muestra jobs, se puede traer cualquiera a primer plano.  Para intercambiar, de nuevo ctrl+z para pausarlo y bg para pasarlo a segundo plano.

Mejor dicho imposible!!!!

---

### Post by pablo.s on 2009-10-09
[SIZE=3][B]      ---   cat   ---
Concatenate files[/B][/SIZE]

El comando cat hace un [concatenado]("http://www.wordreference.com/definicion/concatenar")
de archivos y los presenta en pantalla
por salida directa. Se puede utilizar el
operador > para combinar varios archivos
en uno solo o el operador >> para añadir
archivos a un archivo preexistente.
Cuando añade a una archivo preexistente
se debe utilizar la combinación de teclas
CTRL+D para finalizar la sesión.

Ejemplos:

```
cat .bashrc
```

Nos muestra el contenido del archivo
.bashrc en pantalla.

```
cat tesis1 tesis2 tesis3 > tesistotal
```

Nos combina los archivos tesis1, tesis2
y tesis3 al archivo tesistotal.

---

### Post by aledruetta on 2009-10-09
> **pablo.s said:**
> [SIZE=3][B]      ---   cat   ---
Concatenate files[/B][/SIZE]


Y, si el archivo no existe, lo crea:
```
cat > nuevo.txt
```el cursor pasa a la línea inferior y es posible añadir texto al contenido del archivo. Para finalizar CTRL+D, y tendremos un archivo con el nombre "nuevo.txt" en el directorio actual, y con el texto que escribimos en su interior.

Si quiero agregar algo al archivo:
```
cat >> nuevo.txt
```

Ahora quiero ver cómo quedó:
```
cat nuevo.txt
```

---

### Post by pablo.s on 2009-10-09
Indice de comandos
publicados esta semana:

[Estructura de directorios]("http://ubuntuforums.org/showpost.php?p=8057648&postcount=2") por Sleeping Beauty
Comando [df]("http://ubuntuforums.org/showpost.php?p=8057439&postcount=1") por pablo.s
Comandos [cd - ls]("http://ubuntuforums.org/showpost.php?p=8058308&postcount=5") por Staar
Comando [chmod]("http://ubuntuforums.org/showpost.php?p=8064006&postcount=20") por pablo.s
Comando [rm]("http://ubuntuforums.org/showpost.php?p=8064384&postcount=21") por santiagoward2000
Comando [watch]("http://ubuntuforums.org/showpost.php?p=8066929&postcount=25") por z37a
Comando [passwd]("http://ubuntuforums.org/showpost.php?p=8069554&postcount=34") por pablo.s
Explicativo de [interrupción de señales]("http://ubuntuforums.org/showpost.php?p=8071588&postcount=36") por faktorqm
Comando [dmesg]("http://ubuntuforums.org/showpost.php?p=8071661&postcount=37") por pablo.s
Comando [cat]("http://ubuntuforums.org/showpost.php?p=8076797&postcount=39") por pablo.s

A seguir posteando!

---

### Post by staar on 2009-10-09
[SIZE="4"]**killall**[/SIZE]

el comando *killall* (mataratodos) envía una determinada [señal]("http://ubuntuforums.org/showpost.php?p=8071588&postcount=36") a todos los procesos que estén corriendo el comando que se le especifica, si no se le indica ninguna señal, envía SIGTERM. es "primo hermano" del comando *kill* con la diferencia que este mata por nombre y el otro por el PID (el identificador del proceso). su uso común, es para matar procesos (por la razón que fuere), por ejemplo, si quiero matar todas las instancias de opera hago```

killall opera
``` si lo quiero matar, pero ya, le mando la señal SIGKILL con ```

killall -9 opera
``` o ```

killall -KILL opera
``` también puede usarse para matar solo los procesos del usuario especificado ```

killall -u *nombredeusuario*
```

saludos

---

### Post by oktubrer on 2009-10-09
Comandos [SIZE="4"]pgrep[/SIZE] y [SIZE="4"]pkill[/SIZE]
pgrep es una variante del comando grep (para mi uno de los fundamentales, pero tan "grande" que no me animo a postearlo yo) que busca en los procesos en ejecución la cadena de texto que le pasemos como parámetro y nos devuelve el PID (Id del proceso)
```
rodrigo@Finisterre:~$ pgrep kwin
1608

```

Si no nos acordamos el nombre completo del proceso no importa, porque busca la ocurrencia de la cadena que le pasemos, así sea una letra.
Si por ejemplo buscamos todos los procesos que contengan la letra x en el nombre:
```
rodrigo@Finisterre:~$ pgrep x
24
1483
1765
1770

```
En estos casos, es útil agregarle el parámetro "-l" para que agregue el nombre del proceso al listado:
```
rodrigo@Finisterre:~$ pgrep -l x
24 ata_aux
1483 x-session-manag
1765 kmix
1770 obex-data-serve

```

Esto puede ser útil para saber si determinado proceso u aplicación está en ejecución o no, por algún eventual (y raro :P) cuelgue, o para obtener el pid de algún proceso en particular que querramos matar por cualquier motivo con el comando KILL.

El primo de este comando es PKILL.
pkill es similar a pgrep, busca el texto que le pasemos como parámetro entre los procesos en ejecución, pero directamente lo mata.  Por este motivo recomiendo siempre pasarle como parámetro el nombre entero del proceso a eliminar, para evitar dolores de cabeza.  Por ejemplo en el caso anterior:
```
pkill x
``` mataría los 4 procesos listados arriba.

Vale aclarar que si el owner del proceso no es el usuario, el comando pkill no tiene autoridad suficiente para matarlo (a menos que se ejecute con sudo adelante).  
Recibe también como parámetro el tipo de señal con que se quiere matar al proceso, tal como el comando killall explicado anteriormente.  Los diferentes tipos de señales creo que están más asociadas al comando kill, lo dejo también para alguien más mentado en la materia.

Hay que tener en cuenta que al matar procesos por nombre, si hay dos o más procesos de la misma aplicación, o que comparten la misma cadena de caracteres que pasamos como parámetro, pkill no discrimina:
```
rodrigo@Finisterre:~$ pgrep -l kat
4469 kate
4470 kate
rodrigo@Finisterre:~$ pkill kat
rodrigo@Finisterre:~$ pgrep -l kat
rodrigo@Finisterre:~$

```
Y los mata bien muertos.

---

### Post by josecuervo86 on 2009-10-09
> **oktubrer said:**
> 
Y los mata bien muertos.

Jaja, muy buenos esos comandos oktuber!

---

### Post by pablo.s on 2009-10-10
[SIZE=3]**Utilización de Pipelines (tuberías)**[/SIZE]

Un pipeline se podría definir como un conjunto 
de comandos encadenados por las salidas o 
entradas que entregan de forma directa al 
siguiente comando. Los comandos se encadenan 
con una "tuberia" (pipe) cuyo símbolo es | 
[I](en algunos teclados aparece presionando
Alt Gr+ 1, en otros teclados aparece junto a la 
barra invertida).
[/I]
**Por ejemplo:**

```
dmesg | less
```

permite ver el contenido de dmesg en la ventana,
pero deslizando el contenido para ver los detalles.

```
ls -al /bin | less
```

Nos hace una lista de los archivos del directorio /bin
con sus atributos, propietarios, fecha de creación y
modificación, tamaño, todo esto de forma que podamos
deslizar la lista de arriba a abajo.

[B][COLOR=Gray][COLOR=Black]NOTA:[/COLOR] Este tema se puede ampliar y los ejemplos son
muy básicos. Lo redacté de esta forma porque para
profundizar el tema hacen falta comandos que no han 
sido explicados y pueden confundir con su uso, como
es el caso de egrep, sed, echo, lspci, y otros tantos que
hacen de pipes una herramienta esencial.[/COLOR][/B]

---

### Post by pablo.s on 2009-10-11
[SIZE=3][B]        ---   NANO   ---
Nano's ANOther editor[/B][/SIZE]

El comando nano es un programa editor 
de texto. Pequeño y sencillo, su nombre 
completo es GNU nano y está presente 
en todas las distribuciones GNU/Linux 
porque para los usuarios novatos se hace
incomprensible el modo de uso del editor vi.

Por lo general se suele llamar junto al archivo
que necesitamos editar. Por ejemplo si escribimos

```
nano .bashrc
```aparecerá el editor con esta apariencia:

[IMG]http://i.imagehost.org/0695/nano.png[/IMG]

En la parte inferior de la ventana podemos ver
que hay una barra con atajos de teclado.
Los que hemos de utilizar con más frecuencia
son CTRL+O (para guardar el archivo), CTRL+K (para
cortar texto) y CTRL+X (para salir).
Si necesitamos editar el texto nos movemos con
las teclas de dirección hasta el punto que 
necesitamos agregar o editar.

Tiene parámetros interesantes, como por ejemplo

```
nano **-B** .bashrc
```que hace un backup del archivo a editar, agregandole
a la versión original un ñuflo antes del nombre.

 ```
nano **-i** ejemplo.py
```que nos hace un autoindentado de las lineas, conservando
el mismo espaciado y tabulación que la linea precendente.

```
nano **-m**  /etc/X11/xorg.conf
```nos habilita el uso del mouse, en caso de que no nos
interese manejar los atajos de teclado.

---

### Post by Mustaine666 on 2009-10-11
> **pablo.s said:**
> 
Para leer con más comodidad la salida de dmesg
se puede hacer un "dump" (volcado) hacia un archivo
de texto, con
```
dmesg > mensajes.txt
```

y nos aparecerá el archivo de texto en nuestra /home.

se puede tambien volcar la informacion de sudo ifconfig .. como se hace con el comando dmesg?

---

### Post by santiagoward2000 on 2009-10-11
> **Mustaine666 said:**
> se puede tambien volcar la informacion de sudo ifconfig .. como se hace con el comando dmesg?

Sí, hacés:
```
sudo ifconfig > archivo_salida
``` y te va a aparecer un **archivo_salida** (o el nombre que le quieras poner) en tu home.
Saludos!

---

### Post by Mustaine666 on 2009-10-11
[CENTER][FONT="Tahoma"]Ahora me toca a mi! .. para mi este es un comando interesante.. capaz que no fundamental..pero bueno..

[B][FONT="Arial Black"][SIZE="4"]Comando --Locate--
[Localizar][/SIZE][/FONT][/B]

Este comando sirve para localizar la ruta de un archivo en linux para saber dónde está guardado. Puede ser más rápido que find ya que almacena las rutas en una base de datos. Es especialmente útil cuando se conoce el nombre del programa pero no se recuerda la ruta.

Es necesario actualizar el índice con el comando updatedb para que reindexe los archivos nuevos.

Pero que es el comando **[FONT="Arial Black"][SIZE="4"]--updatedb--[/SIZE][/FONT]**
Updatedb es un comando incluido en findutils [Findutils es un paquete de GNU que ofrece utilidades básicas de búsqueda en directorios en sistemas GNU y Unix.] que se encarga de actualizar una base de datos con todos los achivos del sistema, utilizada por locate para hallar archivos rápidamente en sistemas de grandes cantidades de ficheros o incluso distintos dispositivos y sistemas de ficheros.

despues de lo teorico.. vamos a lo practico!..

```

updatedb

```

despues de esto.. ya tenemos la base de directorios actualizados!..

falta buscar!..

```

locate "nombre archivo+extension"
[dara la lista de la busqueda y directorio]

```

pero si solo se quiere mostrar una cantidad determinada de resultados hay que agregarle al final "-n[mas numero de cantidad]"

```

locate "Ejemplo.txt" -n 5  

```

como ya dije no es un comando fundamental.. pero es mi pequeño aporte![/FONT][/CENTER]

---

### Post by pablo.s on 2009-10-12
[SIZE=3][B]           ---   ps   ---
processes snapshot[/B][/SIZE]

El comando ps nos muestra un reporte de 
los procesos activos del sistema, aunque
no de forma interactiva.
La cantidad de información en el reporte
varía de acuerdo a la cantidad de parámetros
que utilicemos.

Con el parámetro [COLOR=Blue]**a**[/COLOR] nos muestra una lista de
todos los procesos.
Con el parámetro **[COLOR=Blue]f[/COLOR]** nos muestra una lista tipo
árbol con los subprocesos de cada proceso.
Con el parámetro [COLOR=Blue]**m**[/COLOR] nos muestra los hilos tras
los procesos.

Por lo general se suelen utilizar los parámetros
**[COLOR=Blue]axf[/COLOR]** o  [COLOR=Blue]**axjf**[/COLOR]. Por ejemplo:

```
pablo@raanana:~$ ps axf
  PID TTY      STAT   TIME COMMAND
    2 ?        S<     0:00 [kthreadd]
    3 ?        S<     0:00  \_ [migration/0]
    4 ?        S<     0:00  \_ [ksoftirqd/0]
    5 ?        S<     0:00  \_ [watchdog/0]
    6 ?        S<     0:00  \_ [migration/1]
    7 ?        S<     0:00  \_ [ksoftirqd/1]
    8 ?        S<     0:00  \_ [watchdog/1]
    9 ?        S<     0:00  \_ [events/0]
   10 ?        S<     0:00  \_ [events/1]
   11 ?        S<     0:00  \_ [cpuset]
   12 ?        S<     0:00  \_ [khelper]
   13 ?        S<     0:00  \_ [netns]
   14 ?        S<     0:00  \_ [async/mgr]
   15 ?        S<     0:00  \_ [kintegrityd/0]
   16 ?        S<     0:00  \_ [kintegrityd/1]
   17 ?        S<     0:00  \_ [kblockd/0]
   18 ?        S<     0:00  \_ [kblockd/1]
   19 ?        S<     0:00  \_ [kacpid]
   20 ?        S<     0:00  \_ [kacpi_notify]
   21 ?        S<     0:00  \_ [kacpi_hotplug]
   22 ?        S<     0:00  \_ [ata/0]
   23 ?        S<     0:00  \_ [ata/1]
   24 ?        S<     0:00  \_ [ata_aux]
   25 ?        S<     0:00  \_ [ksuspend_usbd]
   26 ?        S<     0:00  \_ [khubd]
   27 ?        S<     0:00  \_ [kseriod]
   28 ?        S<     0:00  \_ [kmmcd]
   29 ?        S<     0:00  \_ [bluetooth]
   30 ?        S      0:00  \_ [khungtaskd]
   31 ?        S      0:00  \_ [pdflush]
   32 ?        S      0:00  \_ [pdflush]
   33 ?        S<     0:00  \_ [kswapd0]
   34 ?        S<     0:00  \_ [aio/0]
   35 ?        S<     0:00  \_ [aio/1]
   36 ?        S<     0:00  \_ [ecryptfs-kthrea]
   37 ?        S<     0:00  \_ [crypto/0]
   38 ?        S<     0:00  \_ [crypto/1]
   42 ?        S<     0:00  \_ [scsi_eh_0]
   43 ?        S<     0:00  \_ [scsi_eh_1]
   45 ?        S<     0:00  \_ [scsi_eh_2]
   46 ?        S<     0:00  \_ [scsi_eh_3]
   49 ?        S<     0:00  \_ [scsi_eh_4]
   50 ?        S<     0:00  \_ [scsi_eh_5]
   53 ?        S<     0:00  \_ [kstriped]
   54 ?        S<     0:00  \_ [kmpathd/0]
   55 ?        S<     0:00  \_ [kmpathd/1]
   56 ?        S<     0:00  \_ [kmpath_handlerd]
   57 ?        S<     0:00  \_ [ksnapd]
   58 ?        S<     0:00  \_ [kondemand/0]
   59 ?        S<     0:00  \_ [kondemand/1]
   60 ?        S<     0:00  \_ [kconservative/0]
   61 ?        S<     0:00  \_ [kconservative/1]
   62 ?        S<     0:00  \_ [krfcommd]
  310 ?        S<     0:00  \_ [khpsbpkt]
  312 ?        S<     0:00  \_ [usbhid_resumer]
  319 ?        S<     0:00  \_ [knodemgrd_0]
  408 ?        S<     0:00  \_ [reiserfs/0]
  409 ?        S<     0:00  \_ [reiserfs/1]
  697 ?        S<     0:00  \_ [kpsmoused]
  741 ?        S<     0:01  \_ [phy0]
  775 ?        S<     0:00  \_ [hd-audio0]
  848 ?        S<     0:00  \_ [kjournald2]
    1 ?        Ss     0:01 /sbin/init
  472 ?        S      0:00 upstart-udev-bridge --daemon
  478 ?        S<s    0:00 udevd --daemon
 1182 ?        S<     0:00  \_ udevd --daemon
20131 ?        S<     0:00  \_ udevd --daemon
  890 ?        Ss     0:00 dbus-daemon --system --fork
  976 tty4     Ss+    0:00 /sbin/getty -8 38400 tty4
  980 tty5     Ss+    0:00 /sbin/getty -8 38400 tty5
  988 tty2     Ss+    0:00 /sbin/getty -8 38400 tty2
  989 tty3     Ss+    0:00 /sbin/getty -8 38400 tty3
  991 tty6     Ss+    0:00 /sbin/getty -8 38400 tty6
  992 ?        Ss     0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
  994 ?        Ss     0:00 cron
  995 ?        Ss     0:00 atd
 1016 ?        Sl     0:00 rsyslogd -c4
 1017 ?        Ss     0:00 dd if=/proc/kmsg of=/var/run/rsyslog/kmsg
 1018 ?        Ss     0:00 hald --daemon=yes
 1094 ?        S      0:00  \_ hald-runner
 1228 ?        S      0:00      \_ /usr/lib/hal/hald-addon-rfkill-killswitch
 1234 ?        S      0:00      \_ /usr/lib/hal/hald-addon-leds
 1244 ?        S      0:00      \_ /usr/lib/hal/hald-addon-cpufreq
 1248 ?        S      0:00      \_ hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
 1252 ?        S      0:00      \_ hald-addon-input: Listening on /dev/input/event13 /dev/input/event0 /dev/input/event4 
 1255 ?        S      0:01      \_ hald-addon-storage: polling /dev/sr0 (every 2 sec)
 1019 ?        Ss     0:00 gdm-binary
 1107 ?        S      0:00  \_ /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
 1133 tty7     Ss+    1:14      \_ /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-XeJ5hi/database -nolisten t
 1794 ?        S      0:00      \_ /usr/lib/gdm/gdm-session-worker
 7127 ?        Ssl    0:00          \_ gnome-session
 7212 ?        Ss     0:00              \_ /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-ses
 7264 ?        S      0:01              \_ metacity
 7266 ?        S      0:03              \_ gnome-panel
 7286 ?        S      0:02              \_ nautilus
 7291 ?        S      0:00              \_ /usr/lib/gnome-disk-utility/gdu-notification-daemon
 7319 ?        S      0:00              \_ bluetooth-applet
 7329 ?        S      0:00              \_ gnome-volume-control-applet
 7333 ?        Sl     0:00              \_ /usr/lib/evolution/2.28/evolution-alarm-notify
 7336 ?        S      0:00              \_ /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
 7337 ?        S      0:00              \_ gnome-power-manager
 7338 ?        S      0:00              \_ nm-applet --sm-disable
 7339 ?        S      0:00              \_ update-notifier --startup-delay=60
 7341 ?        S      0:00              \_ python /usr/share/system-config-printer/applet.py
 1031 ?        Ssl    0:00 /usr/sbin/console-kit-daemon
 1123 ?        Ss     0:00 avahi-daemon: running 
 1124 ?        Ss     0:00  \_ avahi-daemon: chroot helper
 1130 ?        Ssl    0:00 NetworkManager
 1238 ?        S      0:00  \_ /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-
 1132 ?        S      0:00 /usr/sbin/modem-manager
 1134 ?        Ss     0:00 /usr/sbin/sshd
 1187 ?        S      0:00 /sbin/wpa_supplicant -u -s
 1285 ?        S      0:00 /bin/sh -e /usr/bin/couchdb -a \"/etc/couchdb/default.ini\" -a \"/etc/couchdb/local.ini\" -b -
18271 ?        S      0:00  \_ sleep 5
 1465 ?        Ss     0:00 /usr/sbin/kerneloops
 1613 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session
 1663 ?        S      0:00 /usr/lib/devicekit-power/devkit-power-daemon
 1687 tty1     Ss+    0:00 /sbin/getty -8 38400 tty1
 1800 ?        SNl    0:00 /usr/lib/rtkit/rtkit-daemon
 1804 ?        S      0:00 /usr/lib/policykit-1/polkitd
 7112 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
 7215 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
 7216 ?        Ss     0:00 /bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session
 7220 ?        Ssl    0:10 /usr/bin/pulseaudio --start
 7223 ?        S      0:00  \_ /usr/lib/pulseaudio/pulse/gconf-helper
 7225 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2
 7235 ?        Ssl    0:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 7237 ?        Ss     0:00 seahorse-daemon
 7242 ?        S      0:00 /usr/lib/gvfs/gvfsd
 7247 ?        Ssl    0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/pablo/.gvfs
 7252 ?        S      0:00 /usr/lib/notify-osd/notify-osd
 7288 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19
 7294 ?        S      0:00 /usr/lib/devicekit-disks/devkit-disks-daemon
 7312 ?        S      0:00  \_ devkit-disks-daemon: polling /dev/sr0       
 7345 ?        Ss     0:00 gnome-screensaver
 7353 ?        S      0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory -
 7359 ?        S      0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.10 /org/gtk/gvfs/exec_spaw/0
 7363 ?        S      0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
 7405 ?        S      0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 7448 ?        S      0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwi
 7451 ?        S      0:00 /usr/lib/gnome-applets/gnome-keyboard-applet --oaf-activate-iid=OAFIID:GNOME_KeyboardApplet_Fa
 7516 ?        S      0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.10 /org/gtk/gvfs/exec_spaw/1
 7581 ?        S      0:00 /usr/lib/gvfs/gvfsd-metadata
 7617 ?        S      0:00 /bin/sh -e /usr/bin/couchdb -n -a \"/etc/couchdb/default.ini\" -a \"/home/pablo/.config/deskto
 7643 ?        S      0:00  \_ /bin/sh -e /usr/bin/couchdb -n -a \"/etc/couchdb/default.ini\" -a \"/home/pablo/.config/de
 7653 ?        Ss     0:00          \_ heart -pid 7644 -ht 11
 7655 ?        S      0:00 /usr/lib/indicator-session/indicator-status-service
 7657 ?        S      0:00 /usr/lib/indicator-session/indicator-users-service
 7659 ?        S      0:00 /usr/lib/indicator-session/indicator-session-service
 7805 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataSe
 7813 ?        Sl     0:00 /usr/lib/evolution/2.28/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_E
 8088 ?        Sl     3:28 /usr/lib/firefox-3.5.3/firefox
 8152 ?        S      0:00 /usr/bin/python /usr/lib/system-service/system-service-d
20143 ?        S      0:00 /usr/lib/gvfs/gvfsd-gphoto2 --spawner :1.10 /org/gtk/gvfs/exec_spaw/2
 4677 ?        Sl     0:05 /usr/bin/python /usr/bin/terminator
 4680 ?        S      0:00  \_ gnome-pty-helper
 4681 pts/0    Ss     0:00  \_ /bin/bash
 5806 pts/0    T      0:00  |   \_ top
15455 pts/0    S+     0:00  |   \_ man ps
15468 pts/0    S+     0:00  |       \_ pager -s
16361 pts/1    Ss     0:00  \_ /bin/bash
18299 pts/1    R+     0:00      \_ ps axf
```

---

### Post by aledruetta on 2009-10-12
> **Mustaine666 said:**
> [CENTER][FONT=Tahoma][B][FONT=Arial Black][SIZE=4]Comando --Locate--
[Localizar][/SIZE][/FONT][/B]


```

updatedb

```[/FONT][/CENTER]

Muy interesante ese comando!!!

Un comentario: haciendo updatedb en terminal me tiró error. Agregándole sudo, funcionó.

---

### Post by Mustaine666 on 2009-10-12
> **aledruetta said:**
> Muy interesante ese comando!!!

Un comentario: haciendo updatedb en terminal me tiró error. Agregándole sudo, funcionó.


ami tambien..lo q pasa es q no lo postee con "sudo" por que es muy peligroso.. ya que entras como super usuario.. entonces podes estropear todo!

---

### Post by pablo.s on 2009-10-13
**[SIZE=3]                        ---   grep   ---[/SIZE]**
[SIZE=3]**General Regular Expression Parser**[/SIZE]


El comando grep trabaja con patrones
de búsqueda dentro de un archivo o
grupo de archivos. Su salida por defecto
es mostrar las lineas con el patrón que
encuentra.

Con el parámetro **-w** busca una palabra
dentro de un archivo.

```
pablo@raanana:~/Desktop$ grep -w Gibbons FlashForward.S01E03.720p.srt
- D. Gibbons es un hombre malo.
y al que hemos estado llamando D. Gibbons.
Dijo "D. Gibbons es un hombre malo".
Puede que D. Gibbons esté relacionado con ellos.
persiguiendo al Sospechoso Cero o D.Gibbons
del teléfono móvil de D. Gibbons.

```Con el parámetro **-e** busca un patrón determinado
dentro de un archivo

```
pablo@raanana:~/Desktop$ grep -e nv /var/log/Xorg.0.log
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
```Su utilidad se multiplica al ser utilizado
con pipe. Por ejemplo, quiero listar un directorio
y dentro del directorio me interesan solo los
archivos que comiencen con el patrón "py".

```
pablo@raanana:~/Desktop$ ls /var/cache/apt/archives | grep -e py
libpython2.6_2.6.3-0ubuntu1_i386.deb
libpython2.6_2.6.3-0ubuntu2_i386.deb
libpython2.6_2.6.4~rc1-0ubuntu1_i386.deb
libpython2.6_2.6.4~rc1-0ubuntu2_i386.deb
python2.6_2.6.3-0ubuntu1_i386.deb
python2.6_2.6.3-0ubuntu2_i386.deb
python2.6_2.6.4~rc1-0ubuntu1_i386.deb
python2.6_2.6.4~rc1-0ubuntu2_i386.deb
```

---

### Post by SLA_leandrin on 2009-10-13
el grep está bueno, nunca aprendí a usarlo, siempre copiando lo que hay colgado en la web, pero es un comando espectacular si uno lo sabe usar bien.

Gracias!

---

### Post by aledruetta on 2009-10-13
> **SLA_leandrin said:**
> el grep está bueno, nunca aprendí a usarlo, siempre copiando lo que hay colgado en la web, pero es un comando espectacular si uno lo sabe usar bien.

Gracias!
Creo que la dificultad más grande no es aprender a usar grep, sino saber qué buscar y dónde. Ahí es dónde a uno se le queman los papeles, al menos a mí...

---

### Post by pablo.s on 2009-10-13
> **aledruetta said:**
> Creo que la dificultad más grande no es aprender a usar grep, sino saber qué buscar y dónde.

Buen punto. Grep se destaca en busquedas
por expresiones regulares. Si tenés que buscar
en un archivo con mucha información, un log o
incluso un libro, te muestra en que línea se 
encuentra la información que querés. Incluso he
visto lineas de comandos armadas para hacer
grep en directorios de servidores y bajar archivos
(combinado con curl y wget) o para buscar en 
wikipedia por tema.
Todo depende de la creatividad y la necesidad.

---

### Post by pablo.s on 2009-10-14
[SIZE=3]**---   wget   ---**[/SIZE]
El comando GNU Wget es un
programa creado para descargar
archivos mediante protocolos HTTP,
HTTPS y FTP.
Al ser un comando no-interactivo, 
se puede llamar mediante scripts de
Bash, trabajos cron o desde la linea
de comandos.
Tiene muchas caracteristicas a pesar
de ser un programa pequeño, como
resumir descargas, hacer un mirror de
un repositorio y ejecutarse en background.

```
wget http://catb.org
```

Descarga TODO el sitio de Eric S. Raymond.

```
wget -k -r http://www.fsf.org
```

Descarga TODO el sitio de la Free Software
Foundation, con el parametro -k baja los sitios
que linkea y con el parámetro -r baja de forma 
recursiva.

```
wget -A .mov http://www.sitio-al-estilo-vimeo.com
```

Mediante el parámetro -A descarga solamente
los archivos de tipo que especificamos.

---

### Post by faktorqm on 2009-10-15
> **pablo.s said:**
> Grep se destaca en busquedas
por expresiones regulares

grep, awk y sed. explicar esos 3 comandos sin pasar por expresiones regulares es intentar explicar como es un semieje sin explicar rulemanes... ¿como hacemos?

---

### Post by aledruetta on 2009-10-15
> **faktorqm said:**
> grep, awk y sed. explicar esos 3 comandos sin pasar por expresiones regulares es intentar explicar como es un semieje sin explicar rulemanes... ¿como hacemos?

Yo diría que es como explicar la teoría de la relatividad... Es bien difícil el tema de las expresiones regulares.

---

### Post by pablo.s on 2009-10-15
> **faktorqm said:**
> grep, awk y sed. explicar esos 3 comandos sin pasar por expresiones regulares es intentar explicar como es un semieje sin explicar rulemanes... ¿como hacemos?

Probá tu mejor explicación...
De todas formas el objetivo de
este thread no se está cumpliendo,
porque esperaba bastante más
colaboración. No era literal lo de
"Un comando cada dia". Me hubiera
gustado que preguntaran más
como vos hacés, o aclarado como
vos haces.
Si tenés un ratito, posteate una
explicación sobre regexp.

---

### Post by SLA_leandrin on 2009-10-15
> **pablo.s said:**
> 
De todas formas el objetivo de
este thread no se está cumpliendo,
porque esperaba bastante más
colaboración

Pablo, aunque muchos no hayamos aportado mucho, seguramente el provecho que se le saca a este thread es grande (me cuento entre los que aprendimos algunas cosas). 
Me parecería bueno que el thread siga vivo.

Saludos.

---

### Post by pablo.s on 2009-10-16
Indice de comandos
publicados esta semana:

[killall]("http://ubuntuforums.org/showpost.php?p=8080554&postcount=42") por Staar
[pgrep y pkill]("http://ubuntuforums.org/showpost.php?p=8080801&postcount=43") por oktubrer
[[SIZE=1]Utilización de Pipelines (tuberías)[/SIZE]]("http://ubuntuforums.org/showpost.php?p=8082563&postcount=45") por pablo.s
[nano]("http://ubuntuforums.org/showpost.php?p=8087671&postcount=46") por pablo.s
[locate]("http://ubuntuforums.org/showpost.php?p=8088453&postcount=49") por Mustaine666
[ps]("http://ubuntuforums.org/showpost.php?p=8092432&postcount=50") por pablo.s
[grep]("http://ubuntuforums.org/showpost.php?p=8099711&postcount=53") por pablo.s
[wget]("http://ubuntuforums.org/showpost.php?p=8106073&postcount=57") por pablo.s

Gracias a todos los que aportaron
al crecimiento de esta Comunidad!

[SIZE=3]**---   cdparanoia   ---**[/SIZE]

El comando cdparanoia transfiere las
pistas de audio de CD a archivos sin
comprimir en nuestra /home. Por
defecto el formato es .wav.
Es lo que en la jerga se llama cd ripper.
Posee verificación de datos y es bastante
acertado en la transferencia.

No es muy complejo de utilizar y la
forma más básica es invocarlo con el
parámetro -B (que separa la salida en
pistas independientes, cada pista con
su número en el nombre)

```
cdparanoia -B
```Los simbolos de progreso nos dan una
idea del estado de la transferencia.

**:-)**[INDENT]La operación transcurre normal.
[/INDENT]**:-|**[INDENT]La operación transcurre normal, 

pero hay un salto en la lectura.
[/INDENT]**:-/**[INDENT]Leyendo un rayón.
[/INDENT]8-|[INDENT]Problemas de lectura repetidos
en el mismo lugar.
[/INDENT]:-O[INDENT]Error SCSI/ATAPI. No tiene relación
con el estado del disco.
[/INDENT]:-([INDENT]Rayonazo detectado.
[/INDENT];-([INDENT]Incapaz de corregir problema.
[/INDENT]8-X[INDENT]Error desconocido e incorregible.
[/INDENT]:^D[INDENT]Terminado.
[/INDENT][INDENT]Un espacio en blanco en la linea de
progreso significa que no hacen falta
hacer correcciones.
[/INDENT]-[INDENT]Corrección de salto fué pedida.
[/INDENT]+[INDENT]Errores de lectura.
[/INDENT]![INDENT]Hay errores incluso después de
haber correcciones. Repetidos
errores de lectura.
[/INDENT]e[INDENT]Errores de transporte corregidos.
[/INDENT]V[INDENT]Error no corregido o salto de lectura.
[/INDENT]

---

### Post by oktubrer on 2009-10-16
Pablo, como consejo, editaría el primer post del thread con el índice de comandos publicados, para no tener que buscar el índice semanal y facilitar la navegación.

Dicho lo dicho...

[SIZE="5"]**--- chown ---**[/SIZE]
[SIZE="4"]change owner[/SIZE]

El comando chown lo que hace es cambiar el owner y/o grupo de un archivo o un directorio.
Es muy util cuando quizás copiamos algún archivo o grupo de archivos utilizando sudo, o las creamos con sudo, y quedan con owner y grupo root.
```

drwxr-xr-x 2 root    root    4096 2009-10-16 20:43 prueba
```
Dicho directorio no puede ser modificado por el usuario normal, por lo que si necesitamos utilizarlo por cualquier motivo, y no es un directorio de sistema o crítico, invocando al comando chown podemos "apropiarnos" del mismo.
```

rodrigo@Finisterre:~$ sudo chown rodrigo prueba

rodrigo@Finisterre:~$ ls -ld prueba/

drwxr-xr-x 2 rodrigo root 4096 2009-10-16 20:43 prueba/
```
Se invoca con sudo ya que un usuario final no debería tener la posibilidad de cambiar el dueño de un archivo de otro usuario.

Opcionalmente, se puede cambiar también el grupo
```

rodrigo@Finisterre:~$ ls -ld prueba/

drwxr-xr-x 2 root root 4096 2009-10-16 20:43 prueba/

rodrigo@Finisterre:~$ sudo chown rodrigo:rodrigo prueba/

rodrigo@Finisterre:~$ ls -ld prueba/

drwxr-xr-x 2 rodrigo rodrigo 4096 2009-10-16 20:43 prueba/
```
separando usuario y grupo con ":"
El parámetro más util de este comando es [SIZE="3"]-R[/SIZE]
Indica Recursividad, cambiando el owner (y el grupo si fuera el caso) al directorio especificado y recursivamente a todos sus subdirectorios y archivos que contiene.

Un ejemplo práctico de su utilidad es si por ejemplo queremos usar un Home que antes pertenecía a otro usuario.  Con tan solo cambiarle owner y grupo recursivamente por el del usuario que lo va a utilizar, y modificando en el /etc/passwd la ruta del home, ya se puede comenzar a utilizar como propio heredando todos los archivos y configuraciones de aplicaciones y entorno del usuario antiguo.

---

### Post by pablo.s on 2009-10-16
> **oktubrer said:**
> Pablo, como consejo, editaría el primer post del thread con el índice de comandos publicados, para no tener que buscar el índice semanal y facilitar la navegación.

Aceptado. No obstante, como no tengo
poderes de moderador para borrar posts
de los índices semanales, voy a proceder
a tu sugerencia a partir del próximo índice,
digamos el viernes que viene, para hacerlo
de manera más prolija.

---

### Post by EnriqueK on 2009-10-16
Los comandos están explicados en las páginas **man** , pero el problema está en que al menos para mi resulta poco menos que inentendible por que faltaría algo así como una piedra de Roseta para conocer los convencionalismos , por esta razón es que me resulta mas fácil y práctico recurrir a Google para encontrar el uso particularizado de un comando, cuando lo lógico sería usar las páginas man, en resúmen, sería bueno publicar el como interpretar lo que dicen las páginas man, con un  detalle de las convenciones que allí figuran.
Por otra parte y dejando mi pequeño aporte, una de las acciones que al menos a mi mas me fastidian al usar terminal, es la de tener que introducir las rutas a los ficheros, esto se facilita con la simple acción de arrastrar al terminal el fichero y ya queda introducida su ruta absoluta entre comillas simples con el fin de evitar problemas de encontrar en el camino con carpetas con nombres compuestos.

---

### Post by oktubrer on 2009-10-16
> **EnriqueK said:**
> Los comandos están explicados en las páginas **man** , pero el problema está en que al menos para mi resulta poco menos que inentendible por que faltaría algo así como una piedra de Roseta para conocer los convencionalismos , por esta razón es que me resulta mas fácil y práctico recurrir a Google para encontrar el uso particularizado de un comando, cuando lo lógico sería usar las páginas man, en resúmen, sería bueno publicar el como interpretar lo que dicen las páginas man, con un  detalle de las convenciones que allí figuran.


Creo que si se empezaran a explicar los manuales sería un post gigante que nadie leería.  En mi humilde opinión lo mejor sería seguir como hasta ahora con algunos ejemplos prácticos y explicado con nuestras palabras, y si surgen dudas puntuales sobre algún parámetro consultarlo.

> **EnriqueK said:**
> Por otra parte y dejando mi pequeño aporte, una de las acciones que al menos a mi mas me fastidian al usar terminal, es la de tener que introducir las rutas a los ficheros, esto se facilita con la simple acción de arrastrar al terminal el fichero y ya queda introducida su ruta absoluta entre comillas simples con el fin de evitar problemas de encontrar en el camino con carpetas con nombres compuestos.

Otra opción también es aprovechar el autocompletado de la terminal (con TAB) para ir autocompletando la ruta y no tener que escribirla completa.

---

### Post by pablo.s on 2009-10-16
> **EnriqueK said:**
> Los comandos están explicados en las páginas **man**

Exacto. De hecho la mayoría de la
información que publicamos está
extractada de las paginas man, y
de otras fuentes.

> **EnriqueK said:**
> pero el problema está en que al menos para mi resulta poco menos que inentendible por que faltaría algo así como una piedra de Roseta para conocer los convencionalismos

Es algo que buscamos solventar
con este thread. La regla más
importante que puse fué que las
explicaciones de los comandos
sean tan simples que mi sobrino 
de tres años las pueda entender.
Exageraciones aparte, es un punto
fuerte. Vas a ver que no explicamos
todos los parámetros que aparecen 
en las páginas man, sino los más
básicos para que se entienda el
funcionamiento del comando.
Al descomplejizar los comandos
se ve la punta del iceberg y se abre
la puerta a la investigación por parte
de cada persona que entra al thread.
Creo que ese objetivo se cumple.

> **EnriqueK said:**
> por esta razón es que me resulta mas fácil y práctico recurrir a Google para encontrar el uso particularizado de un comando, cuando lo lógico sería usar las páginas man

Cada uno tiene su propia manera
de aprender. Supuse que una de 
las críticas que iba a tener era que
"hay mucha información en la red,
hay tutoriales en Ubuntu-Ar, para 
qué hacés un thread con algo que
se puede tener en otro sitio".
Pero en el foro hay mucho tráfico
de usuarios y usuarias que vienen
a por respuestas y las necesitan
urgente.

> **EnriqueK said:**
> en resúmen, sería bueno publicar el como interpretar lo que dicen las páginas man, con un  detalle de las convenciones que allí figuran.

Concuerdo con oktubrer en este punto.
Haríamos igual de complejo algo que
si tenés el conocimiento adecuado no
te hace falta, y si no tenés el conocimiento
no vas a adquirirlo por arte de magia.
Los usuarios novatos necesitan que
se les explique con mucha paciencia
y certeza, sobre todo.
Los posts no son cien por ciento fiables,
ya lo hemos comprobado, pero como
esta comunidad se ayuda a si misma, los
que más saben ayudan a los novatos y
los novatos ayudan a los que mas saben.

---

### Post by josecuervo86 on 2009-10-16
Yo hago un aporte, no precisamente del tipo que pidieron, pero que puede servir bastante.

[[img]http://i.imagehost.org/t/0627/comandos.jpg[/img]](http://i.imagehost.org/view/0627/comandos)

Es algo asi como un ayuda memoria, bastante util para mi

---

### Post by EnriqueK on 2009-10-16
> **pablo.s said:**
> 



Concuerdo con oktubrer en este punto.
Haríamos igual de complejo algo que
si tenés el conocimiento adecuado no
te hace falta, y si no tenés el conocimiento
no vas a adquirirlo por arte de magia.
Los usuarios novatos necesitan que
se les explique con mucha paciencia
y certeza, sobre todo.
Los posts no son cien por ciento fiables,
ya lo hemos comprobado, pero como
esta comunidad se ayuda a si misma, los
que más saben ayudan a los novatos y
los novatos ayudan a los que mas saben.
Está muy bien lo que se intenta hacer, pero el problema está en que pronto vas a requerir conocer mas, mas y mas y la única forma es el poder interpretar las páginas man, el problema está en que están llenas de convencionalismos , que son pocos y que seguramente con el tiempo luego de varios intentos de prueba y error, vas a ir descifrando pero de una manera intuitiva, lo que digo es conocer algún tuto o sitio en donde se trascriba a lenguaje humano todas esas convenciones. Una vez me estaba volviendo loco tratando de entender una man , se me ocurrió la "brillante" idea de poner en terminal  **man man** , para que , por poco me interno en el Borda.

---

### Post by pablo.s on 2009-10-16
> **EnriqueK said:**
>  Una vez me estaba volviendo loco tratando de entender una man , se me ocurrió la "brillante" idea de poner en terminal  **man man** , para que , por poco me interno en el Borda.

¿De cual comando se trataba?
Puede ser candidato a un post
explicativo.

---

### Post by EnriqueK on 2009-10-16
Estaba tratando de entender la man de mplayer y al ver que no entendía nada de nada por no conocer las convenciones. se me ocurrió poner **man man **para ver si allí ezplicaban como entender las man, para que. Pero de esto hace ya tiempo y como te comenté antes, a partir de entonces abandoné todo intento de entender las man, en su lugar uso los buscadores para encontrar algún truquillo o algo simplificado , tal como lo que se viene publicando en este thread , es una lástima que tenga que proceder de esta manera y todo por no conocer las muy pocas convenciones para interpretar las man como es debido.

---

### Post by oktubrer on 2009-10-17
No se si entraría dentro de este post o convendría abrir uno nuevo, pero propongo que vuelvas a leer el man del mplayer (o cualquiera que prefieras) y postees cuales son las convenciones que no conoces, asi vamos viendo entre todos como podemos clarificar el asunto, y que de paso sirva para el resto.

---

### Post by guillermolisi on 2009-10-17
> **EnriqueK said:**
> Estaba tratando de entender la man de mplayer y al ver que no entendía nada de nada por no conocer las convenciones. se me ocurrió poner **man man **para ver si allí ezplicaban como entender las man, para que. Pero de esto hace ya tiempo y como te comenté antes, a partir de entonces abandoné todo intento de entender las man, en su lugar uso los buscadores para encontrar algún truquillo o algo simplificado , tal como lo que se viene publicando en este thread , es una lástima que tenga que proceder de esta manera y todo por no conocer las muy pocas convenciones para interpretar las man como es debido.
Movido a un [nuevo thread en Software.]("http://ubuntuforums.org/showthread.php?t=1293613")

---

### Post by Mustaine666 on 2009-10-17
yo soy novato y hace muy poco que estoy con linux.. y sinceramente prefiero buscar los comandos aca y no en un foro cualquiera ya que estos comandos tienen un cierto respaldo de la comunidad .. 
creo a su vez que estan muy bien.. explicados.. y si por una de esas casualidades de la vida.. le erras en un comando mal escrito o lo que sea.. sabes que aca te ayudan para solucionarlo.. ami me ayudaron hasta con los conkys.. yo apoyo este post.. y quiero que siga.. pero si como lei.. que el indice de comandos sea en la primer pagina.. asi es menos engorroso buscarlo.. 
como conclusion..de este post aprendi.. y mucho.. asi q quiero que siga en pie.. y con muchos aportes!.. y ya vendra mi segundo aporte! .. apenas aprenda un comando nuevo!:KS

---

### Post by pablo.s on 2009-10-17
[SIZE=3]**---   uname   ---**[/SIZE]

El comando uname presenta
información acerca de la máquina
y el sistema operativo.

Los parámetros mas comunes son:

```
uname [COLOR=Red]-a[/COLOR]
Linux raanana 2.6.31-12-generic #41-Ubuntu SMP Wed Oct 7 18:42:46 UTC 2009 i686 GNU/Linux
```Muestra el sistema operativo, el
nombre de la máquina y la versión
del núcleo

```
uname [COLOR=Red]-o[/COLOR]
GNU/Linux
```Muestra el sistema operativo

```
uname [COLOR=Red]-r[/COLOR]
2.6.31-12-generic
```Muestra la versión del núcleo

```
uname [COLOR=Red]-v[/COLOR]
#41-Ubuntu SMP Wed Oct 7 18:42:46 UTC 2009
```Muestra datos de la compilación
del núcleo.

---

### Post by pablo.s on 2009-10-19
[SIZE=3]**---   tee   ---**[/SIZE]

El comando tee toma la salida
de datos obtenida por otro comando
y la envía tanto a la salida por pantalla
como a un volcado a archivo.
Su nombre proviene de la forma de la
letra T en inglés fonético.
Es un comando que se suele utilizar en
conjunto con los pipes. Estos últimos
van usando la salida de datos y la siguen
procesando/filtrando para llegar a un
dato en particular.

Por ejemplo, quiero hacer un listado de
mi /home pero solo de las carpetas o archivos
que contengan en su nombre una letra D
mayúscula. Ese listado a su vez quiero que
lo muestre en pantalla y lo vuelque a un
archivo de texto denominado letra_d.

```
pablo@raanana:~$ ls -l | grep D | tee letra_d
```En la pantalla me aparecerá la salida así:

```
drwxr-xr-x  2 pablo pablo   4096 2009-07-20 21:53 Azureus Downloads
drwxrwxrwx 11 pablo pablo   4096 2009-10-19 14:15 Desktop
drwxr-xr-x  2 pablo pablo   4096 2009-09-07 20:17 Documents
drwxr-xr-x  3 pablo pablo   4096 2009-08-18 10:01 Downloads
```Y en mi /home aparecerá esta misma 
salida pero en un archivo de texto, si es
que necesito imprimir la salida, postearla 
en un foro o enviarla por correo electrónico.

---

### Post by faktorqm on 2009-10-20
Una observación que me parece que vale la pena hacer sobre un modificador de tee para evitar sorpresas.

-a	Agrega la salida a un archivo existente. Si el archivo no existe lo crea.

---

### Post by aledruetta on 2009-10-20
> **faktorqm said:**
> Una observación que me parece que vale la pena hacer sobre un modificador de tee para evitar sorpresas.

-a    Agrega la salida a un archivo existente. Si el archivo no existe lo crea.

Lo probé sin la opción y crea el archivo, por más que éste no exista.

```
~$ tee --help
Uso: tee [OPCIÓN]... [FICHERO]...
Copia la entrada estándar a cada FICHERO, y también a salida estándar.

  -a, --append              añade a los FICHEROs dados, no los sobreescribe
```

---

### Post by faktorqm on 2009-10-20
> **aledruetta said:**
> Lo probé sin la opción y crea el archivo, por más que éste no exista.

```
~$ tee --help
Uso: tee [OPCIÓN]... [FICHERO]...
Copia la entrada estándar a cada FICHERO, y también a salida estándar.

  -a, --append              añade a los FICHEROs dados, no los sobreescribe
```

a ver,

```
lspci | tee nombre_de_archivo
```

es el equivalente a hacer

```
lspci > nombre_de_archivo
```

```
lspci | tee -a nombre_de_archivo
```

es el equivalente a hacer

```
lspci >> nombre_de_archivo
```

si haces tee solo, te guarda la salida de lo que estas haciendo en el nombre de archivo que especifiques, si existe, lo sobreescribe, y si no existe lo crea.

si haces tee -a, te AGREGA la salida de lo que estas haciendo en el FINAL del archivo llamado nombre de archivo que especificaste, si existe, lo agrega, y si no existe lo crea.

Es una convención puramente literaria la de "si no existe lo crea", lo vas a ver en todos los comandos y queda explicito en
todas las ayudas que leas, ya sea man o --help.

---

### Post by guillermolisi on 2009-10-21
> **faktorqm said:**
> a ver,

```
lspci | tee nombre_de_archivo
```es el equivalente a hacer

```
lspci > nombre_de_archivo
``````
lspci | tee -a nombre_de_archivo
```es el equivalente a hacer

```
lspci >> nombre_de_archivo
```si haces tee solo, te guarda la salida de lo que estas haciendo en el nombre de archivo que especifiques, si existe, lo sobreescribe, y si no existe lo crea.

si haces tee -a, te AGREGA la salida de lo que estas haciendo en el FINAL del archivo llamado nombre de archivo que especificaste, si existe, lo agrega, y si no existe lo crea.

Es una convención puramente literaria la de "si no existe lo crea", lo vas a ver en todos los comandos y queda explicito en
todas las ayudas que leas, ya sea man o --help.
La diferencia funcional mas importante que existe entre el redireccionamiento usando "> o >>" y "|" (tee) es que si necesitamos interconectar (piping) dos procesos (la salida que produce uno para que funcione como datos de entrada del segundo) es este ultimo redireccionador el indicado.

Aqui deberiamos hablar de los tres canales de intercomunicacion que existen en los sistema *nix: Standard input, Standard output & Standard error.

Los redireccionadores "> y >>" modifican el flujo de datos entre un proceso y los tres canales. Tee intercomunica procesos sin modificar el flujo entre canales.

Corrijanme si me equivoque en algo.

---

### Post by faktorqm on 2009-10-21
> **guillermolisi said:**
> La diferencia funcional mas importante que existe entre el redireccionamiento usando "> o >>" y "|" (tee) es que si necesitamos interconectar (piping) dos procesos (la salida que produce uno para que funcione como datos de entrada del segundo) es este ultimo redireccionador el indicado.

Aqui deberiamos hablar de los tres canales de intercomunicacion que existen en los sistema *nix: Standard input, Standard output & Standard error.

Los redireccionadores "> y >>" modifican el flujo de datos entre un proceso y los tres canales. Tee intercomunica procesos sin modificar el flujo entre canales.

Corrijanme si me equivoque en algo.

Si, esta bien lo que indicas, solo que yo lo omiti para no abrumarlos con muchas cosas, a algunos todavia les puede resultar un poco abstracto el tema del standard input, output y error. De hecho cuando haces un script, desde el punto de vista más purista de *nix, sólo deberías usar tee para intercomunicar, y nunca ">" o ">>". A veces anda igual, a veces no. 

El ejemplo que siempre sale es cuando quieren hacer, no se

lspci > /etc/apt/sources.list

entonces les dice que no tienen permisos de escritura, y tienden a hacer

sudo lspci > /etc/apt/sources.list

que tampoco anda. entonces, como se resuelve el problema? haciendo

lspci | sudo tee /etc/apt/sources.list

**BUSQUEN OTRO ARCHIVO PARA HACER LA PRUEBA**, lo puse de ejemplo por que es el primero que se me ocurrió.

---

### Post by guillermolisi on 2009-10-21
> **faktorqm said:**
> Si, esta bien lo que indicas, solo que yo lo omiti para no abrumarlos con muchas cosas, a algunos todavia les puede resultar un poco abstracto el tema del standard input, output y error. De hecho cuando haces un script, desde el punto de vista más purista de *nix, sólo deberías usar tee para intercomunicar, y nunca ">" o ">>". A veces anda igual, a veces no. 

El ejemplo que siempre sale es cuando quieren hacer, no se

lspci > /etc/apt/sources.list

entonces les dice que no tienen permisos de escritura, y tienden a hacer

sudo lspci > /etc/apt/sources.list

que tampoco anda. entonces, como se resuelve el problema? haciendo

lspci | sudo tee /etc/apt/sources.list

**BUSQUEN OTRO ARCHIVO PARA HACER LA PRUEBA**, lo puse de ejemplo por que es el primero que se me ocurrió.

Por ejemplo, usen
```
lspci | sudo tee /tmp/prueba_con_tee.list
```

asi no rompen la lista de repositorios !! :)

---

### Post by aledruetta on 2009-10-21
Qué bueno! Gracias a que no entendí lo que había dicho faktorqm, ahora entiendo un poco más. Y nos viene al pelo, porque es justo lo que estamos estudiando en el grupo de estudios Bash.

---

### Post by pablo.s on 2009-10-21
[SIZE=3][B]---   du   ---
disk usage[/B][/SIZE]

El comando du muestra en salida 
de pantalla un listado de cada
archivo de cada subdirectorio del
directorio donde nos encontremos
junto al tamaño en KB que ocupan
en disco.
Una aplicación para este comando
podría ser en el caso que necesitemos
ver un listado de los archivos que
hemos subido a nuestra cuenta de
UbuntuOne.

```
[513][pablo:Ubuntu One]$ du **-a**
440    ./segunda_mitad.pdf
780    ./cuarta_parte.pdf
0    ./Shared With Me
0    ./quick_primera.odt
236    ./quinta_parte.pdf
392    ./quick_tercera.odt
452    ./seg_parte.pdf
116    ./Terminus.ttf
776    ./tercera_parte.pdf
392    ./quick_segunda.odt
7940    ./video/meet.ogv
7944    ./video
216    ./literatura/cat_bazar.pdf
320    ./literatura/cripto_dos.odt
32    ./literatura/troll.odt
100    ./literatura/pdf philip k dick/La hormiga electrica.pdf
64    ./literatura/pdf philip k dick/Algunas clases de vida.pdf
52    ./literatura/pdf philip k dick/9millones_nombres.pdf
40    ./literatura/pdf philip k dick/Roog.pdf
932    ./literatura/pdf philip k dick/VALIS.pdf
44    ./literatura/pdf philip k dick/Algunas peculiaridades de los ojos.pdf
104    ./literatura/pdf philip k dick/Adios, Vincent.pdf
556    ./literatura/pdf philip k dick/Simak-Los hijos de.pdf
64    ./literatura/pdf philip k dick/Sobre manzanas marchitas.pdf
284    ./literatura/pdf philip k dick/El hombre variable.pdf
80    ./literatura/pdf philip k dick/La pequeña rebelion.pdf
104    ./literatura/pdf philip k dick/El cliente perfecto.pdf
888    ./literatura/pdf philip k dick/El hombre en el castillo.pdf
896    ./literatura/pdf philip k dick/Ojo en el cielo.pdf
764    ./literatura/pdf philip k dick/BABEL 17.pdf
796    ./literatura/pdf philip k dick/clanes de la luna alfana.pdf
512    ./literatura/pdf philip k dick/congreso futurologia.pdf
56    ./literatura/pdf philip k dick/el_principio_yehudi.pdf
80    ./literatura/pdf philip k dick/Pieza de coleccion.pdf
196    ./literatura/pdf philip k dick/La paga.pdf
824    ./literatura/pdf philip k dick/Fluyan mis lagrimas, dijo el policia.pdf
916    ./literatura/pdf philip k dick/Ir tirando.pdf
20    ./literatura/pdf philip k dick/El cuento final de todos los cuentos.pdf
868    ./literatura/pdf philip k dick/Confesiones de un artista de ******.pdf
44    ./literatura/pdf philip k dick/Sacrificio.pdf
144    ./literatura/pdf philip k dick/Cadbury el castor que fracaso.pdf
36    ./literatura/pdf philip k dick/La mente alien.pdf
9468    ./literatura/pdf philip k dick
28    ./literatura/como_pulseaudio.txt
316    ./literatura/almostperfect.pdf
1652    ./literatura/codigo 2.0-interior.pdf
728    ./literatura/in_the_begin_remix.pdf
1004    ./literatura/quicksilver.odt
1580    ./literatura/Command-Line.pdf
1296    ./literatura/Doctorow - Little Brother.pdf
328    ./literatura/cripto_tres.odt
692    ./literatura/anathem.odt
364    ./literatura/criptonomicon.odt
436    ./literatura/era_diam.odt
224    ./literatura/manual.odt
16    ./literatura/instrucciones.txt
1340    ./literatura/free_software.es.pdf
20044    ./literatura
32    ./intro.pdf
400    ./criptonomicon.odt
460    ./primera_mitad.pdf
340    ./parte1_cont.pdf
```Con el parámetro -h nos muestra en
un formato de KB, MB y GB

```
[514][pablo:Ubuntu One]$ du -ah
440K    ./segunda_mitad.pdf
780K    ./cuarta_parte.pdf
0    ./Shared With Me
0    ./quick_primera.odt
236K    ./quinta_parte.pdf
392K    ./quick_tercera.odt
452K    ./seg_parte.pdf
116K    ./Terminus.ttf
776K    ./tercera_parte.pdf
392K    ./quick_segunda.odt
7.8M    ./video/meet.ogv
7.8M    ./video
216K    ./literatura/cat_bazar.pdf
320K    ./literatura/cripto_dos.odt
32K    ./literatura/troll.odt
100K    ./literatura/pdf philip k dick/La hormiga electrica.pdf
64K    ./literatura/pdf philip k dick/Algunas clases de vida.pdf
52K    ./literatura/pdf philip k dick/9millones_nombres.pdf
40K    ./literatura/pdf philip k dick/Roog.pdf
932K    ./literatura/pdf philip k dick/VALIS.pdf
44K    ./literatura/pdf philip k dick/Algunas peculiaridades de los ojos.pdf
104K    ./literatura/pdf philip k dick/Adios, Vincent.pdf
556K    ./literatura/pdf philip k dick/Simak-Los hijos de.pdf
64K    ./literatura/pdf philip k dick/Sobre manzanas marchitas.pdf
284K    ./literatura/pdf philip k dick/El hombre variable.pdf
80K    ./literatura/pdf philip k dick/La pequeña rebelion.pdf
104K    ./literatura/pdf philip k dick/El cliente perfecto.pdf
888K    ./literatura/pdf philip k dick/El hombre en el castillo.pdf
896K    ./literatura/pdf philip k dick/Ojo en el cielo.pdf
764K    ./literatura/pdf philip k dick/BABEL 17.pdf
796K    ./literatura/pdf philip k dick/clanes de la luna alfana.pdf
512K    ./literatura/pdf philip k dick/congreso futurologia.pdf
56K    ./literatura/pdf philip k dick/el_principio_yehudi.pdf
80K    ./literatura/pdf philip k dick/Pieza de coleccion.pdf
196K    ./literatura/pdf philip k dick/La paga.pdf
824K    ./literatura/pdf philip k dick/Fluyan mis lagrimas, dijo el policia.pdf
916K    ./literatura/pdf philip k dick/Ir tirando.pdf
20K    ./literatura/pdf philip k dick/El cuento final de todos los cuentos.pdf
868K    ./literatura/pdf philip k dick/Confesiones de un artista de ******.pdf
44K    ./literatura/pdf philip k dick/Sacrificio.pdf
144K    ./literatura/pdf philip k dick/Cadbury el castor que fracaso.pdf
36K    ./literatura/pdf philip k dick/La mente alien.pdf
9.3M    ./literatura/pdf philip k dick
28K    ./literatura/como_pulseaudio.txt
316K    ./literatura/almostperfect.pdf
1.7M    ./literatura/codigo 2.0-interior.pdf
728K    ./literatura/in_the_begin_remix.pdf
1004K    ./literatura/quicksilver.odt
1.6M    ./literatura/Command-Line.pdf
1.3M    ./literatura/Doctorow - Little Brother.pdf
328K    ./literatura/cripto_tres.odt
692K    ./literatura/anathem.odt
364K    ./literatura/criptonomicon.odt
436K    ./literatura/era_diam.odt
224K    ./literatura/manual.odt
16K    ./literatura/instrucciones.txt
1.4M    ./literatura/free_software.es.pdf
20M    ./literatura
32K    ./intro.pdf
400K    ./criptonomicon.odt
460K    ./primera_mitad.pdf
340K    ./parte1_cont.pdf
```Si lo **combinamos con tee**, es posible ver en
pantalla el listado y a su vez redirigir la salida
a un volcado a archivo

```
du -ah | tee listado_ubuntuone
```Si a su vez **utilizamos grep** para separar los
archivos .ODT solamente y [B]lo combinamos
también con tee[/B], es algo así:

```
du -ah  | grep .odt | tee listado_ubuntuone
```

---

### Post by bruno9779 on 2009-10-21
No se si ya alguien lo escribió:

```
Ctrl + Alt + F1
```

Es muy util quando el sistema se bloquea.

En un sentir es parecido a:

```
Ctrl + Alt + Canc
```

de este otro sistema operativo.

---

### Post by pol666 on 2009-10-22
Ese no es el comando, ese es el atajo. Pero en realidad no se cual es el comando que representa.

---

### Post by pablo.s on 2009-10-23
[B][SIZE="3"]---   sudo   ---
superuser do[/SIZE][/B]

El comando sudo permite a un usuario
la ejecución de comandos como 
superusuario. Para que un usuario pueda
ejecutar el comando sudo efectivamente
tiene que estar autorizado en la lista del
archivo /etc/sudoers. Si un usuario que no
esté autorizado trata de ejecutar el comando
sudo, se le notificará al superusuario.
Al usuario que utilice sudo se le pedirá su
contraseña. El tiempo máximo por defecto
que el usuario está habilitado para ejecutar
comandos con sudo es de cinco minutos,
aunque se puede modificar ese tiempo en
el archivo etc/sudoers.

Algunos parámetros interesantes:

```
sudo** -b** apt-get update
```
Ejecuta el comando en el background.

```
sudo **-l**
```
Hace un listado de todos los comandos que
el usuario tiene permitido ejecutar en la
maquina y luego sale.

```
sudo **-u** facundito passwd
```
Ejecuta el comando como si fuera el usuario
especificado, en lugar de superusuario

---

### Post by pablo.s on 2009-10-24
[SIZE=3]**---   clear   ---**[/SIZE]

El comando clear limpia la terminal. 
Si presiona la combinación de teclas
CTRL + L dá el mismo resultado.

---

### Post by pablo.s on 2009-10-25
[B][SIZE=3]           ---   dpkg   ---
Debian Package Manager[/SIZE][/B]

El comando dpkg se utiliza para la
gestión de paquetes .deb de una
manera básica y rápida. Una de las
herramientas más completas para
realizar esta misma función es
aptitude. dpkg no descarga paquetes
de repositorios ni resuelve dependencias
por sí mismo. Para ese tipo de tareas
puede utilizar apt o alguna variante.

Los parámetros más utilizados son:

```
dpkg **-i** paquetito.deb
```
Instala el paquete.

```
dpkg **-r** paquetito.deb
```
Desinstala el paquete

```
dpkg **-P** paquetito.deb
```
Purga el paquete. Esto quiere decir
que además de desinstalarlo, también
borra los archivos de configuración del
paquete.

---

### Post by josecuervo86 on 2009-10-25
> **pablo.s said:**
> [B][SIZE=3]           ---   dpkg   ---
Debian Package Manager[/SIZE][/B]



Jaja, justo hoy me estaba preguntando que significaba!

---

### Post by pablo.s on 2009-10-27
[SIZE=3][B]     ---   fsck   ---
Filesystem Checker[/B][/SIZE]

El comando fsck cumple una funciòn
muy importante: chequea (comprueba)
un sistema de archivos en busca de
errores y opcionalmente tiene la capacidad
de corregirlos.
Por defecto fsck se ejecuta de manera
interactiva, solo pausando para pedir al
usuario permiso para arreglar los errores.
Este comando no se utiliza tanto en la
actualidad como se hacia antes, cuando el
sistema de archivos ext2 era el sistema por
defecto de GNU/Linux.

Los paràmetros màs utilizados son:

```
fsck **-A**
```
Ejecuta fsck en todas las particiones que
aparecen en /etc/fstab

```
fsck **-N**
```
Ejecuta el comando pero solo muestra las
correcciones que se deben hacer.

```
fsck **-f**
```
Provoca el forzado del chequeo.

```
fsck **-p**
```
Repara el sistema de archivos sin pedir
permiso para efectuar las reparaciones.

```
fsck **-y**
```
Responde afirmativamente a todos los
pedidos de permiso.

---

### Post by pablo.s on 2009-10-28
[SIZE=3][B]  ---   lsmod   ---
List kernel modules[/B][/SIZE]

El comando lsmod efectùa un informe 
en pantalla  de los mòdulos del nùcleo
cargados que lista: nombre del mòdulo,
tamaño, cuenta de uso y otros mòdulos
relacionados.
La finalidad màs bàsica es la de informar
al usuario si el mòdulo que se precisa està
siendo utilizado en ese mismo momento.

---

### Post by pablo.s on 2009-10-29
[SIZE=3]**---   apt-get   ---**[/SIZE]

El comando apt-get es parte del 
sistema de gestiòn **APT** (Advanced 
Package Tool; en castellano 
Herramienta Avanzada para Paquetes).
Su forma de uso difiere de la que
usa **dpkg**, porque no trabaja con
archivos .deb sino que utiliza los 
nombres de los paquetes. 
Su funcionamiento es a travès de
una base de datos de paquetes, la
cual permite al comando poder
actualizarlos junto a sus respectivas
dependencias a medida que la base
de datos actualice las fuentes.


[COLOR=Blue][I]<Este comando se utiliza 
como superusuario>[/I][/COLOR]

Los parametros màs utilizados son:

```
apt-get **install** pyroom
```Instala el paquete llamado pyroom
junto con sus dependencias.

```
apt-get **remove** pyroom
```Desinstala el paquete pyroom
junto con sus dependencias

```
apt-get **update**
```Actualiza la base de datos de
paquetes tomando como punto
el archivo .sources.list donde se
detallan los repositorios.

```
apt-get **upgrade**
```Actualiza los paquetes que hayan
renovado en los repositorios.
Es preciso ejecutar apt-get update
previamente, o no actualizarà.

```
apt-get **dist-upgrade**
```Actualiza TODA la distribuciòn a
la màs reciente.

---

### Post by pablo.s on 2009-11-05
[SIZE=3][B]---   cal   ---
 Calendar[/B][/SIZE]

El comando cal nos muestra un
calendario en pantalla en el formato
tradicional.

Algunos parámetros interesantes son:

```
cal **-3**
```
Nos muestra tres calendarios, con el
mes pasado primero, el mes en curso
y el mes próximo a continuación.

```
cal **-m**
```
Nos muestra el calendario del mes en
curso pero con la salvedad que le dia de
la semana comienza en Lunes, en lugar
de comenzar el Domingo.

```
cal **-y**
```
Nos muestra el calendario de todos los
meses de el año en curso. Si le agregamos 
un año en particular (2011, 1976) luego del
parámetro, nos muestra ese año.

---

### Post by Mauro22 on 2009-11-05
**[SIZE="5"]---calendar---[/SIZE]**

*Espero que no esté*

Al anterior de pablo.s le sumo este.

Al hacer 'calendar' en la consola, nos devuelve fechas `importantes` entre hoy y mañana de la historia.


```
blackice@blackice-paradise:~$ calendar 
nov 05 	Roy Rogers born, 1912
nov 05 	Guy Fawkes' Plot, 1605
nov 05 	4th Cross-Quarter Day
nov 05 	Aujourd'hui, c'est la St(e) Sylvie.
nov 05 	N'oubliez pas les Sylvette !
nov 05 	Bonne fête aux Sylviane !
nov 05 	Aujourd'hui, c'est la St(e) Zacharie.
nov 05 	N'oubliez pas les Élisabeth !
nov 05*	Election Day in USA (1st Tuesday after 1st Monday for even years)
nov 05 	Día Nacional de la Aviación Civil
nov 06 	Green March Day in Morocco
nov 06 	Bonne fête aux Bertille !
nov 06 	Aujourd'hui, c'est la St(e) Léonard.
nov 06 	N'oubliez pas les Winnoc !
nov 06 	Reichstagswahl: Rückgang der NSDAP, 1932
```

---

### Post by SLA_leandrin on 2009-11-07
> **pablo.s said:**
> [SIZE=3][B]---   cal   ---
 Calendar[/B][/SIZE]


Este comando está muy bueno...

---

### Post by pablo.s on 2009-11-17
[SIZE=3]**---   whois   ---**[/SIZE]

El comando whois consulta a la base 
de datos Whois. Esta base de datos
tiene información de nombres de dominio,
direcciones IP asignadas y registrantes de
un dominio en particular.
Por ejemplo, se nos ocurre registrar el
dominio [www.google.com](www.google.com) porque nos
parece un buen nombre para un buscador.

En una terminal escribimos:

```
whois www.google.com
```

y nos devuelve la siguiente información:

```
 Whois Server Version 2.0

Domain names in the .com and .net domains can now be registered
with many different competing registrars. Go to http://www.internic.net
for detailed information.

   Server Name: WWW.GOOGLE.COM.VN
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: http://www.enom.com

   Server Name: WWW.GOOGLE.COM.TW
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: http://www.enom.com

   Server Name: WWW.GOOGLE.COM.TR
   Registrar: TUCOWS INC.
   Whois Server: whois.tucows.com
   Referral URL: http://domainhelp.opensrs.net

   Server Name: WWW.GOOGLE.COM.SA
   Registrar: OMNIS NETWORK, LLC
   Whois Server: whois.omnis.com
   Referral URL: http://domains.omnis.com

   Server Name: WWW.GOOGLE.COM.PE
   Registrar: ABACUS AMERICA, INC. DBA NAMES4EVER
   Whois Server: whois.names4ever.com
   Referral URL: http://www.names4ever.com

   Server Name: WWW.GOOGLE.COM.MX
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: http://www.enom.com

   Server Name: WWW.GOOGLE.COM.CO
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: http://www.enom.com

   Server Name: WWW.GOOGLE.COM.BR
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: http://www.enom.com

   Server Name: WWW.GOOGLE.COM.AU
   Registrar: MELBOURNE IT, LTD. D/B/A INTERNET NAMES WORLDWIDE
   Whois Server: whois.melbourneit.com
   Referral URL: http://www.melbourneit.com

   Server Name: WWW.GOOGLE.COM.AR
   Registrar: ENOM, INC.
   Whois Server: whois.enom.com
   Referral URL: http://www.enom.com

>>> Last update of whois database: Tue, 17 Nov 2009 16:06:52 UTC <<<

NOTICE: The expiration date displayed in this record is the date the 
registrar's sponsorship of the domain name registration in the registry is 
currently set to expire. This date does not necessarily reflect the expiration 
date of the domain name registrant's agreement with the sponsoring 
registrar.  Users may consult the sponsoring registrar's Whois database to 
view the registrar's reported date of expiration for this registration.

TERMS OF USE: You are not authorized to access or query our Whois 
database through the use of electronic processes that are high-volume and 
automated except as reasonably necessary to register domain names or 
modify existing registrations; the Data in VeriSign Global Registry 
Services' ("VeriSign") Whois database is provided by VeriSign for 
information purposes only, and to assist persons in obtaining information 
about or related to a domain name registration record. VeriSign does not 
guarantee its accuracy. By submitting a Whois query, you agree to abide 
by the following terms of use: You agree that you may use this Data only 
for lawful purposes and that under no circumstances will you use this Data 
to: (1) allow, enable, or otherwise support the transmission of mass 
unsolicited, commercial advertising or solicitations via e-mail, telephone, 
or facsimile; or (2) enable high volume, automated, electronic processes 
that apply to VeriSign (or its computer systems). The compilation, 
repackaging, dissemination or other use of this Data is expressly 
prohibited without the prior written consent of VeriSign. You agree not to 
use electronic processes that are automated and high-volume to access or 
query the Whois database except as reasonably necessary to register 
domain names or modify existing registrations. VeriSign reserves the right 
to restrict your access to the Whois database in its sole discretion to ensure 
operational stability.  VeriSign may restrict or terminate your access to the 
Whois database for failure to abide by these terms of use. VeriSign 
reserves the right to modify these terms at any time. 

The Registry database contains ONLY .COM, .NET, .EDU domains and
Registrars.
```

---

### Post by lucasgz on 2009-11-17
pueden explicar el comando "dos2unix" y "unix2dos"?

---

### Post by jandry on 2009-11-17
Recien me engancho,muy buena la idea de los comandos.Pregunta: hay algun indice de los comandos explicados hasta ahora? Yo uso mucho el comando top, para saber que a&#7765;licaciones consumen mas recursos y para "matar" algun proceso rebelde ya que me da el PID. Desde hoy ya miro dia por dia, como siempre un orgullo pertenecer a esta comunidad. Abrazo ubuntero
Alejandro

---

### Post by pablo.s on 2009-11-17
> **jandry said:**
> Recien me engancho,muy buena la idea de los comandos.Pregunta: hay algun indice de los comandos explicados hasta ahora?

Va a aparecer posiblemente el día
jueves en el primer post una lista
de los comandos, con links a cada
uno por separado. Al principio lo
hacia a cada semana. Ahora le voy
a poner mas cuidado al thread.

---

### Post by aledruetta on 2009-11-18
> **jandry said:**
> Recien me engancho,muy buena la idea de los comandos.Pregunta: hay algun indice de los comandos explicados hasta ahora? Yo uso mucho el comando top, para saber que a&#7765;licaciones consumen mas recursos y para "matar" algun proceso rebelde ya que me da el PID. Desde hoy ya miro dia por dia, como siempre un orgullo pertenecer a esta comunidad. Abrazo ubuntero
Alejandro

También existe **htop**, que es más interactivo. Te lo recomiendo.

---

### Post by oktubrer on 2009-11-18
> **aledruetta said:**
> También existe **htop**, que es más interactivo. Te lo recomiendo.

Vale aclarar que previamente hay que instalarlo, mediante sudo apt-get install htop o su gestor de paquetes favorito.

---

### Post by aledruetta on 2009-11-19
> **oktubrer said:**
> Vale aclarar que previamente hay que instalarlo, mediante sudo apt-get install htop o su gestor de paquetes favorito.

Es cierto, me olvidé decirlo.

Aquí les dejo un link con un artículo que complementa el post de Pablo sobre apt-get. Comentan una serie de cosas interesantes sobre el sistema APT, que es muy potente y flexible.

[El poder de APT]("http://www.puntogeek.com/2009/11/16/el-poder-de-apt-the-power-of-apt/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+Puntogeek+%28PuntoGeek+-+El+punto+de+encuentro+para+todo+Geek%29")

---

### Post by Mauro22 on 2009-11-19
[SIZE="4"]**---history---**[/SIZE]

```
history
```

Este comando nos devuelve los 501 ultimos comandos (en realidad 500 porque 'history' es siempre el 501)

Lo mejor (y util) es que al ver la lista, si queres repetir un comando solo hacemos:

```
!n
```

donde n es el número que aparece al lado del comando.



Sirve para varias cosas, entre ellas ver que se hizo por consola.


Al igual que cualquier comando, pero con una diferencia:

```

sudo su
history

```

podemos ver el historial de root. ;)

---

### Post by guillermolisi on 2009-11-19
> **lucasgz said:**
> pueden explicar el comando "dos2unix" y "unix2dos"?
              [FONT=verdana][SIZE=4][COLOR=#cc0000]** Linux / Unix Command: [FONT=verdana][SIZE=4][COLOR=#cc0000][B]*[FONT=verdana][SIZE=4][COLOR=#cc0000]dos2unix[/COLOR][/SIZE][/FONT]***[/COLOR][/SIZE][/FONT][/B][/COLOR][/SIZE][/FONT]           [IMG]http://z.about.com/[/IMG]            [IMG]http://z.about.com/[/IMG]        [[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]Command        Library [/SIZE][/FONT]]("http://linux.about.com/library/cmd/blcmdl.htm")      
**NAME**

   dos2unix - DOS/MAC to UNIX text file format converter 
   
**SYNOPSYS**

   dos2unix [options] [-c convmode] [-o file ...] [-n infile outfile ...] 
  Options: 
  [-hkqV] [--help] [--keepdate] [--quiet] [--version] 
   
**DESCRIPTION**

   
  This manual page documents dos2unix, the program that converts plain text files in DOS/MAC format to UNIX format. 


**Trad**: [COLOR=Blue]Este manual documenta dos2unix, el programa que convierte **archivos de texto plano** en formato DOS/MAC a formato Unix[/COLOR].

   
**OPTIONS**

   The following options are available: 
**-h --help**   Print online help.  
**-k --keepdate**   Keep the date stamp of output file same as input file.[COLOR=Blue] (Preserva la fecha del archivo de salida igual a la del archivo de entrada)[/COLOR]
**-q --quiet**   Quiet mode. Suppress all warning and messages.  
**-V --version**   Prints version information.  
**-c --convmode convmode**   Sets conversion mode. Simulates dos2unix under SunOS.  
**-o --oldfile file ...**   Old file mode. Convert the file and write output to it. The program  default to run in this mode. Wildcard names may be used. [COLOR=Blue](Antiguo modo de archivo. Convierte el archivo y escribe en el. Este es el modo por defecto en que este programa corre. Nombres con comodines pueden ser usados).[/COLOR]
**-n --newfile infile outfile ...**   New file mode. Convert the infile and write output to outfile. File names must be given in pairs and wildcard names should NOT be used or you WILL  lost your files. [COLOR=Blue](Nuevo modo de archivo. Convierte el archivo de entrada y escribe en uno distinto de salida. Los nombres de archivos deben ser definidos en pares y nombres con comodines NO deben ser usados ya que PERDERAS tus archivos)
[/COLOR]  
   **EXAMPLES**

   
  Get input from stdin and write output to stdout. 

**dos2unix**   
   Convert and replace a.txt. Convert and replace b.txt. 

**dos2unix a.txt b.txt**  
**dos2unix -o a.txt b.txt**   
   Convert and replace a.txt in ASCII conversion mode.  Convert and replace b.txt in ISO conversion mode. Convert c.txt from Mac to Unix ascii format.


**dos2unix a.txt -c iso b.txt**  
**dos2unix -c ascii a.txt -c iso b.txt**  
**dos2unix -c mac a.txt  b.txt**   
   Convert and replace a.txt while keeping original date stamp. 

**dos2unix -k a.txt**  
**dos2unix -k -o a.txt**   
   Convert a.txt and write to e.txt. 

**dos2unix -n a.txt e.txt**   
   Convert a.txt and write to e.txt, keep date stamp of e.txt same as a.txt. 

**dos2unix -k -n a.txt e.txt **   
   Convert and replace a.txt. Convert b.txt and write to e.txt. 

**dos2unix a.txt -n b.txt e.txt**  
**dos2unix -o a.txt -n b.txt e.txt**   
   Convert c.txt and write to e.txt. Convert and replace a.txt. Convert and replace b.txt. Convert d.txt and write to f.txt. 

**dos2unix -n c.txt e.txt -o a.txt b.txt -n d.txt f.txt**   
   **SEE ALSO**

  [unix2dos]("http://linux.about.com/library/cmd/blcmdl1_unix2dos.htm")(1) [mac2unix]("http://linux.about.com/library/cmd/blcmdl1_mac2unix.htm")(1) 



(extractado del man page del comando)

Si necesitan aclarar alguna parte de lo que no traduje, por favor pedirlo.

---

### Post by jandry on 2009-11-19
Gracias Aledruetta!!! Una barbaridad htop!! No lo conocia,me gusto mucho.
Abrazo ubuntero

---

### Post by sierrasdetandil on 2009-11-20
[SIZE="3"]**--- Ack ---**  (ack-grep en Ubuntu)[/SIZE]

Siguiendo con los comandos alternativos a los "tradicionales" (top -> htop), vale la pena tener en cuenta el comando **ack-grep** ([http://betterthangrep.com/](http://betterthangrep.com/)) como alternativa a grep.
Está pensado sobre todo para programadores, pero puede ser útil para cualquiera.

Algunas diferencias respecto a grep:
[LIST]
[*]Busca en el directorio indicado y sus subdirectorios.
   *Ack*: [FONT="Lucida Console"]ack-grep patronabuscar[/FONT]
   *grep*: [FONT="Lucida Console"]grep -R patronabuscar[/FONT]
[*]Permite indicar los tipos de archivo a incluir/excluir.
   *Ack (incl.)*: ack --php patronabuscar
   *grep (incl.)*: [FONT="Lucida Console"]grep patronabuscar $(find . -name '*.php' -or -name '*.phpt' -or -name '*.php4' -or -name '*.php5')[/FONT]
   *Ack (excl.)*: ack --nohtml --noxml patronabuscar
   *grep (excl.)*: [FONT="Lucida Console"]grep patronabuscar $(find . -type f | grep -v '\.htm|\.html|\.shtml|\.xhtml|\.xml|\.dtd|\.xslt|\.ent')[/FONT]
[*]Excluye los subdirectorios agregados por sistemas de control de versiones (.svn, CVS, ...) y otras cosas que generalmente son "basura" en las búsquedas, como archivos de backup o binarios.
   *Ack*: [FONT="Lucida Console"]ack-grep patronabuscar[/FONT]
   *grep*: [FONT="Lucida Console"]grep -R patronabuscar $(find . -type f | grep -v '\.svn|~$|[._].*\.swp$|#.+#$|core.\d+')[/FONT]
[/LIST]

También se puede usar para armar listas de archivos de tipos dados; para eso se usa el parámetro -f, que hace que muestre los archivos que coinciden con el criterio, pero no busque dentro de ellos. Por ejemplo, para listar todos los XMLs en ~/.kde/share/apps/:
```
ack-grep -f --xml ~/.kde/share/apps/
```
Muestra algo así como:
```
/home/.../.kde/share/apps/konsole/bookmarks.xml
/home/.../.kde/share/apps/basket/tags.xml
/home/.../.kde/share/apps/basket/baskets/baskets.xml
/home/.../.kde/share/apps/krusader/krbookmarks.xml
/home/.../.kde/share/apps/krdc/bookmarks.xml
/home/.../.kde/share/apps/okular/bookmarks.xml
...(sigue)...
```

Para ver todos los tipos de archivo que conoce por defecto:
```
ack-grep --help-types
```

Antes de poder usarlo hay que instalarlo:
```
sudo aptitude install ack-grep
```

---

### Post by Mauro22 on 2009-12-06
[SIZE="5"]**--- dict ---**[/SIZE]

Dict no viene por defecto en ubuntu, pero se instala sin agregar repositorios ni nada, solo :

sudo apt-get install dict


Dictes un cliente del Dictionary Server Protocol, una transaccion TCP que provee acceso a varios diccionarios.

***Uso: dict dato***

Ejemplos:

```

blackice@Hell:~$ dict gnu
7 definitions found
[...]

From Jargon File (4.3.1, 29 Jun 2001) [jargon]:

  GNU /gnoo/, _not_ /noo/ 1. [acronym: `GNU's Not Unix!', see {{recursive
     acronym}}] A Unix-workalike development effort of the Free Software
     Foundation headed by Richard Stallman <<rms@gnu.org>>. GNU EMACS and the
     GNU C compiler, two tools designed for this project, have become very
     popular in hackerdom and elsewhere. The GNU project was designed partly
     to proselytize for RMS's position that information is community property
     and all software source should be shared. One of its slogans is "Help
     stamp out software hoarding!" Though this remains controversial (because
     it implicitly denies any right of designers to own, assign, and sell the
     results of their labors), many hackers who disagree with RMS have
     nevertheless cooperated to produce large amounts of high-quality
     software for free redistribution under the Free Software Foundation's
     imprimatur. The GNU project has a web page at `http://www.gnu.org'. See
     {EMACS}, {copyleft}, {General Public Virus}, {Linux}. 2. Noted Unix
     hacker John Gilmore <<gnu@toad.com>>, founder of Usenet's anarchic alt.*
     hierarchy.

       

From THE DEVIL'S DICTIONARY ((C)1911 Released April 15 1993) [devils]:

  GNU, n.  An animal of South Africa, which in its domesticated state
  resembles a horse, a buffalo and a stag.  In its wild condition it is
  something like a thunderbolt, an earthquake and a cyclone.
  
      A hunter from Kew caught a distant view
          Of a peacefully meditative gnu,
      And he said:  "I'll pursue, and my hands imbrue
          In its blood at a closer interview."
      But that beast did ensue and the hunter it threw
          O'er the top of a palm that adjacent grew;
      And he said as he flew:  "It is well I withdrew
          Ere, losing my temper, I wickedly slew
          That really meritorious gnu."
                                                             Jarn Leffer

```


Lo bueno es que busca en varios diccionarios. Todo lo que aparece {asi} se puede buscar.

Otra funcion que tiene es explicar lo que a veces se ven en los foros y chat (ejemplo: imho, rtfm, brb, oic, etc)

```

blackice@Hell:~$ dict rtfm
3 definitions found

From Virtual Entity of Relevant Acronyms (Version 1.9, June 2002) [vera]:

  RTFM
       Read The Flaming / ******* Manual (telecommunication-slang, Usenet,
       IRC)
[...]

```

---

### Post by lucasgz on 2009-12-09
hay algun paquete para tener el comando dict en español?

---

### Post by euzkoarima on 2009-12-09
**[SIZE="5"]--- find ---[/SIZE]**

El comando find nos sirve para buscar, a partir de un directorio dado, archivos que cumplan ciertas condiciones.

El formato básico es

```
find <directorio a partir del cuál buscar> <condiciones a cumplir> <acciones a realizar>
```

La acción por defecto, si no se explicita ninguna, es listar las coincidencias.

Ejemplos:

```
find . -name *.jpg
```

buscar a patir del directorio donde estoy parado ( . ) archivos cuyo nombre termine en .jpg

```
find / -type d -iname '*fotos*'
```

buscar desde la raíz todos los directorios (-type d) cuyo nombre contenga "fotos" sin importar si está en mayúsculas o minúsculas

También hay opciones para preguntar por la antigüedad o el tamaño de los archivos (ver el man).

Un ejemplo con acción, si uno se copia directorios provenientes de mac osx, vienen con unos archivos que son metadata para administrador de archivos de mac, pero inútiles en ubuntu. Podemos buscarlos y borrarlos del siguiente modo (estando parados en el directorio que acabamos de copiar):

```
find . -name *.DS_Store -type f -delete
```

Saludos,
Eduardo

---

### Post by thegreeneyes on 2009-12-14
Hola!!, muy buena la idea, buscando información de otro tema encontré esta hebra, y ... todavía lo otro sigue sin solución. 

No sé mucho de Linux y sus comandos, pero es útil tener idea de ellos, aquí va el comando 


HELP 


que sirve para listar los comandos internos (accesibles por defecto) en el entorno (shell) en que uno se encuentra trabajando. Puede venir bien tenerlo presente cuando uno trata de recordar un comando, pero no está seguro de cuál era. Quizás leyéndolo el Alzheimer se evapora (momentaneamente) y uno puede seguir haciendo lo que pretendía hacer (con suerte, si es que no se olvidó qué problema quería resolver!!!). 

No todos los comandos se enlistan con "help", por ejemplo no vi top ni htop, que, posiblemente por tener que ser instalados, se ignoran. 

Una pregunta que me planteo al releer lo escrito, es si todos estos comandos de los que estamos hablando existen en todos los entornos en que uno trabaja, o si depende de si uno está en bash o en otra cosa. Algún comentario?

Otra pregunta que se me ocurre es si hay algún modo de listar todos los comandos accesibles, incluyendo aquellos que no están en el entorno por defecto.

Suerte y espero que sigan posteando nuevas colaboraciones, que nos vienen bien a quienes no somos para nada expertos.

Gracias!!!.

---

### Post by biale on 2009-12-16
Listar comandos: accionando desde el prompt la tecla <tab> dos veces, ofrece la posibilidad de listar "las 2749 posibilidades". Saludos.

---

### Post by sdennie on 2009-12-16
[SIZE="5"]-- Bang Dollar --[/SIZE]

Bue, no es un comando pero es un parte de bash (y tcsh y supongo que otros).  !$ es la ultima cosa que dijiste en la ultima comando.  Lo uso mucho:

```

sdennie@ihatework [~]$ mkdir -p some/long/path/that/I/do/not/want/to/type     
sdennie@ihatework [~]$ ls !$
ls some/long/path/that/I/do/not/want/to/type
sdennie@ihatework [~]$ touch !$/vamos_argentina
touch some/long/path/that/I/do/not/want/to/type/vamos_argentina
sdennie@ihatework [~]$ echo "Connecticut sucks" > !$
echo "Connecticut sucks" > some/long/path/that/I/do/not/want/to/type/vamos_argentina
sdennie@ihatework [~]$ rm !$ 
rm some/long/path/that/I/do/not/want/to/type/vamos_argentina

```

Saludos

---

### Post by thegreeneyes on 2009-12-18
ENVIAR AL SOTANO (SEND TO BACKGROUND)

&

Esto no sé si es un comando o un modificador, no sé cómo se calificará, pero me parece útil. 

Sirve para que la terminal mantenga el control después de haber iniciado un proceso sin que ese proceso haya terminado. 

Por ejemplo, si tengo un proceso bajo WINE que lo inicio desde la terminal, digamos:

wine multiedit

hasta que la ventana del proceso "multiedit" que inicié con wine no se cierre, no puedo usar la terminal, a no ser que el comando lo ingrese como 

wine multiedit &

en cuyo caso, aunque en la terminal reciba algunos mensajes de iniciación de wine, puedo seguir ingresando comandos desde la terminal sin necesidad de cerrar multiedit, ni tampoto tener que abrir una segunda terminal para ingresar comandos.

Lo que todavía no sé es cómo evitar toda la verborragia de wine en la terminal cuando ingreso el comando de ese modo... alguna sugerencia??, probé con >null antes de & sin éxito.

Suerte...

---

### Post by oktubrer on 2009-12-18
> **thegreeneyes said:**
> 
Lo que todavía no sé es cómo evitar toda la verborragia de wine en la terminal cuando ingreso el comando de ese modo... alguna sugerencia??, probé con >null antes de & sin éxito.

Suerte...

Deberías derivarlo a /dev/null
```
wine multiedit > /dev/null &
```

Asi redireccionas la salida estandar, para redireccionar la salida de errores:
```
wine multiedit 2> /dev/null &
```

Y para redireccionar ambas al mismo lugar
```
wine multiedit &> /dev/null &
```

Edito:
Tené en cuenta que las salidas pueden ser útiles en algunos casos y si las derivas a /dev/null están cayendo en un agujero negro.  Quizas es conveniente derivar la salida a un archivo o abrir otra terminal, hoy por hoy el consumo es mínimo.

---

