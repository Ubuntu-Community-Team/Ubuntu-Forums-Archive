---
title: "Lost harddrive or Partition"
date: 2006-08-08
forum: Desktop Environments
---

### Post by onlybui on 2006-08-08
Im not to sure what happen cause I haven't used the PC in like two weeks(family been using it) and I come home and I lost my 2nd Harddrive all data gone or maybe its just not being mounted correctly

My 2nd harddrive is listed as  sdb5(279GB)
I treid to edit my /etc/fstab and still no go

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda9       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda10      none            swap    sw              0       0
/dev/sdb5       /media/sdb5     ext3    defaults,errors=remount -ro 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


Please help I LOST 260GB of data... and no back up....

---

### Post by orb9220 on 2006-08-08
isn't /dev/sdb5 /media/sdb5 ext3 defaults,errors=remount -ro 0 suppose to have two numbers there like 0 1?

Just a thought

---

### Post by onlybui on 2006-08-08
added that and still all data is gone... only shows Lost+Found :(

---

### Post by onlybui on 2006-08-08
any program to get data back....

---

### Post by orb9220 on 2006-08-08
testdisk in synaptic

Partition scanner and disk recovery tool
TestDisk checks the partition and boot sectors of your disks.
It is very useful in recovering lost partitions.
It works with :
* DOS/Windows FAT12, FAT16 and FAT32
* NTFS ( Windows NT/2K/XP )
* Linux Ext2 and Ext3
* BeFS ( BeOS )
* BSD disklabel ( FreeBSD/OpenBSD/NetBSD )
* CramFS (Compressed File System)
* HFS and HFS+, Hierarchical File System
* JFS, IBM's Journaled File System
* Linux Raid
* Linux Swap (versions 1 and 2)
* LVM and LVM2, Linux Logical Volume Manager
* Netware NSS
* ReiserFS 3.5 and 3.6
* Sun Solaris i386 disklabel
* UFS and UFS2 (Sun/BSD/...)
* XFS, SGI's Journaled File System

PhotoRec is file data recovery software designed to recover
lost pictures from digital camera memory or even Hard Disks.
It has been extended to search also for non audio/video headers.
It searchs for
* Sun/NeXT audio data (.au)
* RIFF audio/video (.avi/.wav)
* BMP bitmap (.bmp)
* bzip2 compressed data (.bz2)
* Source code written in C (.c)
* Canon Raw picture (.crw)
* Canon catalog (.ctg)
* FAT subdirectory
* Microsoft Office Document (.doc)
* Nikon dsc (.dsc)
* HTML page (.html)
* JPEG picture (.jpg)
* MOV video (.mov)
* MP3 audio (MPEG ADTS, layer III, v1) (.mp3)
* Moving Picture Experts Group video (.mpg)
* Minolta Raw picture (.mrw)
* Olympus Raw Format picture (.orf)
* Portable Document Format (.pdf)
* Perl script (.pl)
* Portable Network Graphics (.png)
* Raw Fujifilm picture (.raf)
* Contax picture (.raw)
* Rollei picture (.rdc)
* Rich Text Format (.rtf)
* Shell script (.sh)
* Tar archive (.tar )
* Tag Image File Format (.tiff)
* Microsoft ASF (.wma)
* Sigma/Foveon X3 raw picture (.x3f)
* zip archive (.zip)

---

