---
title: "not able to boot up windows"
date: 2008-12-28
forum: General Help
---

### Post by amityak on 2008-12-28
hello all.

actually i could normally not have cared less, but since israeli news channels are all broadcasting their videos only for windows, and due to the fact that there is much action going on there at the moment and i want to be updated with news from home, i need now my windows working... 

so to the technical details:

when selecting Windows , grub shows the following:

```
root(hd0,0)
Filesystem type unknown, partition type 0x7
chainloader +1
```

output of fdisk:

```
root@jts-laptop:/# fdisk -l

Platte /dev/sda: 40.0 GByte, 40007761920 Byte
255 Köpfe, 63 Sektoren/Spuren, 4864 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x000633f9

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        4736    22683780   83  Linux
/dev/sda3            4737        4864     1028160    5  Erweiterte
/dev/sda5            4737        4864     1028128+   7  HPFS/NTFS

```


relecant part of menu.lst

```
title		Windows XP
root		(hd0,0)
# savedefault
# makeactive
chainloader	+1
```

geometry of GRUB

```
grub> geometry (hd0)
drive 0x80: C/H/S = 4864/255/63, The number of sectors = 78140160, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x7


```

how can I fix the mess??
i must say all the mess started after ive installed the SuSe like gfxmenu, even though im not sure because ive just now tried to load windows, after few months i havent been using it. With the partitions though i didnt do anything, so windows must exist still.

thank you all

amit

---

### Post by caljohnsmith on 2008-12-28
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by amityak on 2008-12-28
there you go, thank you for the detailed explanation, and for your time (:

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for its boot files.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Mounting failed:  
mount: Sie müssen den Dateisystemtyp angeben

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Platte /dev/sda: 40.0 GByte, 40007761920 Byte
255 Köpfe, 63 Sektoren/Spuren, 4864 Zylinder, zusammen 78140160 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0x000633f9

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *          63    30716279    15358108+   7  HPFS/NTFS
/dev/sda2        30716280    76083839    22683780   83  Linux
/dev/sda3        76083840    78140159     1028160    5  Erweiterte
/dev/sda5        76083903    78140159     1028128+   7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="72feaa8b-f7b9-4922-b5f8-d2f9b41d9d53" TYPE="ext3" 
/dev/sda5: UUID="909CA8C99CA8AAE4" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/jts/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jts)

=========================== sda2/boot/grub/menu.lst: ===========================


# gfxmenu /boot/grub/message.ububrown

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
# kopt=root=UUID=72feaa8b-f7b9-4922-b5f8-d2f9b41d9d53 ro

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

title		Ubuntu 8.04
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=72feaa8b-f7b9-4922-b5f8-d2f9b41d9d53 ro quiet splash vga=0x031b
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=72feaa8b-f7b9-4922-b5f8-d2f9b41d9d53 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=72feaa8b-f7b9-4922-b5f8-d2f9b41d9d53 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=72feaa8b-f7b9-4922-b5f8-d2f9b41d9d53 ro single
#initrd		/boot/initrd.img-2.6.24-19-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=72feaa8b-f7b9-4922-b5f8-d2f9b41d9d53 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=72feaa8b-f7b9-4922-b5f8-d2f9b41d9d53 ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
root		(hd0,0)
# savedefault
# makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=72feaa8b-f7b9-4922-b5f8-d2f9b41d9d53 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=08775b0b-fbf6-4102-800b-0173f85e78d2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda2/boot: ==================================

insgesamt 55928
drwxr-xr-x  3 root root    4096 2008-12-05 15:30 .
drwxr-xr-x 23 root root    4096 2008-12-26 04:20 ..
-rw-r--r--  1 root root  422607 2008-04-10 18:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  422667 2008-08-21 06:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-10-22 05:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root   79964 2008-04-10 18:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   80049 2008-08-21 06:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-10-22 05:12 config-2.6.24-21-generic
drwxr-xr-x  2 root root    4096 2008-12-27 15:28 grub
-rw-r--r--  1 root root 7865456 2008-08-20 04:18 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7349268 2008-04-22 20:00 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7476912 2008-08-26 12:43 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7476680 2008-08-20 01:37 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7313999 2008-12-05 15:30 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 9534703 2008-11-21 10:42 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 12:06 memtest86+.bin
-rw-r--r--  1 root root  899892 2008-04-10 18:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root  905170 2008-08-21 06:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-10-22 05:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root 1904248 2008-04-10 18:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1921464 2008-08-21 06:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1920760 2008-10-22 05:12 vmlinuz-2.6.24-21-generic

=============================== sda2/boot/grub: ===============================

insgesamt 512
drwxr-xr-x 2 root root   4096 2008-12-27 15:28 .
drwxr-xr-x 3 root root   4096 2008-12-05 15:30 ..
-rw-r--r-- 1 root root    197 2008-12-27 15:28 default
-rw-r--r-- 1 root root     15 2008-08-20 04:19 device.map
-rw-r--r-- 1 root root   7444 2008-12-27 15:28 e2fs_stage1_5
-rw-r--r-- 1 root root   7268 2008-12-27 15:28 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-08-20 04:19 installed-version
-rw-r--r-- 1 root root   6580 2008-12-27 15:28 iso9660_stage1_5
-rw-r--r-- 1 root root   8064 2008-12-27 15:28 jfs_stage1_5
-rw-r--r-- 1 root root   5440 2008-12-27 15:03 menu.lst
-rw-r--r-- 1 root root   5432 2008-11-21 11:13 menu.lst~
-rw-r--r-- 1 root root   5446 2008-11-21 09:59 menu.lst_backup
-rw-r--r-- 1 root root 128000 2008-11-21 09:59 message.suse
-rw-r--r-- 1 root root 160768 2008-11-21 10:30 message.ububrown
-rw-r--r-- 1 root root   6740 2008-12-27 15:28 minix_stage1_5
-rw-r--r-- 1 root root   9012 2008-12-27 15:28 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-27 15:28 stage1
-rw-r--r-- 1 root root 100948 2008-12-27 15:28 stage2
-rw-r--r-- 1 root root   8700 2008-12-27 15:28 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sda1: unknown volume type
```

---

### Post by amityak on 2008-12-28
a small translation of the german sentence in the first 'sda1' section:

"mount: Sie müssen den Dateisystemtyp angeben"
which means: You must define the filesystem type"

---

### Post by caljohnsmith on 2008-12-28
OK, how about first trying:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```
If that says it completes successfully please post the output of:
```
sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
ls -l /media/sda1
```

---

### Post by amityak on 2008-12-28
```
root@jts-laptop:/home/jts# ntfsfix /dev/sda1
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.

```

---

### Post by caljohnsmith on 2008-12-28
Do you have your Windows Install CD? If you do, I would boot that, go to the "recovery console" and run:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors, assuming you can get as far as running that command; I'm doubtful whether Windows will even see your sda1 partition as NTFS and allow you to run that command, because I think sda1 might be corrupted beyond repair. But how about giving it a shot and let me know how it goes.

---

### Post by amityak on 2008-12-29
i don't have a rescue CD, trying to get one. But actually since I've found a way to watch Israeli news using Linux i guess it's maybe a good chance to clean some 15GB from my HD and free my computer from winblows... ???

I guess thats also a solution.. even though i wouldnt really mark this thread as solved. thank you very much for the help

Amit, Berlin.

---

