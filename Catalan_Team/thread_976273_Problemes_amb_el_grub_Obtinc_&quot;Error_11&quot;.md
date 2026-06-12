---
title: "Problemes amb el grub: Obtinc &quot;Error 11&quot;"
date: 2008-11-09
forum: Catalan Team
---

### Post by Marc_CAT on 2008-11-09
Bon dia a tothom!

Primer de tot, fer-vos saber que sóc principiant en Ubuntu, l'he fet servir uns quants cops però sempre a nivell d'usuari. 

Ara us vull plantejar un problema que m'ha sorgit quan he volgut instal·lar la nova versió d'Ubuntu.
-A l'ordinador tenia instal·lat en una partició un Windows XP, amb una altra partició per a dades. També tenia reservada una petita partició de 15 GB per a posar-hi l'Ubuntu 8.10.

El problema em sorgeix quan una vegada instal·lat l'Ubuntu, vull carregar Windows i obtinc 

**Error 11: Unrecognized device string**


Imagino que serà cosa del grub, i més concretament, de la partició que indico que ha d'estar el Windows. Us enganxo el menu.lst
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

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
# kopt=root=UUID=ec94d835-4df8-432f-83a2-ab26fdbfa389 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ec94d835-4df8-432f-83a2-ab26fdbfa389

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

title		Iniciar Windows XP
root		hda(1,0)
makeactive
chainloader	+1

title		Ubuntu 8.10
uuid		ec94d835-4df8-432f-83a2-ab26fdbfa389
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ec94d835-4df8-432f-83a2-ab26fdbfa389 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ec94d835-4df8-432f-83a2-ab26fdbfa389
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ec94d835-4df8-432f-83a2-ab26fdbfa389 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ec94d835-4df8-432f-83a2-ab26fdbfa389
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```

i el respectiu fdisk per si fes falta
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe377e377

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1960        7058    40957717+   7  HPFS/NTFS
/dev/sda3            7059       30400   187494615    f  W95 Ext'd (LBA)
/dev/sda4            1825        1959     1084387+  82  Linux swap / Solaris
/dev/sda5            7059       30400   187494583+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdf: 8006 MB, 8006926336 bytes
16 heads, 32 sectors/track, 30544 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       30544     7819248    c  W95 FAT32 (LBA)
```

Algú em podria ajudar a saber què he de fer per a poder iniciar Windows? La família em matarà sino hehehehe

Gràcies!

---

### Post by Rubunter on 2008-11-09
Per anar bé tinc entès que el Windows ha d'anar sempre abans que el Linux en la taula de particions. Com solucionar-ho en el punt on et trobes tu actualment...ni idea.

---

### Post by LitusMayol on 2008-11-09
Ep!

A mi em va passar també fa un temps. EL problema en sí és que l'entrada del GRUB porta a una adreça equivocada. Per exemple, en el meu [cas]("http://ubuntuforums.org/showthread.php?t=901396&highlight=error+11+grub") havia de canviar *scd0* per *sdc0*. 

Jo recomanaria que ens pengéssis el teu */etc/fstab*.

;)

---

### Post by Marc_CAT on 2008-11-09
Aquí teniu:

```

/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ec94d835-4df8-432f-83a2-ab26fdbfa389 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=e664a425-31ca-4f80-9b3f-e91d0389a3ab none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Gràcies!!

---

### Post by LitusMayol on 2008-11-09
Prova de canviar en aquesta línia:

```
UUID=e664a425-31ca-4f80-9b3f-e91d0389a3ab none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Prova de canviar el *"scd0"* per sdc0!

---

### Post by Marc_CAT on 2008-11-09
Continua igual...

---

### Post by papapep on 2008-11-09
Quan has instal·lat l'Ubuntu, li has dit que posi el grub al MBR o a la partició arrel de l'Ubuntu?

---

### Post by Marc_CAT on 2008-11-09
Doncs ho vaig fer fa uns dies i no ho recordo, hi hauria alguna manera d'esbrinar-ho?

Gràcies a tots

---

### Post by SiscoGarcia on 2008-11-09
Una manera d'esbrinar-ho és des del terminal amb la comanda:

```
~$ whereis grub

```

---

### Post by Marc_CAT on 2008-11-09
Dóna això
```
grub: /usr/sbin/grub  /etc/grub.d  /usr/lib/grub  /usr/share/man/man8/grub.8.gz
```

---

### Post by SiscoGarcia on 2008-11-09
Bé, doncs provem una altra cosa; què et diu si fas:

```
cd /boot/

```
i després, quan ja ets a ":/boot$" (sense cometes) hi dius:

```
ls
```

T'hi apareix el grub? Enganxa'ns el resultat, sisplau.

---

### Post by Marc_CAT on 2008-11-09
Sí, sí que hi apareix

Aquí teniu els resultats. He fet un ls -l per veure-ho amb més claredat

```
marc@marc-desktop:/boot$ ls -l
total 11944
-rw-r--r-- 1 root root  507665 2008-10-24 10:29 abi-2.6.27-7-generic
-rw-r--r-- 1 root root   91364 2008-10-24 10:29 config-2.6.27-7-generic
drwxr-xr-x 2 root root    4096 2008-11-08 14:46 grub
-rw-r--r-- 1 root root 8183062 2008-11-05 20:48 initrd.img-2.6.27-7-generic
-rw-r--r-- 1 root root  124152 2008-09-11 22:11 memtest86+.bin
-rw-r--r-- 1 root root 1029585 2008-10-24 10:29 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root    1073 2008-10-24 10:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r-- 1 root root 2244272 2008-10-24 10:29 vmlinuz-2.6.27-7-generic
```

---

### Post by SiscoGarcia on 2008-11-09
Doncs no ho entenc, perquè jo ho tinc semblant i no tinc problemes. El que fa estona que em resulta sospitós és el que tens al menu.lst, ja que hi hauria d'haver una cosa semblant a:
```

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=af58ba2d-7ed4-407b-8d5b-b5dca110bd70 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=af58ba2d-7ed4-407b-8d5b-b5dca110bd70 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
```

que és el que jo tinc, i no el que tens a l'equivalent a les segones línies (les que comencen per root), que em resulta molt estrany.

D'altra banda, veig que tens el sector d'arrencada a sda1 mirant el teu fdisk, no sé si no ho hauries de posar a pèl a les segones línies, vull dir, substituir-les per ```
root  (hd0,1)
``` però és una cosa perillosa que no acabo de controlar i en el teu cas m'esperaria a veure què diuen els que saben. Ara bé, si no és una màquina productiva pots provar-ho i si peta tornar a instal·lar, però no és la forma elegant de treballar :confused:

---

### Post by Marc_CAT on 2008-11-10
Moltes gràcies per les respostes. Bé, tinc la famíla una mica emprenyada perquè no poden fer servir l'ordinador, així que suposo que tiraré pel dret i el desinstal·laré, i quan tingui més temps tornaré a mirar-m'ho, però aquesta vegada sabent des de bon començament què tinc i com ho he de fer.

Marc

---

