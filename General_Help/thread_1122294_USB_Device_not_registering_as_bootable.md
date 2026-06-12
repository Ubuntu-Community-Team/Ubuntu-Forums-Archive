---
title: "USB Device not registering as bootable"
date: 2009-04-10
forum: General Help
---

### Post by gamewolf on 2009-04-10
I have an 80GB USB Hard Drive with an external power source. I have 4 partitions:

1. NTFS Partition for file storage
2. Ext3 Partition for Ubuntu Desktop
3. Ext3 Partition for Ubuntu Server
4. Swap Partition

When I boot my computer, it will freeze when trying to load GRUB on the USB HD. It only has that blinking cursor in the top left corner. I have to either turn off the external power source or unplug the cable, then turn back on/replug USB cable, then reboot and it works. But when I want to reboot, I have to do the same thing again, or it will freeze at the POST.

BIOS boot order is:

1. CD-ROM
2. Hard Drive
3. USB

However, I have my hard drive disabled.

I am not sure if it is because I have the boot flags wrong on my partitions of what is wrong, but I run my server when not home and access it remotely. If I make a change, I need to restart/boot remotely and this prevents me from doing so.

Any help would be appreciated. Thanks.

---

### Post by gamewolf on 2009-04-10
Ok here is an update.

I plugged my external hard drive into another computer. It works just fine. I can restart without having to change a thing.

My first computer (the one that won't work) is a:

Dell XPS 400
Intel Pentium D 2.8GHz
3GB DDR2 533 RAM
GeForce 6800

My second computer is a:

Dell Dimension 2400
Intel Pentium 4 2.2GHz
768MB DDR 333 RAM
GeForce 5500FX

Will it not work because there is 3GB of ram in this first computer?

Hope this info helps.

---

### Post by soltanis on 2009-04-10
More likely not booting because of either your BIOS or grub. Can you post your /boot/grub/menu.lst file?

---

### Post by zephyrcat on 2009-04-10
I can't say I have any solid idea of what the problem might be, but I am suspicious of the boot order on the first computer. Can you put USB before hard drive and see what happens?

Also, does anything appear on the screen before it blanks out that might be useful?

Good luck!

---

### Post by gamewolf on 2009-04-10
The only thing that appears before the blinking cursor is the Dell loading screen.

Ill try putting USB first.

BTW, when switching computers, the new NIC Mac Address is assigned to eth1. What file do I edit to switch it back to eth0?

Here is my menu.lst

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
color cyan/blue white/blue

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
# kopt=root=UUID=e336c259-e311-44fe-886f-d5627b464019 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e336c259-e311-44fe-886f-d5627b464019

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

title		Ubuntu 8.10 Server
uuid		e336c259-e311-44fe-886f-d5627b464019
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e336c259-e311-44fe-886f-d5627b464019 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10 Server (recovery mode)
uuid		e336c259-e311-44fe-886f-d5627b464019
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e336c259-e311-44fe-886f-d5627b464019 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

#title		Ubuntu 8.10, memtest86+
#uuid		e336c259-e311-44fe-886f-d5627b464019
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
title		-------------------------
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10 Desktop
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e1f68d7e-a776-4a01-84cd-c10757744d8d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10 Desktop (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e1f68d7e-a776-4a01-84cd-c10757744d8d ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
#title		Ubuntu 8.10, memtest86+ (on /dev/sdb2)
#root		(hd0,1)
#kernel		/boot/memtest86+.bin  
#savedefault
#boot


```

---

### Post by gamewolf on 2009-04-11
Ok here is an update.

I used the OS Install option on my first computer which limits the ram to 256MB for OS Installations. It works with this. I can restart (however I have to press F1 so it doesn't help my situation much).

---

### Post by gamewolf on 2009-04-11
Here are some errors I get when booting Ubuntu Server on the first machine.

[http://i423.photobucket.com/albums/pp314/gamewolf80/DSCF0900.jpg](http://i423.photobucket.com/albums/pp314/gamewolf80/DSCF0900.jpg)

---

### Post by gamewolf on 2009-04-11
bump

---

### Post by networm1230 on 2009-04-11
try manuly mounting usb drive or look in your Bios for boot device

note use commend line (sudo)

---

### Post by gamewolf on 2009-04-11
Thanks to everyone who helped. I decided to just keep my linux installations on the second computer. It will lower power costs also.

Thanks for the help.

---

