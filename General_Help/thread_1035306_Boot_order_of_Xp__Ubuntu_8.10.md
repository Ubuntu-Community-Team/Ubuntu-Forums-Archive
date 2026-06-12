---
title: "Boot order of Xp / Ubuntu 8.10"
date: 2009-01-09
forum: General Help
---

### Post by Nitewalker on 2009-01-09
I have my laptop set up with dual boot, Ubuntu 8.10 & Win XP, I need to be able to have Win XP boot first instead of Ubuntu but can not find way to change boot order as other Linux Distro's have?  What do I need to do:confused:

---

### Post by linfidel on 2009-01-09
> **Nitewalker said:**
> I have my laptop set up with dual boot, Ubuntu 8.10 & Win XP, I need to be able to have Win XP boot first instead of Ubuntu but can not find way to change boot order as other Linux Distro's have?  What do I need to do:confused:
1.  edit the file /boot/grub/menu.lst, using an editor such as gedit.  You will need to open a terminal, and type gksudo gedit /boot/grub/menu.lst
2.  Scroll to the end, and you should see the options.  Each OS has a few lines in a group, and includes Title (which you can change), uuid (which you'd better not change), kernel (probably shouldn't change this, either), etc.  The one for XP is a little different, although I don't have it, so I don't know exactly what it says. But hopefully it will all be obvious. The main thing is to note it's position in the list, which is most likely the second item.  
3. Then, at the beginning of the file, find the line that starts with "default", and change it to that number (minus 1).  If it's currently set to zero, change it to 1.  You can't really mess up, as you can always override the choice like you do now.

---

### Post by Yellow Pasque on 2009-01-09
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
gksudo gedit /boot/grub/menu.lst
```

Find the line that says default=0 and change it to default=<X>, with X being the number of the Windows entry. To figure out X, count the lines that start with 'title' (start counting with 0) until you reach the Windows entry.

If you somehow screw up the file, you can pop in a LiveCD and copy the old one over it.

---

### Post by sendblink23 on 2009-01-09
Use my Example... 

I have it SET that same way **menu.lst**


> 
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


[COLOR="Lime"]title Windows XP Media Center Edition
root (hd0,1)
savedefault
makeactive
chainloader +1[/COLOR]


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
# kopt=root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=def0e49e-ae0e-4f02-ac61-2c320f743bc0

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
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/memtest86+.bin
quiet

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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
[COLOR="Red"]title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1[/COLOR]







I copied exactly what you read in my Code in the end  [COLOR="Red"]RED[/COLOR] .. and  Copied it.. to where you read the same TEXT but in [COLOR="Lime"]NEON[/COLOR] green


I hope that example of my settings helps for you

---

### Post by stchman on 2009-01-09
> **Nitewalker said:**
> I have my laptop set up with dual boot, Ubuntu 8.10 & Win XP, I need to be able to have Win XP boot first instead of Ubuntu but can not find way to change boot order as other Linux Distro's have?  What do I need to do:confused:

I do not recommend that you edit the /boot/grub/menu.lst file as you can run into trouble if a kernel is updated.  The easiest way to select boot order is to install StartUpManager.  StartUpManger is a GUI front end for boot loading and splash screen config.

```
sudo apt-get install startupmanager
```

This will easily allow you to select which OS is the default boot.

---

### Post by linfidel on 2009-01-09
> **stchman said:**
> I do not recommend that you edit the /boot/grub/menu.lst file as you can run into trouble if a kernel is updated.  The easiest way to select boot order is to install StartUpManager.  StartUpManger is a GUI front end for boot loading and splash screen config.
. . .
So, StartupManager doesn't modify the menu.lst file?  What does it do, then?

If it does modify the file, then your your reason for using it wouldn't make sense, since using it won't solve that problem.

If it doesn't modify the menu.lst file, it's a good idea to know what it does do, in case something goes wrong.

I'm not saying it's not a good suggestion.  For someone who doesn't want to know how it all works, and just wants the easiest way to make changes, it's probably a good tool.  But I thought it was simply a front-end for modifying menu.lst, and would be subject to the same limitations of editing by hand.

Personally, I've found that knowing how grub works gives me a lot more confidence in installing and deleting various distros.  If one of them wipes out my menu, which seems to happen often, I don't worry.  Even if grub gets wiped out completely, it's easy to fix.

---

