---
title: "Help - Grub Error 21!!! Have vital information that i need to recover."
date: 2005-06-01
forum: Desktop Environments
---

### Post by liamk101 on 2005-06-01
Hello!

I've installed Ubuntu 5.04 a few weeks ago and everything was going all right until 2 days ago the disk became full and i couldn't do anything and pressed the reset button on my pc, when it restarted the message "Grub 1.5 .... Error 21" was displayed on the screen. I've got really important information on my disk and through a live cd i could mount the linux partition but was unable to copy all the information because there were a padlock on several folders and i wasn't allowed to copy their content. If i reinstall ubuntu will my folders continue on the partition or will they be completely erased? Can you please help me?

This is my /boot/grub/menu.lst:


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default
entry
# is the entry saved with the command 'savedefault'.
default                0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default
entry
# (normally the first entry defined).
timeout                10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive
editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title                Windows 95/98/NT/2000
# root                (hd0,0)
# makeactive
# chainloader        +1
#
# title                Linux
# root                (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# groot=(hd0,1)

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

title                Ubuntu, kernel 2.6.10-5-386
root                (hd0,1)
kernel                /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd                /boot/initrd.img-2.6.10-5-386
savedefault
boot

title                Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root                (hd0,1)
kernel                /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd                /boot/initrd.img-2.6.10-5-386
savedefault
boot

title                Ubuntu, kernel memtest86+
root                (hd0,1)
kernel                /boot/memtest86+.bin
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title                Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title                Microsoft Windows XP Professional
root                (hd0,0)
savedefault
makeactive
chainloader        +1

---

### Post by enquiry on 2005-06-01
According to the Grub manual, Error 21 means:
> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.
See this thread: [http://forums.suselinuxsupport.de/index.php?showtopic=15920](http://forums.suselinuxsupport.de/index.php?showtopic=15920)

If you're unable to resolve the problem, the good news is that you *can* recover your data using the Ubuntu LiveCD (or any other LiveCD). Make sure you use the sudo command to get root privileges when copying the files, if you use the Ubuntu LiveCD (you need to use the command line). If you use another LiveCD, for example Knoppix, you'll get access to copying the files by being logged in as root.

---

### Post by myshoesrsolight on 2006-01-08
yeah, if you boot from liveCD you can go into 
System-->Administration-->Login Screen Setup 
then uncheck:
All AUTO LOGIN stuff and and TIMED LOGIN
then go to the SECURITY taband CHECK:
Allow root login with GDM

then you can log out and log back in as root and access the files you couldnt before and the "padlocks" will be lifted.:KS 

hope this helps,
daniel

---

### Post by darkultra on 2006-04-30
suggestion:

Why isn't /home a partition of its own? It would make it much better for beginners so they can fill up their home area and not worry about space.

And if the system would get messy and need a reinstall, it would detect this partition and mount it anew in /home and maybe ask the user the password and he would get access granted.

I prefer [programs that store user info in their own directory](http://jooh.no/programs_on_d.html) so I don't have to re-install them after a reformat/reinstall of windows.

---

