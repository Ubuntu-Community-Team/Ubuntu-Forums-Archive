---
title: "You passed an undefined mode number Era: Missatge ¿d'error? al iniciar Ubuntu"
date: 2008-02-18
forum: Catalan Team
---

### Post by lluisalguero on 2008-02-18
Normalment engego el pc i mentrestant carrega vaig fent altres coses. Però avui he vist que em surt un missatge.

Després de seleccionar el sistema operatiu (en el meu cas ubuntu)
em surt el seguent:

boot
you passed an undefined mode number
press<RETURN> to see video mode avaliable, <SPACE> to continue or wait 30 seconds.

Obviament, m'esperat els 30sg (crec que no han estat tants) i s'ha iniciat normalment.

Què pot ser?

Dir també que abans d'allà on fica "boot" em surt alguna cosa més però m'he centrat en memoritzar la segona part. Si creieu que pot ser important, reinicio el pc i miro de encara que sigui fer una foto amb el móvil per veure que hi fica (eren 5-6 linees)

Gràcies,
Lluís

---

### Post by papapep on 2008-02-18
> Dir també que abans d'allà on fica "boot" em surt alguna cosa més però m'he centrat en memoritzar la segona part. Si creieu que pot ser important, reinicio el pc i miro de encara que sigui fer una foto amb el móvil per veure que hi fica (eren 5-6 linees)


Saps què passa? Que no podem saber si és important o no perquè no sabem que diu...:-D

Si poguéssis fer la foto aniria de conya. (no seràs el primer en fer-ho, t'ho asseguro).

---

### Post by lluisalguero on 2008-02-18
A veure, que això és liat..

```
root (hd0,3)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vlinuz-2.6.22-14-generic  root=UUID=8e84d134-32f4-4ea4-ba8b-b7b3
878ll7fc ro quiet splash locale=ca_ES vga=794
   [Linux=bzImage, setup=0x1f8bd000, 0x732199 bytes]
```

i després el que ja us he comentat abans

```
boot
You passed an undefined mode number
Press <RETURN> to see video modes avaliable, <SPACE> to continue or wait 30secs
```

---

### Post by papapep on 2008-02-18
El missatge té a veure amb el paràmetre que li passes a l'arrencada a la placa gràfica (vga=794). El que no entenc és com que si abans no es queixava per què ho ha de fer ara...
Sigui com sigui, en funció de la ressolució que vulguis fer servir i de la quantitat de colors, has de verificar que tens la opció correcta segons la següent taula:

..........| .... 640x480 .... 800x600 .... 1024x768 .... 1280x1024
---------|--------------------------------------------------------------
08 bpp | ...... 769 ........... 771 ............ 773 ............ 775
16 bpp | ...... 785 ........... 788 ............ 791 ............ 794
32 bpp | ...... 786 ........... 789 ............ 792 ............ 795

O sigui, que tal i com ho tens ara li estàs dient que vols tenir 1280x1024 a 16 bpp de profunditat. No sé si és normal, però a mi no m'ho sembla...no hauries de tenir el 795 que és a 32 bits??

Si vas i ho modifiques al /boot/grub/menu.lst podràs provar a veure si et funciona amb el 795 (recorda fer-ne una còpia abans de tocar-lo!)

---

### Post by lluisalguero on 2008-02-18
Vaig voler instalar un boot splash (es diu així?) per a que no fos el típic menú de fons negre i lletres blanques, crec que de llavors surt això.

La pantalla que faig servir és de 17" panoràmica i a sistema->preferències->preferències de la resolució de la pantalla, tinc ficat a 1440x900 i la velocitat de refresc a 50Hz.

---

### Post by lluisalguero on 2008-02-18
He provat allà on fica <RETURN> to see video modes avaliables, i m'ha sortit lo seguent:

```
Video Adapter: VESA VGA
Mode:         COLSxROWS
0   00F0            80X25
1   0F01            80X50
2   0F02            80X43
3   0F03            80X28
4   0F05            80X30
5   0F06            80X34
6   0F07            80X60

Enter mode number or 'scan':
```

Primer he fet 'scan' i m'ha tornat a sortir la mateixa llista, i com que estava en un bucle tancat, he tirat pel dret i he agafat la primera opció, s'ha iniciat igual que abans, i no he vist cap diferència respecte a les altres postes en marxa

---

### Post by papapep on 2008-02-19
....ara si que em perdo. A veure:

- Quina gràfica té l'ordinador?
- Tens una còpia de seguretat del menu.lst?

La primera perquè el que t'he dit de la taula de paràmetres a l'arrencada només és per les Intel. I sembla que el sistema ara et carrega el controlador Vesa.
La segona, perquè si el restaures, en teoria, deixaràs de tenir aquest problema.

---

### Post by lluisalguero on 2008-02-19
> **papapep said:**
> ....ara si que em perdo. A veure:

- Quina gràfica té l'ordinador?
 nVidia GeForce Go 7600

> **papapep said:**
> 
- Tens una còpia de seguretat del menu.lst?


La veritat es que no, ho sento...sé que l'hagués tingut que fer abans de tocar res...

Et fico la sortida del menu.lst per si veus alguna cosa extranya

```
#gfxmenu /boot/grub/message.ultimate
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
default		0

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=8e84d134-32f4-4ea4-ba8b-b7b3878667fc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# defoptions=quiet splash locale=ca_ES vga=794

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8e84d134-32f4-4ea4-ba8b-b7b3878667fc ro quiet splash locale=ca_ES vga=795
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Debian GNU/Linux, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8e84d134-32f4-4ea4-ba8b-b7b3878667fc ro single
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Debian GNU/Linux, kernel memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by lluisalguero on 2008-02-19
He googlejat una mica i he trobat aquesta possible solució

[http://www.linuxquestions.org/questions/linux-newbie-8/undefined-mode-number-error-320298/](http://www.linuxquestions.org/questions/linux-newbie-8/undefined-mode-number-error-320298/)

---

### Post by ilku on 2008-02-20
jo canviaria:
# defoptions=quiet splash locale=ca_ES vga=794

per

# defoptions=vga=794=quiet splash locale=ca_ES

Tot i que jo aniria probant amb les diferents vga= que t'ha dit en papapep comença amb un 791 per exemple.

Despres si vols pots modificar el /etc/usplash.conf que es comenta en un altre fil del forum. No tinc temps per possar-te el link, pero cerca'l.

---

