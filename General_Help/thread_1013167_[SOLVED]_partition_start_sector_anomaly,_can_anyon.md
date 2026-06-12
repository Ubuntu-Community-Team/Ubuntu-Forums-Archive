---
title: "[SOLVED] partition start sector anomaly, can anyone explain?"
date: 2008-12-16
forum: General Help
---

### Post by mdurham on 2008-12-16
Hi, As you will see below sfdisk reports that each start sector is incorrect. Can anyone explain what's going on and, should I correct this?
If so, how?
Cheers, Mike

> mike@jaunty-2:~$ sudo sfdisk -l

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   2742    2743-  22033116    c  W95 FAT32 (LBA)
/dev/sda2       2743    5485    2743   22033147+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3       5486   36973   31488  252927360    f  W95 Ext'd (LBA)
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda4      36974   38912    1939   15575017+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda5       5486+   7397    1912-  15358108+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda6       7398+   9309    1912-  15358108+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda7       9310+  11221    1912-  15358108+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda8      11222+  13133    1912-  15358108+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda9      13134+  13388     255-   2048256   82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda10     13389+  19762    6374-  51199123+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda11     19763+  24861    5099-  40957686    b  W95 FAT32
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda12     24862+  29960    5099-  40957686   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda13     29961+  36973    7013-  56331891   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)


---

### Post by mdurham on 2008-12-17
??????????

---

### Post by caljohnsmith on 2008-12-17
How about posting the output of:
```
sudo fdisk -lu
sudo sfdisk -d /dev/sda
sudo parted /dev/sda print
```
And we can work from there if you want.

---

### Post by mdurham on 2008-12-17
Thanks for your help caljohnsmith, see below as you requested.

> mike@jaunty-2:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b3f2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    44066294    22033116    c  W95 FAT32 (LBA)
/dev/sda2        44066295    88132589    22033147+  83  Linux
/dev/sda3        88132590   593987309   252927360    f  W95 Ext'd (LBA)
/dev/sda4       593987310   625137344    15575017+  83  Linux
/dev/sda5        88132653   118848869    15358108+  83  Linux
/dev/sda6       118848933   149565149    15358108+  83  Linux
/dev/sda7       149565213   180281429    15358108+  83  Linux
/dev/sda8       180281493   210997709    15358108+  83  Linux
/dev/sda9       210997773   215094284     2048256   82  Linux swap / Solaris
/dev/sda10      215094348   317492594    51199123+  83  Linux
/dev/sda11      317492658   399408029    40957686    b  W95 FAT32
/dev/sda12      399408093   481323464    40957686   83  Linux
/dev/sda13      481323528   593987309    56331891   83  Linux


mike@jaunty-2:~$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 44066232, Id= c, bootable
/dev/sda2 : start= 44066295, size= 44066295, Id=83
/dev/sda3 : start= 88132590, size=505854720, Id= f
/dev/sda4 : start=593987310, size= 31150035, Id=83
/dev/sda5 : start= 88132653, size= 30716217, Id=83
/dev/sda6 : start=118848933, size= 30716217, Id=83
/dev/sda7 : start=149565213, size= 30716217, Id=83
/dev/sda8 : start=180281493, size= 30716217, Id=83
/dev/sda9 : start=210997773, size=  4096512, Id=82
/dev/sda10: start=215094348, size=102398247, Id=83
/dev/sda11: start=317492658, size= 81915372, Id= b
/dev/sda12: start=399408093, size= 81915372, Id=83
/dev/sda13: start=481323528, size=112663782, Id=83


mike@jaunty-2:~$ sudo parted /dev/sda print
Model: ATA ST3320620A (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags    
 1      32.3kB  22.6GB  22.6GB  primary   fat32        boot, lba
 2      22.6GB  45.1GB  22.6GB  primary   ext3                  
 3      45.1GB  304GB   259GB   extended               lba      
 5      45.1GB  60.9GB  15.7GB  logical   ext3                  
 6      60.9GB  76.6GB  15.7GB  logical   ext3                  
 7      76.6GB  92.3GB  15.7GB  logical   ext3                  
 8      92.3GB  108GB   15.7GB  logical   ext3                  
 9      108GB   110GB   2097MB  logical   linux-swap            
10      110GB   163GB   52.4GB  logical   ext3                  
11      163GB   204GB   41.9GB  logical   fat32                 
12      204GB   246GB   41.9GB  logical   ext3                  
13      246GB   304GB   57.7GB  logical   ext3                  
 4      304GB   320GB   15.9GB  primary   ext3                   


---

### Post by caljohnsmith on 2008-12-17
I forgot to ask in my previous post, but do you know what might have caused the CHS values to be changed in your partition table? Did you use testdisk to change your partition table or something? How about doing the following commands and please post the output:
```
sudo sfdisk -d /dev/sda |  sudo sfdisk --force  /dev/sda
sudo sfdisk -l
```
That might be enough to correct the problem.

---

### Post by mdurham on 2008-12-17
I tried your suggestion but it seems I guess I must do it from the live CD. I can't do it right now, I'll try later and report back.
I've no idea what caused this, I haven't used testdisk. I also have no idea how long it's been like this, I saw sfdisk used in a forum post and thought I'd try it to see what my partitions looked like and this was the result. Everything seems to work as normal though.

Thanks caljohnsmith.

> Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   2742    2743-  22033116    c  W95 FAT32 (LBA)
/dev/sda2       2743    5485    2743   22033147+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3       5486   36973   31488  252927360    f  W95 Ext'd (LBA)
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda4      36974   38912    1939   15575017+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda5       5486+   7397    1912-  15358108+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda6       7398+   9309    1912-  15358108+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda7       9310+  11221    1912-  15358108+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda8      11222+  13133    1912-  15358108+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda9      13134+  13388     255-   2048256   82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda10     13389+  19762    6374-  51199123+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda11     19763+  24861    5099-  40957686    b  W95 FAT32
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda12     24862+  29960    5099-  40957686   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda13     29961+  36973    7013-  56331891   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)


New situation:
No partitions found

sfdisk: no partition table present.



---

### Post by caljohnsmith on 2008-12-17
For some reason it looks like the sfdisk may have failed because of your strange CHS settings in the partition table; the last thing it returned was "no partition table found", so I think you might need to rewrite your partition table again. First check with:
```
sudo fdisk -lu
```
If that doesn't show your sda drive partition table, then please download the attached "partition_table.txt" file to your desktop (if you are still in Ubuntu on your HDD that's fine, or from the Live CD is OK too), and do:
```
sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
```
And after that check that your partition table is back with:
```
sudo fdisk -lu
sudo sfdisk -l
```
And please post the output.

---

### Post by mdurham on 2008-12-17
caljohnsmith, fantastic. I did as you suggested "sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt" see result below. After that, I rebooted and it seems to have fixed the problem perfectly so far, I haven't yet booted from partitions other than sda2. If I get more trouble with this I'll post again if that's ok with you.
Thanks for all your help, it's much appreciated.
Cheers, Mike

> mike@jaunty-2:~$ sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
[sudo] password for mike: 
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   2742    2743-  22033116    c  W95 FAT32 (LBA)
/dev/sda2       2743    5485    2743   22033147+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3       5486   36973   31488  252927360    f  W95 Ext'd (LBA)
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda4      36974   38912    1939   15575017+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda5       5486+   7397    1912-  15358108+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda6       7398+   9309    1912-  15358108+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda7       9310+  11221    1912-  15358108+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda8      11222+  13133    1912-  15358108+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda9      13134+  13388     255-   2048256   82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda10     13389+  19762    6374-  51199123+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda11     19763+  24861    5099-  40957686    b  W95 FAT32
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda12     24862+  29960    5099-  40957686   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda13     29961+  36973    7013-  56331891   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  44066294   44066232   c  W95 FAT32 (LBA)
/dev/sda2      44066295  88132589   44066295  83  Linux
/dev/sda3      88132590 593987309  505854720   f  W95 Ext'd (LBA)
/dev/sda4     593987310 625137344   31150035  83  Linux
/dev/sda5      88132653 118848869   30716217  83  Linux
/dev/sda6     118848933 149565149   30716217  83  Linux
/dev/sda7     149565213 180281429   30716217  83  Linux
/dev/sda8     180281493 210997709   30716217  83  Linux
/dev/sda9     210997773 215094284    4096512  82  Linux swap / Solaris
/dev/sda10    215094348 317492594  102398247  83  Linux
/dev/sda11    317492658 399408029   81915372   b  W95 FAT32
/dev/sda12    399408093 481323464   81915372  83  Linux
/dev/sda13    481323528 593987309  112663782  83  Linux
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
mike@jaunty-2:~$ 


---

### Post by caljohnsmith on 2008-12-18
That's great news that did the trick, Mike. If you have any more problems related to you partitions though, please let me know. Cheers and have fun with Ubuntu. :)

---

