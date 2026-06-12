---
title: "Ubuntu missing modules"
date: 2009-03-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by SolrK on 2009-03-19
Hello, this is my problem after i install Ubuntu 8.10 in my Dell Server PowerEdge 830 the system not load he came up whit this 

Boot from (hd0 ,0) ext3 fe89cff7-ed40-41d7-b96e-bb7fdf15d5c6
starting up ....
Loading, please wait ...

Gave up waiting for root device.
Common problems:
-Boot args( cat/proc/cmdline).
-check rootdelay=( did the system wait long enough?).
- check root= (did the system wait for the righ device?).
-Missing modules ( cat/proc/modules;ls/dev)
Alert!(/dev/disk/by-uuid/fe89cff7-ed40-41d7-b96e-bb7fdf15d5c6 does not exist. Dropping to a shell!

BusyBox v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built in shell (ash)
Enter help for a lst of built in commands
(initramfs)
[90.051450] 8139cp 0000:06:00.0: this (id 10ec:8139 rev 10) is not an 8139+ compatiblechip
[90.051511] 8139cp 0000:06:00.0 try the 8139too driver instead

So i run the live cd to check the uuid in the fstab and the menu.lst from grub wish come up whit this

fstab:

# /etc/fstab: static file system information.
#
#
proc /proc proc defaults 0 0
# /dev/sda1
UUID=fe89cff7-ed40-41d7-b96e-bb7fdf15d5c6 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda2
UUID=a2168780-de34-45aa-88b7-5e72feb9555c /home ext3 relatime 0 2
# /dev/sda3
UUID=f646e03e-f70a-4123-b92f-cb3f2f2fb9cf none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

and the menu.lst from grub this:

# menu.lst - See: grub(algooooo, info grub, update-grub(algooooo
# grub-install(algooooo, grub-floppy(algooooo,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fe89cff7-ed40-41d7-b96e-bb7fdf15d5c6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fe89cff7-ed40-41d7-b96e-bb7fdf15d5c6

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid fe89cff7-ed40-41d7-b96e-bb7fdf15d5c6
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=fe89cff7-ed40-41d7-b96e-bb7fdf15d5c6 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid fe89cff7-ed40-41d7-b96e-bb7fdf15d5c6
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=fe89cff7-ed40-41d7-b96e-bb7fdf15d5c6 ro single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
uuid fe89cff7-ed40-41d7-b96e-bb7fdf15d5c6
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

then i think maybe the uuid are wrong but there were ok just as said the fstab and grub anyways i change my fstab and delete the uuid and use in stead the original path /dev/sda1 ect. but dint work out either. so now i am clueless this happens every time that i install ubuntu 8.10 desktop or server the 8.04 i can not install because jump straight to the error  so any ideas.??!

---

### Post by SolrK on 2009-03-24
Please can anyone give me a hint whit this:confused:

---

### Post by grogo on 2009-03-24
I'd check the Dell site for any Linux drivers.  They do some weird stuff with their integrated components on the desktops (don't expect lmsensors to work out of the box).  But they do have more support on the server side of things from what I've seen.

Have you tried the 9.04 installer?  What about other distros?  Fedora or CentOS are good alternatives if you need something to test with.

---

### Post by SolrK on 2009-03-28
Thanks for answer back, in this moment the only distro that i posses is Ubuntu and maybe Suse need to look for that one the version 9.04 from Ubuntu is not in me repertory since i don't have enough bandwidth to download the image i will have to wait to shipit next month. If anyone has any ideas please don't hesitate in share whit me i really need any answer.

---

