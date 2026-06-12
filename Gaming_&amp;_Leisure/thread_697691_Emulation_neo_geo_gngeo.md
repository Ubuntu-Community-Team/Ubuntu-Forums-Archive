---
title: "Emulation neo geo: gngeo"
date: 2008-02-15
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-02-15
Hello, 

Neo geo is powered by gngeo 
a nice emulator, and lucky : no gui !!
I made a deb:
[http://www.megaupload.com/nl/?d=IL6P3AL4](http://www.megaupload.com/nl/?d=IL6P3AL4)


I am looking for a frontend without java ;...

---

### Post by frenchn00b on 2008-02-15
xgngeo ist also working as crap 
I get this error message

```
Sorry, this configuration cannot be saved because one or more parameters does not look valid. Please check it up then try to save again... ^^;
```

---

### Post by RemmyLee on 2008-02-15
Emulators aren't exactly simple to create. It requires a huge amount of research on the hardware you are trying to emulate.

If you want to see better emulation, contact authors of emulators and ask them to collaborate and exchange information.. It's not like the hardware developers of these systems are passing out the technical specifications. They have to reverse engineer most of it save internal leaks.

To this day, we are still without a completely emulated NES system. The core is there, 98% of the games work, but developers created their own extensions to carts (mappers) that allowed them to extend the systems functionality in one way or another.

There are very few cases where you will find a fully emulated console.You really can't blame enthusiast developers.

---

### Post by frenchn00b on 2008-02-15
sorry I got it, with this :
> 

Todos recordamos la mítica consola de videojuegos Neo-Geo de los años 90, aquella consola basada en cartuchos en la versión para maquinas recreativas y que podía ser vista en algunos hogares privilegiados en su versión posterior con tecnología CD. Fue creada por la famosa compañía SNK en 1990, esta magnifica consola estaba muy adelantada (Tecnológicamente hablando) con todas las demás videoconsolas de la época, neo-geo decidió sustituir los cartuchos usados en maquinas para recreativas, por CDs y disminuir así su precio para poder implantarse poco a poco en los hogares, aún con el cambio de cartuchos a CDs la consola seguía con un precio muy elevado para una familia media, por lo que tardó bastante en integrarse y aun así no lo hizo del todo, por lo que fue un pequeño fracaso en su versión hogareña.

Existen multitud de emuladores, uno de los mas famosos es el neorageX, este emulador es para sistemas Window$, en GNU/Linux como en la mayoría de los casos tenemos un “sustituto” llamado GnGeo, el emulador, aun siendo libre (Bajo licencia GPL) y ejecutando tantas o incluso mas roms que otros emuladores afamados, puede resultar de difícil uso ya que esta basado en linea de comandos. Para solucionar esto y facilitarle la vida al usuario existen los frontend, que lo único que hacen es utilizar esa linea de comandos por debajo facilitando al usuario una interfaz gráfica para su uso, tenemos disponibles :

GGF, Gngeogui, Xgngeo.
Nosotros instalaremos Gngeo+Xgngeo, Empezemos:

Neo-Geo Linux

Lo primero es nombrar las dependencias (Descargarlas con vuestro gestor de paquetes o compilarlas ;)):

-librerías SDL
-aceleración 3D (drivers de la targeta gráfica)
-zlib
-NASM (opcional y recomendado)
-GTK+ (2.6=<)
-python (2.2=<)
-pygtk(2.6=<)
-pygame(1.6=<)(opcional, es para el joystick)

Después de instalar todas esas dependencias ya sea compilando o con gestor de paquetes, descargamos estos dos tar:

Descargar Gngeo
Descargar Xgngeo

Los descomprimimos en algún sitio, en mi caso el home:

$ cd /sitio/donde/descomprimir
$ tar xvf /home/slok/Desktop/gngeo-0.7.tar.gz
$ tar xvf /home/slok/Desktop/XGngeo-16.tar.bz2

Compilamos primero Gngeo:


$ cd ./gngeo-0.7
$ ./configure
$ make
# make install

Tenemos gngeo instalado, podríamos usarlo perfectamente en linea de comandos, ahora instalaremos el frontend Xgngeo

$ cd ../Xgngeo-16/
# python setup.py install

Ya lo tenemos todo instalado, ahora es el turno de la BIOS:

Creamos el directorio en nuestro usuario llamado ./gngeo y dentro de el “bios” en caso de que estuviese creado nos lo saltamos, de tal forma que quedaría algo similar a esto: /home/slok/.gngeo/bios

Descargamos y descomprimimos en ese directorio: bios neo-geo :

$ unzip /home/slok/Desktop/neogeo.zip -d /home/slok/.gngeo/bios

El directorio de los drivers de las roms que vienen por defecto esta mal, al menos en nuestro caso, para resolverlo:

# updatedb
$ locate romrc.d

Nos saldrá una lista inmensa con el direcotrio correcto, en nuestro caso /usr/local/share/gngeo/romrc.d/




---

### Post by frenchn00b on 2008-02-15
pddffffff 

Finally working : [http://img520.imageshack.us/img520/2775/finallyneogeoworkingfr5.jpg](http://img520.imageshack.us/img520/2775/finallyneogeoworkingfr5.jpg)

---

### Post by frenchn00b on 2008-02-15
> **RemmyLee said:**
> Emulators aren't exactly simple to create. It requires a huge amount of research on the hardware you are trying to emulate.

If you want to see better emulation, contact authors of emulators and ask them to collaborate and exchange information.. It's not like the hardware developers of these systems are passing out the technical specifications. They have to reverse engineer most of it save internal leaks.

To this day, we are still without a completely emulated NES system. The core is there, 98% of the games work, but developers created their own extensions to carts (mappers) that allowed them to extend the systems functionality in one way or another.

There are very few cases where you will find a fully emulated console.You really can't blame enthusiast developers.

I edited my post, and really you are right. I just hoped that all could work more easily ... hence I will write something, teh procedure how I could make neo geo work... it wasnt easy at all

---

### Post by frenchn00b on 2008-02-15
```
I had to do ::

 mkdir  /usr/share/gngeo/romrc.d -p ;  cp -a neogeo/gngeo-0.7/romrc.d/  /usr/share/gngeo/
``` 
to get the drivers workign

---

### Post by parabellum_org on 2008-03-18
I can't open Xgngeo, what is the localization of Gngeo executable that I should fill in the last field of the configuration window?

---

### Post by Cresho on 2008-03-31
try gxmame.  latest version .  there is a deb file too

gxmame_0.35beta2-1_i386.deb
[http://sourceforge.net/project/showfiles.php?group_id=50621](http://sourceforge.net/project/showfiles.php?group_id=50621)

to fix audio problem, try libsdl1.2debian-esd  for some reason on my system running hardy heron, none of them work but this one for zsnes and gxmame.  

after I installed libsdl1.2debian-esd, i uninstalled this one and installed libsdl1.2debian-all which fixed my broken audio.  If I nstalled the "all" first, its freaky but it didnt fix anything.  so esd then uninstall and then install all.

Everything works now.  crazy stuff.  I read up on tons of stuff related to broken audio in zsnes and other emulators.  Currently no fixes but This worked for me.

update:  if your having problems with zsnes, install the all libsdl 1.2 and in terminal use "zsnes -ad sdl"

---

### Post by parabellum_org on 2008-04-10
Thanks for the idea! 
On my computer it works just flawlessly - no need to install anything additional, maybe that's because I use 7.10 distribution. 
It's only a pity I don't see an option to change the keyboard controls...

---

### Post by Ideastone on 2008-04-11
NeoGeo is so sweet. Metal Slug and Samauri Showdown are still incredible.

---

