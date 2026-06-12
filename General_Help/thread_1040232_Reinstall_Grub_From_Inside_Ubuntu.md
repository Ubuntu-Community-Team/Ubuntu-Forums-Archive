---
title: "Reinstall Grub From Inside Ubuntu"
date: 2009-01-15
forum: General Help
---

### Post by joey-elijah on 2009-01-15
Hi, i've had lots of grub issues lately after installing Windows 7. So far nothing has helped - from using a live cd to using supergrubdisk to install. However supergrubdisc on a USB has let me FINALLY get back inside Ubuntu so i was just wondering how i reinstall Grub from within Ubuntu. is it the same set of commands as installing it from a Live Cd?

E.G. Sudo Grub > stage 1 etc

---

### Post by utnubuuser on 2009-01-15
Probably not, since your partitions are mounted when Ubuntu is running, and you can't just un-mount them.  Can't use the live CD to access the partitions at all?

---

### Post by caljohnsmith on 2009-01-15
> **joey-elijah said:**
> Hi, i've had lots of grub issues lately after installing Windows 7. So far nothing has helped - from using a live cd to using supergrubdisk to install. However supergrubdisc on a USB has let me FINALLY get back inside Ubuntu so i was just wondering how i reinstall Grub from within Ubuntu. is it the same set of commands as installing it from a Live Cd?

E.G. Sudo Grub > stage 1 etc
Sure, you can reinstall Grub while you are booted into your Ubuntu install, you don't have to use the Live CD. Just do the usual Grub commands that you've probably all ready seen before:

```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how it goes or if you run into problems.

---

### Post by joey-elijah on 2009-01-15
Hi many thanks! I've just done the steps above and will reboot and hope for the best!

---

### Post by blazemore on 2009-01-15
If it doesn't work:
```
sudo apt-get install grub -y
``` just to be sure.

Then just
```
sudo update-grub
```

---

### Post by joey-elijah on 2009-01-15
> **blazemore said:**
> If it doesn't work:
```
sudo apt-get install grub -y
``` just to be sure.

Then just
```
sudo update-grub
```

it didn't work, so i'll try the above!

---

### Post by joey-elijah on 2009-01-16
STILL have no grub! I really don't understand.

is there some way to manually create it or some super powerful option?

I guess an easy way to get it would be to install another distro...?

---

### Post by caljohnsmith on 2009-01-16
It's up to you if you want to install another distro, but I think there might be other issues at play; it would help to get a better picture of your setup in order to figure out what the problem is, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by joey-elijah on 2009-01-16
Okay, thanks. here are the results: -

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #3 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on boot drive #1 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda5 
                       and looks at sector 297870694 of the same hard drive 
                       for the stage2 file and on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  Geometry: 255 Heads and 32 sectors per Track. 
                       According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 63. Grub in the file /ubninit 
                       looks at sector 1101 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x682a8121

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    48725144    24362541   83  Linux
/dev/sda2        48726016   110532607    30903296    7  HPFS/NTFS
/dev/sda3       174020608   287473663    56726528    7  HPFS/NTFS
/dev/sda4       287483175   312576704    12546765    5  Extended
/dev/sda5       287483238   312576704    12546733+  83  Linux

sfdisk -V /dev/sda:

Warning: partition 2 does not start at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      411647      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2          411648    82569215    41078784    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

sfdisk -V /dev/sdb:

Warning: partition 1 does not end at a cylinder boundary

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 2048 MB, 2048901120 bytes
255 heads, 63 sectors/track, 249 cylinders, total 4001760 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     4001759     2000848+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(249, 24, 63)

sfdisk -V /dev/sdc:

Warning: partition 1 extends past end of disk

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc7087ef7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   976768064   488384001    7  HPFS/NTFS

sfdisk -V /dev/sdd:

/dev/sdd: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="CCF490FBF490E94A" TYPE="ntfs" 
/dev/sda3: UUID="74A0075DA0072568" LABEL="Shared Space" TYPE="ntfs" 
/dev/sda5: UUID="63ef1824-9468-4f34-bb50-eaac561eb896" TYPE="ext3" 
/dev/sdb1: UUID="1C64AE2C64AE089A" TYPE="ntfs" 
/dev/sdb2: UUID="B6F0ABD6F0AB9B5F" TYPE="ntfs" 
/dev/sdc1: LABEL="YOUESBE" UUID="8ACD-100B" TYPE="vfat" 
/dev/sdd1: UUID="5D5165E912592A10" LABEL="ExTeRnAl DriiiiVe" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/joey/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joey)
/dev/sdd1 on /media/ExTeRnAl DriiiiVe type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/YOUESBE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda3 on /media/Shared Space_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=========================== sda5/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=63ef1824-9468-4f34-bb50-eaac561eb896 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=63ef1824-9468-4f34-bb50-eaac561eb896

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

title        Ubuntu 8.10, kernel 2.6.27-9-generic
uuid        63ef1824-9468-4f34-bb50-eaac561eb896
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=63ef1824-9468-4f34-bb50-eaac561eb896 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid        63ef1824-9468-4f34-bb50-eaac561eb896
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=63ef1824-9468-4f34-bb50-eaac561eb896 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        63ef1824-9468-4f34-bb50-eaac561eb896
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=63ef1824-9468-4f34-bb50-eaac561eb896 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        63ef1824-9468-4f34-bb50-eaac561eb896
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=63ef1824-9468-4f34-bb50-eaac561eb896 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        63ef1824-9468-4f34-bb50-eaac561eb896
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=63ef1824-9468-4f34-bb50-eaac561eb896 / ext3 relatime,errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

================================== sda5/boot: ==================================

total 25524
drwxr-xr-x  3 root root    4096 2009-01-02 21:30 .
drwxr-xr-x 21 root root    4096 2009-01-08 19:03 ..
-rw-r--r--  1 root root  503560 2008-11-04 20:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 23:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 20:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 23:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-16 01:40 grub
-rw-r--r--  1 root root 8670885 2009-01-02 21:29 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8671023 2009-01-02 21:30 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 20:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 23:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 20:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 23:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 20:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 23:30 vmlinuz-2.6.27-9-generic

=============================== sda5/boot/grub: ===============================

total 232
drwxr-xr-x 2 root root   4096 2009-01-16 01:40 .
drwxr-xr-x 3 root root   4096 2009-01-02 21:30 ..
-rw-r--r-- 1 root root    197 2009-01-02 19:24 default
-rw-r--r-- 1 root root     45 2009-01-02 19:24 device.map
-rw-r--r-- 1 root root   8108 2009-01-02 19:24 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-02 19:24 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-02 19:24 installed-version
-rw-r--r-- 1 root root   8712 2009-01-02 19:24 jfs_stage1_5
-rw-r--r-- 1 root root   5101 2009-01-16 01:40 menu.lst
-rw-r--r-- 1 root root   5101 2009-01-16 01:40 menu.lst~
-rw-r--r-- 1 root root   5101 2009-01-05 01:52 menu.lst_backup
-rw-r--r-- 1 root root   7352 2009-01-02 19:24 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-02 19:24 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-02 19:24 stage1
-rw-r--r-- 1 root root 121460 2009-01-02 19:24 stage2
-rw-r--r-- 1 root root   9556 2009-01-02 19:24 xfs_stage1_5

================================== sdb1/Boot: ==================================

total 600
drwxrwxrwx 1 root root   4096 2009-01-12 00:05 .
drwxrwxrwx 1 root root   4096 2009-01-11 16:07 ..
-rwxrwxrwx 1 root root  32768 2009-01-16 15:52 BCD
-rwxrwxrwx 1 root root  29696 2009-01-16 15:44 BCD.LOG
-rwxrwxrwx 2 root root      0 2009-01-12 00:05 BCD.LOG1
-rwxrwxrwx 2 root root      0 2009-01-12 00:05 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2009-01-12 00:05 bootstat.dat
drwxrwxrwx 1 root root      0 2009-01-12 00:05 cs-CZ
drwxrwxrwx 1 root root      0 2009-01-12 00:05 da-DK
drwxrwxrwx 1 root root      0 2009-01-12 00:05 de-DE
drwxrwxrwx 1 root root      0 2009-01-12 00:05 el-GR
drwxrwxrwx 1 root root      0 2009-01-12 00:05 en-US
drwxrwxrwx 1 root root      0 2009-01-12 00:05 es-ES
drwxrwxrwx 1 root root      0 2009-01-12 00:05 fi-FI
drwxrwxrwx 1 root root      0 2009-01-12 00:05 Fonts
drwxrwxrwx 1 root root      0 2009-01-12 00:05 fr-FR
drwxrwxrwx 1 root root      0 2009-01-12 00:05 hu-HU
drwxrwxrwx 1 root root      0 2009-01-12 00:05 it-IT
drwxrwxrwx 1 root root      0 2009-01-12 00:05 ja-JP
drwxrwxrwx 1 root root      0 2009-01-12 00:05 ko-KR
-rwxrwxrwx 1 root root 473864 2008-12-13 07:01 memtest.exe
drwxrwxrwx 1 root root      0 2009-01-12 00:05 nb-NO
drwxrwxrwx 1 root root      0 2009-01-12 00:05 nl-NL
drwxrwxrwx 1 root root      0 2009-01-12 00:05 pl-PL
drwxrwxrwx 1 root root      0 2009-01-12 00:05 pt-BR
drwxrwxrwx 1 root root      0 2009-01-12 00:05 pt-PT
drwxrwxrwx 1 root root      0 2009-01-12 00:05 ru-RU
drwxrwxrwx 1 root root      0 2009-01-12 00:05 sv-SE
drwxrwxrwx 1 root root      0 2009-01-12 00:05 tr-TR
drwxrwxrwx 1 root root      0 2009-01-12 00:05 zh-CN
drwxrwxrwx 1 root root      0 2009-01-12 00:05 zh-HK
drwxrwxrwx 1 root root      0 2009-01-12 00:05 zh-TW

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/sdd1

00000000  eb 5b 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.[.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  00 4c 38 3a 00 00 00 00  |.........L8:....|
00000030  04 00 00 00 00 00 00 00  c0 84 a3 03 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  10 2a 59 12 e9 65 51 5d  |.........*Y..eQ]|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 fa 33 c0  |..............3.|
00000060  8e d0 bc 00 7c fb b8 c0  07 8e d8 c7 06 54 00 00  |....|........T..|
00000070  00 c7 06 56 00 00 00 c7  06 5b 00 10 00 b8 00 0d  |...V.....[......|
00000080  8e c0 2b db e8 07 00 68  00 0d 68 66 02 cb 50 53  |..+....h..hf..PS|
00000090  51 52 06 66 a1 54 00 66  03 06 1c 00 66 33 d2 66  |QR.f.T.f....f3.f|
000000a0  0f b7 0e 18 00 66 f7 f1  fe c2 88 16 5a 00 66 8b  |.....f......Z.f.|
000000b0  d0 66 c1 ea 10 f7 36 1a  00 88 16 25 00 a3 58 00  |.f....6....%..X.|
000000c0  a1 18 00 2a 06 5a 00 40  3b 06 5b 00 76 03 a1 5b  |...*.Z.@;.[.v..[|
000000d0  00 50 b4 02 8b 16 58 00  b1 06 d2 e6 0a 36 5a 00  |.P....X......6Z.|
000000e0  8b ca 86 e9 8a 36 25 00  b2 80 cd 13 58 72 2a 01  |.....6%.....Xr*.|
000000f0  06 54 00 83 16 56 00 00  29 06 5b 00 76 0b c1 e0  |.T...V..).[.v...|
00000100  05 8c c2 03 d0 8e c2 eb  8a 07 5a 59 5b 58 c3 be  |..........ZY[X..|
00000110  59 01 eb 08 be e3 01 eb  03 be 39 01 e8 09 00 be  |Y.........9.....|
00000120  ad 01 e8 03 00 fb eb fe  ac 3c 00 74 09 b4 0e bb  |.........<.t....|
00000130  07 00 cd 10 eb f2 c3 1d  00 41 20 64 69 73 6b 20  |.........A disk |
00000140  72 65 61 64 20 65 72 72  6f 72 20 6f 63 63 75 72  |read error occur|
00000150  72 65 64 2e 0d 0a 00 29  00 41 20 6b 65 72 6e 65  |red....).A kerne|
00000160  6c 20 66 69 6c 65 20 69  73 20 6d 69 73 73 69 6e  |l file is missin|
00000170  67 20 66 72 6f 6d 20 74  68 65 20 64 69 73 6b 2e  |g from the disk.|
00000180  0d 0a 00 25 00 41 20 6b  65 72 6e 65 6c 20 66 69  |...%.A kernel fi|
00000190  6c 65 20 69 73 20 74 6f  6f 20 64 69 73 63 6f 6e  |le is too discon|
000001a0  74 69 67 75 6f 75 73 2e  0d 0a 00 33 00 49 6e 73  |tiguous....3.Ins|
000001b0  65 72 74 20 61 20 73 79  73 74 65 6d 20 64 69 73  |ert a system dis|
000001c0  6b 65 74 74 65 20 61 6e  64 20 72 65 73 74 61 72  |kette and restar|
000001d0  74 0d 0a 74 68 65 20 73  79 73 74 65 6d 2e 0d 0a  |t..the system...|
000001e0  00 17 00 5c 4e 54 4c 44  52 20 69 73 20 63 6f 6d  |...\NTLDR is com|
000001f0  70 72 65 73 73 65 64 2e  0d 0a 00 00 00 00 55 aa  |pressed.......U.|
00000200


=============================== StdErr Messages: ===============================

/dev/sda1: unknown volume type
```

Also, as a British user the '#' is called a hash... the 'pound sign' is '£'. Cultural differences :KS

---

### Post by caljohnsmith on 2009-01-16
OK, if you are still booting straight into Windows, it is clear your BIOS is set to boot the 80 GB sdb drive on start up. Fortunately you still have Grub installed properly to your Ubuntu sda drive, so if you set your BIOS to boot the 160 GB sda drive, you should be able to boot into Ubuntu. But before you try that, how about first doing:
```
sudo sfdisk -A1 /dev/sda
```
That will mark the first partition on the sda drive as bootable; it is good to do that to avoid problems with your BIOS, because some modern BIOSes will refuse to boot a drive that doesn't have one partition marked as bootable. So after you've done that, how about rebooting, set your BIOS to boot the 160 GB Ubuntu drive, and hopefully you will be able to boot into Ubuntu if all goes well. Let me know how it goes or if you run into problems.

---

### Post by dcstar on 2009-01-16
> **joey-elijah said:**
> Hi, i've had lots of grub **issues lately after installing Windows 7**. So far nothing has helped 
.......

Does anyone know if Windows 7 totally stuffs up Linux installations now??

---

