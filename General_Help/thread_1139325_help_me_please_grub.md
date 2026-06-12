---
title: "help me please: grub"
date: 2009-04-26
forum: General Help
---

### Post by dark_mage93 on 2009-04-26
hi,
I really need some help. I've looked all over for solutions but still can't fix this.
I was trying to make Grub have a graphic interface just to look better.. I thought it would be an easy thing to do just to make things better looking. Unfortunately, it didn't work out. Whatever thread I was following told me to uninstall grub and install some other bootloader. I think that's what my problem is. Now, when I startup, I just go straight to a Grub prompt. It doesn't give me the boot options from my menu.lst file, and I can't boot into XP (on an IDE drive) or Ubuntu (on a SATA drive). This is not good.. how should I go about reinstalling Grub when I can't even boot??!?

thanks for help :)

---

### Post by Merk42 on 2009-04-26
Get a LiveCD then follow these instructions
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by dark_mage93 on 2009-04-27
I followed that guide; grub said that it was successful, but on reboot nothing changes - I go right to the grub menu but what do I do from there??!

---

### Post by Merk42 on 2009-04-27
What does GRUB have for options?
(seen in /boot/grub/menu.lst)

---

### Post by dark_mage93 on 2009-04-27
this is my menu.lst file:

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
timeout		5

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
# kopt=root=UUID=100a754d-7c13-4c0b-ad0e-335ca30a9e35 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=100a754d-7c13-4c0b-ad0e-335ca30a9e35

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
uuid		100a754d-7c13-4c0b-ad0e-335ca30a9e35
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=100a754d-7c13-4c0b-ad0e-335ca30a9e35 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		100a754d-7c13-4c0b-ad0e-335ca30a9e35
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=100a754d-7c13-4c0b-ad0e-335ca30a9e35 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		100a754d-7c13-4c0b-ad0e-335ca30a9e35
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=100a754d-7c13-4c0b-ad0e-335ca30a9e35 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		100a754d-7c13-4c0b-ad0e-335ca30a9e35
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=100a754d-7c13-4c0b-ad0e-335ca30a9e35 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		100a754d-7c13-4c0b-ad0e-335ca30a9e35
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=100a754d-7c13-4c0b-ad0e-335ca30a9e35 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		100a754d-7c13-4c0b-ad0e-335ca30a9e35
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=100a754d-7c13-4c0b-ad0e-335ca30a9e35 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		100a754d-7c13-4c0b-ad0e-335ca30a9e35
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

---

### Post by dark_mage93 on 2009-04-27
I got to that file by accessing it through the live cd though; I can't find it when I boot from my hard drive and it goes right to the grub> prompt..

---

### Post by thegr8brian on 2009-04-27
I am having a similar issue with the computer just sitting at the grub prompt after trying to reinstall grub multiple times on a live-cd...any ideas?

---

### Post by Merk42 on 2009-04-30
dark_mage93

What was the other bootloader?

Does /boot/grub contain the files listed? As in **vmlinuz-2.6.27-11-generic** and **initrd.img-2.6.27-11-generic**?

I'm not sure what's going on with those map values for dual booting XP.  Maybe just put a # in front of every line from title to chainloader after **### END DEBIAN AUTOMAGIC KERNELS LIST**  it'll comment it out, so Windows won't boot, but let's try to solve one problem at a time.

---

### Post by dark_mage93 on 2009-04-30
I installed from a live CD and it fixed (reinstalled) grub to the new partition.. I am now able to boot into my old install as well as windows so I'm fine thanks

---

### Post by lisati on 2009-04-30
One way way of dollying up the grub menu that is simple and safe is to uncomment the line in menu.lst that deals with colour. On my systems I changed the line that reads: > #color cyan/blue white/blue to read: ```
color cyan/blue white/blue
```

---

