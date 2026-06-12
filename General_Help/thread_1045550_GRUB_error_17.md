---
title: "GRUB error 17"
date: 2009-01-20
forum: General Help
---

### Post by arsen13 on 2009-01-20
Lets start with that I had Windows Vista and Ubuntu 8.10 installed on my pc and everything was working fine. Then I decided to install Windows 7Beta to try it, I made one more partition using Paragon Partition Manager 9.0, but didn't format it and left as free space, when I tried to install Win7 there I had some problems and it stopped installation almost at the beginning but it had already made some changes to the partition, it showed that partition had some data on it. After that i tried to run Windows to format that partition, and now I'm getting GRUB error 17.

Can someone help me fix this, please?

Thanks
-arsen13

---

### Post by caljohnsmith on 2009-01-20
Maybe what happened is your Ubuntu partition changed numbers since you created another partition. If that's the case, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands before doing "quit". If it completes successfully, try rebooting and let me know how far you get.

---

### Post by arsen13 on 2009-01-20
```
sudo grub
Probing devices to guess BIOS drivers. This may take a long time.

          [ Minimal BASH-like line editing is supported. For
          the first word, TAB lists possible command 
          completions. Anywhere else TAB lists the possible
          completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
  (hd0,3)
grub> find /grub/stage1
find /grub/stage1

Error 15: File not found
grub> root (hd0,3)
root (hd0,3)
grub>setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are 
embedded. succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,3)/boot
/grub/stage2 /boot/grub/menu.list"... succeeded
Done.


```

But I don't think it's because of the index problem, because i was able to boot ubuntu after partitioning. And now I can't even boot Windows, the error appears before boot menu.

---

### Post by arsen13 on 2009-01-20
Never mind. About what i think is a problem.

---

### Post by caljohnsmith on 2009-01-20
So are you still getting the Grub error 17 before seeing the boot menu? If so, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by arsen13 on 2009-01-20
```
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
```

---

### Post by caljohnsmith on 2009-01-20
You have to first download that boot_info_script.sh file to your desktop before you can run that command. Please see the link in my previous post.

---

### Post by arsen13 on 2009-01-20
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda4 
                       and looks at sector 269585017 of the same hard drive 
                       for the stage2 file and on partition #4 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   de  Dell Utility
/dev/sda2   *      208845   198691919    99241537+   7  HPFS/NTFS
/dev/sda3       198692864   251142143    26224640    7  HPFS/NTFS
/dev/sda4       251144145   312576704    30716280   83  Linux

sfdisk -V /dev/sda:

Warning: partition 3 does not start at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-080E" TYPE="vfat" 
/dev/sda2: UUID="242EF72D2EF6F720" TYPE="ntfs" 
/dev/sda3: UUID="1CF47A5FF47A3B5A" TYPE="ntfs" 
/dev/sda4: UUID="9f172ed6-4ecf-4125-9d9c-71888717f0b2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

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
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================== sda2/Boot: ==================================

total 520
drwxrwxrwx 1 root root   4096 2009-01-20 23:11 .
drwxrwxrwx 1 root root  12288 2009-01-20 23:11 ..
-rwxrwxrwx 1 root root  20480 2009-01-20 23:11 BCD
-rwxrwxrwx 1 root root  17408 2009-01-20 23:11 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-09-27 19:43 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-09-27 19:43 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-12-20 16:52 bootstat.dat
drwxrwxrwx 1 root root      0 2008-12-21 02:16 cs-CZ
drwxrwxrwx 1 root root      0 2008-12-21 02:16 da-DK
drwxrwxrwx 1 root root      0 2008-12-21 02:16 de-DE
drwxrwxrwx 1 root root      0 2008-12-21 02:16 el-GR
drwxrwxrwx 1 root root      0 2008-12-21 02:16 en-US
drwxrwxrwx 1 root root      0 2008-12-21 02:16 es-ES
drwxrwxrwx 1 root root      0 2008-12-21 02:16 fi-FI
drwxrwxrwx 1 root root      0 2008-12-21 02:16 Fonts
drwxrwxrwx 1 root root      0 2008-12-21 02:16 fr-FR
drwxrwxrwx 1 root root      0 2008-12-21 02:16 hu-HU
drwxrwxrwx 1 root root      0 2008-12-21 02:16 it-IT
drwxrwxrwx 1 root root      0 2008-12-21 02:16 ja-JP
drwxrwxrwx 1 root root      0 2008-12-21 02:16 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 07:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-12-21 02:16 nb-NO
drwxrwxrwx 1 root root      0 2008-12-21 02:16 nl-NL
drwxrwxrwx 1 root root      0 2008-12-21 02:16 pl-PL
drwxrwxrwx 1 root root      0 2008-12-21 02:16 pt-BR
drwxrwxrwx 1 root root      0 2008-12-21 02:16 pt-PT
drwxrwxrwx 1 root root      0 2008-12-21 02:16 ru-RU
drwxrwxrwx 1 root root      0 2008-12-21 02:16 sv-SE
drwxrwxrwx 1 root root      0 2008-12-21 02:16 tr-TR
drwxrwxrwx 1 root root      0 2008-12-21 02:16 zh-CN
drwxrwxrwx 1 root root      0 2008-12-21 02:16 zh-HK
drwxrwxrwx 1 root root      0 2008-12-21 02:16 zh-TW

=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=9f172ed6-4ecf-4125-9d9c-71888717f0b2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9f172ed6-4ecf-4125-9d9c-71888717f0b2

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		9f172ed6-4ecf-4125-9d9c-71888717f0b2
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9f172ed6-4ecf-4125-9d9c-71888717f0b2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		9f172ed6-4ecf-4125-9d9c-71888717f0b2
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9f172ed6-4ecf-4125-9d9c-71888717f0b2 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9f172ed6-4ecf-4125-9d9c-71888717f0b2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9f172ed6-4ecf-4125-9d9c-71888717f0b2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9f172ed6-4ecf-4125-9d9c-71888717f0b2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9f172ed6-4ecf-4125-9d9c-71888717f0b2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9f172ed6-4ecf-4125-9d9c-71888717f0b2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=9f172ed6-4ecf-4125-9d9c-71888717f0b2 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda4/boot: ==================================

total 25528
drwxr-xr-x  3 root root    4096 2008-12-21 03:56 .
drwxr-xr-x 20 root root    4096 2008-12-21 03:55 ..
-rw-r--r--  1 root root  503560 2008-11-04 20:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 23:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 20:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 23:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-21 03:55 grub
-rw-r--r--  1 root root 8670881 2008-12-21 03:54 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8672739 2008-12-21 03:56 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 20:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 23:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 20:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 23:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 20:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 23:30 vmlinuz-2.6.27-9-generic

=============================== sda4/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2008-12-21 03:55 .
drwxr-xr-x 3 root root   4096 2008-12-21 03:56 ..
-rw-r--r-- 1 root root    197 2008-12-21 03:38 default
-rw-r--r-- 1 root root     15 2008-12-21 03:38 device.map
-rw-r--r-- 1 root root   8108 2008-12-21 03:38 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-21 03:38 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-21 03:38 installed-version
-rw-r--r-- 1 root root   8712 2008-12-21 03:38 jfs_stage1_5
-rw-r--r-- 1 root root   5101 2008-12-21 03:55 menu.lst
-rw-r--r-- 1 root root   5017 2008-12-21 03:55 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-21 03:38 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-21 03:38 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-21 03:38 stage1
-rw-r--r-- 1 root root 121460 2008-12-21 03:38 stage2
-rw-r--r-- 1 root root   9556 2008-12-21 03:38 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/sda1

00000000  eb 54 90 44 65 6c 6c 20  38 2e 30 00 02 04 01 00  |.T.Dell 8.0.....|
00000010  02 00 02 00 00 f8 cc 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  8e 2f 03 00 80 00 29 0e  08 d8 07 44 65 6c 6c 55  |./....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 10 00  |tilityFAT16   ..|
00000040  01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 33 c0  8e d0 bc 00 07 fc b9 80  |......3.........|
00000060  00 8e d8 be 00 7c b8 00  20 8e c0 33 ff f3 66 a5  |.....|.. ..3..f.|
00000070  ea 75 00 00 20 8e d8 be  cc 01 b8 01 02 b9 01 00  |.u.. ...........|
00000080  b6 00 8a 16 24 00 bb 00  02 cd 13 0f 82 0c 01 80  |....$...........|
00000090  3e c2 03 06 74 0e c6 06  c2 03 06 b8 01 03 cd 13  |>...t...........|
000000a0  0f 82 f7 00 66 0f b7 06  0e 00 66 03 06 1c 00 66  |....f.....f....f|
000000b0  0f b7 0e 16 00 66 d1 e1  66 03 c1 66 a3 46 00 66  |.....f..f..f.F.f|
000000c0  0f b7 0e 11 00 89 0e 52  00 83 c1 0f c1 e9 04 88  |.......R........|
000000d0  0e 40 00 66 03 c1 66 a3  4e 00 b8 00 30 a3 44 00  |.@.f..f.N...0.D.|
000000e0  8e c0 e8 d4 00 33 db b9  0b 00 be e1 01 8b fb f3  |.....3..........|
000000f0  a6 74 0f 83 c3 20 ff 0e  52 00 75 eb be d7 01 e9  |.t... ..R.u.....|
00000100  99 00 26 8b 47 1a a3 54  00 a1 16 00 a3 52 00 66  |..&.G..T.....R.f|
00000110  0f b7 06 0e 00 66 03 06  1c 00 66 a3 46 00 a1 52  |.....f....f.F..R|
00000120  00 3d 40 00 76 02 b0 40  a2 40 00 e8 8b 00 66 0f  |.=@.v..@.@....f.|
00000130  b6 06 40 00 66 01 06 46  00 29 06 52 00 74 09 c1  |..@.f..F.).R.t..|
00000140  e0 05 01 06 44 00 eb d6  c7 06 44 00 70 00 a0 0d  |....D.....D.p...|
00000150  00 a2 40 00 66 0f b7 06  54 00 66 83 e8 02 66 0f  |..@.f...T.f...f.|
00000160  b6 0e 0d 00 66 f7 e1 66  03 06 4e 00 66 a3 46 00  |....f..f..N.f.F.|
00000170  e8 46 00 8b 36 54 00 b8  00 30 d1 e6 73 03 05 00  |.F..6T...0..s...|
00000180  10 8e c0 26 ad 3d f8 ff  73 16 a3 54 00 0f b6 06  |...&.=..s..T....|
00000190  0d 00 c1 e0 09 01 06 42  00 eb b9 e8 0d 00 eb fe  |.......B........|
000001a0  8a 16 24 00 33 ed ea 00  00 70 00 b4 0e ac bb 07  |..$.3....p......|
000001b0  00 cd 10 80 3c 00 75 f3  c3 b4 42 8a 16 24 00 be  |....<.u...B..$..|
000001c0  3e 00 cd 13 72 01 c3 be  cc 01 eb cf 44 69 73 6b  |>...r.......Disk|
000001d0  20 65 72 72 6f 72 00 4e  6f 20 6c 6f 61 64 65 72  | error.No loader|
000001e0  00 44 45 4c 4c 42 49 4f  20 42 49 4e 00 00 00 00  |.DELLBIO BIN....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

No errors were reported.

---

### Post by caljohnsmith on 2009-01-20
It appears Grub is installed just fine to your HDD, so to get a Grub error 17 in those circumstances sometimes can result from how you have your HDD set up in BIOS. Or, if you're lucky, I've seen where using a slightly different version of Grub can sometimes fix the problem, so I would recommend downloading the [Super Grub Disk]("http://www.supergrubdisk.org") and using that to restore Grub to the HDD. How about trying that and let me know how it goes.

---

### Post by arsen13 on 2009-01-21
I downloaded the GRUB put in on the usb stick and even without it when i restarted my computer everything was fine, I have no idea how that happened but now everything is fine. oh yes I've tried to format the new partition using ubuntu live cd, maybe it helped i don't know but now everything is fine.
Thank you for your help

---

### Post by arsen13 on 2009-01-21
And one more question, out of theme.
How can I enter the directories which contain spaces in their names, using the terminal.
just cd name doesn't work. eg
```
cd new directory
bash: cd: new: No such file or directory
```

---

### Post by Noblacktie on 2009-01-21
I use a wildcard, which I'm sure is the wrong way to do it but just in case you need to go there urgently, try

```
$ cd new*
```

---

### Post by caljohnsmith on 2009-01-21
When you have spaces between the words in a directory name, you can either use quotes or a backslash to escape the space:
```
cd "new directory"
cd new\ directory
```
I think using quotes is more readable, but it's up to you. And if you don't have any other directories starting with "new" in the directory where you run the cd command, you can always do as Noblacktie suggested and use a wildcard.

---

