---
title: "[SOLVED] lost grub"
date: 2009-01-01
forum: General Help
---

### Post by karan_sharma01 on 2009-01-01
i had ubuntu and windows xp .....after reinstalling windows i am not getting the list of all os....i think i lost the grub ........

i followed the steps as given in [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


but after writing setup (hd0) iam gettig this as output ..



grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested


please help:confused::confused::confused:

---

### Post by karan_sharma01 on 2009-01-01
i had ubuntu and windows xp .....after reinstalling windows i am not getting the list of all os....i think i lost the grub ........

i followed the steps as given in [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


but after writing setup (hd0) iam gettig this as output ..



grub> find /boot/grub/stage1
(hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested


please help

---

### Post by cariboo on 2009-01-01
Could paste the output of:

```
sudo fdisk -l
```

in your next post, so that we can see what yor partition layout looks like.

Jim

---

### Post by karan_sharma01 on 2009-01-01
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd05dd05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         653     5245191    b  W95 FAT32
/dev/sda2             654        2422    14209492+   7  HPFS/NTFS
/dev/sda3            2423        9732    58717575    f  W95 Ext'd (LBA)
/dev/sda4            4845        7266    19454683+   7  HPFS/NTFS
/dev/sda5            2423        4246    14651217   83  Linux
/dev/sda6            4247        4844     4803403+  82  Linux swap / Solaris
/dev/sda7            7267        9732    19808113+   7  HPFS/NTFS

Disk /dev/sdb: 2054 MB, 2054160384 bytes
255 heads, 63 sectors/track, 249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0217934c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         250     2005984+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(248, 254, 63) logical=(249, 188, 3)

---

### Post by caljohnsmith on 2009-01-01
Sometimes that kind of Grub error in the Grub CLI is due to a corrupt partition table; in addition to posting what cariboo907 asked for, please also post:
```
sudo sfdisk -luS
sudo sfdisk -V

```

---

### Post by karan_sharma01 on 2009-01-01
root@ubuntu:/home/ubuntu# sudo sfdisk -luS

Disk /dev/sda: 9733 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  10490444   10490382   b  W95 FAT32
/dev/sda2      10490445  38909429   28418985   7  HPFS/NTFS
/dev/sda3      38909430 156344579  117435150   f  W95 Ext'd (LBA)
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda4      77818923 116728289   38909367   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda5      38909556  68211989   29302434  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,2,1)
/dev/sda6      68212053  77818859    9606807  82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda7     116728353 156344579   39616227   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)

Disk /dev/sdb: 1011 cylinders, 64 heads, 62 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 1011/64/62).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *        63   4012031    4011969   e  W95 FAT16 (LBA)
		end: (c,h,s) expected (249,188,3) found (248,254,63)
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty

---

### Post by karan_sharma01 on 2009-01-01
root@ubuntu:/home/ubuntu# sudo sfdisk -V
Warning: partition 4 does not start at a cylinder boundary
Warning: partition 1 extends past end of disk

---

### Post by Rocket2DMn on 2009-01-01
Threads merged, please don't double post, it's not fair to those trying to help you.  Thank you.

---

### Post by caljohnsmith on 2009-01-01
> **karan_sharma01 said:**
> ```
root@ubuntu:/home/ubuntu# sudo sfdisk -luS

Disk /dev/sda: 9733 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  10490444   10490382   b  W95 FAT32
/dev/sda2      10490445  38909429   28418985   7  HPFS/NTFS
[COLOR="Red"]/dev/sda3      38909430 156344579[/COLOR]  117435150   f  W95 Ext'd (LBA)
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
[COLOR="Red"]/dev/sda4      77818923[/COLOR] 116728289   38909367   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda5      38909556  68211989   29302434  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,2,1)
/dev/sda6      68212053  77818859    9606807  82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda7     116728353 156344579   39616227   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
```

Unfortunately you do have a partition table problem, because your sda4 primary partition is inside of your sda3 extended partition; sda4 should instead be a logical partition. To fix the problem, how about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
**If you are using Version 6.8:**
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", "Proceed", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deeps search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.

**If you are using Version 6.9:**
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deeps search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.

---

### Post by karan_sharma01 on 2009-01-01
sir iam not been able to make Ubuntu Universe repository enable.......could you please elaborate a bit more on how to make it enable from software source window .....
i have widows xp 
and ubuntu 8.04(hardy)
kernel linux 2.6.24-19-generic installed 

right now iam using live ubuntu cd

---

### Post by caljohnsmith on 2009-01-01
How about we take a different approach; please post the output of:
```
sudo sfdisk -d /dev/sda
```
Do you have all your important data on all the partitions backed up? It is always a good idea to do that before doing any partition changes. In addition, can you currently access all your partitions OK?

---

### Post by karan_sharma01 on 2009-01-01
root@ubuntu:/home/ubuntu# sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 10490382, Id= b, bootable
/dev/sda2 : start= 10490445, size= 28418985, Id= 7
/dev/sda3 : start= 38909430, size=117435150, Id= f
/dev/sda4 : start= 77818923, size= 38909367, Id= 7
/dev/sda5 : start= 38909556, size= 29302434, Id=83
/dev/sda6 : start= 68212053, size=  9606807, Id=82
/dev/sda7 : start=116728353, size= 39616227, Id= 7


yes i can access every partition

---

### Post by karan_sharma01 on 2009-01-01
root@ubuntu:/home/ubuntu# sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 10490382, Id= b, bootable
/dev/sda2 : start= 10490445, size= 28418985, Id= 7
/dev/sda3 : start= 38909430, size=117435150, Id= f
/dev/sda4 : start= 77818923, size= 38909367, Id= 7
/dev/sda5 : start= 38909556, size= 29302434, Id=83
/dev/sda6 : start= 68212053, size=  9606807, Id=82
/dev/sda7 : start=116728353, size= 39616227, Id= 7


yes i can access every partition

---

### Post by caljohnsmith on 2009-01-01
OK, please first make sure you have all your important data backed up, download the attached "partition_table.txt" file to your Ubuntu desktop, and then do the following:
```
sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
```
That will produce a lot of output including warnings, and please post the output. Next reboot, boot your Live CD again, and post the new output of:
```
sudo fdisk -l
sudo sfdisk -luS -V
sudo sfdisk -d /dev/sda
```
And also post the output of:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
And we can work from there.

---

### Post by karan_sharma01 on 2009-01-01
ubuntu@ubuntu:~$ sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 9733 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+    652     653-   5245191    b  W95 FAT32
/dev/sda2        653    2421    1769   14209492+   7  HPFS/NTFS
/dev/sda3       2422    9731    7310   58717575    f  W95 Ext'd (LBA)
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda4       4844+   7265    2422-  19454683+   7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda5       2422+   4245    1824-  14651217   83  Linux
                start: (c,h,s) expected (1023,254,63) found (1023,2,1)
/dev/sda6       4246+   4843     598-   4803403+  82  Linux swap / Solaris
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda7       7266+   9731    2466-  19808113+   7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  10490444   10490382   b  W95 FAT32
/dev/sda2      10490445  38909429   28418985   7  HPFS/NTFS
/dev/sda3      38909430 156344579  117435150   f  W95 Ext'd (LBA)
/dev/sda4             0         -          0   0  Empty
/dev/sda5      38909556  68211989   29302434  83  Linux
/dev/sda6      68212053  77818859    9606807  82  Linux swap / Solaris
/dev/sda7      77818923 116728289   38909367   7  HPFS/NTFS
/dev/sda8     116728353 156344579   39616227   7  HPFS/NTFS
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
ubuntu@ubuntu:~$

---

### Post by karan_sharma01 on 2009-01-01
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd05dd05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         653     5245191    b  W95 FAT32
/dev/sda2             654        2422    14209492+   7  HPFS/NTFS
/dev/sda3            2423        9732    58717575    f  W95 Ext'd (LBA)
/dev/sda5            2423        4246    14651217   83  Linux
/dev/sda6            4247        4844     4803403+  82  Linux swap / Solaris
/dev/sda7            4845        7266    19454683+   7  HPFS/NTFS
/dev/sda8            7267        9732    19808113+   7  HPFS/NTFS

Disk /dev/sdb: 2054 MB, 2054160384 bytes
255 heads, 63 sectors/track, 249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0217934c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         250     2005984+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(248, 254, 63) logical=(249, 188, 3)



ubuntu@ubuntu:~$ sudo sfdisk -luS -V

Disk /dev/sda: 9733 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  10490444   10490382   b  W95 FAT32
/dev/sda2      10490445  38909429   28418985   7  HPFS/NTFS
/dev/sda3      38909430 156344579  117435150   f  W95 Ext'd (LBA)
/dev/sda4             0         -          0   0  Empty
/dev/sda5      38909556  68211989   29302434  83  Linux
/dev/sda6      68212053  77818859    9606807  82  Linux swap / Solaris
/dev/sda7      77818923 116728289   38909367   7  HPFS/NTFS
/dev/sda8     116728353 156344579   39616227   7  HPFS/NTFS
/dev/sda: OK

Disk /dev/sdb: 1011 cylinders, 64 heads, 62 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 1011/64/62).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *        63   4012031    4011969   e  W95 FAT16 (LBA)
		end: (c,h,s) expected (249,188,3) found (248,254,63)
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty
Warning: partition 1 extends past end of disk



ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 10490382, Id= b, bootable
/dev/sda2 : start= 10490445, size= 28418985, Id= 7
/dev/sda3 : start= 38909430, size=117435150, Id= f
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 38909556, size= 29302434, Id=83
/dev/sda6 : start= 68212053, size=  9606807, Id=82
/dev/sda7 : start= 77818923, size= 38909367, Id= 7
/dev/sda8 : start=116728353, size= 39616227, Id= 7
ubuntu@ubuntu:~$

---

### Post by karan_sharma01 on 2009-01-01
grub> root (hd0,4)      

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
:D:D:D:D:D:D:D:D:

---

### Post by logos34 on 2009-01-01
A suggestion:

try it this way to get rid of that empty partition listing in the table:

> sudo sfdisk -d /dev/sda | sudo  sfdisk  --force /dev/sda

EDIT: ok, I see it worked after all.

---

### Post by caljohnsmith on 2009-01-01
> **logos34 said:**
> A suggestion:

try it this way to get rid of that empty partition listing in the table:

```
sudo sfdisk -d /dev/sda | sudo sfdisk --force /dev/sda 
```

EDIT: ok, I see it worked after all.
Actually, sfdisk always reports which primary partitions are empty, so since his sda4 primary partition has now been converted to the sda7 logical partition, sfdisk correctly shows that sda4 no longer exists. The above trick that you show is a way to get rid of empty logical partitions that don't exist, but are erroneously listed in one of the EBRs (Extended Boot Records). That didn't happen to be karan_sharma01's case. :)

---

### Post by karan_sharma01 on 2009-01-01
thanx everyone esp. caljohnsmith sir n happy new year

---

### Post by caljohnsmith on 2009-01-01
> **karan_sharma01 said:**
> thanx everyone esp. caljohnsmith sir n happy new year
Glad that worked OK; cheers and Happy New Year to you too. :)

---

### Post by karan_sharma01 on 2009-01-02
grub has been installed but Ubuntu is still not booting ......

on selecting Ubuntu option from grub menu its showing ...

Error 17 : cannot mount selected partition 
Press any key to continue...... 


please help....

---

### Post by caljohnsmith on 2009-01-02
OK, how about on start up when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers (or if it has a "uuid" line select that instead), press "e" to edit it, change it to "root (hd0,4)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "# groot=(hdX,Y)" to use the (hd0,4) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems though.

---

### Post by karan_sharma01 on 2009-01-02
now ubuntu is booting fine .....:):)thanx a lot sir

---

### Post by caljohnsmith on 2009-01-02
You're certainly welcome, and I hope you don't run into any other major problems. Cheers and have fun with Ubuntu. :)

---

