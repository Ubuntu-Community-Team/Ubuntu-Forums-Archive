---
title: "Problems with grub"
date: 2009-03-06
forum: General Help
---

### Post by _El_Chojin_ on 2009-03-06
I was using windows fine, i have halted pc, and al morning when i tryed to enter to windows i get the error on grub:
Error 12: Invalid device requested

I have been reading but the changes that people say to make to menu.lst of the grub i have already done on it, i have the next menu.lst
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
# kopt=root=UUID=f7d0a8d7-5fce-44a5-803f-9c9d83b28581 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f7d0a8d7-5fce-44a5-803f-9c9d83b28581

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		f7d0a8d7-5fce-44a5-803f-9c9d83b28581
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f7d0a8d7-5fce-44a5-803f-9c9d83b28581 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		f7d0a8d7-5fce-44a5-803f-9c9d83b28581
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f7d0a8d7-5fce-44a5-803f-9c9d83b28581 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f7d0a8d7-5fce-44a5-803f-9c9d83b28581
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f7d0a8d7-5fce-44a5-803f-9c9d83b28581 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f7d0a8d7-5fce-44a5-803f-9c9d83b28581
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f7d0a8d7-5fce-44a5-803f-9c9d83b28581 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f7d0a8d7-5fce-44a5-803f-9c9d83b28581
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
makeactive
savedefault
chainloader	+1
```

What can i do because i need to enter to Windows and i wouln't like to reinstall windows or linux because will be too much heavy

---

### Post by oldos2er on 2009-03-06
Can you please post the output of
```
sudo fdisk -l
```
?

---

### Post by _El_Chojin_ on 2009-03-08
Disco /dev/sda: 40.0 GB, 40060403712 bytes
255 cabezas, 63 sectores/pista, 4870 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xf868459a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1              10        4869    39037950   83  Linux

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x48064806

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1       63741   511999551    7  HPFS/NTFS
/dev/sdb2           63742      121601   464760450    f  W95 Ext'd (LBA)
/dev/sdb5           63742       71036    58597056   83  Linux
/dev/sdb6           71037       71158      979933+  82  Linux swap / Solaris
/dev/sdb7           71159      121601   405183366   83  Linux

Disco /dev/sdc: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xcce4e1de

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdc5               2       60801   488375968+   7  HPFS/NTFS

Disco /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xab7ee5be

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdd1   *           2      121601   976752000    f  W95 Ext'd (LBA)
/dev/sdd5               2      121601   976751968+   7  HPFS/NTFS

---

### Post by meierfra. on 2009-03-08
Open the file "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Add the following to the end of the file:

title Microsoft Windows XP Professional (hd1)
root (hd1,0)
map  (hd0) (hd1)
map  (hd1) (hd0)
chainloader	+1

title Microsoft Windows XP Professional (hd2)
root (hd2,0)
map  (hd0) (hd2)
map  (hd2) (hd0)
chainloader	+1

title Microsoft Windows XP Professional (hd3)
root (hd3,0)
map  (hd0) (hd3)
map  (hd3) (hd0)
chainloader	+1


Save the file. Reboot and  try all three entries. If one of them works, you can delete all the other from menu.lst. 

If none of them worked, report any error messages you got.

---

### Post by _El_Chojin_ on 2009-03-08
Thanks, the first: title Microsoft Windows XP Professional (hd1) has worked ^^ i have another time windows.

---

### Post by meierfra. on 2009-03-08
> Thanks, the first: title Microsoft Windows XP Professional (hd1) has worked

Glad to be of help. Have fun with XP and Ubuntu,

---

