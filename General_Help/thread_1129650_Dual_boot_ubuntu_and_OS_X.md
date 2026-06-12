---
title: "Dual boot ubuntu and OS X"
date: 2009-04-18
forum: General Help
---

### Post by Predtech on 2009-04-18
Hi guys, i really need some help with a little problem i have, so here goes...
I have 160GB SATA drive that i have partitioned into 3 partitions.
let's call it sda, so....
Mac OS X is on sda1
Ubuntu is on sda2
SWAP is on sda3.

I have grub working to boot my windows XP installation on my slave drive but i can't get grub to boot OS X no matter what i try.
here is a copy of my menu.lst
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		3

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
# kopt=root=UUID=a4f8022b-a0cd-4def-bd4c-21ec7c7c50f5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a4f8022b-a0cd-4def-bd4c-21ec7c7c50f5

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
uuid		a4f8022b-a0cd-4def-bd4c-21ec7c7c50f5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a4f8022b-a0cd-4def-bd4c-21ec7c7c50f5 ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		a4f8022b-a0cd-4def-bd4c-21ec7c7c50f5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a4f8022b-a0cd-4def-bd4c-21ec7c7c50f5 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.27-11-generic

title           MacOSX Leopard
root            (hd0,0)
makeactive
chainloader     +1
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd1) (hd0)
chainloader	+1

Everytime i try to boot into OS X i get an error. Either error 17, 18, or 13 (i think!)
No matter what (drive,partition) numbers i choose i always seem to get some sort of error, mostly 18 or 17.

Can anyone PLEEEEEEEEEEASE help me figure out what is going wrong so i can fix it.

Thanks

---

### Post by Locutus_of_Borg on 2009-04-18
[http://www.insanelymac.com/forum/lofiversion/index.php/t85508.html](http://www.insanelymac.com/forum/lofiversion/index.php/t85508.html)

this works for me using osx86

---

### Post by Shazaam on 2009-04-18
First move this...
```
title MacOSX Leopard
root (hd0,0)
makeactive
chainloader +1

```
to here...
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd1) (hd0)
chainloader +1 
```
between "root" and the Windows entry.
Next run this in terminal...
```
sudo fdisk -lu
```
(lowercase LU) and check your partition info (hd0,0) to make sure you have OSX listed correctly in grub.

---

### Post by Predtech on 2009-04-18
@ Locutus_of_Borg
> **Locutus_of_Borg said:**
> [http://www.insanelymac.com/forum/lofiversion/index.php/t85508.html](http://www.insanelymac.com/forum/lofiversion/index.php/t85508.html)

this works for me using osx86

regarding this, i don't understand the guide when it refers to
"2) dd boot1h to the partition you have OS X installed onto."

I have no idea what this means....

@ Shazaam
> **Shazaam said:**
> First move this...
```
title MacOSX Leopard
root (hd0,0)
makeactive
chainloader +1

```
to here...
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd1) (hd0)
chainloader +1 
```
between "root" and the Windows entry.
Next run this in terminal...
```
sudo fdisk -lu
```
(lowercase LU) and check your partition info (hd0,0) to make sure you have OSX listed correctly in grub.

After doing what you said not all i get is
Error 23: Error parsing number

Now what i have is....
> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
title           MacOSX Leopard
root            (h0,0)
makeactive
chainloader     +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd1) (hd0)
chainloader	+1



Any ideas?

---

### Post by Shazaam on 2009-04-18
Sorry I should have made it clearer...
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda
title MacOSX Leopard
root (h0,0)
makeactive
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd1) (hd0)
chainloader +1
```
If you run into trouble here is a good site for grub help...
[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors)
Here is the entry for your grub error...
```
Quoted from the GNU/GRUB manual

    23 : Error while parsing number
        This error is returned if GRUB was expecting to read a number and encountered bad data. 

For example, this error can be reproduced in CLI mode GRUB by typing 'root (hdO)' insetad of  'root (hd0)'.

The '0' in  '(hd0)' is a number zero, not a capital letter 'O'. If you type a capital letter 'O' in pace of a number '0' in this context, you will receive this error message.

I try to make sure there is no confusion between the number 0 and letter O in my web pages by using bitstream vera sans mono font wherever I think of it, that way the number 0 has a dot in the middle of it like terminal font.
For example, you can see that 0 is different from O.



```

---

### Post by Locutus_of_Borg on 2009-04-19
skip the chameleon part

just use the PC_EFI method

---

### Post by Predtech on 2009-04-19
> **Locutus_of_Borg said:**
> skip the chameleon part

just use the PC_EFI method

Holy **** Batman, it actually worked. Once i did the PC_EFI method it booted perfectly.

Thanks man, you're a lifesaver

:D

---

### Post by Shazaam on 2009-04-19
> **Locutus_of_Borg said:**
> skip the chameleon part

just use the PC_EFI method

Thanks for the info!

---

