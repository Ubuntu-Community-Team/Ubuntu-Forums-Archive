---
title: "Corrupt partition table"
date: 2009-04-14
forum: General Help
---

### Post by vinothchandar on 2009-04-14
Hi all,

First of all, I thank the community for the wonderful support.

My Kubuntu Hardy heron installation crashed last night and when I booted the machine up, the partition tables were all over the place.

sda1 - my windows recovery partition
sda2 - c: of windows
sda3 - swap 
sda4 - My ubuntu installation
sda5 - my home parition
sda6 - D: windows


```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6dfd45bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8193116    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sda2            1021       10889    79272742+   7  HPFS/NTFS
/dev/sda3           11412       11543     1049592   82  Linux swap / Solaris
/dev/sda4           11543       19458    63584451    f  W95 Ext'd (LBA)
/dev/sda5           11543       12195     5242880   83  Linux
/dev/sda6           12197       19457    58323951    c  W95 FAT32 (LBA)

```

```
root@ubuntu:~# dumpe2fs /dev/sda4 
dumpe2fs 1.40.8 (13-Mar-2008)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4
Couldn't find valid filesystem superblock.

root@ubuntu:~# sfdisk -d /dev/sda
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 16386232, Id= b, bootable
/dev/sda2 : start= 16386300, size=158545485, Id= 7
/dev/sda3 : start=183324672, size=  2099184, Id=82
/dev/sda4 : start=185423868, size=127168902, Id= f
/dev/sda5 : start=185425920, size= 10485760, Id=83
/dev/sda6 : start=195928803, size=116647902, Id= c


```

I did a lot of googling and found this tool -- testdisk. I was able to backup my data safely. I also have the start-end of each partition from TestDisk [cylinder,track,sector]

I just donot know how to fix all this and restore the system to normalcy. parted shows the entire disk as "unallocated". I think some MBRs are also corrupt. 

Please help me!! 

thanks
Vinoth

---

### Post by callie510 on 2009-04-14
You should be able to fix the partition table with testdisk. Did you apply changes? Be a little more specific about what you did with it?

I don't remember the exact syntax, but when I saw my partition tables all messed up like yours, testdisk actually fixed them.

---

### Post by meierfra. on 2009-04-14
> Partition 1 does not end on cylinder boundary.
This is just a warning from fdisk, which you can ignore. I never have seen this actually cause a  problem.


> dumpe2fs /dev/sda4 
dumpe2fs 1.40.8 (13-Mar-2008 )
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4
Couldn't find valid filesystem superblock.
/dev/sda4  is an extended partition, that is a container for other partitions. It does not have a file system. So of course "dumpe2fs /dev/sda4" will give you an error message,

> parted shows the entire disk as "unallocated". 

This is the only indication that something is wrong with your partition table.  Otherwise I cannot find any problems. Could you post the output of

```
sudo parted print
```
this might tell us why parted is having  a problem with the partition table.

Do you have any other problems? 
Are you able to boot into all your OS?
Do you know what your partition table looked like before your computer crashed?

---

### Post by vinothchandar on 2009-04-14
Hi,

Thanks for the info.

```


root@ubuntu:~#parted /dev/sda print 
Error: Can't have a partition outside the disk!
Information: Don't forget to update /etc/fstab, if necessary.


```

I am not able to boot into the machine; grub fails with error 17.
I am doing everything from a live cd now. I am not sure about the partition table before the crash :(

The full story is this : 

First, I was not able to access my home partition; I used testdisk, it found the home partition [sda5] and backed up my data. it presented a new partition table and after that, I have not been able to access sda4. 

testdisk's quick search does not show sda4. But,when I do a "deeper search" I am able to access the sda4,sda5,sda6.
[That is how I noted the start-end for each partition]
In any case, when I try to list files in sda1,sda2 using testdisk, it complains saying "No file. Filesystem seems corrupted".

I used the backupBS feature for both sda1,sda2 to correct any errors in MBR. testdisk atleast mentions that the boot sectors are ok for those partitions now.
 
Any thoughts ? 

thanks
Vinoth

---

### Post by meierfra. on 2009-04-14
Post the output of the testdisk deep search (copy and paste the whole terminal)

---

### Post by vinothchandar on 2009-04-15
```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
* FAT32                    0   1  1  1019 254 58   16386232 [NO NAME] [I am not able to list anything; getting "File system may be corrupt"]
D HPFS - NTFS           1020   0  1 10888 254 63  158545485 [I am not able to list anything; getting "File system may be corrupt"]
D HPFS - NTFS           1274 241 56 10366 150 24  146057216 [ACER] [I am able to list files here; this is my c:]
D Linux                10366 150 25 11411  77 58   16783360 [I am able to list; My ubuntu installation]
D HPFS - NTFS          10366 150 25 19457  21 20  146038784
D Linux                10367 252 62 11412 180 32   16783360
D Linux                10368 160 33 11413  88  3   16783360
D Linux                10371 208 14 11416 135 47   16783360
D Linux                10372  50 47 11416 233 17   16783360
D Linux                10374  93 24 11419  20 57   16783360
D Linux                10375   0 58 11419 183 28   16783360
D Linux                10375 228 30 11420 155 63   16783360
D Linux                10376  38 31 11420 221  1   16783360
D Linux                10376  70 63 11420 253 33   16783360
D Linux                10378  16  7 11422 198 40   16783360
D Linux                10378  48 39 11422 231  9   16783360
D Linux                10379 151 13 11424  78 46   16783360
D Linux                10379 248 46 11424 176 16   16783360
D Linux                10380 123 48 11425  51 18   16783360
D Linux                10382 133 56 11427  61 26   16783360
D Linux                10383 171 29 11428  98 62   16783360
D Linux Swap           11411 110 28 11542  25 51    2099184
D Linux                11542  58 37 12194 239 13   10485760 [I am able to list; my home partition]
D Linux                11542 221  8 12195 146 47   10485760
D Linux                11543 193 43 12196 119 19   10485760
D Linux                11544 101 14 12197  26 53   10485760
D Linux                11545  41 17 12197 221 56   10485760
D Linux                11548  88 61 12201  14 37   10485760
D Linux                11549  61 33 12201 242  9   10485760
D Linux                11550  34  5 12202 214 44   10485760
D Linux                11554   2  1 12206 182 40   10485760
D Linux                11554 216 55 12207 142 31   10485760
D Linux                11556 226 63 12209 152 39   10485760
D FAT32 LBA            12196   1  1 19456 254 63  116647902 [able to list files; my D:]
```

I have added some comments on the side of the entries; 
I dont know what numerous other entries are. The ones with comments are the ones that matter. All others just fail to list files saying "Filesystem seems damaged". This is what made me feel my partition table is screwed up big time..

---

### Post by meierfra. on 2009-04-15
Use the "left/right" arrow keys to mark the partitions as follows:

```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]P[/COLOR] FAT32                    0   1  1  1019 254 58   16386232 [NO NAME] [I am not able to list anything; getting "File system may be corrupt"]
D HPFS - NTFS           1020   0  1 10888 254 63  158545485 [I am not able to list anything; getting "File system may be corrupt"]
[COLOR="Red"]* [/COLOR]HPFS - NTFS           1274 241 56 10366 150 24  146057216 [ACER] [I am able to list files here; this is my c:]
[COLOR="Red"]P[/COLOR] Linux                10366 150 25 11411  77 58   16783360 [I am able to list; My ubuntu installation]
D HPFS - NTFS          10366 150 25 19457  21 20  146038784
D Linux                10367 252 62 11412 180 32   16783360
D Linux                10368 160 33 11413  88  3   16783360
D Linux                10371 208 14 11416 135 47   16783360
D Linux                10372  50 47 11416 233 17   16783360
D Linux                10374  93 24 11419  20 57   16783360
D Linux                10375   0 58 11419 183 28   16783360
D Linux                10375 228 30 11420 155 63   16783360
D Linux                10376  38 31 11420 221  1   16783360
D Linux                10376  70 63 11420 253 33   16783360
D Linux                10378  16  7 11422 198 40   16783360
D Linux                10378  48 39 11422 231  9   16783360
D Linux                10379 151 13 11424  78 46   16783360
D Linux                10379 248 46 11424 176 16   16783360
D Linux                10380 123 48 11425  51 18   16783360
D Linux                10382 133 56 11427  61 26   16783360
D Linux                10383 171 29 11428  98 62   16783360
[COLOR="Red"]L[/COLOR] Linux Swap           11411 110 28 11542  25 51    2099184
[COLOR="Red"]L[/COLOR] Linux                11542  58 37 12194 239 13   10485760 [I am able to list; my home partition]
D Linux                11542 221  8 12195 146 47   10485760
D Linux                11543 193 43 12196 119 19   10485760
D Linux                11544 101 14 12197  26 53   10485760
D Linux                11545  41 17 12197 221 56   10485760
D Linux                11548  88 61 12201  14 37   10485760
D Linux                11549  61 33 12201 242  9   10485760
D Linux                11550  34  5 12202 214 44   10485760
D Linux                11554   2  1 12206 182 40   10485760
D Linux                11554 216 55 12207 142 31   10485760
D Linux                11556 226 63 12209 152 39   10485760
[COLOR="Red"]L[/COLOR] FAT32 LBA            12196   1  1 19456 254 63  116647902 [able to list files; my D:]
```

Press Continue and choose "write".

---

### Post by vinothchandar on 2009-04-15
Hi,

Great progress !! I got my grub back. I was able to boot up kubuntu.

But, when I try to login , I get 
"Could not start kstartupconfig. Check your installation" message box.

thanks
vinoth

---

### Post by meierfra. on 2009-04-15
> "Could not start kstartupconfig. Check your installation" message box.

Sorry, I don't know anything about this error. But  I suggest to run a file system check on your ubuntu and  home partitions.

From a terminal in the live CD:

```
sudo umount /dev/sda3
sudo e2fsck -fyv /dev/sda3
```
(ignore any "not mounted" error message from the first command)

Run "e2fsck" as often as it takes, that is until it does not fix any more errors.


Repeat this procedure with "/dev/sda6" in place of "/dev/sda3"

---

### Post by vinothchandar on 2009-04-15
```
root@ubuntu:~# e2fsck -fyv /dev/sda6
e2fsck 1.40.8 (13-Mar-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

   23943 inodes used (3.65%)
    1238 non-contiguous inodes (5.2%)
         # of inodes with ind/dind/tind blocks: 1736/49/0
  424022 blocks used (32.35%)
       0 bad blocks
       1 large file

   20141 regular files
    3768 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
      25 symbolic links (25 fast symbolic links)
       0 sockets
--------
   23934 files


root@ubuntu:~# e2fsck -fyv /dev/sda3
e2fsck 1.40.8 (13-Mar-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  143227 inodes used (13.64%)
    1496 non-contiguous inodes (1.0%)
         # of inodes with ind/dind/tind blocks: 6954/89/0
  985378 blocks used (46.97%)
       0 bad blocks
       1 large file

  118855 regular files
   13889 directories
     114 character device files
      26 block device files
       2 fifos
     485 links
   10332 symbolic links (9789 fast symbolic links)
       0 sockets
--------
  143703 files
root@ubuntu:~# 
```

I guess the disk is ok now.. I still have the kdestartupconfig problem though

---

### Post by vinothchandar on 2009-04-15
Hi,

Fixed it. It was due to some entry in fstab I had commented out earlier. Hence, my home partition was never mounted in /home.

I had commented it out earlier coz ubuntu was not able to boot up, since sda6 was corrupt..

I guess that solves the case. Thanks for all the help..
I really appreciate it and gives me immense motivation and push to be able to contribute back to the community someday soon..

thanks
Vinoth

---

### Post by meierfra. on 2009-04-15
> Fixed it. 

Great.  Are you able to boot into Windows, too?

---

### Post by vinothchandar on 2009-04-15
It boots up. But, when booting up, it tries to do a chkdsk and reports an error "The disk looks like a non windows xp disk" [I have Vista btw :) ]

Windows is trying to mount another disk, in addition to my old c and d. I guess that is causing the warning message.

I hardly use windows. So, as long as the data is there and ubuntu runs I am good..

thanks
vinoth

---

