---
title: "Boot problems. (5.75... not responding)"
date: 2009-04-24
forum: General Help
---

### Post by AnimalCrosser5 on 2009-04-24
I have a few questions. First of all, I'm running Vista/Ubuntu dual boot. Sometimes, when I boot into Ubuntu, I get the countdown (press to enter menu in 5..4..3..etc.) Then I get an error saying 5.7(string of numbers here) Not Responding. Then the computer resets into the loader. Other times, The boot goes fine, but instead of the login screen, (or in my case now, the desktop) I get a black screen and I have to reboot. Most of the time however, Ubuntu loads just fine.

Second of all, is there a way to remove the "press esc. to enter boot menu" countdown or make it shorter?

Lastly, I want to disable the boot loader automatically choosing Windows after several seconds.

---

### Post by AnimalCrosser5 on 2009-04-24
bump

---

### Post by Monotoko on 2009-04-24
in /boot/grub/menu.lst just comment the hiddenmenu option out to stop it doing the countdown thing and just display the menu.

As for your other problem, i shall get back to you, as i am rather stumped, can you post the output of

```
gedit /boot/grub/menu.lst
``` here please?

---

### Post by AnimalCrosser5 on 2009-04-24
Like this?

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
# kopt=root=UUID=52C0023FC00229B5 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

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
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=52C0023FC00229B5 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=52C0023FC00229B5 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1
```

---

### Post by zonyl on 2009-04-26
Im having the same problems just now as well, except everytime I boot I get the 'xxxx not responding' message.  The only way I can get my machine to come up is to use a previous kernel.

I see a printk in the kernel source that matches the error here: [http://www.linux.org/docs/ldp/howto/Linux-i386-Boot-Code-HOWTO/smpboot.html](http://www.linux.org/docs/ldp/howto/Linux-i386-Boot-Code-HOWTO/smpboot.html), which could possibly indicate this is some sort of CPU SMP issue?   Only errors on the latest kernel for Jaunty for me, other kernels will boot fine.

---

### Post by dr_voodoo on 2009-10-12
hi guys... any developments on this? I have just started having the same problem. I have dual-boot Jaunty/XP... had the PC switched on constantly for about 2 days in Linux no problem, it was starting to run a bit sluggish and not do various things (for example, it was refusing to search in firefox when using the search box, drag and drop was flaky and the whole system was generally laggy) - now I am getting the '5.xxx not responding' error regardless of which kernel or recovery/normal mode I chose to boot into. XP works fine. Interestingly enough the 5.xxx nuber seems to vary periodically - I've had 5.7xxx, 5.666x - it's hard to get the exact message since it's only on the screen for about a second. 
Would prefer not to have to reinstall from the LiveCD all over again if poss...

[edit] OK interestingly enough it booted fine after I powered down for 5 minutes although GNOME is no longer as I left it - Emerald isn't running and GNOME appears to have reverted back to its standard nasty beige theme... although COMPIZ appears to be running OK as the desktop transparency is still there... so perhaps the problem lies therein?  Will update if any more developments...

---

