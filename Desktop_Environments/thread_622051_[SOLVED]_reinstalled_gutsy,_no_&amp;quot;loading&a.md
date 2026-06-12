---
title: "[SOLVED] reinstalled gutsy, no &amp;quot;loading&amp;quot; screen after grub"
date: 2007-11-24
forum: Desktop Environments
---

### Post by spyder0080 on 2007-11-24
Hello all,

I posted this in the "installation" forum but got no responses, so I'll ask here also:

I reinstalled gutsy yesterday and everything is working except that I get no ubuntu "loading" screen after the grub menu. Specifically, the screen that says "ubuntu" and has the orange progress bar. I also don't get this screen when I shut down or restart. Is there any way to get the screen back up? Thanks!

---

### Post by cooljdude on 2007-11-24
Hm, that's weird. Is it maybe disabled?

---

### Post by ajgreeny on 2007-11-24
Can we see your /boot/grub/menu.lst file to see if the splash is disabled.  If you don't know how it's ```
cat /boot/grub/menu.lst
``` and just copy the output to this forum.

---

### Post by spyder0080 on 2007-11-24
here it is:

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=6ada1949-2f65-4248-bd74-3b7e4aa2b212 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6ada1949-2f65-4248-bd74-3b7e4aa2b212 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6ada1949-2f65-4248-bd74-3b7e4aa2b212 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1



```

---

### Post by danwood76 on 2007-11-24
I had this when I installed gusty for the first time.

The splash screen config file is specifying a size that is too large or not compatible with your screen resolution.
The file is located /etc/usplash.conf

It normally states a screen resolution of 1280x1024 which didnt work on my system.
You should probably set it to 1024x768 as this is what worked on mine.

regards,
Danny

---

### Post by spyder0080 on 2007-11-24
> **danwood76 said:**
> I had this when I installed gusty for the first time.

The splash screen config file is specifying a size that is too large or not compatible with your screen resolution.
The file is located /etc/usplash.conf

It normally states a screen resolution of 1280x1024 which didnt work on my system.
You should probably set it to 1024x768 as this is what worked on mine.

regards,
Danny
thanks for the tip! It restored the screen when I shut down.
unfortunately, it still doesn't show up when I start up. Any other ideas?

---

### Post by drama1981 on 2007-11-24
> **spyder0080 said:**
> thanks for the tip! It restored the screen when I shut down.
unfortunately, it still doesn't show up when I start up. Any other ideas?

since you edited the file already try doing the following in a terminal

sudo dpkg-reconfigure usplash

it will then update the image. now restart and see if it fixed it.

---

### Post by spyder0080 on 2007-11-24
> **drama1981 said:**
> since you edited the file already try doing the following in a terminal

sudo dpkg-reconfigure usplash

it will then update the image. now restart and see if it fixed it.
awesome! problem solved!
thanks to everyone for their help

---

