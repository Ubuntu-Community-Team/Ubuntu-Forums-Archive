---
title: "how to grub"
date: 2009-06-05
forum: General Help
---

### Post by Zom-b on 2009-06-05
how do I add another partition to my grub menu, or edit it to show one I have made?

---

### Post by philinux on 2009-06-05
Depends what you've installed on this new partition.

---

### Post by jgor on 2009-06-05
In a terminal type:
```
sudo mousepad /boot/grub/menu.lst
```
This file is very well commented but be careful with editing it, faulty editing can prevent Grub from starting. If Grub cannot start you will need a live CD or the like to fix it. Because of this I recommend reading the entire file before editing it.

---

### Post by Zom-b on 2009-06-05
it's zenwalk, I was going to try it out, and I installed it over an old xubuntu partition I had, and when it go to the part where it wanted to know if I wanted to use lilo or not, because I figured it would just show up on grub

---

### Post by VMC on 2009-06-05
> **Zom-b said:**
> it's zenwalk, I was going to try it out, and I installed it over an old xubuntu partition I had, and when it go to the part where it wanted to know if I wanted to use lilo or not, because I figured it would just show up on grub

So how did you answer the question - Grub or Lilo?

---

### Post by Zom-b on 2009-06-05
I said grub. but it doesn't show up, it's just ubuntu shown on boot up

---

### Post by Legace on 2009-06-05
Post the contents of menu.lst here.
```
sudo gedit /boot/grub/menu.lst
```

Also post the output of the following command:
```
sudo fdisk -l
```

And, tell us what (Windows?) you want to add to GRUB and which partition its on-

---

### Post by Zom-b on 2009-06-05
here is the output of munu.lst
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
# kopt=root=UUID=032afc87-0ad0-4c46-8d62-314ba10973ba ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=032afc87-0ad0-4c46-8d62-314ba10973ba

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		032afc87-0ad0-4c46-8d62-314ba10973ba
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=032afc87-0ad0-4c46-8d62-314ba10973ba ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		032afc87-0ad0-4c46-8d62-314ba10973ba
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=032afc87-0ad0-4c46-8d62-314ba10973ba ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		032afc87-0ad0-4c46-8d62-314ba10973ba
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.24-24-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.24-24-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f ro single 
initrd		/boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=99c70166-80da-457d-85db-51c97b01ffb3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=99c70166-80da-457d-85db-51c97b01ffb3 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

and here is the output of fdisk -l

```

zomb@zomb-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51d751d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4083    32796666   83  Linux
/dev/sda2            4084        9729    45351495    5  Extended
/dev/sda5            9472        9729     2072353+  82  Linux swap / Solaris
/dev/sda6            8173        9410     9944172   83  Linux
/dev/sda7            9411        9471      489951   82  Linux swap / Solaris
/dev/sda8            4084        7998    31447174+  83  Linux
/dev/sda9            7999        8172     1397623+  82  Linux swap / Solaris

Partition table entries are not in disk order
zomb@zomb-laptop:~$ 

```

---

### Post by Legace on 2009-06-06
You didn't tell what entry you want to add to GRUB (Windows, a Linux distro, etc.) :)

---

### Post by Zom-b on 2009-06-08
> **Legace said:**
> You didn't tell what entry you want to add to GRUB (Windows, a Linux distro, etc.) :)

ahh, how would I go about adding that then?

---

