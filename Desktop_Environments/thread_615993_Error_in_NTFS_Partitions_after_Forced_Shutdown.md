---
title: "Error in NTFS Partitions after Forced Shutdown"
date: 2007-11-17
forum: Desktop Environments
---

### Post by hi_mostafa on 2007-11-17
Hello,

I need help trying to correct some errors in NTFS Partitions i have making them not automatically mountable in Ubuntu start and preventing me totally from booting into windows xp .
Thanks in advance :)

MY HDD :
C fat32 ~16 GB , D NTFS ~27GB , E NTFS ~38 GB , G NTFS ~19 GB , linux ext3 ~9  GB , swap  ~2 GB
In Physical Order .

I am using Windows Boot-loader , and used System Rescue CD (using dd) to be able to boot both Windows xp and Ubuntu .

I am having Windows ME on C , Windows XP on D , and Ubuntu 7.10 on the Partition after G .

My ubuntu 7.10 Session was :
1 - I was copying some files from a dvd which seems that it made D drive Full , however Archive manager (while decompressing .iso files to D) showed no error but the last fie was in copy was small in size .. and i shutdown Arcchive manager because dvd-rom no longer active ...

2 - Ubuntu hanged while trying to do some process and it refused ejecting the dvd ... so i pressed on reset button of my pc ...

3 - Windows XP sp2 become no longer Bootable ... showing Fatal error (blue screen) and automatically restarts .. Safe Mode doesn't help too ... Error message is :
Stop: 0x00000073 (0x00000001,oxc000017D,0x00000001,oxEDDB5BA8)

4- I tried using Hirens Boot CD , in which both Pargagon and Partition Magic Showed Error in D partition ,, however it couldn't provide a help except runnung CHKDSK which i can't reach in my case .....

5- System Rescue CD using gparted didn't help in solving errors of ntfs partitions .

Some results using Terminal :
1 - sudo fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a0049ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2089    16779861    c  W95 FAT32 (LBA)
/dev/sda2            2090       18020   127965757+   f  W95 Ext'd (LBA)
/dev/sda3           18021       19195     9438187+  83  Linux
/dev/sda4           19196       19457     2104515   82  Linux swap / Solaris
/dev/sda5            2090        5614    28314531    7  HPFS/NTFS
/dev/sda6            5615       10575    39849201    7  HPFS/NTFS
/dev/sda7           10576       15536    39849201    7  HPFS/NTFS
/dev/sda8           15537       18020    19952698+   7  HPFS/NTFS

2- sudo gpart /dev/sda

Begin scan...
Possible partition(DOS FAT), size(16386mb), offset(0mb)
Possible extended partition at offset(16386mb)
   Possible partition(Windows NT/W2K FS), size(27650mb), offset(16386mb)
   Possible partition(Windows NT/W2K FS), size(38915mb), offset(44037mb)
   Possible partition(Windows NT/W2K FS), size(38915mb), offset(82952mb)
   Possible partition(Windows NT/W2K FS), size(19485mb), offset(121868mb)
Possible partition(Linux ext2), size(9216mb), offset(141353mb)
Possible partition(Linux swap), size(2055mb), offset(150570mb)
End scan.

Checking partitions...
Partition(DOS or Windows 95 with 32 bit FAT, LBA): primary 
   Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): logical 
   Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): logical 
   Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): logical 
   Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): logical 
Partition(Linux ext2 filesystem): primary 
Partition(Linux swap or Solaris/x86): primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 012(0x0C)(DOS or Windows 95 with 32 bit FAT, LBA)
   size: 16386mb #s(33559722) s(63-33559784)
   chs:  (0/1/1)-(1023/254/63)d (0/1/1)-(2088/254/63)r

Primary partition(2)
   type: 015(0x0F)(Extended DOS, LBA)
   size: 124966mb #s(255931515) s(33559785-289491299)
   chs:  (1023/254/63)-(1023/254/63)d (2089/0/1)-(18019/254/63)r

Primary partition(3)
   type: 131(0x83)(Linux ext2 filesystem)
   size: 9216mb #s(18874368) s(289491300-308365667)
   chs:  (1023/254/63)-(1023/254/63)d (18020/0/1)-(19194/223/9)r

Primary partition(4)
   type: 130(0x82)(Linux swap or Solaris/x86)
   size: 2055mb #s(4209024) s(308367675-312576698)
   chs:  (1023/254/63)-(1023/254/63)d (19195/0/1)-(19456/254/57)r

---

### Post by szaka on 2007-11-17
The Microsoft reply: [http://support.microsoft.com/kb/291808](http://support.microsoft.com/kb/291808)

"0xc000017d: STATUS_NO_LOG_SPACE is one of the most typical causes of this error. This parameter indicates that Windows does not have enough hard disk space available on the system drive. Free some disk space on your system drive to resolve this issue."

So boot Linux and free enough space.

---

### Post by hi_mostafa on 2007-11-17
I have emptied about 1 GB from D partition using ubuntu , however Ubuntu still see the partition as Full.

btw i am forcing ubuntu to mount the ntfs partitions every time I boot in it .

> **szaka said:**
> The Microsoft reply: [http://support.microsoft.com/kb/291808](http://support.microsoft.com/kb/291808)

"0xc000017d: STATUS_NO_LOG_SPACE is one of the most typical causes of this error. This parameter indicates that Windows does not have enough hard disk space available on the system drive. Free some disk space on your system drive to resolve this issue."

So boot Linux and free enough space.

---

### Post by hi_mostafa on 2007-11-18
Any help ??

---

### Post by szaka on 2007-11-18
[http://ntfs-3g.org/support.html#diskspace](http://ntfs-3g.org/support.html#diskspace)

---

### Post by hi_mostafa on 2007-11-18
Thanks alot for help . Problem Solved .

Problem was : D partition Full no mroe .

Solved :
by deleting files in .Trash folder in D partition using
sudo rm *  ; inside that folder using Terminal

---

