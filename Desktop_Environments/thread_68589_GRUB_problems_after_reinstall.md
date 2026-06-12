---
title: "GRUB problems after reinstall"
date: 2005-09-23
forum: Desktop Environments
---

### Post by Shamanix on 2005-09-23
My linux partition is on SDB6, My windows partition is on SDA1. I recently installed windows xp again, so i went into rescue mode from the kubuntu dvd. i selected SDB6 as root åpartition and after that i wrote "grub-install /dev/sda1"(where mbr is).

grub wqas successfully reinstalled, but every time i select to boot windows xp it goes straight back to the grub menu, so only linux is bootable... where does the problem lie? tried MANY times :P

---

### Post by mlomker on 2005-09-23
You need to take a look at the /boot/grub/menu.lst file.  If you have questions about it then post the contents and we'll take a look.

---

### Post by Shamanix on 2005-09-24
[QUOTE=mlomker]You need to take a look at the /boot/grub/menu.lst file.  If you have questions about it then post the contents and we'll take a look.[/QUOTE]

Here's my munu.ist:

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
# kopt=root=/dev/sdb6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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

title		Ubuntu, kernel 2.6.10-5-k7 
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/sdb6 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-k7
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-k7 (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/sdb6 ro single
initrd		/boot/initrd.img-2.6.10-5-k7
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd1,5)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by mlomker on 2005-09-24
> 
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

That's the part for your Windows and the commands look right.  Is Windows on the first drive and in the first partition?

What is the output of **sudo fdisk -l** and **df -h**?  You'll want to confirm that this line matches your hard disk layout.

---

### Post by Shamanix on 2005-09-24
[QUOTE=mlomker]That's the part for your Windows and the commands look right.  Is Windows on the first drive and in the first partition?

What is the output of **sudo fdisk -l** and **df -h**?  You'll want to confirm that this line matches your hard disk layout.[/QUOTE]

Yes, Windows is on the first partition on the first HD, while linux is on the last partition on the second(last) HD.


fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         319     2562336    7  HPFS/NTFS
/dev/sda2             320       19457   153725985    f  W95 Ext'd (LBA)
/dev/sda5            1277        6376    40965718+   7  HPFS/NTFS
/dev/sda6            6377       19457   105073101    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23046   185116963+   c  W95 FAT32 (LBA)
/dev/sdb2           23047       24321    10241437+   f  W95 Ext'd (LBA)
/dev/sdb5           23047       23174     1028128+  82  Linux swap / Solaris
/dev/sdb6   *       23175       24321     9213246   83  Linux


df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6             8.8G  8.5G  370M  96% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev/sdb1             177G  173G  3.4G  99% /media/fat32
/dev                  8.8G  8.5G  370M  96% /.dev
none                  5.0M  2.9M  2.2M  57% /dev

---

### Post by mlomker on 2005-09-24
[QUOTE=Shamanix]Yes, Windows is on the first partition on the first HD, while linux is on the last partition on the second(last) HD.
[/quote]

Try changing the root line to: **rootnoverify(hd0,0)**

---

### Post by Shamanix on 2005-09-27
Edited the file to:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

Correct? Didn't work :(

---

### Post by mlomker on 2005-09-27
There shouldn't be a space before the parenthesis.  

That's the only thing that I could find searching Google.  If that doesn't resolve it then you should boot your Windows XP cd and run **fixmbr** from their system recovery prompt.  That'll get the Windows MBR back and you can veryify that it still runs.  You can try the **grub-install /dev/sda** after you verify that there isn't a problem with the Windows partition.

---

### Post by Shamanix on 2005-09-27
[QUOTE=mlomker]There shouldn't be a space before the parenthesis.  

That's the only thing that I could find searching Google.  If that doesn't resolve it then you should boot your Windows XP cd and run **fixmbr** from their system recovery prompt.  That'll get the Windows MBR back and you can veryify that it still runs.  You can try the **grub-install /dev/sda** after you verify that there isn't a problem with the Windows partition.[/QUOTE]

Windows always boots if i don't install grub, when grub is reinstalled, windows won't boot. Tried to take away the space, but then it became invalid when trying to boot win xp. Could it be that the partition is NTFS?

---

### Post by mlomker on 2005-09-27
> Could it be that the partition is NTFS?

That shouldn't matter.  I've heard that some people use the Windows boot manager to boot into linux instead of the other way around.  They edit the c:\boot.ini file in Windows to add the lines for linux.  You might want to look around and see if that would work.

---

### Post by Shamanix on 2005-09-29
thanks for all your help, but i'm not giving up on GRUB yet, heh. wanna use as little microsoft software as possible.

---

### Post by yesplease on 2005-09-29
I have similar problems and put grub on a floppy. That worked (but I did not solve the original problem yet). On the upside: now I actually use the floppy drive :)

Note: My original plan was to put grub on the Linux disk, so there would be no problems when Windows needs to be reinstalled. BIOS should then start from the linux disk and the windows disk should become disk 2. Windows can be on disk 2 by tricking it to think it is on disk 1 with the map command in grub.

---

