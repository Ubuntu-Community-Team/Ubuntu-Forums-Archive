---
title: "Boot Loader problem"
date: 2009-01-10
forum: General Help
---

### Post by oldtraveler on 2009-01-10
Boot Loader for Ubuntu 8.10.  I just installed this distro and it set up a new boot loader with, not suprprisingly, Ubuntu 8.10 as the default OS to be booted. I can opt to boot my other Linux distro and/or Windows XP.  I wish to set Windows as the default OS. How do I do this using the boot loader that Ubuntu 8.10 installed by default?

Or alternatively I have GAG which will boot any of my OS EXCEPT Ubuntu.  When I try to add the Ubuntu OS to that loader it tells me that it doesn't see that OS.

---

### Post by 2hot6ft2 on 2009-01-10
You could either edit the menu.lst file. There are hints in the file to help.
```
gksudo gedit /boot/grub/menu.lst
```
or install Start-Up Manager and set it with it. In synaptic search for "sum" without the ""'s mark it for install and hit apply.
System>Administration>Synaptic Package Manager

Then it will be in
System>Administration>Start-Up Manager
You can use it to set other options as well

---

### Post by oldtraveler on 2009-01-11
I'm afraid that I don't really understand the syntax of Menu.1st.  Below is a copy.  Will you steer me in the right direction so that I can set 
[color=blue] # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1 [/color]
as the default boot?


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
# kopt=root=UUID=4fa05936-9e3f-4f26-a031-cce8fd33ad4b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4fa05936-9e3f-4f26-a031-cce8fd33ad4b

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		4fa05936-9e3f-4f26-a031-cce8fd33ad4b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4fa05936-9e3f-4f26-a031-cce8fd33ad4b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		4fa05936-9e3f-4f26-a031-cce8fd33ad4b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4fa05936-9e3f-4f26-a031-cce8fd33ad4b ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4fa05936-9e3f-4f26-a031-cce8fd33ad4b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4fa05936-9e3f-4f26-a031-cce8fd33ad4b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4fa05936-9e3f-4f26-a031-cce8fd33ad4b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4fa05936-9e3f-4f26-a031-cce8fd33ad4b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4fa05936-9e3f-4f26-a031-cce8fd33ad4b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

[color=blue]
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1[/color]


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title		linux - PCLINUXOS (on /dev/sdb6)
root		(hd1,5)
kernel		/boot/vmlinuz BOOT_IMAGE=linux_-_PCLINUXOS root=/dev/hdb6 acpi=on resume=/dev/hdb7 vga=791 
initrd		(hd1,5)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title		failsafe (on /dev/sdb6)
root		(hd1,5)
kernel		/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/hdb6 failsafe acpi=on resume=/dev/hdb7 
initrd		(hd1,5)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title		linux-Xandros (on /dev/sdb6)
root		(hd1,5)
kernel		/boot/vmlinuz BOOT_IMAGE=linux-Xandros root=/dev/hdb8 
initrd		(hd1,5)/boot/initrd.img
savedefault
boot

==========================================
Also I tried to find Start_UP Manager by looking for "In synaptic search for "sum" without the ""'s mark it for install and hit apply."  In Synaptic Manager using search nothing turned up for sum.

---

### Post by chex_m8 on 2009-01-11
near the beginning of the menu.lst there is a section that says
default 0
change this to say 
default 6
windows is the 7th entry in your menu but linux starts count from 0
GL

---

### Post by oldtraveler on 2009-01-11
That fixed it.  Thank you.

---

