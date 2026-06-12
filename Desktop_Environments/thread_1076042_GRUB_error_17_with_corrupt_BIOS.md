---
title: "GRUB error 17 with corrupt BIOS"
date: 2009-02-20
forum: Desktop Environments
---

### Post by SwooshyCueb on 2009-02-20
I recently booted my computer and was greeted with the following error:
> GRUB loading stage 1.5.

GRUB loading, please wait...
Error 17

Yay! Now I can't get into Ubuntu OR Windows! (My copy of XP decided to eat its own registry.)

I have read that I have to change the boot order thru the BIOS, but my BIOS is flash protected AND corrupt.

Hooray! I can't boot to DVDs, anything you hook up via USB, or anything of that sort. I can use Smart Boot Manager to boot to a CD, but the BIOS's boot order is floppy then HD. It really grinds my gears that I can't boot to a DVD, because I just got a copy of Windows 7, and guess what? It installs via DVD!

But I digress. If I could get GRUB fixed, I'll be happy for a while.

---

### Post by caljohnsmith on 2009-02-21
So was Ubuntu/Grub working OK on your computer before you received the Grub error 17? Do you remember anything you did in Ubuntu or to the computer before getting the Grub error? In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by SwooshyCueb on 2009-02-22
Ubuntu 8.10 64 bit and GRUB were working fine before this happened, besides the fact that GRUB couldn't boot into Windows. (NTLDR was also corrupt. I have been using an NTLDR floppy to get into Windows.) I have tried reinstalling 64 bit and 32 bit versions to no avail. Here's the results.txt:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com /wubildr.mbr

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0172a202

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    66,043,214    66,043,152   7 HPFS/NTFS
/dev/sda2          66,043,215    80,276,804    14,233,590   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99809980

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    37,383,254    37,383,192  83 Linux
/dev/sdb2          37,383,255    39,102,209     1,718,955   5 Extended
/dev/sdb5          37,383,318    39,102,209     1,718,892  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x854d854d

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   320,143,319   320,143,257   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   488,392,064   488,392,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="308C57FC8C57BB54" LABEL="Other hard drive" TYPE="ntfs" 
/dev/sda2: UUID="B444864044860578" LABEL="Small" TYPE="ntfs" 
/dev/sdb1: UUID="852a2891-36f5-49a2-a65d-bb6a5bf48ca7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="5a1f3d92-dbe6-477a-a3fb-66126e44bf89" TYPE="swap" 
/dev/sdc1: UUID="6A5827215826EC0F" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdd1: LABEL="CHAINOFFOOT" UUID="682A-0050" TYPE="vfat" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/scd2 on /media/UDF Volume type udf (ro,nosuid,nodev,uhelper=hal,uid=999)
/dev/sdd1 on /media/CHAINOFFOOT type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[Boot Loader]

timeout=15

Default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS.0

[Operating Systems]

multi(0)disk(0)rdisk(2)partition(1)\WINDOWS.0="1ST TRY THIS seleccione esto primero" /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0="2ND TRY THIS essayez ceci en deuzieme" /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS.0="3RD TRY THIS wahlen Sie diesen Third" /fastdetect

multi(0)disk(0)rdisk(1)partition(0)\WINDOWS.0="4TH TRY THIS selezioni questo fourth" /fastdetect

multi(0)disk(0)rdisk(0)partition(0)\WINDOWS.0="5TH TRY THIS selecione este fifth" /fastdetect

multi(0)disk(0)rdisk(2)partition(0)\WINDOWS.0="6TH TRY THIS seleccione este sexto" /fastdetect

multi(0)disk(0)rdisk(3)partition(0)\WINDOWS.0="7TH TRY THIS essayez ceci en septieme" /fastdetect

multi(0)disk(0)rdisk(3)partition(1)\WINDOWS.0="8TH TRY THIS wahlen Sie dieses achte" /fastdetect

C:\="9TH TRY THIS selezioni questo nono"

D:\="10TH TRY THIS selecione este decimo"

c:\wubildr.mbr="Ubuntu"


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=852a2891-36f5-49a2-a65d-bb6a5bf48ca7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=852a2891-36f5-49a2-a65d-bb6a5bf48ca7

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
uuid		852a2891-36f5-49a2-a65d-bb6a5bf48ca7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=852a2891-36f5-49a2-a65d-bb6a5bf48ca7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		852a2891-36f5-49a2-a65d-bb6a5bf48ca7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=852a2891-36f5-49a2-a65d-bb6a5bf48ca7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		852a2891-36f5-49a2-a65d-bb6a5bf48ca7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=852a2891-36f5-49a2-a65d-bb6a5bf48ca7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=5a1f3d92-dbe6-477a-a3fb-66126e44bf89 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   8.4GB: boot/grub/menu.lst
   8.3GB: boot/grub/stage2
   8.4GB: boot/initrd.img-2.6.27-7-generic
   8.4GB: boot/vmlinuz-2.6.27-7-generic
   8.4GB: initrd.img
   8.4GB: vmlinuz

================================ sdc1/boot.ini: ================================

[Boot Loader]

timeout=15

Default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS.0



[Operating Systems]

multi(0)disk(0)rdisk(2)partition(1)\WINDOWS.0="1ST TRY THIS seleccione esto primero" /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0="2ND TRY THIS essayez ceci en deuzieme" /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS.0="3RD TRY THIS wahlen Sie diesen Third" /fastdetect

multi(0)disk(0)rdisk(1)partition(0)\WINDOWS.0="4TH TRY THIS selezioni questo fourth" /fastdetect

multi(0)disk(0)rdisk(0)partition(0)\WINDOWS.0="5TH TRY THIS selecione este fifth" /fastdetect

multi(0)disk(0)rdisk(2)partition(0)\WINDOWS.0="6TH TRY THIS seleccione este sexto" /fastdetect

multi(0)disk(0)rdisk(3)partition(0)\WINDOWS.0="7TH TRY THIS essayez ceci en septieme" /fastdetect

multi(0)disk(0)rdisk(3)partition(1)\WINDOWS.0="8TH TRY THIS wahlen Sie dieses achte" /fastdetect

C:\="9TH TRY THIS selezioni questo nono"

D:\="10TH TRY THIS selecione este decimo"

c:\wubildr.mbr="Ubuntu"

```

If you need the boot.ini code from the floppy, just say so.

---

### Post by caljohnsmith on 2009-02-22
Can you set your BIOS to boot the 20 GB Ubuntu sdb drive on start up? If so, how about doing:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
```
Then set your BIOS so that the sdb drive is before your other drives in the boot order, and I think you should be able to boot Ubuntu fine. Let me know how that goes or if you run into problems.

---

### Post by SwooshyCueb on 2009-02-22
My BIOS is CORRUPT. When I go into setup, it's just a blank screen with a blinking cursor. I have to reboot.

---

### Post by caljohnsmith on 2009-02-22
My mistake, I forgot you all ready made that clear. How about downloading the [Super Grub Disk]("http://www.supergrubdisk.org"), burn that to CD, boot it, and when you get the main menu, press "c" to get the command line, and do:
```
grub> geometry (hd0)
grub> geometry (hd1)
grub> geometry (hd2)
grub> geometry (hd3)
```
And let me know the output of all the commands; that will tell us what your BIOS boot order is, and from there we will know how to install Grub to your first boot drive in order to boot Ubuntu.

---

### Post by SwooshyCueb on 2009-02-22
OK, and speaking of sgd, is there any way to get it to boot to a DVD?

---

### Post by SwooshyCueb on 2009-02-22
The CD version did not work: SBM gave me disk error 0x07. I used the floppy version I had from a previous attempt at solving this problem, and here's the results (excluding hd3, which doesn't exist.)

```
              filesystem   partition

hd0 (number of sectors = 80293248)
Partition 0:   unknown        0x7
Partition 1:   unknown        0x7

hd1 (number of sectors = 39102336)
Partition 0:   ext2fs        0x83
Partition 4: No BSD/SOLARIS sub-partition found (0x82)

hd2 (number of sectors = 320173056
Partition 0:   unknown        0x7
```

---

### Post by caljohnsmith on 2009-02-22
> **SwooshyCueb said:**
> OK, and speaking of sgd, is there any way to get it to boot to a DVD?
Not that I know of, but I'm not an expert with SGD either.

---

### Post by caljohnsmith on 2009-02-22
> **SwooshyCueb said:**
> 
```
              filesystem   partition

hd0 (number of sectors = 80293248)
Partition 0:   unknown        0x7
Partition 1:   unknown        0x7

hd1 (number of sectors = 39102336)
Partition 0:   ext2fs        0x83
Partition 4: No BSD/SOLARIS sub-partition found (0x82)

hd2 (number of sectors = 320173056
Partition 0:   unknown        0x7
```
According to the results you posted above, your sda drive is first in BIOS boot order or (hd0), and your Ubuntu sdb drive is second or (hd1). That's not good, because according to the script the Grub in the MBR of your sda drive is all ready configured to boot the first partition of the second boot drive, which should be your Ubuntu install on sdb1. How about booting your SGD floppy again, go to the command line, and do:
```
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
```
If those commands complete successfully, continue with:
```
grub> rootnoverify (hd1)
grub> chainloader +1
grub> boot
```
And let me know if that boots Ubuntu or not.

---

### Post by SwooshyCueb on 2009-02-22
It worked!

Am I gonna have to do that every time I boot my PC?

---

### Post by caljohnsmith on 2009-02-22
> **SwooshyCueb said:**
> It worked!

Am I gonna have to do that every time I boot my PC?
Glad to hear that worked OK. What you can do is make a dedicated Grub boot floppy for your Ubuntu install, and just boot with that. How about downloading the attached "menu.lst.txt" to your desktop, and then do:
```
sudo modprobe floppy
sudo mkfs.ext2 /dev/fd0
sudo mount /dev/fd0 /mnt
sudo mkdir -p /mnt/boot/grub
sudo cp ~/Desktop/menu.lst.txt /mnt/boot/grub/menu.lst
sudo cp /usr/lib/grub/*pc/* /mnt/boot/grub/
sudo grub
grub> root (fd0)
grub> setup (fd0)
grub> quit
```
If all the commands complete successfully, try booting from your floppy and let me know how that goes.

---

### Post by SwooshyCueb on 2009-02-23
```
ubuntu@ubuntu:~$ sudo mount /dev/fd0 -t ext2 /mnt
mount: /dev/fd0: can't read superblock
ubuntu@ubuntu:~$ sudo mount /dev/fd0  /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount /dev/fd0 -t ext2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/fd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ 

```

---

### Post by caljohnsmith on 2009-02-23
How about showing the output of all the commands in my previous post, including:
```
sudo mkfs.ext2 /dev/fd0

```

---

