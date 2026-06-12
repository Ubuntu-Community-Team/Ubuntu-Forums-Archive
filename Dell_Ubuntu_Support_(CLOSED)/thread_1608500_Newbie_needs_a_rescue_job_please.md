---
title: "Newbie needs a rescue job please"
date: 2010-10-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by SpeedyJohn on 2010-10-29
Greetings from a total newbie! Whilst in London UK recently a friend did a "clean" install of Ubuntu Maverick on my Dell 1525. I had previously only ever had Vista on this machine - where did XP come from?. Anyway, two days back in New Zealand and I have a crash for unknown (to me) reason. From working fine to the next boot getting a grub rescue prompt. Via Skype on another friends laptop, I was advised by friend one to go through a series of commands using a LiveCD  which has left me with just a grub prompt. Several other commands also deliver different results. 

For example #ubuntu@ubuntu:~$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos#

Friend one has now suggested a new install but I'm keen to repair this and learn at the same time. I have tried following numerous on line ideas but generally get messages blocking further progress. Some information that may help someone help me follows:

#ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00013bb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       19131       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris

Also ran the Boot Info Script:

  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    307,337,216   312,578,047     5,240,832   c W95 FAT32 (LBA)
/dev/sda2         299,810,814   312,580,095    12,769,282   5 Extended
/dev/sda5         299,810,816   312,580,095    12,769,280  82 Linux swap / Solaris

/dev/sda1 overlaps with /dev/sda2
/dev/sda1 overlaps with /dev/sda5

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3205-F432                              vfat       MEDIADIRECT                   
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0dc87756-6143-4eee-82c1-d4050f0e24eb   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/MEDIADIRECT       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  cb 09 84 d6 b7 12 44 e0  f5 56 c5 6c 9d f7 30 9d  |......D..V.l..0.|
00000010  25 d0 fb 7a 2b e8 67 5d  c8 e0 e6 b1 75 31 b6 16  |%..z+.g]....u1..|
00000020  8d 46 0a b7 07 d8 f3 5f  3c 78 67 e2 be ad 60 56  |.F....._<xg...`V|
00000030  3b ef f4 88 c7 f1 03 86  af 40 b1 f8 9f a4 ea 10  |;........@......|
00000040  aa 99 c2 49 fd d7 e2 b2  c4 46 5e cd f2 ee 5e 16  |...I.....F^...^.|
00000050  31 f6 d1 53 d8 ec ad e2  2d 08 0c 3b 91 fa f1 fd  |1..S....-..;....|
00000060  29 c9 0e d3 d2 b3 74 3f  10 59 5d ef 02 55 e0 82  |).....t?.Y]..U..|
00000070  39 ad 98 ee ad e4 19 57  07 f1 a5 41 ca 54 d3 96  |9......W...A.T..|
00000080  e1 8b 84 61 5a 51 8e c4  91 c0 40 0c 07 4a 96 58  |...aZQ....@..J.X|
00000090  a3 0c 14 ae 32 a5 b7 0e  a2 9a 2e e2 48 89 1f 36  |....2.......H..6|
000000a0  39 c0 a7 d9 5c c4 d9 96  49 50 60 60 28 3d 3d 6b  |9...\...IP``(==k|
000000b0  63 99 92 ab dc 5a a8 66  55 92 3f ef 29 e7 f2 a8  |c....Z.fU.?.)...|
000000c0  b5 1d 76 d6 3b 62 04 db  49 c0 da c3 69 ea 3b 1a  |..v.;b..I...i.;.|
000000d0  66 a3 ac e9 76 16 6c e2  48 c3 1c 02 7d 8f 15 e6  |f...v.l.H...}...|
000000e0  7e 35 f8 87 a3 34 8e a6  78 e4 da 46 02 72 78 34  |~5...4..x..F.rx4|
000000f0  c4 a2 7a 7e 9f e3 eb 7d  39 67 2c ca ec 00 c0 07  |..z~...}9g,.....|
00000100  ae 2a a6 a7 f1 4e 67 b1  62 22 58 d9 c1 02 be 76  |.*...Ng.b"X....v|
00000110  bf f8 85 ba 6c db d8 7c  a0 e7 e6 7c 67 f2 ac cb  |....l..|...|g...|
00000120  df 1c df 5c 5c 79 a2 da  dd 3d 17 04 8f e7 5b 46  |...\\y...=....[F|
00000130  6d 2b 18 cb 09 09 4b 99  9e 95 e2 1f 1a ce ee cc  |m+....K.........|
00000140  93 e0 af 24 e7 84 1e e7  d6 bc e7 59 f1 64 a4 4b  |...$.......Y.d.K|
00000150  15 bc ac ec ec 4b b1 e8  4f f5 ac 0d 5f 5b bd d4  |.....K..O..._[..|
00000160  98 f9 ac 11 0f 54 41 b4  56 68 ce 79 e6 92 6d 1b  |.....TA.Vh.y..m.|
00000170  4a 9c 64 d5 c9 ae 6e a6  b9 90 bc b2 33 13 ea 6a  |J.d...n.....3..j|
00000180  12 32 29 c5 70 47 5e 68  23 03 22 a6 e6 aa 23 15  |.2).pG^h#."...#.|
00000190  59 98 28 19 24 e0 0a f4  6d 1a 18 b4 cd 3e 38 15  |Y.(.$...m....>8.|
000001a0  40 65 19 73 dd 98 d7 9f  da 90 b7 51 33 74 0e 09  |@e.s.......Q3t..|
000001b0  fc eb be b8 8e 47 52 c8  d9 19 cd 71 e3 1d 00 fe  |.....GR....q....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d8 c2 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Any ideas most welcome!!!

---

### Post by mikewhatever on 2010-10-29
The output you posted looks odd. First, there is no Linux partition, and second, the partitions spanning the disk are nowhere near the size of 160 GB. Knowing what you've done so far might be helpful, also, sometimes simply reinstalling is much more practical then fixing.

---

### Post by SpeedyJohn on 2010-10-29
Yes, it certainly did not correlate with any information I could glean from various forum comments. The initial comment when I got the grub rescue prompt was " unknown filesystem". The commands I was given and executed follow in the order they were entered:

sudo mount /dev/sda2 /mnt
 sudo mount /dev/sda1 /mnt
 sudo grub-install --root-directory=/mnt/ /dev/sda
 sudo blkid  
sudo mount /dev/sda2 /mnt
 sudo mount /dev/sda2 /mnt /t ext4
 sudo mount -t ext4 /dev/sda2 /mnt 
 sudo fdisk -l /dev/sda

Obviously something here further corrupted the system and as you suggest,
 a total new install may be the only answer.

---

