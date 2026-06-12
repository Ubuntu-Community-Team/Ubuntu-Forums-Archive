---
title: "[SOLVED] Error 11: Unrecognized device string"
date: 2008-08-26
forum: Catalan Team
---

### Post by LitusMayol on 2008-08-26
Bones!

Estava arrencant l'ordinador i de cop:
```
 Error 11: Unrecognized device string
Press any key to continue
```

No crec que sigui massa greu, perqùe he pogut engegar tranquilament després de prémer qualsevol tecla per continuar. 

Però em preocupa. A UbuntuForums he trobat [aquest]("http://ubuntuforums.org/showthread.php?t=485022") post que té el mateix títol... Però no dec tenir el mateix. Perquè acaben resolent que es culpa del **Windows** i jo no en tinc pas en aquest ordinador!...

Algú sap què és?




Us poso el grub, per si té res a veure...
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
timeout		15

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
# kopt=root=UUID=98300a0c-c554-4d92-9d5f-a25f4e04ca50 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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



# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Escull el sistema operatiu desitjat:
root





## ## End Default Options ##

title		UbuntuStudio 8.04.1
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=98300a0c-c554-4d92-9d5f-a25f4e04ca50 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

#title		UbuntuStudio 8.04.1 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=98300a0c-c554-4d92-9d5f-a25f4e04ca50 ro single
#initrd		/boot/initrd.img-2.6.24-19-rt

#title		UbuntuStudio 8.04.1, kernel 2.6.24-16-rt
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=98300a0c-c554-4d92-9d5f-a25f4e04ca50 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-rt
#quiet

#title		UbuntuStudio 8.04.1, kernel 2.6.24-16-rt (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=98300a0c-c554-4d92-9d5f-a25f4e04ca50 ro single
#initrd		/boot/initrd.img-2.6.24-16-rt

#title		UbuntuStudio 8.04.1, memtest86+
#root		(hd0,2)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST




# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.1
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=950d8be1-e06a-4bef-9f1a-4f532c68993b ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu 8.04.1 (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=950d8be1-e06a-4bef-9f1a-4f532c68993b ro single 
#initrd		/boot/initrd.img-2.6.24-19-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sda2)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=950d8be1-e06a-4bef-9f1a-4f532c68993b ro quiet splash 
#initrd		/boot/initrd.img-2.6.24-16-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda2)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=950d8be1-e06a-4bef-9f1a-4f532c68993b ro single 
#initrd		/boot/initrd.img-2.6.24-16-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu 8.04.1, memtest86+ 
#root		(hd0,1)
#kernel		/boot/memtest86+.bin  
#savedefault
#boot
```

---

### Post by papapep on 2008-08-26
Jo crec que si no ens amplies una mica l'entorn de l'error és molt complicat Litus....en quin moment de l'arrencada surt? què es veu abans i després en el procés d'arrencada?? has canviat alguna cosa i per això ara surt? o ja sortia abans i no t'havies fixat??? tindrà a veure amb els malabars que portes fent fa dies amb el grub, l'fstab i demés galindaines???? :-D

---

### Post by LitusMayol on 2008-08-27
A veure...


> en quin moment de l'arrencada surt?
L'error el dóna just abans de deixar-me escollir entre **Ubuntu** i **UbuntuStudio**.

> què es veu abans i després en el procés d'arrencada?? 
Doncs no sé... lo que sempre es veu mentre arrenca l'ordinador... Primer la BIOS i tota la pesca, després em fa escollir OS i arrenca normal.

> has canviat alguna cosa i per això ara surt? o ja sortia abans i no t'havies fixat??? tindrà a veure amb els malabars que portes fent fa dies amb el grub, l'fstab i demés galindaines???? 
Ahir a la tarda hi vaig estar rumiant i crec que surt desde que vaig fer l'automontatge de la partició. (El *grub* està a dalt i jo diria que no té res de raro), pel que fa al "*fstab*" ara no el puc *post*ejar, sóc a la feina, però a veure si el meu germà el penja.

Però tampoc ho entenc, en principi l'automontatge no hauria de tenir-hi res a veure, no?

A veure si algú sap que pot ser! ;)

Merci!

---

### Post by LitusMayol on 2008-08-27
Bones, 
(sóc el germà del Carles)
Això es el que tenim al "*fstab*"

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=950d8be1-e06a-4bef-9f1a-4f532c68993b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=cf672e53-68b4-4f57-ad1a-9321503dbf0c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda3
UUID=98300a0c-c554-4d92-9d5f-a25f4e04ca50 /media/UbuntuStudio               ext3    relatime,errors=remount-ro 0       1

---

### Post by oriolsbd on 2008-08-27
Hola, una cosa. No sé si és això, però em sona molt malament lo del "/dev/scd0". No hauria de ser "/dev/sdc0"? Pot ser que no sigui això (no ho puc comprovar perquè no estic a casa) però lliga amb el missatge, on diu que no es reconeix el nom del dispositiu.

Fes la prova modificant el fstab. Si veus que no és això, torna-ho a deixar com estava. :-)  (Si no era això, l'únic que pot passar és que no puguis utilitzar el CDROM fins que no tornis a fer el canvi a la inversa)

Salut!

Oriol.

---

### Post by LitusMayol on 2008-08-27
> **oriolsbd said:**
> Hola, una cosa. No sé si és això, però em sona molt malament lo del "/dev/scd0". No hauria de ser "/dev/sdc0"? Pot ser que no sigui això (no ho puc comprovar perquè no estic a casa) però lliga amb el missatge, on diu que no es reconeix el nom del dispositiu.

Fes la prova modificant el fstab. Si veus que no és això, torna-ho a deixar com estava. :-)  (Si no era això, l'únic que pot passar és que no puguis utilitzar el CDROM fins que no tornis a fer el canvi a la inversa)

Salut!

Oriol.

Clavada.

Era això. No sé pas com vaig arribar a modificar-ho, però si: era això. Ara que he anat a dinar a casa ho he provat i ja està. Solucionat.


Merci a tots! ;)

---

