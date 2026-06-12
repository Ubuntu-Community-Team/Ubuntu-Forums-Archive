---
title: "Booting"
date: 2009-02-03
forum: General Help
---

### Post by lulemurfan on 2009-02-03
Hello, This is the first time in trying xubuntu.

When my laptop boots up it get to the stage saying 'Press 'ESC' to enter the menu.. 2' At this point it stops, the only way to boot is pressing 'ESC' and enter.

Is there anyway of stopping happening?

Thanks

---

### Post by cmnorton on 2009-02-03
It sounds like your /boot/grub/menu.lst file got fouled up. Either your timeout line was commented out or you have a long timeout

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

Once you boot, edit the file as sudo and make sure this is set properly.

---

### Post by lulemurfan on 2009-02-04
I don't understand the last thread - can i have some help!!

---

### Post by plucky on 2009-02-04
> **lulemurfan said:**
> I don't understand the last thread - can i have some help!!

1) Boot Xubuntu operating system
2) Login
3) Open a terminal window **Applications > Accessories > Terminal** and input these commands ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
``` 
It will ask for your password,input login password,which will not echo any output.This command makes a backup copy of the file menu.lst.

Then ```
sudo nano /boot/grub/menu.lst
```

Scroll down until you find the text indicated by **cmnorton** and see what the timeout value is set to.Change it to 3.

**Try a reboot to see if it works.**


If that doesn't work,then, copy and paste to the forum the output of this terminal command ```
cat /boot/grub/menu.lst
```


Good Luck

---

### Post by lulemurfan on 2009-02-04
not working here is the code:-
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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=78bffc2a-6701-423b-bcf2-cdb5d5a48153 ro

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=78bffc2a-6701-423b-bcf2-cdb5d5a48153 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=78bffc2a-6701-423b-bcf2-cdb5d5a48153 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=78bffc2a-6701-423b-bcf2-cdb5d5a48153 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=78bffc2a-6701-423b-bcf2-cdb5d5a48153 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by plucky on 2009-02-04
The menu.lst file looks ok,the only thing is that you have ```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```
enabled.Perhaps edit the file and put a # in front of **hiddenmenu** just to see if the boot menu actually comes up.

> 'Press 'ESC' to enter the menu.. 2'

That number should count down.

Does the countdown actually stop?
What happens if you don't press "ESC" and "enter"?

Edit:Just tried booting my Xubuntu 8.04.2 using your menu.lst file with the default root device changed to my system and it booted ok.

---

### Post by lulemurfan on 2009-02-04
it doesn't count down

---

### Post by icanfly0307 on 2009-02-04
Try removing the timeout line completely. that would just give you the normal GRUB menu.

---

### Post by cmnorton on 2009-02-05
> **icanfly0307 said:**
> Try removing the timeout line completely. that would just give you the normal GRUB menu.

How do you have no timeout?

---

