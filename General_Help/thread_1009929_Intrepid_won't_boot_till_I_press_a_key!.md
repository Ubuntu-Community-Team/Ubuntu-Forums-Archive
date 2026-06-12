---
title: "Intrepid won't boot till I press a key!"
date: 2008-12-13
forum: General Help
---

### Post by Friccy on 2008-12-13
Hi guys!
I still have a problem with Intrepid.
It will not boot untill I keep pressing a key!
Please help, because I have lots of things installed and don't want to reinstall the older version of Ubuntu!
Here are the specs: HP Pavilion 6645en, AMD Turion 64X2, Nvidia graphics.
Thanks!

---

### Post by linux_tech on 2008-12-13
1st backup menu.lst
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

Edit menu.lst
```
sudo gedit /boot/grub/menu.lst
```

then post menu.lst

---

### Post by maestrobwh1 on 2008-12-13
Not sure where your hangup is occurring.  Mine was due to an upgrade from hardy.  If the progress bar on the Usplash goes part way over, and is hanging there, make sure your /etc/network/interfaces file only has this entry:

auto lo
iface lo inet loopback

and comment out everything else... don't delete the lines in case you have network issues.  Intrepid seems to use other means of identifying and connecting to a network.  Other things in there seem to cause a hang.  I found this out when I booted in recovery mode and saw where the text stopped scrolling.

---

### Post by Friccy on 2008-12-13
Hi!
Here you have the outcome of the menu.lst

menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=14bb5e39-b350-43c7-8c8d-9ba815de10fe ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=14bb5e39-b350-43c7-8c8d-9ba815de10fe

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
uuid		14bb5e39-b350-43c7-8c8d-9ba815de10fe
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=14bb5e39-b350-43c7-8c8d-9ba815de10fe ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		14bb5e39-b350-43c7-8c8d-9ba815de10fe
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=14bb5e39-b350-43c7-8c8d-9ba815de10fe ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		14bb5e39-b350-43c7-8c8d-9ba815de10fe
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista/Longhorn (loader)
root		(hd0,3)
savedefault
makeactive
chainloader	+1

---

### Post by Friccy on 2008-12-13
It hang up right from the start.
After I choose from the grub Ubuntu, just a black screen apears.
If I press a key the Usplash apeares but that's all. So I have to keep a key pressed till it loads and the desktop showes up.

---

### Post by Friccy on 2008-12-14
Please help!
It takes a lot to start Ubuntu if I am a little away and not pressing a key!

---

### Post by azmo35 on 2008-12-14
I am not sure but I believe that root is missing from menu.1st
ex:
title		Ubuntu 8.04.1
root		(hd0,1)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=ad51ef36-da6e-4e45-8d6a-c989ffa69d2f  ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
you can see windows have root (hd0.0) I hope that helps,but perhaps it is best to wait for other answers,AZMO):P

---

