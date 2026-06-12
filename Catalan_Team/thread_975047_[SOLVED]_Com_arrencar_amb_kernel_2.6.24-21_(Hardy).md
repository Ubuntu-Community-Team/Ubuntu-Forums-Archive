---
title: "[SOLVED] Com arrencar amb kernel 2.6.24-21 (Hardy)"
date: 2008-11-08
forum: Catalan Team
---

### Post by enricXIII on 2008-11-08
Bones!
Tinc instalat el kernel 2.6.24-21, 2.6.24-19, i el 2.6.24-16.[ATTACH]91669[/ATTACH]
Faig servir l'startupmanager per configurar el menú del grub d'arrencada i el problema es que l'ultim kernel (2.6.24-21) no surt enlloc per poderlo posar com arrencada per defecte...[ATTACH]91670[/ATTACH] 
He provat totes les opcions que permet l'startup (crec) i no m'en surto. Nomes puc arrancar amb el 24-16 o 24-19..

Alguna sugerencia de que pot estar passant?

P.D. De moment no vull actualitzar a l'Intrepid perquè la Hardy em rutlla de maravella i ja que es una LTS i jo necessito per motius de feina la màxima estabilitat possible...

Gràcies nois! Salut!

---

### Post by Pablitus on 2008-11-08
Bon dia!

Si vols enganxa el contingut de l'arxiu menu.lst del grub. És el document on hi ha la informació amb que treballa l'Startupmanager. Es troba a /boot/grub. Si hi veiem l'opció del kernel que vols és molt fàcil editar-lo per què t'arrenqui amb aquesta opció per defecte.

Salut!

---

### Post by enricXIII on 2008-11-08
Ostres...em penso que el 24-21 no hi surt...

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
default         0

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
# kopt=root=UUID=c14f1e2c-8cb9-4a9d-ab6a-2aaa77c9e0f9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c14f1e2c-8cb9-4a9d-ab6a-2aaa77c9e0f9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c14f1e2c-8cb9-4a9d-ab6a-2aaa77c9e0f9 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c14f1e2c-8cb9-4a9d-ab6a-2aaa77c9e0f9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c14f1e2c-8cb9-4a9d-ab6a-2aaa77c9e0f9 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by Pablitus on 2008-11-08
Ups!

Doncs aquí jo em planto, no sé com afegir l'opció del nou kernel amb total seguretat, se m'acut afegir-lo a mà però no sé si és una burrada. 

Només dir que el segon "paràgraf", on hi fica> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0 és on es marca amb quina opció arrencar per defecte, i editant l'última línia d'aquest paràgraf canvies l'opció, ara hi tens el 0, que és la 1a opció de les que tens llistades més avall, un 1 seria la segona, i així successivament.

Pots provar l'ordre ```
update-grub
```, en trobaras més info fent```
man update-grub
```, crec que serveix precissament per actualitzar el menu.lst amb els kernels instal·lats. Però ja et dic, això serien provatures que jo faria al meu ordinador però no sé massa com va la cosa. 

Fins ara!

---

### Post by enricXIII on 2008-11-08
Gràcies Pablitus! M'esperaré abans de provar-ho a veure si algú em pot donar una mica mes d'informació...o em poden confirmar que les ordres que m'has passat son correctes..
Salut company!

---

### Post by oriolsbd on 2008-11-08
En el fitxer menu.lst no t'hi surt cap referència al kernel "2.6.24-21". L'hi hauries d'afegir. Primer, fes-te una còpia de seguretat del fitxer menu.lst. Després, afegeix aquestes línies:

```
title Ubuntu 8.04.1, kernel 2.6.24-21-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=c14f1e2c-8cb9-4a9d-ab6a-2aaa77c9e0f9 ro quiet splash
initrd /boot/initrd.img-2.6.24-21-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=c14f1e2c-8cb9-4a9d-ab6a-2aaa77c9e0f9 ro single
initrd /boot/initrd.img-2.6.24-21-generic

```

Posa-les, per exemple, davant del kernel 2.6.24-19. L'únic que he fet és agafar les mateixes línies que tu ja tenies i canviar "2.6.24-19" per "2.6.24-21". Llavors, ja les hauries de veure a l'StartUp-Manager, i també en arrancar l'ordinador.

Salut!

---

### Post by Pablitus on 2008-11-08
amb```
man update-grub
```l'únic que fas és veure la pàgina del manual d'aquesta ordre. També la pots consultar a la web: [http://manpages.ubuntu.com/manpages/hardy/en/man8/update-grub.html]("http://manpages.ubuntu.com/manpages/hardy/en/man8/update-grub.html").
Alhora d'actualitzar el menu.lst, sempre et pots fer una còpia de seguretat i si no surt bé la jugada tornar-ho a deixar com estava.

edito: Ops... No havia vist que ja t'han donat una solució més directa...

---

### Post by enricXIII on 2008-11-08
Perfecte! Gràcies companys! fent el que deia l'Oriolbsd ha funcionat a la primera.
Gràcies a tu també Pablitus per l'interes a ajudar i a tots aquells que encara que no hagin dit res , estic segur que s'ho han mirat!

---

### Post by papapep on 2008-11-08
Mengeu cues de pansa per recordar tancar els fils que s'han resolt, vinga. :-)

---

### Post by enricXIII on 2008-11-08
Vale vale! :):) Paciencia que ja m'hi estava posant!

(T'entenc papapep, es quelcom que es sol passar per alt...)

---

