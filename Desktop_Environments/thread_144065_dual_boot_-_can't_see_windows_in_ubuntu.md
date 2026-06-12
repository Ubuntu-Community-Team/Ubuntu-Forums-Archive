---
title: "dual boot - can't see windows in ubuntu"
date: 2006-03-13
forum: Desktop Environments
---

### Post by dotdot on 2006-03-13
Hi folks ....

I have a simple config  - dual boot  : ubu breezy fully patched / win2k

.. only problem is ...
I can't see my windows partition..
why would i want to ? ... well my cd burner works in windows..
i've just downloaded  dapper and i cant burn then install it - if i can't see windows..
to copy then burn the image..

I know it's a story - but then isn't it always :)

I've included output from df / mount and grub menu.lst - for ref / comment.

# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda5             12634332   4775160   7217380  40% /
tmpfs                   318816         0    318816   0% /dev/shm
tmpfs                   318816     12588    306228   4% /lib/modules/2.6.12-10-386/volatile

mount :
/dev/hda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)


grub..
# cat menu.lst
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows 2000 Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


in case this helps.

..cheers

..

---

### Post by Koybe on 2006-03-13
Can you type ```
sudo fdisk -l 
``` so we can see hos is your disk partitionated.

You'll probably need to mount your patition then... [Look here](https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29)

---

### Post by KnottyMan on 2006-03-13
Have you tried installed k3b for cd/dvd burning purposes?  It's very nice.

---

### Post by dotdot on 2006-03-13
fdisk -l .. as req

# fdisk -l

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         440     3534268+   b  W95 FAT32
/dev/hda2            1716        1977     2104483+  82  Linux swap / Solaris
/dev/hda3             441        1715    10241406   83  Linux
/dev/hda4            1978        3648    13422307+   f  W95 Ext'd (LBA)
/dev/hda5   *        1978        3575    12835903+  83  Linux
/dev/hda6            3576        3648      586341   82  Linux swap / Solaris

Partition table entries are not in disk order
 (nice cmd..)

k3b - will investigate.. 

..any ideas ?  - much apprec !

..

---

### Post by Koybe on 2006-03-13
```
sudo mkdir /mnt/win
sudo mount -t vfat /dev/hda1 /mnt/win
```

Then browse /mnt/win to get the file you want. If you want to auto mount or get more information, look [this link ](https://wiki.ubuntu.com/MountingWindowsPartitions?highlight=%28mount%29%7C%28windows%29)

---

### Post by dotdot on 2006-03-13
cheers !

who knows why it didn't work on install - it did fine on the other laptops i've installed on... 

..

---

### Post by bobpur on 2006-03-13
I've got the same thing in my computer. Windows doesn't "see" Ubuntu and when I'm on Ubuntu it doesn't "see" Windows. However, unlike you, I have each OS on a different harddrive in one computer. I have Belarc Adviser on the windows side and it doesn't see the Ubuntu harddrive at all. I've never worried about it as i'm not experienced enough in Ubuntu to try to move files between OS's. I'll eventually lose Windows and use that harddrive for additional storage.

---

