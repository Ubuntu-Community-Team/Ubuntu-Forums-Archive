---
title: "Super Grub Disk"
date: 2008-05-09
forum: Catalan Team
---

### Post by Joan Marc on 2008-05-09
Hola,
Com bé sabreu la majoria, i seguint aquest [fil]("http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB"), que ha postat en **MiquelUbuntero** [aquí]("http://ubuntuforums.org/showthread.php?t=786795") es pot arreglar el GRUB mitjançant aquest programa.
Per fer-ho, pots gravar-lo en un CD, en un disquet, o bé en un disc extraïble.
El cas és que jo, per provar, l'he posat al llapis (descomprimit de la ISO en que està), i seguidament he reiniciat, i li he donat prioritat d'arranc al llapis des de la BIOS. Seguidament he tornat a reiniciar, amb l'esperança que em sortís el programa, però m'ha sortit el GRUB, és a dir m'ha arrencat amb normalitat.
A què pot ser degut?
   - A que la BIOS no reconeix el llapis?
   - A que el Super Grub Disk no està ben posat al llapis?
   - ...?

Gràcies

---

### Post by lesergi on 2008-05-09
He trobat un manual que et pot ajudar:
[http://linux.adslzone.net/howtos-manuales/how-to-instalar-linux-en-un-usb/](http://linux.adslzone.net/howtos-manuales/how-to-instalar-linux-en-un-usb/)

Salut!

**Edite:** l'enllaç del syslinux que indica el manual no funciona. Pren este: [http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-3.63.tar.bz2](http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-3.63.tar.bz2)

---

### Post by Joan Marc on 2008-05-10
Merci,
Ara no estic davant de cap ubuntu, però ho provaré.
He de fer servir el programa syskinux per col·locar correctament la imatge en .iso no?

---

### Post by Joan Marc on 2008-05-10
lsergi, un cop instal·lat el syslinux (sudo apt-get install syslinux) com el puc obrir?
Ni posant syslinux al terminal ni buscant-lo a aplicacions em surt. L'únic que em surt quan ho faig per terminal és això:
```
gami@gami:~$ syslinux
Usage: syslinux [-sfr][-d directory][-o offset] device
gami@gami:~$
```
I no entenc què m'està dient.
Merci

---

### Post by lesergi on 2008-05-10
Hola Joan,

L'enllaç que t'he posat serveix únicament per a la distribució SLAX, això em passa per enviar un comentari sense quasi temps, sorry!

He llegit a un readme del Super Grub disk açò:

> 
(ES)
Instalar SGD en un usb pen desde linux

    * haces el untar del fichero en tu dispositivo usb montado
    * desmontas
    * abres grub como root
    * device (hd2,0) /dev/sdb
    * root (hd2,0)
    * setup (hd2)
    * quit
    * reinicias o usas qemu y ya lo tienes


Has de descomprimir la ISO al teu USB, desmuntes l'USB i executes "sudo grub". Després executes les comandes que et diuen substituint els dispositius pels teus.

Espere que et funcione!!

---

### Post by Joan Marc on 2008-05-12
Perdona per no contestar-te fins avui...ho provaré a veure què tal

Gracies :)

---

### Post by adrian15 on 2008-05-15
> **lesergi said:**
> 
He llegit a un readme del Super Grub disk açò:



Has de descomprimir la ISO al teu USB, desmuntes l'USB i executes "sudo grub". Després executes les comandes que et diuen substituint els dispositius pels teus.

Espere que et funcione!!

Teneis las instrucciones actualizadas aqui:
[How to make a Super Grub Disk USB](http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB.).

Os animo a sacaros una cuenta en el wiki y traducirlo al catalán y ya de paso al castellano ;).

Por cierto en [http://www.supergrubdisk.org](http://www.supergrubdisk.org) hay un foro en castellano para plantear estas dudas. Si hay mucha demanda no me importaria abrir uno en catalán pero yo respondería en castellano. :p

Por cierto todos los howtos para hacer el usb dicen de copiar los datos del  tar.gz o tar.bz2 que tiene la versión preparada para usb.

Se puede hacer tranquilamente con los datos del cd (lo que hay dentro, nada del .iso tal cual) ya que ahí están todos los ficheros necesarios pero yo me buscaria el directorio S10en y en el directorio donde está, borraria todos los directorios de idiomas menos el S20cat (si no me falla la memoria). De 8 MB te bajará a 1 MB.



adrian15

---

### Post by CarlesOriol on 2008-05-15
i ja posats a l'italià i al francés.

Ok tovaritz?

---

