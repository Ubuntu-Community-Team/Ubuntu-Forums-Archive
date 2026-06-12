---
title: "how to reinstall grub from a live cd?"
date: 2008-12-17
forum: General Help
---

### Post by miked860 on 2008-12-17
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I was following this guys tutorial and it says Error 22: No such partition when I get to the setup part and I followed the tutorial 100%, Can someone show me a better tutorial or tell me what I might be doing wrong?

---

### Post by caljohnsmith on 2008-12-17
How about posting the output of all the following commands:
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

---

### Post by miked860 on 2008-12-17
```
grub> find /boot/grub/stage1
 (hd0,6)

grub> root (hd0,6)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,6)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition
```

I get the same problem.

---

### Post by caljohnsmith on 2008-12-17
Sometimes that type of Grub error behavior can be because your partition table is slightly corrupt. How about posting the output of:
```
sudo sfdisk -l
sudo fdisk -lu
sudo parted /dev/sda print

```
By the way, I have to leave in about 5 minutes and won't be around for another 8 hours or so, but we can pick up then if you want.

---

### Post by miked860 on 2008-12-17
```
ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/sda: 24321 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+    472     473-   3799341    b  W95 FAT32
/dev/sda2        473   24320   23848  191559060    f  W95 Ext'd (LBA)
/dev/sda3      12387+  24320   11934-  95859823+   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5        473+    596     124-    995967   82  Linux swap / Solaris
/dev/sda6        597+  12386   11790-  94703143+  83  Linux

Disk /dev/sdb: 102 cylinders, 173 heads, 57 sectors/track
Units = cylinders of 5048832 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+    101     102-    502885+   b  W95 FAT32
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd2e1d2e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     7598744     3799341    b  W95 FAT32
/dev/sda2         7598745   390716864   191559060    f  W95 Ext'd (LBA)
/dev/sda3       198997218   390716864    95859823+   7  HPFS/NTFS
/dev/sda5         7598871     9590804      995967   82  Linux swap / Solaris
/dev/sda6         9590868   198997154    94703143+  83  Linux

Disk /dev/sdb: 514 MB, 514981888 bytes
173 heads, 57 sectors/track, 102 cylinders, total 1005824 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x211a2b42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          51     1005821      502885+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.                                 
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.                                 
ubuntu@ubuntu:~$ 

```

---

### Post by caljohnsmith on 2008-12-17
> **miked860 said:**
> ```
ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/sda: 24321 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+    472     473-   3799341    b  W95 FAT32
/dev/sda2        473   24320   23848  191559060    f  W95 Ext'd (LBA)
/dev/sda3      12387+  24320   11934-  95859823+   7  HPFS/NTFS
		[COLOR="Red"]start: (c,h,s) expected (1023,254,63) found (1023,1,1)[/COLOR]
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5        473+    596     124-    995967   82  Linux swap / Solaris
/dev/sda6        597+  12386   11790-  94703143+  83  Linux

Disk /dev/sdb: 102 cylinders, 173 heads, 57 sectors/track
Units = cylinders of 5048832 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+    101     102-    502885+   b  W95 FAT32
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
ubuntu@ubuntu:~$ sudo fdisk -lu
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd2e1d2e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     7598744     3799341    b  W95 FAT32
/dev/sda2         7598745   390716864   191559060    f  W95 Ext'd (LBA)
/dev/sda3       198997218   390716864    95859823+   7  HPFS/NTFS
/dev/sda5         7598871     9590804      995967   82  Linux swap / Solaris
/dev/sda6         9590868   198997154    94703143+  83  Linux

Disk /dev/sdb: 514 MB, 514981888 bytes
173 heads, 57 sectors/track, 102 cylinders, total 1005824 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x211a2b42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          51     1005821      502885+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo parted /dev/sda print
[COLOR="Red"]Error: Can't have overlapping partitions. [/COLOR]                                
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.                                 
ubuntu@ubuntu:~$ 

```
Unfortunately your partition table is corrupt it looks like. I can help you fix it tomorrow morning if you want, but in the meantime, how about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
**If you are using Version 6.8:**
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "Proceed", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results if you would like help recovering your partitions.
[B]
If you are using Version 6.9:[/B]
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results if you would like help recovering your partitions.

---

### Post by miked860 on 2008-12-17
I won't be around in the morning but I'll see if you're around in the afternoon sometime.

---

### Post by miked860 on 2008-12-17
Anyone else willing to give it a try?

---

### Post by caljohnsmith on 2008-12-18
When you're around again, how about also posting:
```
sudo sfdisk -d /dev/sda
```
And we can work from there.

---

### Post by miked860 on 2008-12-18
```
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=  7598682, Id= b, bootable
/dev/sda2 : start=  7598745, size=383118120, Id= f
/dev/sda3 : start=198997218, size=191719647, Id= 7
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=  7598871, size=  1991934, Id=82
/dev/sda6 : start=  9590868, size=189406287, Id=83
ubuntu@ubuntu:~$ 
```

---

### Post by caljohnsmith on 2008-12-18
What is on your current sda3 NTFS partition? Is that just a data partition, or do you have Windows there? We can fix your partition problem two ways: you can have sda3 as either a primary partition or a logical partition. If sda3 has Windows, it would be best to make it a primary partition, but if it doesn't have Windows (which looks like might be the case), then it is totally up to you whether to make it primary or logical. The evidence would lead me to believe that sda3 was originally a logical partition though, because it starts exactly 64 sectors after the end of sda6, which is necessary for it to be a logical partition. Let me know how you would like it and we can work from there.

---

### Post by miked860 on 2008-12-18
> **caljohnsmith said:**
> What is on your current sda3 NTFS partition? Is that just a data partition, or do you have Windows there? We can fix your partition problem two ways: you can have sda3 as either a primary partition or a logical partition. If sda3 has Windows, it would be best to make it a primary partition, but if it doesn't have Windows (which looks like might be the case), then it is totally up to you whether to make it primary or logical. The evidence would lead me to believe that sda3 was originally a logical partition though, because it starts exactly 64 sectors after the end of sda6, which it necessary for it to be a logical partition. Let me know how you would like it and we can work from there.

I'm pretty sure it's Windows XP.

---

### Post by caljohnsmith on 2008-12-18
OK, how about first posting the following before we go any further in order to see whether you have XP on sda3:
```
sudo mount /dev/sda3 /mnt
ls -l /mnt
cat /mnt/boot.ini
```
Note "-l" is a lowercase L, not a one.

---

### Post by miked860 on 2008-12-18
> **caljohnsmith said:**
> OK, how about first posting the following before we go any further in order to see whether you have XP on sda3:
```
sudo mount /dev/sda3 /mnt
ls -l /mnt
cat /mnt/boot.ini
```
Note "-l" is a lowercase L, not a one.

```
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
ubuntu@ubuntu:~$ ls -l /mnt
total 1548340
drwxrwxrwx 1 root root          0 2008-12-18 02:36 ATI
drwxrwxrwx 1 root root       4096 2008-12-18 02:22 Documents and Settings
-rwxrwxrwx 1 root root 1585446912 2008-12-18 02:38 pagefile.sys
drwxrwxrwx 1 root root       8192 2008-12-18 02:43 Program Files
drwxrwxrwx 1 root root       4096 2008-12-18 02:21 System Volume Information
drwxrwxrwx 1 root root       8192 2008-12-18 20:27 Users
drwxrwxrwx 1 root root      28672 2008-12-18 02:38 WINDOWS
ubuntu@ubuntu:~$ cat /mnt/boot.ini
cat: /mnt/boot.ini: No such file or directory
ubuntu@ubuntu:~$ 
```

What do I do now? It's definitely XP.

---

### Post by caljohnsmith on 2008-12-18
OK, so it does look like you have XP on sda3, but XP is currently missing its boot files, so you won't be able to boot XP in its present condition. Before we change your partition table, please make sure you have everything important backed up, because that's always good insurance before making any partition table changes. Then to fix your partition table problem, how about downloading the attached "partition_table.txt" to your desktop and do:
```
sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
```
Then reboot, and please post the new output of:
```
sudo sfdisk -luS
sudo parted /dev/sda print
sudo hexdump -s 28 -n 4 -e '"%d\n"' /dev/sda3

```
And we can work from there.

---

### Post by miked860 on 2008-12-18
Windows XP isn't missing any boot files. I just booted into it and it worked just fine. Oh, and I can't save the text file because I'm on a live cd.

---

### Post by caljohnsmith on 2008-12-18
> **miked860 said:**
> Windows XP isn't missing any boot files. I just booted into it and it worked just fine.
OK, sorry, let me clarify: your Windows sda3 *partition* is missing its boot files, so if you can boot into Windows, then the Windows boot files must be in your sda1 FAT partition. That means that your Windows partition must have been a logical partition to start with, otherwise Windows would not have put its boot files in a primary partition. I think if you look in sda1 you will find the three XP boot files there: boot.ini, ntldr, and NTDETECT.COM. 

So you don't have an internet connection from the Live CD? Is that why you can't download the attached file? Can you download the file from where you are posting right now and transfer it to your Live CD via floppy or USB drive maybe?

---

### Post by miked860 on 2008-12-18
> **caljohnsmith said:**
> OK, sorry, let me clarify: your Windows sda3 *partition* is missing its boot files, so if you can boot into Windows, then the Windows boot files must be in your sda1 FAT partition. That means that your Windows partition must have been a logical partition to start with, otherwise Windows would not have put its boot files in a primary partition. I think if you look in sda1 you will find the three XP boot files there: boot.ini, ntldr, and NTDETECT.COM. 

So you don't have an internet connection from the Live CD? Is that why you can't download the attached file? Can you download the file from where you are posting right now and transfer it to your Live CD via floppy or USB drive maybe?

nevermind got it saved. am I going to lose everythimg? Couldn't I just reinstall Ubuntu? I can lose those files. I didn't really want to do that at first but I guess I have no real choice if I will lose everything on my XP drive as well.

---

### Post by caljohnsmith on 2008-12-18
> **miked860 said:**
> nevermind got it saved. am I going to lose everythimg? Couldn't I just reinstall Ubuntu? I can lose those files. I didn't really want to do that at first but I guess I have no real choice if I will lose everything on my XP drive as well.
Reinstalling Ubuntu won't help if you keep your current partitions, because the problem will be the same after you install. Also, it is highly likely that the Ubuntu installer will fail when it goes to install Grub, because the installer has to do basically what you were trying to do in your first post. 

I wasn't trying to scare you by saying that you should back up all your data; that is just always a good practice before doing partition changes. Keep in mind that making this type of partition change does not touch the data in the partitions on the drive; "sfdisk" only changes the partition info in the MBR (Master Boot Record) and the EBRs (Extended Boot Records) that come before each logical partition. So as long as we are careful not to create any EBRs inside a partition, then the data in the partitions is untouched. I've double-checked the numbers in that partition_table.txt file you've downloaded, so to the best of my knowledge, you should be fine. It's up to you whether you want to pursue a different course of action though.

---

### Post by miked860 on 2008-12-18
```
ubuntu@ubuntu:~$ sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 24321 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+    472     473-   3799341    b  W95 FAT32
/dev/sda2        473   24320   23848  191559060    f  W95 Ext'd (LBA)
/dev/sda3      12387+  24320   11934-  95859823+   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5        473+    596     124-    995967   82  Linux swap / Solaris
/dev/sda6        597+  12386   11790-  94703143+  83  Linux
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63   7598744    7598682   b  W95 FAT32
/dev/sda2       7598745 390716864  383118120   f  W95 Ext'd (LBA)
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5       7598871   9590804    1991934  82  Linux swap / Solaris
/dev/sda6       9590868 198997154  189406287  83  Linux
/dev/sda7     198997218 390716864  191719647   7  HPFS/NTFS
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

I just put that there in case we need it later.

---

### Post by miked860 on 2008-12-18
the output of those three commands

```
ubuntu@ubuntu:~$ sudo sfdisk -luS

Disk /dev/sda: 24321 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63   7598744    7598682   b  W95 FAT32
/dev/sda2       7598745 390716864  383118120   f  W95 Ext'd (LBA)
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5       7598871   9590804    1991934  82  Linux swap / Solaris
/dev/sda6       9590868 198997154  189406287  83  Linux
/dev/sda7     198997218 390716864  191719647   7  HPFS/NTFS

Disk /dev/sdb: 102 cylinders, 173 heads, 57 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *        51   1005821    1005771   b  W95 FAT32
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA WDC WD2000JD-22H (scsi)
Disk /dev/sda: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  3891MB  3891MB  primary   fat32        boot 
 2      3891MB  200GB   196GB   extended               lba  
 5      3891MB  4910MB  1020MB  logical   linux-swap        
 6      4911MB  102GB   97.0GB  logical   ext3              
 7      102GB   200GB   98.2GB  logical   ntfs              

ubuntu@ubuntu:~$ sudo hexdump -s 28 -n 4 -e '"%d\n"' /dev/sda3
hexdump: /dev/sda3: No such file or directory
ubuntu@ubuntu:~$ 
```

---

### Post by caljohnsmith on 2008-12-18
Great, looks like your partition table is OK now. You will have to reconfigure your boot.ini file though since XP is now on a logical partition, so to change it do:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/sda1/boot.ini
```
And change only the partition numbers as follows:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition[COLOR="Blue"](4)[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition[COLOR="Blue"](4)[/COLOR]\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
```
When you reboot, do you get the Grub menu on start up yet? If not, how about following the directions from post #2 and please post the output.

---

### Post by miked860 on 2008-12-18
when I open boot.ini it opens a blank text editor. I paste what the bootloader info you posted and it does not save. It says "Could not find the file /mnt/sda1/boot.ini."

---

### Post by caljohnsmith on 2008-12-18
OK, how about posting:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Also, do you get the Grub menu on start up yet? Did you run the commands from post #2?

---

### Post by miked860 on 2008-12-18
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ gksudo gedit /mnt/sda1/boot.ini

** (gedit:8075): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.3XRZLU': No such file or directory

I/O error : No such file or directory
I/O error : No such file or directory
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ ls -l /mnt
total 119016
drwx------ 2 ubuntu root      4096 2007-06-26 15:04 _285953_
-rwx------ 1 ubuntu root         0 2008-12-17 21:18 AUTOEXEC.BAT
-rwx------ 1 ubuntu root        45 2003-08-08 17:24 autorun.inf.aug.8
-rwx------ 1 ubuntu root       588 2005-06-06 14:53 BATCH.LOG
-rwx------ 1 ubuntu root       284 2002-05-30 10:24 BATCH.OLD
-rwx------ 1 ubuntu root       262 2008-12-17 21:12 boot.ini
-rwx------ 1 ubuntu root       512 2008-12-17 21:01 bootsect.dos
-rwx------ 1 ubuntu root         0 2008-12-17 21:18 CONFIG.SYS
-rwx------ 1 ubuntu root       102 2003-10-04 14:06 Desktop.ini
-rwx------ 1 ubuntu root      8121 2003-06-12 18:52 Folder.htt
-rwx------ 1 ubuntu root         0 2005-06-06 14:53 FULL
-rwx------ 1 ubuntu root         0 2001-06-17 23:31 graph
-rwx------ 1 ubuntu root         0 2001-06-17 23:31 graph16
-rwx------ 1 ubuntu root         0 2007-06-21 20:42 HPCD.sys
drwx------ 5 ubuntu root      4096 2005-06-06 14:39 i386
-rwx------ 1 ubuntu root     40960 2002-09-10 15:54 Info.exe
-r-x------ 1 ubuntu root         0 2008-12-17 21:18 IO.SYS
-rwx------ 1 ubuntu root    136862 2005-06-06 14:53 MassStorage.log
-rwx------ 1 ubuntu root       994 2007-06-21 19:51 master.log
-rwx------ 1 ubuntu root         0 2004-05-04 10:46 menund
drwx------ 7 ubuntu root      4096 2005-06-06 14:49 MiniNT
-rwx------ 1 ubuntu root         0 2004-01-13 11:14 move
-r-x------ 1 ubuntu root         0 2008-12-17 21:18 MSDOS.SYS
-r-x------ 1 ubuntu root     47564 2006-02-28 12:00 NTDETECT.COM
-rwx------ 1 ubuntu root         0 2001-06-18 23:53 ntfs
-r-x------ 1 ubuntu root    250032 2006-02-28 12:00 ntldr
-rwx------ 1 ubuntu root 120586240 2008-12-17 21:02 pagefile.sys
drwx------ 2 ubuntu root      4096 2004-01-13 12:25 PRELOAD
-rwx------ 1 ubuntu root    319545 2003-06-12 17:41 protect.ed
-rwx------ 1 ubuntu root         0 2007-06-18 13:05 RCBoot.sys
drwx------ 2 ubuntu root      4096 2007-11-20 18:52 $RECYCLE.BIN
drwx------ 2 ubuntu root      4096 2005-06-06 16:44 Recycled
-rwx------ 1 ubuntu root    245920 2003-05-27 11:27 stldr
dr-x------ 2 ubuntu root      4096 2005-06-06 14:53 System Restore
drwx------ 4 ubuntu root      4096 2005-06-06 16:18 System Volume Information
drwx------ 8 ubuntu root      4096 2005-06-06 14:49 updgoi
-rwx------ 1 ubuntu root       492 2005-05-04 16:47 USER
-rwx------ 1 ubuntu root     96774 2003-06-12 18:43 warning.bmp
-rwx------ 1 ubuntu root        10 2002-08-29 13:00 win51
-rwx------ 1 ubuntu root        11 2001-01-22 03:00 win51.b2
-rwx------ 1 ubuntu root        10 2001-08-23 11:00 win51ic
-rwx------ 1 ubuntu root        11 2001-03-20 03:00 win51ic.b2
-rwx------ 1 ubuntu root        11 2001-07-25 04:00 win51ic.rc1
-rwx------ 1 ubuntu root        11 2001-07-25 04:00 win51ic.rc2
-rwx------ 1 ubuntu root        10 2002-08-29 13:00 win51ip
-rwx------ 1 ubuntu root        11 2001-01-22 03:00 win51ip.b2
-rwx------ 1 ubuntu root        11 2001-07-25 09:47 win51ip.rc2
-rwx------ 1 ubuntu root         2 2002-08-29 13:00 win51ip.sp1
-rwx------ 1 ubuntu root        11 2001-07-25 04:00 win51.rc1
-rwx------ 1 ubuntu root        11 2001-07-25 09:47 win51.rc2
-rwx------ 1 ubuntu root       185 2001-09-13 20:29 winbom.ini
-rwx------ 1 ubuntu root         0 2004-01-13 11:14 xga
ubuntu@ubuntu:~$ 

I do not get grub I get the Windows bootloader. I got it to open by just dragging and dropping the file with gksudo gedit at the beginning.

---

### Post by miked860 on 2008-12-18
ok windows boots but I still don't get grub. I guess I'll follow the original tutorial that I had. I think it should work now.

---

### Post by miked860 on 2008-12-18
Everything works fine now. Thanks for all your help. I would have been screwed without it.

---

### Post by caljohnsmith on 2008-12-18
Glad to hear its all working OK now; cheers and have fun with Ubuntu and Windows. :)

---

