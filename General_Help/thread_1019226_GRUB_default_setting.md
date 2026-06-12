---
title: "GRUB default setting"
date: 2008-12-22
forum: General Help
---

### Post by snowman12 on 2008-12-22
I have just installed xubuntu and am using GRUB bootloader to chose my OS (I have to use windows because everything is written for it:() the only problem is if I turn my computer on and then go off to do whatever it chooses windows by default. Is there anyway to change this?

---

### Post by ushimitsudoki on 2008-12-22
If your boot manager is GRUB, then you should find its configuration at:
/boot/grub/menu.lst

You can probably read it and make sense of the options.

With everything "straight out the box", the first listed option should be the "default" boot option.

---

### Post by taurus on 2008-12-22
You can edit /boot/grub/menu.lst and set the **default** to whichever OS you want to boot.  Remember, each _title_ counts as one and you start counting from 0.  So, first title is 0 and the second title is 1...

```
sudo nano -Bw /boot/grub/menu.lst
```

---

### Post by snowman12 on 2008-12-23
so I found the file no problem....but now what exactly do I need to change?

---

### Post by x1a4 on 2008-12-23
> **snowman12 said:**
> but now what exactly do I need to change?
```

*<snip>*
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
*<snip>*
**default         [color=blue]0[/color]**
*<snip>*

```

---

### Post by snowman12 on 2008-12-24
thanks ushimitsudoki.
this is odd.....I tried it 0,1 and 2, but no change, still selected windows by default

---

### Post by caljohnsmith on 2008-12-24
Did you install Xubuntu inside of Windows via Wubi? If so, that would be the issue, because the first boot menu you get on start up is the Windows boot loader, not Grub. But if that's not your case and you are using Grub on start up, how about posting the full contents of your menu.lst so we can help you figure out what the problem is.

---

### Post by snowman12 on 2009-02-13
sorry for the long wait everyone, been rather hectic over the last few months and never got around to checking. . . . .

yes I did install with wubi and here is my menu.lst
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
Default         0
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
# kopt=root=UUID=DC6051E36051C544 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=DC6051E36051C544 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=DC6051E36051C544 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

hope this all helps

---

### Post by caljohnsmith on 2009-02-13
Since you have a Wubi install, if you want to boot Windows by default, you have to modify the Windows boot.ini file. Here's a link for how to modify the boot.ini file in Windows:

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

Basically your boot.ini file will probably look something like:
```
[boot loader]
timeout=30
[COLOR="Blue"]default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS[/COLOR]
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn
C:\wubildr.mbr="Ubuntu"
```
So to make Xubuntu you default, you would do:
```
[boot loader]
timeout=30
[COLOR="Blue"]default=C:\wubildr.mbr[/COLOR]
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn
C:\wubildr.mbr="Ubuntu"
```
And then Xubuntu should be the default after that. Let me know how it goes or if you run into problems.

---

### Post by snowman12 on 2009-02-13
caljohnsmith,

worked like a charm! brilliant thank you soo much!!!

---

### Post by caljohnsmith on 2009-02-13
Glad that worked out OK; cheers and enjoy Ubuntu and Windows. :)

---

