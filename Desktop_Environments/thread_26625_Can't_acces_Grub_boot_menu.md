---
title: "Can't acces Grub boot menu"
date: 2005-04-13
forum: Desktop Environments
---

### Post by kresten on 2005-04-13
Hi!
I have 2 problem witch troubles me a great deal.

1)  When I turn on my laptop the screen is totaly black until the nvidia logo appears. This means I can't boot into WXP I cant even boot from my CD drive....
 
2)screen is somewhat more dim than it use to be, to the point where it is exausting to look at.

Ubuntu seems to work, as it has been doing for the past week and as 4.10 did for almost half a year.

my laptop is a toshiba proM30 1.5M GHz 
512mb ram

As I am a new to linux I really don't know where to start....   so please help me [-o<

---

### Post by devil28 on 2005-04-13
if you could go to /boot/grub/menue.lst and post whats in there, we should be able to set things right for you.

---

### Post by kresten on 2005-04-13
OK here is my /boot/grub/menu.lst


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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,6)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,6)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,6)
kernel		/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by devil28 on 2005-04-13
if your xp is on the first part. of your first harddrive, then I dont understand why you dont get a grub-screen. you could try in terminal sudo update grub and see if that helps.

---

### Post by kresten on 2005-04-13
Well i have tried to update Grub but that don't have any effekt:(
The funny thing is that my computer worked like a charm until a few hours ago. 
  It had begun to hypernate when I came home this afternoon, I could not "wake" it and just restartet it, and then I realized that the problems described above.

It really worries me that I cannot boot from my CD drive the way I use to (F12)

---

### Post by kamstrup on 2005-04-13
You don't get any bios messages or anything on boot up, and can't boot from removable 
media? If that is correct, I doubt that it is Ubuntu giving you trouble... 

First make sure that the laptop is *fully* recharged. Then try again.

If this doesn't work, try setting "default" to 3, in menu.lst, and comment out the lines for the divider. Ie. add a # before both of the lines:
 
title Other operating systems:
root

WARNING: This boots you into Windows (as that isn't bad enough itself) from where you do not have acces to menu.lst - so you can't reverse this change if you don't have some way of reinstalling Grub or rebooting into linux (a Live cd will do).

Good luck

---

