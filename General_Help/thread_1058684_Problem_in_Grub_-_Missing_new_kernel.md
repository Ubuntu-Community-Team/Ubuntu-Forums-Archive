---
title: "Problem in Grub - Missing new kernel"
date: 2009-02-03
forum: General Help
---

### Post by Georgie.Mathews on 2009-02-03
Hi there, I have updated my kubuntu system and I did see the new kernel (2.6.27-11) as an addition to the older one (2.6.27-7).

Now for some reason it doesn't appear in grub anymore. Here is the output of sudo update-grub

```
gmathews@KDE-Machine:~$ sudo update-grub
[sudo] password for gmathews:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

And here is my /boot/grub/menu.lst

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
# kopt=root=UUID=22c51a1a-122a-4f37-b761-1b65d3c90ffb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=22c51a1a-122a-4f37-b761-1b65d3c90ffb

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		22c51a1a-122a-4f37-b761-1b65d3c90ffb
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=22c51a1a-122a-4f37-b761-1b65d3c90ffb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		22c51a1a-122a-4f37-b761-1b65d3c90ffb
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=22c51a1a-122a-4f37-b761-1b65d3c90ffb ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		22c51a1a-122a-4f37-b761-1b65d3c90ffb
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
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6559b77f-731b-4437-a827-cd57d3a2aa19 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6559b77f-731b-4437-a827-cd57d3a2aa19 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

How do I get my new kernel to show? Thanks.

---

### Post by caljohnsmith on 2009-02-03
It wouldn't be difficult to manually add an entry in your menu.lst for the new kernel, but it is a bit concerning that "update-grub" finds the new kernel and yet does not put it in your menu.lst. How about trying:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo update-grub
```
And let me know if update-grub then adds the new kernel to your menu.lst. We can work from there if necessary.

---

### Post by Georgie.Mathews on 2009-02-03
Hey caljohnsmith

I added this line and it worked..just concerned about it not doing it automatically..

```
title		Kubuntu 8.10, kernel 2.6.27-11-generic
uuid		22c51a1a-122a-4f37-b761-1b65d3c90ffb
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=22c51a1a-122a-4f37-b761-1b65d3c90ffb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```

Will try your method if my line gets removed for some reason :)

---

