---
title: "Grub Error 17"
date: 2009-05-01
forum: General Help
---

### Post by Evilchaosz on 2009-05-01
After spending a few hours trying to fix this dreaded error 17 with all sorts of solutions given by users in this forum, I still cannot fix this problem and finally decided to seek help.

I guess it all started when grub was still loading, I accidentally shut the computer down (don't ask) and voila, error 17 popped out when I rebooted the computer.

Here's what fdisk -l and menu.lst says:

fdisk -l
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0df50df4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       30401   141797722+   7  HPFS/NTFS

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       17025   136753281    c  W95 FAT32 (LBA)
/dev/sdf2           17026       18241     9767520    5  Extended
/dev/sdf5           17026       18241     9767488+  82  Linux swap / Solaris

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       20522   164842933+   7  HPFS/NTFS
/dev/sdg2           20523       45574   201230190   83  Linux
/dev/sdg3           45575       97808   419569605    7  HPFS/NTFS
/dev/sdg4           97809      121601   191117272+   7  HPFS/NTFS

Disk /dev/sdh: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c6d0c6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1        2108    16932478+   7  HPFS/NTFS
/dev/sdh2            2109       14593   100285762+   7  HPFS/NTFS

```menu.lst
```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d05b2d7b-407f-4372-9cb1-a4559dce38fe
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d05b2d7b-407f-4372-9cb1-a4559dce38fe ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d05b2d7b-407f-4372-9cb1-a4559dce38fe
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d05b2d7b-407f-4372-9cb1-a4559dce38fe ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-11-generic
uuid        d05b2d7b-407f-4372-9cb1-a4559dce38fe
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=d05b2d7b-407f-4372-9cb1-a4559dce38fe ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid        d05b2d7b-407f-4372-9cb1-a4559dce38fe
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=d05b2d7b-407f-4372-9cb1-a4559dce38fe ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d05b2d7b-407f-4372-9cb1-a4559dce38fe
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```And the results.txt from running this as sudo:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdf
 => Grub0.97 is installed in the MBR of /dev/sdg and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdg2 and 
                       looks at sector 443014058 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdg. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdg3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0df50df4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   488,392,064   283,595,445   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63   273,506,624   273,506,562   c W95 FAT32 (LBA)
/dev/sdf2         273,506,625   293,041,664    19,535,040   5 Extended
/dev/sdf5         273,506,688   293,041,664    19,534,977  82 Linux swap / Solaris


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  63   329,685,929   329,685,867   7 HPFS/NTFS
/dev/sdg2         329,685,930   732,146,309   402,460,380  83 Linux
/dev/sdg3         732,146,310 1,571,285,519   839,139,210   7 HPFS/NTFS
/dev/sdg4       1,571,285,520 1,953,520,064   382,234,545   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c6d0c6d

Partition  Boot         Start           End          Size  Id System

/dev/sdh1    *             63    33,865,019    33,864,957   7 HPFS/NTFS
/dev/sdh2          33,865,020   234,436,544   200,571,525   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5A58F30B58F2E523" LABEL="winxp" TYPE="ntfs" 
/dev/sda2: UUID="D83C14553C14314C" LABEL="data" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdf1: UUID="49D2-CEAF" TYPE="vfat" 
/dev/sdf5: UUID="8bd7bf8d-16f6-49bb-ba22-60d98fb3e69c" TYPE="swap" 
/dev/sdg1: UUID="06045B28B200FB90" LABEL="Games" TYPE="ntfs" 
/dev/sdg2: UUID="d05b2d7b-407f-4372-9cb1-a4559dce38fe" TYPE="ext3" 
/dev/sdg3: UUID="1548279C37B8AE71" LABEL="Videos" TYPE="ntfs" 
/dev/sdg4: UUID="BF89B1494072BBA1" LABEL="Photography" TYPE="ntfs" 
/dev/sdh1: UUID="3A00D8B600D879F9" LABEL="Junk" TYPE="ntfs" 
/dev/sdh2: UUID="3E40DA9640DA546D" LABEL="Music" TYPE="ntfs" 

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
/dev/sdf1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdg2 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdg1 on /media/Games type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdg3 on /media/Videos type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdg4 on /media/Photography type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdh1 on /media/Junk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdh2 on /media/Music type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
c:\wubildr.mbr="Ubuntu" 

=========================== sdg2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d05b2d7b-407f-4372-9cb1-a4559dce38fe ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d05b2d7b-407f-4372-9cb1-a4559dce38fe

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d05b2d7b-407f-4372-9cb1-a4559dce38fe
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d05b2d7b-407f-4372-9cb1-a4559dce38fe ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d05b2d7b-407f-4372-9cb1-a4559dce38fe
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d05b2d7b-407f-4372-9cb1-a4559dce38fe ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-11-generic
uuid        d05b2d7b-407f-4372-9cb1-a4559dce38fe
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=d05b2d7b-407f-4372-9cb1-a4559dce38fe ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid        d05b2d7b-407f-4372-9cb1-a4559dce38fe
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=d05b2d7b-407f-4372-9cb1-a4559dce38fe ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d05b2d7b-407f-4372-9cb1-a4559dce38fe
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdg2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc2
UUID=d05b2d7b-407f-4372-9cb1-a4559dce38fe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=8bd7bf8d-16f6-49bb-ba22-60d98fb3e69c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdg2: Location of files loaded by Grub: ===================


 226.8GB: boot/grub/menu.lst
 226.8GB: boot/grub/stage2
 226.8GB: boot/initrd.img-2.6.27-11-generic
 226.8GB: boot/initrd.img-2.6.28-11-generic
 226.7GB: boot/vmlinuz-2.6.27-11-generic
 226.8GB: boot/vmlinuz-2.6.28-11-generic
 226.8GB: initrd.img
 226.8GB: initrd.img.old
 226.8GB: vmlinuz
 226.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdh

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 a1 18 79 0c 00 00  |.......|....y...|
000001b0  00 00 80 41 00 f3 0e 00  6d 0c 6d 0c 00 00 80 01  |...A....m.m.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 fd bc 04 02 00 00  |......?.........|
000001d0  c1 ff 07 fe ff ff 3c bd  04 02 85 7a f4 0b 00 00  |......<....z....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

And also device.map:
```

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

```

Hope someone can find a solution to my problem. :P

---

### Post by Thelasko on 2009-05-01
I've heard that the [Super Grub Disk]("http://www.supergrubdisk.org/") is a simple way to solve this problem.

---

### Post by sshu on 2009-05-03
Hi!

I have seen many threads about Grub error 17, but I didn't see the same case like I have.
I have the following problem:
I installed Ubuntu 9.04 (I have Windows Vista on my laptop as well). And it loads excellent until I insert any USB storage (like usb-stick or usb hard drive). If I insert usb-storage and reboot my system it would show me grub error 17. I checked boot order in BIOS, but everything is OK there. What could cause such a problem?

---

### Post by caljohnsmith on 2009-05-03
**Evilchaosz**, it looks like your Grub error 17 is probably due to how you have your drives set up in the BIOS boot order. If you boot your 250 GB sda drive on start up, that is probably what is giving you the Grub error 17; but if you can change your BIOS boot order to boot your 1 TB sdg Ubuntu drive, I think you should be be able to boot Ubuntu just fine. How about giving that a shot and let me know how it goes.

**SShu**, is your Ubuntu/Vista drive set to boot first in your BIOS boot order, or is the USB drive before it? It sounds like your USB drive comes before your Ubuntu/Vista drive in the BIOS boot order, but if that's not true, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal), and **while you have your USB drive is connected**, run the following command:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

Cheers,
John

---

### Post by sshu on 2009-05-03
**caljohnsmith, **thank you for reply. 
BIOS order is the following:

[LIST=1]
[*]CD/DVD
[*]Hard Drive
[*]USB
[/LIST]
Here is my results.txt:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
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

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe479c362

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   218,789,234   218,789,172   7 HPFS/NTFS
/dev/sda2         218,789,235   234,436,544    15,647,310   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0625e5cc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1EB06CF7B06CD6B5" LABEL="OS" TYPE="ntfs" 
/dev/sda2: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sdb1: UUID="a3d8d52a-8517-4529-968a-5be86e2e08b8" TYPE="ext4" 
/dev/sdb5: UUID="42601b95-7547-46e3-8a30-1e9c08dbb2be" TYPE="swap" 
/dev/sdc1: LABEL="My Book" UUID="3E0F-2B5F" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/shura/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shura)
/dev/sdc1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


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
# kopt=root=UUID=a3d8d52a-8517-4529-968a-5be86e2e08b8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a3d8d52a-8517-4529-968a-5be86e2e08b8

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Ubuntu 9.04, kernel 2.6.28-11-generic
root            (hd1,0)
uuid        a3d8d52a-8517-4529-968a-5be86e2e08b8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a3d8d52a-8517-4529-968a-5be86e2e08b8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet


title        Windows Vista (loader)
rootnoverify    (hd0,0)
chainloader    +1
savedefault
makeactive

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
chainloader    +1
savedefault
makeactive

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Linux systems:
root


title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root            (hd1,0)
uuid        a3d8d52a-8517-4529-968a-5be86e2e08b8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a3d8d52a-8517-4529-968a-5be86e2e08b8 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root            (hd1,0)
uuid        a3d8d52a-8517-4529-968a-5be86e2e08b8
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST




=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=a3d8d52a-8517-4529-968a-5be86e2e08b8 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=42601b95-7547-46e3-8a30-1e9c08dbb2be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   1.9GB: boot/grub/menu.lst
   1.8GB: boot/grub/stage2
   1.7GB: boot/initrd.img-2.6.28-11-generic
   1.8GB: boot/vmlinuz-2.6.28-11-generic
   1.7GB: initrd.img
   1.8GB: vmlinuz

```

---

### Post by JK3mp on 2009-05-03
Odd issue, if it isn't boot order. Do you have any live bootable content on the USB drive that may be opting it to try and boot from it first then fail? I know some laptops(mostly netbooks) are set to automatically prioritize USB drives first for boot aside from what BIOS says. Also caljohnsmith YOUR ON A ROLL in the ForuM! :p

---

### Post by sshu on 2009-05-03
**JK3mp,** I don't have any bootable content on the USB. It behaves like that even with brand new formatted USB-stick.

---

### Post by caljohnsmith on 2009-05-03
Sshu, it looks like the issue is you have two HDDs besides the USB drive. Currently Grub is installed in the MBR of the sda drive, but Grub looks on the second boot drive (the second drive in your BIOS boot order) for its boot files on start up. When you don't have your USB drive connected, Grub boots fine since your Linux sdb drive must be the second boot drive, and Grub finds its boot files just fine. But when you connect the USB drive, it obviously becomes the second boot drive, because that's what would lead to your Grub error 17. 

Do you have any way in your BIOS to set the sdb Ubuntu drive as first in the boot order? If so, it would be easy to fix your problem. If not, there are some other booting options that would work so that your USB drive does not interfere, but they are not as ideal as if you can simply boot the Ubuntu sdb drive on start up. So let me know if you can boot sdb or not, and we can work from there.

Cheers,
John

---

### Post by sshu on 2009-05-03
**caljohnsmith, **I do not have such settings in my BIOS :(

---

### Post by JK3mp on 2009-05-03
> **sshu said:**
> **JK3mp,** I don't have any bootable content on the USB. It behaves like that even with brand new formatted USB-stick.

Ahh..wasn't payin attention that you had 2nd drive. Cal's probably right...never had to deal with that problem much and if your bios don't have the options to change it then idk, sorry couldn't be much help hopefully cal can work your solution. Gl

---

### Post by caljohnsmith on 2009-05-03
> **sshu said:**
> **caljohnsmith, **I do not have such settings in my BIOS :(
I was afraid of that, but we can work around it. One option is to use [EasyBCD]("http://neosmart.net/dl.php?id=1") in Vista to boot both Vista and Ubuntu; you would want to use EasyBCD's "NeoGrub" boot loader to "chainload" the Ubuntu drive. Here are some instructions on using NeoGrub:

[http://neosmart.net/wiki/display/EBCD/NeoGrub](http://neosmart.net/wiki/display/EBCD/NeoGrub)

Basically you would want to set up a menu.lst (see the page above) that has the following entries:
```
title 2nd Boot Drive
rootnoverify (hd1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

title 3rd Boot Drive
rootnoverify (hd2)
map (hd2) (hd0)
map (hd0) (hd2)
chainloader +1
```
That way when you don't have your USB drive connected, you would use the "2nd Boot Drive" option above to boot Ubuntu, but when the USB drive is connected, you would have to use the "3rd Boot Drive" to boot Ubuntu since the USB drive would be the 2nd boot drive as I explained in my previous post. Would that work for you? It would of course be easier if you simply don't connect your USB drive on start up any more, but instead wait until after you've booted into Vista/Ubuntu, because then you could just keep your current booting setup the way it is. Is that an option?

John

---

### Post by sshu on 2009-05-03
**caljohnsmith**, I found out there is much newer BIOS version for my laptop. I'm going to update BIOS. Hopefully it will have much better boot settings. If it wont help I'll try your approach.

---

### Post by meierfra. on 2009-05-03
```
title 3rd Boot Drive
rootnoverify (hd1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```

caljohnsmith: did you mean

```
title 3rd Boot Drive
rootnoverify (hd2)
map (hd2) (hd0)
map (hd0) (hd2)
chainloader +1
```

---

### Post by caljohnsmith on 2009-05-03
> **meierfra. said:**
> 
caljohnsmith: did you mean

```
title 3rd Boot Drive
rootnoverify (hd2)
map (hd2) (hd0)
map (hd0) (hd2)
chainloader +1
```
Yes I did mean that, thanks for catching my mistake, meierfra. :) Hopefully it will be a non-issue if sshu can get a BIOS upgrade that will make it possible to boot the Ubuntu drive.

John

---

### Post by sshu on 2009-05-06
Hi!

I updated BIOS, but it did not help. After that I just installed ubuntu on my first hard drive and everything is ok now. Anyway, thanks for help.

---

