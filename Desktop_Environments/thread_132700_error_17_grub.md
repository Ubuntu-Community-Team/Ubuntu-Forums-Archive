---
title: "error 17 grub"
date: 2006-02-18
forum: Desktop Environments
---

### Post by joey111 on 2006-02-18
hi, can someone please help me. i desperarely look for some way to fix that but cannot find;
my problem: i installed xp again, and, as i knew it killed my GRUB. So far so good, but to reinstall GRUB was much more complicated than I ever thought. I tried different methods but it never worked out;
I am using Ubuntu 5.10 and Kde 3.5.1
my 
**first error message I got from GRUB was:**
[I]mount:mounting /dev/hda6 on /root failed no such device
mount: mounting /root/dev on /dev/.static/dev failed.no such file or directory
mount:mounting /dev on /root/dev failed : no such file or directory.
Target file system doesn't have /sbin/init
/bin/sh can't access tty: job control turned off. [/I]
so then i tried e.g.

[I]
mkdir -p /tmp/lalala

mount /dev/ide......./part12345 /tmp/lalala

^^ part12345 = my/

chroot /tmp/


mount -t proc proc /proc

mount -a 
grub-install hd0



grub-install /dev/hda [/I]
**so i tried**


mkdir -p /tmp/lalala

mount /dev/ide......./part12345 /tmp/lalala

^^ part12345 = dein /

chroot /tmp/lalala

mount -t proc proc /proc

mount -a 
grub-install hd0

then came error:
*the file /mnt/hda5/boot/grub/stage1 not read correctly *;
so Xp ( as i could read in the fstab gave new numbers to my devices e.g. (hda 5(where boot is) was new hda7 and so on, i fixed that with knoppix and got from now on:

[I]filesystem type unknown, partition type 0x5 kernel xxxx.686 root=( dev/hda6ro quiet splash
error 17: cannot mount system partition. Press any key to continue... [/I]

**_fstab_**:

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda5 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda3 /home ext3 defaults,atime,auto,rw,dev,exec,suid,nouser 0 2
/dev/hda1 /media/win ntfs umask=0,utf8,uid=0,gid=0,auto,rw,nouser 0 0
/dev/hda8 /media/winprogs vfat umask=0,iocharset=utf8,uid=0,gid=0,auto,rw,nouser 0 0
/dev/hda9 /media/hda9 vfat umask=0,iocharset=utf8,uid=0,gid=0,auto,rw,nouser 0 0
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/usb1 vfat umask=000,uid=0,gid=0,noauto,rw,user 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/sda2 /mnt/ipod vfat sync,uid=0,gid=0,noauto,rw,user 0 0
/dev/sda3 /mnt/ipod vfat sync,uid=0,gid=0,noauto,rw,user 0 0
/dev/hda11 /media/data ext3 umask=0,iocharset=utf8,uid=0,gid=0,auto,rw,nouser 0 0
/dev/hda12 /media/mp ext3 umask=0,iocharset=utf8,uid=0,gid=0,auto,rw 0 0
/dev/hda7 /media/fedora xfs umask=0,iocharset=utf8,uid=0,gid=0,atime,auto,rw,dev,exec,suid 0 0
/dev/sr0 /media/cdroms iso9660 noauto 0 0
/dev/hdc /media/cdromc iso9660 noauto 0 0[/B]





[**U][B]menu.lst**[/U]
# menu.lst - See: grub(Cool08), info grub, update-grub(Cool08)
# grub-install(Cool08), grub-floppy(Cool08),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,4)
# kernel /vmlinuz root=/dev/hda6 ro
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
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
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
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## ## End Default Options ##

title Ubuntu, kernel 2.6.12-10-686
root (hd0,4)
kernel /boot/vmlinuz-2.6.12-10-686 root=/dev/hda6 ro quiet splash
initrd /boot/initrd.img-2.6.12-10-686
savedefault
boot

title Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.12-10-686 root=/dev/hda6 ro single
initrd /boot/initrd.img-2.6.12-10-686
boot

title Ubuntu, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1
[/B]
thnx
ps what i also saw: i dont have a file called boot.conf where should it be, necessary?so GRUB comes to stage 1.5 but then when i select ubuntu he isnt able to start it and gives me the error 17 message;
Win XP he has no prob to start;

---

### Post by aysiu on 2006-02-19
[QUOTE=joey111]
my problem: i installed xp again, and, as i knew it killed my GRUB. So far so good, but to reinstall GRUB was much more complicated than I ever thought. I tried different methods but it never worked out[/quote] Which methods did you try? Did you try [this](http://ubuntuforums.org/showthread.php?t=24113)?

---

### Post by joey111 on 2006-02-19
hi, yes i tried but when i get partition disks it doesnt recognize any partition neither ntfs win nor the several ext3 partitions from linux. it just shows one big empty 40 GB partition and i didnt dare to do"write changes to disk as i feared it would do what it claimed to be there and format all.
usually it should recognize all partitions (windows and so on ) in partitions right?
to be more precise:
....
4. Mount your appropriate linux partions

/
/boot
swap
..... 
i cannot do that they do not appear; how can i make them appear?

---

