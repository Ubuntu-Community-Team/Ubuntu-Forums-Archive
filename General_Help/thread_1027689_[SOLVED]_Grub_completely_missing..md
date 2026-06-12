---
title: "[SOLVED] Grub completely missing."
date: 2009-01-01
forum: General Help
---

### Post by utter-imadness on 2009-01-01
Hi all.
I had a major problem with my ubuntu but decided to freshly install the new 8.10 instead of fixing the problem. I decided to do a fresh install so I completely erased my root partition and reinstalled. I had /sda1 to be my root (/) partition and /sda4 to be my home partition.
Now the problem is when I reinstalled grub seemed to be missing so I wasn't able to start up my computer. When the computer would try to find grub it would give me Error 15 meaning that it was missing. I ran ubuntu off a usb stick and found that the boot folder was missing most of the files that it should have. This is what's in it:
```
ubuntu@ubuntu:/media/disk-1/boot$ dir
abi-2.6.27-7-generic	 System.map-2.6.27-7-generic
config-2.6.27-7-generic  vmcoreinfo-2.6.27-7-generic
memtest86+.bin		 vmlinuz-2.6.27-7-generic
```

I remember that before the installation the folder had grub and the different kernels. I tried reinstalling 8.04 again, then 8.10, multiple times with different settings. But no matter what I tried grub was still missing. 
I also have Windows Vista as a separate partition so I was thinking that might somehow be the problem.

Here's some info on my system:
```
ubuntu@ubuntu:/media/disk-1/boot$ sudo sfdisk -V
/dev/sda: OK
Warning: partition 1 extends past end of disk
```

This is something that I found on some of the other threads:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```

...which gives:

```
============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab /boot

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 403617060. BootPart in the file 
                       /NST/nst_grub.mbr is trying to chain load sector #63 
                       on boot drive #1
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /bootmgr /grldr /Boot /NST

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda5: _________________________________________________________________________

    File system:       swap

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x09e709e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    13317884     6658911   83  Linux
/dev/sda2   *   403617060   476246924    36314932+   7  HPFS/NTFS
/dev/sda3       476246925   488392064     6072570    5  Extended
/dev/sda4        13317885   403617059   195149587+  83  Linux
/dev/sda5       476246988   488392064     6072538+  82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 8011 MB, 8011120640 bytes
16 heads, 32 sectors/track, 30560 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1eec2611

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    15646719     7823344    c  W95 FAT32 (LBA)

sfdisk -V /dev/sdc:

Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="665f79d6-e657-4802-8107-055201e21dda" TYPE="ext3" 
/dev/sda2: UUID="3210569510565FC1" TYPE="ntfs" 
/dev/sda4: UUID="1da56650-dc3d-4d4a-bcdd-b155284c3898" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="6c7f6b86-9655-41b3-8f1d-9cd8699d3843" TYPE="swap" 
/dev/sdc1: LABEL="IMAD" UUID="493E-D5A8" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="dd02a5f5-d70e-4ab5-82dd-c0d47ca8b040" TYPE="ext3" 

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
/dev/sdc1 on /cdrom type vfat (rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=665f79d6-e657-4802-8107-055201e21dda /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=1da56650-dc3d-4d4a-bcdd-b155284c3898 /home           ext3    relatime        0       2
# /dev/sda5
UUID=6c7f6b86-9655-41b3-8f1d-9cd8699d3843 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 3944
drwxr-xr-x  2 root root    4096 2009-01-01 13:07 .
drwxr-xr-x 20 root root    4096 2009-01-01 13:04 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2009-01-01 16:45 vmlinuz-2.6.27-7-generic

============================== sda2/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File

#

# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst

# Please see the EasyBCD Documentation for information on how to create/modify entries:

# http://neosmart.net/wiki/display/EBCD



title		Ubuntu 8.04.1, kernel 2.6.24-21-generic

root		(hd0,0)

kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=34eca8d3-4a43-40c9-ab04-d50b336082ac ro quiet splash

initrd		/boot/initrd.img-2.6.24-21-generic

quiet




title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)

root		(hd0,0)

kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=34eca8d3-4a43-40c9-ab04-d50b336082ac ro single

initrd		/boot/initrd.img-2.6.24-21-generic



title		Ubuntu 8.04.1, kernel 2.6.24-19-generic

root		(hd0,0)

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=34eca8d3-4a43-40c9-ab04-d50b336082ac ro quiet splash

initrd		/boot/initrd.img-2.6.24-19-generic

quiet



title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)

root		(hd0,0)

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=34eca8d3-4a43-40c9-ab04-d50b336082ac ro single

initrd		/boot/initrd.img-2.6.24-19-generic



title		Ubuntu 8.04.1, kernel 2.6.24-16-generic

root		(hd0,0)

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=34eca8d3-4a43-40c9-ab04-d50b336082ac ro quiet splash

initrd		/boot/initrd.img-2.6.24-16-generic

quiet



title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)

root		(hd0,0)

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=34eca8d3-4a43-40c9-ab04-d50b336082ac ro single

initrd		/boot/initrd.img-2.6.24-16-generic



title		Ubuntu 8.04.1, memtest86+

root		(hd0,0)

kernel		/boot/memtest86+.bin

quiet


================================== sda2/Boot: ==================================

total 548
drwxrwxrwx 1 root root   4096 2008-10-26 06:11 .
drwxrwxrwx 1 root root  12288 2009-01-01 03:08 ..
-rwxrwxrwx 1 root root  32768 2009-01-01 19:16 BCD
-rwxrwxrwx 2 root root  24576 2008-10-27 08:00 BCD.Backup.0001
-rwxrwxrwx 1 root root  29696 2009-01-01 19:16 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-10-26 06:11 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-10-26 06:11 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-10-26 06:11 bootstat.dat
drwxrwxrwx 1 root root      0 2008-10-26 06:11 cs-CZ
drwxrwxrwx 1 root root      0 2008-10-26 06:11 da-DK
drwxrwxrwx 1 root root      0 2008-10-26 06:11 de-DE
drwxrwxrwx 1 root root      0 2008-10-26 06:11 el-GR
drwxrwxrwx 1 root root      0 2008-10-26 06:11 en-US
drwxrwxrwx 1 root root      0 2008-10-26 06:11 es-ES
drwxrwxrwx 1 root root      0 2008-10-26 06:11 fi-FI
drwxrwxrwx 1 root root      0 2008-10-26 06:11 Fonts
drwxrwxrwx 1 root root      0 2008-10-26 06:11 fr-FR
drwxrwxrwx 1 root root      0 2008-10-26 06:11 hu-HU
drwxrwxrwx 1 root root      0 2008-10-26 06:11 it-IT
drwxrwxrwx 1 root root      0 2008-10-26 06:11 ja-JP
drwxrwxrwx 1 root root      0 2008-10-26 06:11 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 09:51 memtest.exe
drwxrwxrwx 1 root root      0 2008-10-26 06:11 nb-NO
drwxrwxrwx 1 root root      0 2008-10-26 06:11 nl-NL
drwxrwxrwx 1 root root      0 2008-10-26 06:11 pl-PL
drwxrwxrwx 1 root root      0 2008-10-26 06:11 pt-BR
drwxrwxrwx 1 root root      0 2008-10-26 06:11 pt-PT
drwxrwxrwx 1 root root      0 2008-10-26 06:11 ru-RU
drwxrwxrwx 1 root root      0 2008-10-26 06:11 sv-SE
drwxrwxrwx 1 root root      0 2008-10-26 06:11 tr-TR
drwxrwxrwx 1 root root      0 2008-10-26 06:11 zh-CN
drwxrwxrwx 1 root root      0 2008-10-26 06:11 zh-HK
drwxrwxrwx 1 root root      0 2008-10-26 06:11 zh-TW

================================== sda2/NST: ==================================

total 25
drwxrwxrwx 1 root root     0 2009-01-01 18:55 .
drwxrwxrwx 1 root root 12288 2009-01-01 03:08 ..
-rwxrwxrwx 1 root root  1684 2008-10-26 00:45 menu.lst
-rwxrwxrwx 1 root root  8192 2008-04-08 17:50 NeoGrub.mbr
-rwxrwxrwx 1 root root   512 2009-01-01 18:55 nst_grub.mbr

=============================== StdErr Messages: ===============================

Unknown MBR on /dev/sdc

00000000  fa be 00 7c bf 00 7a b9  00 01 fc 0e 1f 0e 07 f3  |...|..z.........|
00000010  a5 ea 16 7a 00 00 bb be  7b 33 c9 80 3f 80 75 06  |...z....{3..?.u.|
00000020  fe c5 8b f3 eb 07 80 3f  00 75 02 fe c1 83 c3 10  |.......?.u......|
00000030  81 fb fe 7b 72 e5 83 f9  04 74 0b 81 f9 03 01 74  |...{r....t.....t|
00000040  0a bb a5 7a eb 2c bb 87  7a eb 27 8b 4c 02 8b 14  |...z.,..z.'.L...|
00000050  b8 01 02 bb 00 7c cd 13  73 05 bb bc 7a eb 13 2e  |.....|..s...z...|
00000060  a1 fe 7d 3d 55 aa 74 05  bb bc 7a eb 05 ea 00 7c  |..}=U.t...z....||
00000070  00 00 2e 8a 07 3c 00 74  0c 53 bb 07 00 b4 0e cd  |.....<.t.S......|
00000080  10 5b 43 eb ed eb fe 4e  6f 20 62 6f 6f 74 61 62  |.[C....No bootab|
00000090  6c 65 20 70 61 72 74 69  74 6f 6e 20 69 6e 20 74  |le partiton in t|
000000a0  61 62 6c 65 00 49 6e 76  61 6c 69 64 20 50 61 72  |able.Invalid Par|
000000b0  74 69 74 6f 6e 20 74 61  62 6c 65 00 49 6e 76 61  |titon table.Inva|
000000c0  6c 69 64 20 6f 72 20 64  61 6d 61 67 65 64 20 42  |lid or damaged B|
000000d0  6f 6f 74 61 62 6c 65 20  70 61 72 74 69 74 69 6f  |ootable partitio|
000000e0  6e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |n...............|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  11 26 ec 1e 00 00 80 01  |.........&......|
000001c0  01 00 0c 0f e0 5f 20 00  00 00 e0 bf ee 00 00 00  |....._ .........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

No errors were reported.
```

more info:
```
ubuntu@ubuntu:~/Desktop$ sudo sfdisk -luS

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63  13317884   13317822  83  Linux
/dev/sda2   * 403617060 476246924   72629865   7  HPFS/NTFS
/dev/sda3     476246925 488392064   12145140   5  Extended
/dev/sda4      13317885 403617059  390299175  83  Linux
/dev/sda5     476246988 488392064   12145077  82  Linux swap / Solaris

Disk /dev/sdc: 1021 cylinders, 247 heads, 62 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/16/32 (instead of 1021/247/62).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1   *        32  15646719   15646688   c  W95 FAT32 (LBA)
		end: (c,h,s) expected (1023,15,32) found (863,15,32)
/dev/sdc2             0         -          0   0  Empty
/dev/sdc3             0         -          0   0  Empty
/dev/sdc4             0         -          0   0  Empty
```

...and lastly:
```
ubuntu@ubuntu:~/Desktop$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 13317822, Id=83
/dev/sda2 : start=403617060, size= 72629865, Id= 7, bootable
/dev/sda3 : start=476246925, size= 12145140, Id= 5
/dev/sda4 : start= 13317885, size=390299175, Id=83
/dev/sda5 : start=476246988, size= 12145077, Id=82
```

Any help will be GREATLY appreciated.

---

### Post by caljohnsmith on 2009-01-01
So do you want to use Grub as your boot manager or use Vista's boot manager? If you want to use Grub, when you did the installation, did you click on the "advanced" button near the end and choose to not install Grub? Because otherwise I'm confused why Grub wouldn't be installed as per normal.

---

### Post by kokkus on 2009-01-01
YOu can use the live ubuntu cd and install GRUBEditor to fix this problem.

---

### Post by utter-imadness on 2009-01-01
> **caljohnsmith said:**
> So do you want to use Grub as your boot manager or use Vista's boot manager? If you want to use Grub, when you did the installation, did you click on the "advanced" button near the end and choose to not install Grub? Because otherwise I'm confused why Grub wouldn't be installed as per normal.

I'd rather use GRUB instead of the bootloader made by EasyBCD. I also tried running ubuntu from that bootloader and it still woudln't work. 
And yes, during the installation I clicked the advanced button and chose to have a bootloader installed to /dev/sda

> **kokkus said:**
> YOu can use the live ubuntu cd and install GRUBEditor to fix this problem.

Thanks. I'll try that now and post my results.

BTW, I also tried using the Super Grub Disc with no avail.

---

### Post by caljohnsmith on 2009-01-01
Unfortunately, GrubEditor won't be able to help you because you don't have Grub currently installed. If you would like some help installing Grub, how about trying the following:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt --recheck /dev/sda
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt /bin/bash
apt-get install grub
update-grub
cat /boot/grub/menu.lst
exit
```
And please post the output of all the above commands. We can work from there if you want.

---

### Post by utter-imadness on 2009-01-01
Thanks.
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/boot/grub"] is not on an XFS filesystem
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdc
```

then...
```
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) 
```

Should I put Yes or No?

---

### Post by caljohnsmith on 2009-01-01
Say "Y" to create a new menu.lst. :)

---

### Post by utter-imadness on 2009-01-01
So here's the final output:
```
Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

And here's the menu.lst contents:
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
timeout		3

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
# kopt=root=UUID=665f79d6-e657-4802-8107-055201e21dda ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=665f79d6-e657-4802-8107-055201e21dda

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
uuid		665f79d6-e657-4802-8107-055201e21dda
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=665f79d6-e657-4802-8107-055201e21dda ro quiet splash 
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		665f79d6-e657-4802-8107-055201e21dda
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=665f79d6-e657-4802-8107-055201e21dda ro  single

title		Ubuntu 8.10, memtest86+
uuid		665f79d6-e657-4802-8107-055201e21dda
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

So should it work when I restart now?
And also, will the vista bootloader somehow mess up the start up? I used to only see it when I chose the vista option in the grub menu so I thought that the redundancy shouldn't really matter.

---

### Post by caljohnsmith on 2009-01-01
Yes, go ahead and reboot, and it looks like you should be able to boot into Ubuntu just fine. If that works OK, then once you are in Ubuntu, do:
```
gksudo gedit /boot/grub/menu.lst
```
And add at the bottom:
```
title Windows Vista
root (hd0,1)
chainloader +1
```
And then you should also be able to boot Vista from Grub. You might also want to put a pound sign # in front of the "hiddenmenu" line at the top so that you see the Grub menu by default:
```
# hiddenmenu
```
Let me know how it goes or if you run into problems.

---

### Post by utter-imadness on 2009-01-01
Hmmm. GRUB seems to load fine, but right after that it gets a kernel panic. Here's the error message:

```
Boot from (hd0,0) ext3 665f79d6-e657-4802-8107-0552de21dda
Starting up ...
[   0.868113] Kernel panic - not syncing: VFS: Unable to mount root f s on unknown - block(0,0)
```

And my Caps Lock light keeps flashing; none of the others do.

---

### Post by caljohnsmith on 2009-01-01
It sounds like maybe more went wrong with your Ubuntu install than just Grub not getting installed. If you've not been having any problems booting the Intrepid Live CD, then installing it should not normally lead to a kernel panic. When you did the installation, in the end did it say that everything was installed successfully, or did you get some errors?

---

### Post by utter-imadness on 2009-01-01
When I installed 8.10 it seemed successful and didn't give me any errors. Should I try installing it again? And if I do, will I have to follow the previous steps that you gave me again?

BTW, thanks a lot for helping me so far! :KS

---

### Post by caljohnsmith on 2009-01-01
Which version of Ubuntu did you have installed before? Did you ever have Intrepid fresh-installed (not upgraded from Hardy) and working at any point? I guess you could try reinstalling again, but how about this time not changing any of the Grub settings under the "advanced" button; by default Grub should get installed to the MBR of your sda drive, so see if maybe that works this time. Let me know how it goes.

---

### Post by utter-imadness on 2009-01-01
I originally used 8.04, then about a month ago I upgraded to 8.10. But because of multiple problems (nvidia support, loud system beeping at start up) and my limited schedule to fix them I went back to 8.04. This is also when I created separate root and home partitions. 

And also, last time I installed I kept the bootloader options the same under the Advanced tab. I kept it on sda. The only thing I changed was the choice to participate in the package usage survey.

When I reinstall, should I format/delete the root partition and start off fresh?

---

### Post by caljohnsmith on 2009-01-01
> **utter-imadness said:**
> 
When I reinstall, should I format/delete the root partition and start off fresh?
Yes, I think that sounds like a good idea. Hopefully your install will go better this time. Good luck and let me know how it goes. :)

---

### Post by utter-imadness on 2009-01-01
I just attempted a reinstall 8.10 and it seems that there is an error after the install. The installer gets to about 78% and has the message "Less than a minute left...". Then it suddenly jumps from 78% and instantly boots from the CD without reaching anywhere near 100%. Then the crash reporter gives me an error that the installer crashed and sends an error report. 

I didn't find this suspicious the last few times but now that I think about it it shouldn't boot to the CD after installation. Could the be the fault of a faulty .iso image? I'll try redownloading and burning it to another disc to try.

---

### Post by caljohnsmith on 2009-01-01
> **utter-imadness said:**
> Could the be the fault of a faulty .iso image? I'll try redownloading and burning it to another disc to try.
Might be, I would check the md5 sum of the ISO before burning, and also burn at a slow speed (4X). You can check the md5 sum with:
```
md5sum <iso image>

```
Also, when you boot the Intrepid CD, choose the option from the main menu that allows the CD to check itself for defects. I think that would be a good thing to do before you reinstall again. Let me know how it goes.

---

### Post by utter-imadness on 2009-01-01
Alright. So I finally found the real culprit. It seems that the reason that 8.10 or 8.04 wouldn't install properly is that I would put sda4 as my /home directory. I installed 8.10 without mounting sda4 as /home and the installation went smoothly. 
Now all I have to do is make sda4 my /home directory directly from ubuntu. 

Thanks again for all your help caljohnsmith!

---

### Post by caljohnsmith on 2009-01-01
That's great news, glad to hear you finally got Ubuntu to install OK. Cheers and Happy New Year. :)

---

