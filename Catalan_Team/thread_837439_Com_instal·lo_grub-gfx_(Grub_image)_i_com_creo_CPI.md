---
title: "Com instal·lo grub-gfx (Grub image) i com creo CPIOs"
date: 2008-06-22
forum: Catalan Team
---

### Post by LitusMayol on 2008-06-22
Bones familia!

Us explico, estava ja cansadet el Grub en blanc i negre típic i tòpic. Passejant per [Gnome-Look]("http://www.gnome-look.org")he trobat [aquest]("http://http://www.gnome-look.org/content/show.php/Paris+Grub+Gfx+Theme?content=68593"). La veritat l'he trobat genial. 

L'he baixat i he descobert que era un arxiu "*CPIO*" (format que desconec totalment).Aleshores e m'ha acudit canviar la imatge parisenca de fons per [aquesta]("http://www.engelvoelkers.es/santcugat/es/MonestirSantCugat.jpg") del Monestir de Sant Cugat (el meu estimat poble). He extret l'arxiu en una carpeta i he canviat l'arxiu "*back.jpg*" (que és el que pertany a la imatge parisenca) per un nou "*back.jpg*" que és la imatge del meu monestir. Aquí hi ha el problema.

[LIST=1]
[*]No sé com crear l'arxiu CPIO amb la carpeta que he extret
[*]No sé com hauré d'instal·lar aquest CPIO un cop creat
[/LIST]

Algú se li acut com fer-ho?



Merci de nou!

---

### Post by papapep on 2008-06-22
El nostre company d'equip, i valencià "de pro", Vicent Cubells fa un temps que va fer un post al seu blog sobre com personalitzar la pantalla del grub:

[http://www.vcubells.net/arxiu/2008/01/19/845/](http://www.vcubells.net/arxiu/2008/01/19/845/)

---

### Post by LitusMayol on 2008-06-22
> **papapep said:**
> El nostre company d'equip, i valencià "de pro", Vicent Cubells fa un temps que va fer un post al seu blog sobre com personalitzar la pantalla del grub:

[http://www.vcubells.net/arxiu/2008/01/19/845/](http://www.vcubells.net/arxiu/2008/01/19/845/)

Merci **papapep**, però no és això el que busco. Això ja ho sé fer! :P Però merci igualment. 

Jo parlo de com instal·lar [aquest]("http://www.gnome-look.org/content/show.php/Paris+Grub+Gfx+Theme?content=68593") en concret i de com crear arxius CPIO per tal de fer-ne un clon però amb la imatge que jo vull.

---

### Post by patrickfromspain on 2008-06-23
Com que últimament estic bastant desaparegut, m'he permes el luxe de fer un tutorial al wiki:

[http://wiki.ubuntu.com/CatalanTeam/Recursos/gfx boot](http://wiki.ubuntu.com/CatalanTeam/Recursos/gfx boot)

Encara queden algunes coses per fer, però em sembla que ja et servirà.

salut!

---

### Post by LitusMayol on 2008-06-23
> **patrickfromspain said:**
> 
...però em sembla que ja et servirà.


Renoi! 

Fantàstic tutorial! Si senyor! Gràcies **patrickfromspain**! 
No només m'ho has solucionat sinó que ara sé què és! 


Merci de debò!

[/SOLVED!]

---

### Post by Joan Marc on 2008-06-23
```
Això ens donarà una sortida del tipus (hdX,Y), que és a quin disc dur i a quina partició hi tenim el grub. Sabent això ja podem passar a editar l'arxiu /boot/grub/menu.lst:  gksudo gedit /boot/grub/menu.lst  i allà hi afegim el següent **al principi**:

### GFX BOOT
gfxmenu (hdX,Y)/boot/grub/message.nom_del_tema
```

Perdoneu que m'hi posi pel mig.
Patrick, allà on dius **al principi**, et refereixes al principi del tot del menu.lst? Quedant així: ?
```
### GFX BOOT
gfxmenu (hd0,3)/boot/grub/message.temagrub

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

.....
```

Gràcies pel tutorial! :D

---

### Post by Joan Marc on 2008-06-23
Havia repetit la resposta xD

---

### Post by patrickfromspain on 2008-06-24
prova alla, si. El cas es que com que vaig fer diverses proves, no t'ho se dir del cert (ja ho se, no es massa ajuda xD). Prova-ho, el pitjor que et pot passar possant-ho on no toca es que el grub arranqui normal.

Si veus que alla no va, prova-ho així:
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

### GFX BOOT
gfxmenu (hd0,3)/boot/grub/message.temagrub

```

i ho poses al wiki o ho dius aqui i s'afegeix.

salut!

---

### Post by Joan Marc on 2008-06-24
No em funciona de cap de les dues maneres... 
Es possible que passi perquè tinc uns quants errors am l'ubuntu... dos d'ells són els que surten a la captura d'una actualització que vaig fer just desp&#341;es de seguir els passos del teu tutorial.
Jo diria que l'actualització a Hardy Heron, no va anar massa bé, tot i que en el seu moment no em va donar cap error. Em sembla que faré una instal·lació neta i potser així les coses aniram mes bé.

Salut!

[[IMG]http://img403.imageshack.us/img403/1299/capturashanaplicatelscaut6.th.png[/IMG]](http://img403.imageshack.us/my.php?image=capturashanaplicatelscaut6.png)

---

### Post by papapep on 2008-06-24
No home, no...no treguis conclusions sense tenir-ho clar, que et pot portar molta feina i molts maldecaps.

Això t'està dient simplement que el paquet s'ha d'acabar de configurar. Això ha de ser d'una actualització que has d'haver fet els últims dies.

Fes:

```
sudo dpkg --configure --pending
```

i, en teoria, t'ha de solventar el problema.

(no us penseu que no sóc conscient de que això no toca a aquest fil :-)....si el tema ha de continuar, Joan Marc, obre un fil específic, si us plau.)

---

### Post by patrickfromspain on 2008-06-24
Joan Marc, quin maquinari tens? No t'ho se dir segur, pero em sembla que en un portatil que tinc, amb grafica intel i disc dur ATA no vaig ser capaç de fer-ho funcionar de cap de les maneres... Sento no serte de més ajuda.

---

### Post by Joan Marc on 2008-06-24
**papapep**: Gracies per l'ajuda, pero continua donant-me problemes, ja obriré un fil específic per al meu problema.

**patrick**: Sí, és un portàtil Intel Core 2 Duo, pero el disc dur no tinc ni idea de quina marca és. No pateixis, tampoc és que sigui cap cosa imprescindible :). El que sí que seria interessant de saber és com es fa per rebocar els cambis que es fan al tutorial.

Gràcies als dos!

---

### Post by patrickfromspain on 2008-06-24
revocar els canvis es molt senzill, com pots intuir:
```
sudo apt-get remove grub-gfxboot
sudo apt-get install grub
```

i al /boot/grub/menu.lst borres el que hi has afegit i llestos

---

### Post by LitusMayol on 2008-06-24
Bones!

a mi no em funciona... Al final després de probar-ho diverses vegades amb el tema que havia creat jo amb la base del de París, he decidit que en buscava un de prefet que m'agradés i així comprobava si el que estava malament era el tema o el grub. 


Doncs em segueix apareixent el mateix grub.Se us acut que pot ser?


Per cert, dos dubtes de *tunning* (xD hehe).

**1r.**Al grub m'apareixen els sistemes amb noms d'aques estil: *Ubuntu 8.04, kernel 2.6.24-19-rt*. Hi ha alguna manera de canviar-los per: *Ubuntu*, *UbuntuStudio* (enlloc de l'exemple que us he posat)??

**2n.**Es pot eliminar el "*Other operating systems:*"?
Si a:
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

```
canvio el "*Other operating systems:*" per re (deixo un espai en blanc) o bé poso "*Altres sistemes operatius*", la cosa funcionarà normal? No l'hauré grapejat massa?


Merci de nou!

---

### Post by patrickfromspain on 2008-06-24
al menu.lst, on hi posa title Ubuntu blab bla pots posar el que et dongui la gana. Per exemple, title Ubuntu Studio i apa. 

El other operatinc sistems, si borres tot el tros que has posat, solucionat, ja no apareix. O si vols posar title Altres Sistemes o el que vulguis, tambe es pot fer.

Respecte al gfxboot.. no se noi xD. Dones molt poca informació. Explica que has fet, que no has fet i diguens quin maquinari tens, sobretot si el disc dur es SATA o PATA i la grafica.

salut!

---

### Post by LitusMayol on 2008-06-24
> **patrickfromspain said:**
> al menu.lst, on hi posa title Ubuntu blab bla pots posar el que et dongui la gana. Per exemple, title Ubuntu Studio i apa. 

El other operatinc sistems, si borres tot el tros que has posat, solucionat, ja no apareix. O si vols posar title Altres Sistemes o el que vulguis, tambe es pot fer.

Fantàstic! ;) Ja he aplicat els canvis, merci!

> Respecte al gfxboot.. no se noi xD. Dones molt poca informació. Explica que has fet, que no has fet i diguens quin maquinari tens, sobretot si el disc dur es SATA o PATA i la grafica.


Tens raó. Perdona, a vegades em passa que em poso nerviós i dono la informació en comptagotes com si els que llegiu el post estiguéssiu a casa meva. 

He seguit tot el manual. Pas a pas. Amb el paquet *[message.studio]("http://www.gnome-look.org/content/show.php/Gfxboot+Grub+theme+ubuntustudio?content=68029")*. El grub està a (hd0,0). 


Pel que fa al maquinari... No sé com mirar-ho...:lolflag: Ho sé, no és normal. xD Com ho miro?


Merci per enèssima vegada!

---

### Post by LitusMayol on 2008-06-26
Bones...

Avui he probat d'enrtar a l'**Ubuntu** i em deia 
```
Error 15: File not Founf

Press any key to continue...
```
Després d'aquest missatge ja no m'entra. I em passa amb les tres entrades d'**Ubuntu**, mentre que amb la de **Windows**i les d'**UbuntuStudio** no em passa. 

Aleshores he probat això:
> **patrickfromspain said:**
> revocar els canvis es molt senzill, com pots intuir:
```
sudo apt-get remove grub-gfxboot
sudo apt-get install grub
```

i al /boot/grub/menu.lst borres el que hi has afegit i llestos


Però no ha canviat re...Pot tenir alguna cosa a veure amb el gfx-boot?

---

### Post by patrickfromspain on 2008-06-26
ahir funcionava i avui no? Que ha canviat en aquest dia?

Enganxan's el teu menu.lst

salut

---

### Post by LitusMayol on 2008-06-27
Aquest és el *menu.lst* amb el *gfx*:

```

### GFX BOOT
gfxmenu (hd0,0)/boot/grub/message.studio 


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		UbuntuStudio
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		UbuntuStudio (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		UbuntuStudio (generic)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

#title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro single
#initrd		/boot/initrd.img-2.6.24-19-generic

#title		Ubuntu 8.04, kernel 2.6.24-18-rt
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-18-rt
#quiet

#title		Ubuntu 8.04, kernel 2.6.24-18-rt (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro single
#initrd		/boot/initrd.img-2.6.24-18-rt

#title		Ubuntu 8.04, kernel 2.6.24-18-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-18-generic
#quiet

#title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro single
#initrd		/boot/initrd.img-2.6.24-18-generic

#title		Ubuntu 8.04, kernel 2.6.24-16-rt
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-rt
#quiet

#title		Ubuntu 8.04, kernel 2.6.24-16-rt (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro single
#initrd		/boot/initrd.img-2.6.24-16-rt

#title		Ubuntu 8.04, kernel 2.6.24-16-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
#quiet

#title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=567190ef-b8aa-4bbb-aa0b-3db6c8e4c5c1 ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu 8.04, memtest86+
#root		(hd0,0)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cb207f67-3dad-497b-8744-ae50ed0ee290 ro quiet splash locale=ca_ES 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cb207f67-3dad-497b-8744-ae50ed0ee290 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Ubuntu generic 
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cb207f67-3dad-497b-8744-ae50ed0ee290 ro quiet splash locale=ca_ES 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
#title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda4)
#root		(hd0,3)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cb207f67-3dad-497b-8744-ae50ed0ee290 ro single 
#initrd		/boot/initrd.img-2.6.22-14-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
#title		Ubuntu 8.04, memtest86+ (on /dev/sda4)
#root		(hd0,3)
#kernel		/boot/memtest86+.bin  
#savedefault
#boot

```

merci!

---

### Post by patrickfromspain on 2008-06-27
la vritat es que no se m'acut res. L'unic, no hauras borrat el kernel -16-generic i/o -14-generic de L'ubuntu normal no?

Si pots, munta la particio de l'ubuntu normal des de ubuntu studio i m'enganxes una captura de la carpeta boot d'aquella particio.

salut

---

### Post by LitusMayol on 2008-06-28
Bones!

Aquesta és la carpeta (adjuntada)


Jo no hi he tocat re...! :S 
Merci per tot, eh!

---

### Post by papapep on 2008-06-28
Litus, si us plau, un altre cop adjunta la imatge, no l'enganxis així que és un totxo. Fins i tot fent un simple "ls -la" del directori i enganxant el resultat és brutalment més llegible.

---

### Post by LitusMayol on 2008-06-30
> **papapep said:**
> Litus, si us plau, un altre cop adjunta la imatge, no l'enganxis així que és un totxo. Fins i tot fent un simple "ls -la" del directori i enganxant el resultat és brutalment més llegible.

Ho sento... xD No sabia fer-ho! Apuntat per la pròxima! ;)

---

