---
title: "2 windows on grub"
date: 2006-07-04
forum: Desktop Environments
---

### Post by Mouta on 2006-07-04
Hi, i've installed Ubuntu and i have 2 windows, Vista and XP, i've edited grub and i've managed to get Vista on the grub but i can't boot XP.

Vista is on primary and XP on logical, what do i have to put so i can boot XP too? I really need this.

Thanks in advance.

---

### Post by ciscosurfer on 2006-07-05
Once you install Vista, it rewrites your XP NTLDR file.  At bootup, GRUB will present your OS options.  Choose the option to boot Vista and you will be sent to the Vista boot screen where you can either choose to load Vista or Earlier version of windows.  To load XP, choose 'Earlier version of windows' and your XP partition (or drive, depending how you have it set up) will load no problem.  Please post your **/boot/grub/menu.lst** file [remember, that's an 'l' not a '1'...as in **l**i**st** *not 1st (first)*] and we can alter it to allow you to visually see that choosing the XP option in GRUB will really load Vista's new loader.  A bit confusing, yes, but easily accomplished.  We can blame Vista for all of this.  There are other workarounds, but in my experience, and b/c Vista is still beta, this is the best way of going about things.

To see how your **/boot/grub/menu.lst** file is organized, type into a terminal:```
cat /boot/grub/menu.lst
```then post it in your reply :D

Remember also, that the order in which you have installed your systems has a direct effect on how GRUB sets up your boot options.

---

### Post by Mouta on 2006-07-05
The problem is that when i choose Vista there's no menu, it goes directly for Vista... i'll put asap menu.lst

---

### Post by Mouta on 2006-07-05
Here, the menu.lst

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title Windows Vista
unhide (hd0,0)
rootnoverify (hd0,0)
chainloader +1
makeactive

title Windows XP
unhide (hd0,4)
rootnoverify (hd0,4)
chainloader +1

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by ciscosurfer on 2006-07-05
Going over your menu.lst now, but in the meantime, you may want to check out these threads...they may be just what you are looking for.  

[http://www.ubuntuforums.org/showthread.php?t=208951]("http://www.ubuntuforums.org/showthread.php?t=208951") <-- do away with GRUB altogether

[http://www.ubuntuforums.org/showthread.php?t=169303]("http://www.ubuntuforums.org/showthread.php?t=169303") <--  checking others' setups and advice

**EDIT:**  try moving what I've put in bold from where you have them now to underneath the line that says ### END DEBIAN AUTOMAGIC KERNELS LIST.  Keeping in mind the warning from within menu.lst that states that 

```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```From this:
```
[B]title Windows Vista
unhide (hd0,0)
rootnoverify (hd0,0)
chainloader +1
makeactive

title Windows XP
unhide (hd0,4)
rootnoverify (hd0,4)
chainloader +1[/B] 

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot
[B]
### END DEBIAN AUTOMAGIC KERNELS LIST[/B]
``` 
To this:
```

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

** ### END DEBIAN AUTOMAGIC KERNELS LIST**

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
title Windows Vista
unhide (hd0,0)
rootnoverify (hd0,0)
chainloader +1
makeactive

title Windows XP
unhide (hd0,4)
rootnoverify (hd0,4)
chainloader +1
```

---

### Post by Ptero-4 on 2006-07-05
By looking at your menulst. I can tell you that Windoze Waste really wasted your XP.

---

