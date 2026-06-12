---
title: "boot up switches to run level 1"
date: 2008-12-28
forum: General Help
---

### Post by psycho5 on 2008-12-28
At boot, ubuntu loads the splash screen then switches to text mode as soon as it proceeds to load all the process and startup programs.

Even at shutdown, same problem. 

How do I fix it? I have the quiet splash line already there in my menu file.

Also, I want to know what's the difference between 'quiet' and 'silent' ?

Thank you for your help

---

### Post by psycho5 on 2008-12-28
*bump*

---

### Post by albinootje on 2008-12-28
> **psycho5 said:**
> At boot, ubuntu loads the splash screen then switches to text mode as soon as it proceeds to load all the process and startup programs.

Can you post the output of :
```

cat /boot/grub/menu.lst
sudo fdisk -l

```

---

### Post by psycho5 on 2008-12-28
menu.lst

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
# kopt=root=UUID=9c033811-2433-463c-85a6-556f8a61b44e ro

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
# defoptions=silent splash vga=792 quiet

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
# howmany=4

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=9c033811-2433-463c-85a6-556f8a61b44e ro silent splash vga=792 quiet
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=9c033811-2433-463c-85a6-556f8a61b44e ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=9c033811-2433-463c-85a6-556f8a61b44e ro silent splash vga=792 quiet
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=9c033811-2433-463c-85a6-556f8a61b44e ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9c033811-2433-463c-85a6-556f8a61b44e ro silent splash vga=792 quiet
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9c033811-2433-463c-85a6-556f8a61b44e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb3
title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

fdisk -l :

```
~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c064c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            7268       38913   254196495   83  Linux
/dev/sda3            1913        7267    43014037+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf475003c

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        6750    54219343+  83  Linux
/dev/hdb2            6751        7043     2353522+  82  Linux swap / Solaris
/dev/hdb3   *        7044        8955    15358140    7  HPFS/NTFS
/dev/hdb4            8956       24792   127210702+   5  Extended
/dev/hdb5            8956       24792   127210671    7  HPFS/NTFS

```

---

### Post by Coder543 on 2008-12-28
what do you mean by run level 1? run level 1 is single user mode and ctrl + alt + f1 - f6 gives you multiuser. Also, nonroot logins would be disabled. Have you tried logging in and typing sudo gdm? Are you getting a GUI already? Runlevel 1 is insufficient description unless you are literally getting [runlevel 1]("http://en.wikipedia.org/wiki/Runlevel#Typical_Linux_runlevels").

---

### Post by psycho5 on 2008-12-28
I mean, it doesn't complete booting up with the splash screen on, it falls back to text. But, Ubuntu works fine... gdm does start and I can log in normally. I think something in the startup process runs without X or something, I don't know.. I'm guessing thats why the boot screen goes away after a few seconds.


Well according to the link I guess I'm mistaken with the title of this thread, but anyway I hope you understand what I am trying to express

---

### Post by albinootje on 2008-12-28
> **psycho5 said:**
> I mean, it doesn't complete booting up with the splash screen on, it falls back to text. But, Ubuntu works fine... gdm does start and I can log in normally. I think something in the startup process runs without X or something, I don't know.. I'm guessing thats why the boot screen goes away after a few seconds.


Okay, that sounds like a small problem you can live with for the moment, no ?

And I've never seen the "silent" option before in grub.
Which Ubuntu release is this ? 6.06, 7.10, or 8.04 ?
Or is it Xubuntu or another flavor ?

---

### Post by psycho5 on 2008-12-28
It's 8.04 Ubuntu 64bit


It drops down to text mode on 

loading files needed to boot..... [OK]

from there on it boots in text till the login screen comes. 

I don't know what's causing it.

---

### Post by Coder543 on 2008-12-28
Try installing [startupmanager]("apt:startupmanager") opening it then going to appearance. Now set the usplash theme to "usplash-theme-ubuntu"
then click close
then reboot and see what happened.

---

