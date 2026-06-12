---
title: "Booting Ubuntu 8.10 with grub4dos"
date: 2009-02-08
forum: General Help
---

### Post by ninadb on 2009-02-08
Hi

i have 2 Hard disks in my pc. One is for Win Xp and the other disk I plan to install multiple distros.

I installed Ubuntu 8.10 from the live cd to my second HDD i.e. /dev/sdb1. I also installed grub on /dev/sdb1.

I have unzipped grub4dos and copied the grldr file to c:\
Added the C:\GRLDR to boot.ini also.

When I start my pc it correctly gives 2 options for  booting correctly i.e Win XP and "Start Grub"
When start grub is selected it directly goes to the grub prompt and does not boot ubuntu on sdb1

I feel i am missing some step.
How does grub4dos detect the /dev/sdb1 partition
Earlier I have been using Ubuntu 7.04 successfully by using grub4dos.
I do not want to install grub on mbr

Questions
----------
How do i boot by using grub4dos
What are the other ways of booting from /dev/sdb1


Thanks
Ninad

---

### Post by logos34 on 2009-02-08
You could try this variation:

--boot the live cd, mount sdb1 and the windows partition, write grub to the bootsector of sdb1:

> sudo grub-install --root-directory=/media/disk /dev/sdb1

(replace '/media/disk' with your mountpoint if different)

copy it to C: directory:
> 
sudo dd if=/dev/sdb1 of=/path/to/windows/linux.bin bs=512 count=1

add 'linux.bin' (or 'grub.mbr' or whatever you want to call it) to boot.ini

---

### Post by caljohnsmith on 2009-02-08
It sounds to me like you still need to copy over your Ubuntu's /boot/grub/menu.lst file into your Windows root directory; you need a menu.lst that Grub4DOS can read on start up, otherwise you can get dumped into the Grub command prompt. If you need help with that, how about booting the Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by ninadb on 2009-02-11
Here is the output of fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x50c450c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    52227314    26113626    7  HPFS/NTFS
/dev/sda2        52227315   156280319    52026502+   f  W95 Ext'd (LBA)
/dev/sda5        52227378   104454629    26113626    7  HPFS/NTFS
/dev/sda6       104454693   156280319    25912813+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000aa4ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    19535039     9767488+  83  Linux
/dev/sdb2        19535040    23438834     1951897+  82  Linux swap / Solaris
ubuntu@ubuntu:/$ 
ubuntu@ubuntu:/$ d

---

### Post by caljohnsmith on 2009-02-11
I thought of maybe a better solution for your situation than using Grub4DOS, but it depends on whether you can set your BIOS to boot the sdb Linux drive--can you do that? In other words, can you go into your BIOS and change the "boot order" so that you can boot the Linux sdb drive before the Windows sda drive? If so, you could simply install Grub to the MBR (Master Boot Record) of sdb and boot all your OSes from that drive, including Windows. Also, if anything happens to your linux drive, all you would have to do is change your BIOS back to booting the Windows drive in order to boot into Windows. 

At this point I think it would help to get more info about your system related to booting, so how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and give us a better idea how to best proceed.

---

### Post by ninadb on 2009-02-16
Here is the output of running the script
Sorry about the delayed response



```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /grldr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63. The info in boot sector on the starting 
                       sector of the MFT is wrong. The info in the boot 
                       sector on the starting sector of the MFT Mirror is 
                       wrong.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63. The info in boot sector on the starting 
                       sector of the MFT is wrong. The info in the boot 
                       sector on the starting sector of the MFT Mirror is 
                       wrong.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 13058111 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Boot file info:     Grub0.97 in the file /linux.bin looks at sector 
                       13058111 of the same hard drive for the stage2 file. A 
                       stage2 file is at this location on /dev/sdb. Stage2 
                       looks on partition #1 for /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x50c450c3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    52,227,314    52,227,252   7 HPFS/NTFS
/dev/sda2          52,227,315   156,280,319   104,053,005   f W95 Ext d (LBA)
/dev/sda5          52,227,378   104,454,629    52,227,252   7 HPFS/NTFS
/dev/sda6         104,454,693   156,280,319    51,825,627   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000aa4ba

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    19,535,039    19,534,977  83 Linux
/dev/sdb2          19,535,040    23,438,834     3,903,795  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="E6A040C1A0409A47" TYPE="ntfs" 
/dev/sda5: UUID="A028300F282FE2D0" TYPE="ntfs" 
/dev/sda6: UUID="0C08277C08276444" TYPE="ntfs" 
/dev/sdb1: UUID="2a221a9d-f1c7-4b88-87e6-8df01507d5da" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: TYPE="swap" UUID="a4bc3686-d872-4325-b15b-a00fed1dfb56" 
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


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\GRLDR="Start grub"

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
# kopt=root=UUID=2a221a9d-f1c7-4b88-87e6-8df01507d5da ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2a221a9d-f1c7-4b88-87e6-8df01507d5da

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

title		Ubuntu 8.10, memtest86+
uuid		2a221a9d-f1c7-4b88-87e6-8df01507d5da
kernel		/boot/memtest86+.bin
quiet

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
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=2a221a9d-f1c7-4b88-87e6-8df01507d5da /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=a4bc3686-d872-4325-b15b-a00fed1dfb56 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   6.7GB: boot/grub/menu.lst
   6.6GB: boot/grub/stage2
   6.5GB: boot/initrd.img-2.6.27-7-generic
   6.5GB: initrd.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

MFT Sector of sda5

00000000  46 49 4c 45 30 00 03 00  77 c3 79 9a 00 00 00 00  |FILE0...w.y.....|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  fb 00 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  66 c1 c7 2d c5 59 c7 01  66 c1 c7 2d c5 59 c7 01  |f..-.Y..f..-.Y..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  66 c1 c7 2d c5 59 c7 01  |........f..-.Y..|
000000c0  66 c1 c7 2d c5 59 c7 01  66 c1 c7 2d c5 59 c7 01  |f..-.Y..f..-.Y..|
000000d0  66 c1 c7 2d c5 59 c7 01  00 40 00 00 00 00 00 00  |f..-.Y...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  9b 22 00 00 00 00 00 00  |........."......|
00000120  40 00 00 00 00 00 00 00  00 c0 29 02 00 00 00 00  |@.........).....|
00000130  00 c0 29 02 00 00 00 00  00 c0 29 02 00 00 00 00  |..).......).....|
00000140  32 9c 22 00 00 0c 00 00  b0 00 00 00 50 00 00 00  |2.".........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  50 11 00 00 00 00 00 00  |. ......P.......|
00000180  50 11 00 00 00 00 00 00  31 01 ff ff 0b 31 01 8c  |P.......1....1..|
00000190  d5 32 00 e1 80 e2 35 a9  ff ff ff ff 00 00 00 00  |.2....5.........|
000001a0  00 80 00 00 00 00 00 00  00 80 00 00 00 00 00 00  |................|
000001b0  00 80 00 00 00 00 00 00  31 08 00 00 0c 00 01 00  |........1.......|
000001c0  b0 00 00 00 48 00 00 00  01 00 40 00 00 00 05 00  |....H.....@.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  40 00 00 00 00 00 00 00  00 10 00 00 00 00 00 00  |@...............|
000001f0  08 00 00 00 00 00 00 00  08 00 00 00 00 00 fb 00  |................|
00000200
MFT Sector of sda6

00000000  46 49 4c 45 30 00 03 00  74 b9 23 04 00 00 00 00  |FILE0...t.#.....|
00000010  01 00 01 00 38 00 01 00  98 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  0e 00 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  cc d8 20 25 c5 59 c7 01  cc d8 20 25 c5 59 c7 01  |.. %.Y.... %.Y..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  cc d8 20 25 c5 59 c7 01  |.......... %.Y..|
000000c0  cc d8 20 25 c5 59 c7 01  cc d8 20 25 c5 59 c7 01  |.. %.Y.... %.Y..|
000000d0  cc d8 20 25 c5 59 c7 01  00 40 00 00 00 00 00 00  |.. %.Y...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  bb 09 00 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 c0 9b 00 00 00 00 00  |@...............|
00000130  00 c0 9b 00 00 00 00 00  00 c0 9b 00 00 00 00 00  |................|
00000140  32 bc 09 00 00 0c 00 00  b0 00 00 00 48 00 00 00  |2...........H...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  00 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 10 00 00 00 00 00 00  e0 04 00 00 00 00 00 00  |................|
00000180  e0 04 00 00 00 00 00 00  31 01 ff ff 0b 00 00 00  |........1.......|
00000190  ff ff ff ff 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
000001a0  00 80 00 00 00 00 00 00  00 80 00 00 00 00 00 00  |................|
000001b0  00 80 00 00 00 00 00 00  31 08 00 00 0c 00 01 00  |........1.......|
000001c0  b0 00 00 00 48 00 00 00  01 00 40 00 00 00 05 00  |....H.....@.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  40 00 00 00 00 00 00 00  00 10 00 00 00 00 00 00  |@...............|
000001f0  08 00 00 00 00 00 00 00  08 00 00 00 00 00 0e 00  |................|
00000200
```

---

### Post by caljohnsmith on 2009-02-16
It looks for one thing your Ubuntu installation is missing its "vmlinuz-2.6.27-7-generic" boot file that's necessary to boot. Did you install Ubuntu using a CD that came in a recent Linux magazine? If so, that is most likely the problem, because the CD they sent out is unfortunately slightly corrupt and does not install Ubuntu properly. I would recommend downloading the Ubuntu Live CD ISO file, do a "md5sum" check to make sure it is a good download, and also burn it at slow speed (4X) to a CD. Then I would try reinstalling Ubuntu. Let us know how that goes or if you run into problems.

---

### Post by ninadb on 2009-02-17
Hi

Thanks for the reply.
Also the script is very good.

Will it not work if I copy/download the vmlinuz file from the DVD
to the required location

Thanks
Ninad

---

### Post by caljohnsmith on 2009-02-17
> **ninadb said:**
> 
Will it not work if I copy/download the vmlinuz file from the DVD
to the required location

I don't think that will work, because if you have a corrupted DVD, there is probably more wrong with your installation than merely missing that single boot file. I would burn another Live CD to use for installing, and also use the "check CD for defects" option when you boot the Live CD to make sure the CD is OK.

---

