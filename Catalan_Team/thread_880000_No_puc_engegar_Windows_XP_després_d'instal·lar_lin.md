---
title: "No puc engegar Windows XP després d'instal·lar linux"
date: 2008-08-04
forum: Catalan Team
---

### Post by ktix007 on 2008-08-04
El meu PC té dos discs durs: C i D quan el vaig comprar al C hi havia el Windows Vista i al D hi vaig instal·lar el windows Xp. Avui he tret el vista i he instal·lat el Linux Mint al disc dur C i ara no puc engegar el Windows XP :(. Des del Linux Mint puc entrar al dic D i per tant sé que no s'ha esborrat el Windows XP.

Si em podeu ajudar us ho agraire molt :KS

Pd: Ja sé que això és el fòrum de Ubuntu però no sabia on posar-ho...

---

### Post by Pablitus on 2008-08-04
Hola Ktix007!

Segur que en un forum sobre la teva distribució et poden ajudar més que en aquest, vamos, suposo. No sé fins a quin punt son diferents linux mint i ubuntu. 

Potser és qüestio del GRUB. Pots veure el què és el GRUB a la Viquipèdia. És un gestor d'arrencada que en engegar l'ordinador et pregunta quin sistema operatiu vols iniciar, i és el que s'instal·la amb ubuntu, no sé si amb linux mint tamé. La configuració d'aquest programa està en un fitxer anomenat "menu.lst" a la carpeta /boot/grub.

Penja aquí el què hi hagi en aquest fitxer i a veure què.

No sé si podré ajudar gaire, també soc bastant nou en tot això.

Ah, tens dues particions diferents en el mateix disc dur o dos discs durs diferents?

Salut!

---

### Post by torracastanyes on 2008-08-04
Hola Ktix.

Tal com diu en Pablitus, sembla un problema de GRUB.

Crec que aquestos posts et poden ajudar:

[http://www.espaciolinux.com/foros-tema-t36049.html](http://www.espaciolinux.com/foros-tema-t36049.html)
[http://www.espaciolinux.com/foros-tema-t37227.html](http://www.espaciolinux.com/foros-tema-t37227.html)

Son per Ubuntu, pero Linux Mint és molt semblant i les instruccions serveixen igual en tots dos.

Per cert, Linux Mint no té fòrum en català, que jo sàpiga, però en té un de molt actiu en castellà.

---

### Post by ktix007 on 2008-08-05
Al GRUB em surt el Linux Mint i a "Other Sistems" una cosa per recuperar el windows vista pero no hi surt pas cap error i el Windows Xp no hi surt...

---

### Post by ktix007 on 2008-08-05
Tinc dues particions i al menu.lst hi diu això:
```

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
# kopt=root=UUID=09ccb620-e120-4e0f-94cd-a3a218acd1ec ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Linux Mint (Light Edition), kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=09ccb620-e120-4e0f-94cd-a3a218acd1ec ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Linux Mint (Light Edition), kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=09ccb620-e120-4e0f-94cd-a3a218acd1ec ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint (Light Edition), memtest86+
root		(hd0,1)
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
```

---

### Post by Pablitus on 2008-08-05
I què passa si en engegar l'ordinador tries al GRUB la última opció, que inicii el vista? Ho has provat?

Pel que deies al principi d'unitats C i D sembla que el vista el tenies a la primera partició, que el grub anomena (hd0,0), i l'XP a la segona, (hd0,1), i el linux mint diria que l'has instal·lat on tenies l'XP, a la segona, (hd0,1). Pot ser? L'opció del final, després d'"Other operating systems" és per iniciar el vista, no per recuperar-lo.

Salut!!
Pau

---

### Post by LitusMayol on 2008-08-05
> **Pablitus said:**
> I què passa si en engegar l'ordinador tries al GRUB la última opció, que inicii el vista? Ho has provat?

Pel que deies al principi d'unitats C i D sembla que el vista el tenies a la primera partició, que el grub anomena (hd0,0), i l'XP a la segona, (hd0,1), i el linux mint diria que l'has instal·lat on tenies l'XP, a la segona, (hd0,1). Pot ser? L'opció del final, després d'"Other operating systems" és per iniciar el vista, no per recuperar-lo.

Salut!!
Pau

Crec que en **Pablitus** té raó: has instal·lat el **GNU/Linux** a la partició on hi tenies el **Windows XP**. Compraba-ho.

És tan fàcil com que quan engeguis l'ordinador, al grub escolleixis el **Windows Vista**. Si l'engega correctament és que has instal·lat **GNU/Linux** a l'altra partició. En cas d'error digues que et diu!

Sort!

---

### Post by Randemar on 2008-09-15
A jo també em va passar una cosa similar avui a s'horabaixa quan instal·lava Ubuntu al meu portàtil, malgrat haver respectat la partició del XP. Ho vaig solucionar reinstal·lant Ubuntu i en arribar al pas de les particions vaig posar el signe / al punt de montatge només a la partició de Ubuntu, abans ho havia posat a totes dues i als llocs del meu sistema no hi apareixia la carpeta "BOOT" que és la partició on hi estava XP.
Salutacions.

---

