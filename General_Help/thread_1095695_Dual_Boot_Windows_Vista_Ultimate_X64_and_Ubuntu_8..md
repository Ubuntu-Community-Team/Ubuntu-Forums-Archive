---
title: "Dual Boot Windows Vista Ultimate X64 and Ubuntu 8.04"
date: 2009-03-14
forum: General Help
---

### Post by edifon on 2009-03-14
i finished building a PC so i could run Ubuntu and Vista
I have Three Hard drives
Ubuntu is installed on the First Hard drive
Vista is installed on the Third Hard Drive (I think)
I installed Vista first, then Installed Ubuntu
When Ubuntu prompts me to choose my OS, I get Error 13 When i choose Windows
I have seen lots of threads about this issue and non has helped
I want to state again that i Have 3 hard drives not 1, as most threads deal with dual booting when the individual just has one hard drive.
Can someone please help. Ubuntu is killing me
I should also say that i can run both Operating systems when i change my boot sequence in BIOS, so i know i installed boot correctly.
Help Help help, i am dying

---

### Post by circa82 on 2009-03-14
If you boot Ubuntu, open a terminal (Applications > Accessories > Terminal) and post the output of the following commands here:

```
# [color=blue]sudo fdisk -l[/color]  <-- lowercase L

# [color=blue]cat /boot/grub/menu.lst[/color]
```

---

### Post by sahabcse on 2009-03-14
For fixing the grub error follow below url


[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

---

### Post by edifon on 2009-03-14
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00062a68

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76696   616060588+  83  Linux
/dev/sda2           76697       77825     9068692+   5  Extended
/dev/sda5           76697       77825     9068661   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa636a637

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa5d7a5d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60802   488384512    7  HPFS/NTFS

---

### Post by edifon on 2009-03-14
I am also having trouble with my sound. I cannot hear anything from my speakers

---

### Post by edifon on 2009-03-14
# cat /boot/grub/menu.lst

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00062a68

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76696   616060588+  83  Linux
/dev/sda2           76697       77825     9068692+   5  Extended
/dev/sda5           76697       77825     9068661   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa636a637

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa5d7a5d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60802   488384512    7  HPFS/NTFS
edifon@edifon-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=dd250d97-02cc-4015-b03b-7e1d42f2c24b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=dd250d97-02cc-4015-b03b-7e1d42f2c24b ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=dd250d97-02cc-4015-b03b-7e1d42f2c24b ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=dd250d97-02cc-4015-b03b-7e1d42f2c24b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=dd250d97-02cc-4015-b03b-7e1d42f2c24b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows Vista/Longhorn (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by edifon on 2009-03-14
I solved my sound issue by following 
thestonefox reply
[https://answers.launchpad.net/ubuntu/+question/30688](https://answers.launchpad.net/ubuntu/+question/30688)

---

### Post by edifon on 2009-03-14
Can somebody help me!!!!!!!
I am dying to get my dual boot system working. I have posted my specs

---

### Post by circa82 on 2009-03-14
/boot/grub/menu.lst is pointing to the third (sdc) hard drive for Windows. I would change all (hd2,0) & (hd2) entries to (hd1,0) and (hd1).

Boot Ubuntu again and this time run:
```
# [color=blue]sudo nano /boot/grub/menu.lst[/color]
```
At the very bottom of the file; last entry, make the edits shown in [color=red]red[/color] 

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows Vista/Longhorn (loader)
root [color=red](hd1,0)[/color]
savedefault
makeactive
map (hd0) [color=red](hd1)[/color]
map [color=red](hd1)[/color] (hd0)
chainloader +1
```

Press **CTRL**+**X** and select 'yes' when asked.

---

