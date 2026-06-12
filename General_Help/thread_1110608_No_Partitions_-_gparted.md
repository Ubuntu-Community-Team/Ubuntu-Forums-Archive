---
title: "No Partitions - gparted"
date: 2009-03-30
forum: General Help
---

### Post by ttk1opc on 2009-03-30
I am having a problem, I wanted to do a fresh install of ubuntu but no partitions are showing, with either gparted or running the live CD. It shows the entire disk as unallocated. I am running a dual boot system. When I originally installed I was going by a tutorial and I believe I manually created the partitions. I have tried testdisk, but I believe it found no problems, not sure, its kind of all greek to me.

Here are the results of fdisk

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81920000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           10199       22947   102400000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           22948       29247    50604750    5  Extended
/dev/sda4           23464       29247    46459948+  83  Linux
/dev/sda5           22948       23463     4144707   82  Linux swap / Solaris
```

and testdisk log


```
Thu Mar 26 20:50:41 2009
Command line: TestDisk

TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.28-11-generic (#37-Ubuntu SMP Mon Mar 23 16:40:23 UTC 2009)
Compiler: GCC 4.3 - Nov  7 2008 10:55:40
ext2fs lib: 1.41.4, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
Warning: can't get size for /dev/mapper/control
Hard disk list
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63, sector size=512 - ATA WDC WD2500JS-60N

Partition table type (auto): Intel
Disk /dev/sda - 250 GB / 232 GiB - ATA WDC WD2500JS-60N
Partition table type: Intel

Analyse Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/32/33
NTFS at 10198/177/28
get_geometry_from_list_part_aux head=255 nbr=4
get_geometry_from_list_part_aux head=255 nbr=4
Current partition structure:
 1 * HPFS - NTFS              0  32 33 10198 177 27  163840000
 2 P HPFS - NTFS          10198 177 28 22946 231  5  204800000
 3 E extended             22947   0  1 29246 254 63  101209500
 4 P Linux                23463   1  1 29246 254 63   92919897
Space conflict between the following two partitions
 3 E extended             22947   0  1 29246 254 63  101209500
 4 P Linux                23463   1  1 29246 254 63   92919897
   X extended             22947   0  2 23462 254 63    8289539
 5 L Linux Swap           22947   2  1 23462 254 63    8289414
Computes LBA from CHS for Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
NTFS at 0/1/1
filesystem size           469836927
sectors_per_cluster       8
mft_lcn                   10
mftmirr_lcn               566531
clusters_per_mft_record   -10
clusters_per_index_record 1
   D HPFS - NTFS              0   1  1 29245 254 63  469836927 [HP_PAVILION]
     NTFS, 240 GB / 224 GiB
FAT32 at 29247/0/1
FAT1 : 32-18101
FAT2 : 18102-36171
start_rootdir : 36172 root cluster : 2
Data : 36172-18539003
sectors : 18539010
cluster_size : 8
no_of_cluster : 2312854 (2 - 2312855)
fat_length 18070 calculated 18070

FAT32 at 29247/0/1
   D FAT32 LBA            29247   0  1 30400 254 63   18539010 [HP_RECOVERY]
     FAT32, 9491 MB / 9052 MiB
get_geometry_from_list_part_aux head=255 nbr=4
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=2
get_geometry_from_list_part_aux head=32 nbr=2
get_geometry_from_list_part_aux head=64 nbr=2
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=4

Results
   * HPFS - NTFS              0   1  1 29245 254 63  469836927 [HP_PAVILION]
     NTFS, 240 GB / 224 GiB
   P FAT32 LBA            29247   0  1 30400 254 63   18539010 [HP_RECOVERY]
     FAT32, 9491 MB / 9052 MiB

interface_write()
 1 * HPFS - NTFS              0   1  1 29245 254 63  469836927 [HP_PAVILION]
 2 P FAT32 LBA            29247   0  1 30400 254 63   18539010 [HP_RECOVERY]

search_part()
Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
NTFS at 0/1/1
filesystem size           469836927
sectors_per_cluster       8
mft_lcn                   10
mftmirr_lcn               566531
clusters_per_mft_record   -10
clusters_per_index_record 1
   D HPFS - NTFS              0   1  1 29245 254 63  469836927 [HP_PAVILION]
     NTFS, 240 GB / 224 GiB
NTFS at 0/32/33
filesystem size           163840000
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               10239999
clusters_per_mft_record   -10
clusters_per_index_record 1
   D HPFS - NTFS              0  32 33 10198 177 27  163840000
     NTFS, 83 GB / 78 GiB
NTFS at 10198/177/27
filesystem size           163840000
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               10239999
clusters_per_mft_record   -10
clusters_per_index_record 1
   D HPFS - NTFS              0  32 33 10198 177 27  163840000
     NTFS found using backup sector!, 83 GB / 78 GiB
NTFS at 10198/177/28
filesystem size           204800000
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               12799999
clusters_per_mft_record   -10
clusters_per_index_record 1
   D HPFS - NTFS          10198 177 28 22946 231  5  204800000
     NTFS, 104 GB / 97 GiB
NTFS at 22946/231/5
filesystem size           204800000
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               12799999
clusters_per_mft_record   -10
clusters_per_index_record 1
   D HPFS - NTFS          10198 177 28 22946 231  5  204800000
     NTFS found using backup sector!, 104 GB / 97 GiB
   D Linux Swap           22947   2  1 23462 254 41    8289392
     SWAP2 version 1, 4244 MB / 4047 MiB

recover_EXT2: s_block_group_nr=0/354, s_mnt_count=21/29, s_blocks_per_group=32768, s_inodes_per_group=16384
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 11614987
recover_EXT2: part_size 92919896
   D Linux                23463   1  1 29246 254 62   92919896
     EXT3 Large file Sparse superblock Recover, 47 GB / 44 GiB

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/354, s_mnt_count=0/29, s_blocks_per_group=32768, s_inodes_per_group=16384
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 11614987
recover_EXT2: part_size 92919896
   D Linux                23463   1  1 29246 254 62   92919896
     EXT3 Large file Sparse superblock Backup superblock, 47 GB / 44 GiB
FAT32 at 29247/0/1
FAT1 : 32-18101
FAT2 : 18102-36171
start_rootdir : 36172 root cluster : 2
Data : 36172-18539003
sectors : 18539010
cluster_size : 8
no_of_cluster : 2312854 (2 - 2312855)
fat_length 18070 calculated 18070

FAT32 at 29247/0/1
   D FAT32 LBA            29247   0  1 30400 254 63   18539010 [HP_RECOVERY]
     FAT32, 9491 MB / 9052 MiB
FAT32 at 29247/0/7
FAT1 : 32-18101
FAT2 : 18102-36171
start_rootdir : 36172 root cluster : 2
Data : 36172-18539003
sectors : 18539010
cluster_size : 8
no_of_cluster : 2312854 (2 - 2312855)
fat_length 18070 calculated 18070
set_FAT_info: name from BS used

FAT32 at 29247/0/7
   D FAT32 LBA            29247   0  1 30400 254 63   18539010 [HP_RECOVERY]
     FAT found using backup sector!, 9491 MB / 9052 MiB
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=2
get_geometry_from_list_part_aux head=32 nbr=2
get_geometry_from_list_part_aux head=64 nbr=2
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6

Results
   D HPFS - NTFS              0   1  1 29245 254 63  469836927 [HP_PAVILION]
     NTFS, 240 GB / 224 GiB
   D HPFS - NTFS              0  32 33 10198 177 27  163840000
     NTFS, 83 GB / 78 GiB
   D HPFS - NTFS          10198 177 28 22946 231  5  204800000
     NTFS, 104 GB / 97 GiB
   D Linux Swap           22947   2  1 23462 254 41    8289392
     SWAP2 version 1, 4244 MB / 4047 MiB
   D Linux                23463   1  1 29246 254 62   92919896
     EXT3 Large file Sparse superblock Recover, 47 GB / 44 GiB
   * FAT32 LBA            29247   0  1 30400 254 63   18539010 [HP_RECOVERY]
     FAT32, 9491 MB / 9052 MiB

interface_write()
 1 * FAT32 LBA            29247   0  1 30400 254 63   18539010 [HP_RECOVERY]
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

TestDisk exited normally.
```

Sorry if this is too much info, or I am in the wrong forum.
Thanks for any help you can provide.

---

### Post by ttk1opc on 2009-04-01
anybody?

---

### Post by xenophed on 2009-04-02
looks like your partitions are there 
/dev/sda1   *           1       10199    81920000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           10199       22947   102400000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           22948       29247    50604750    5  Extended
/dev/sda4           23464       29247    46459948+  83  Linux
/dev/sda5           22948       23463     4144707   82  Linux swap / Solaris

/dev/sda1 is your recovery disk from HP
/dev/sda2 is your XP drive
/dev/sda3 is an extended partition 
that is then split into two more 1.linux drive and 2.swap to cache memory to disk
if you want to use whole disk then delete all of the above with cfdisk and write to disk then reboot and make new partitions
/dev/sda1 [will be type 83]all but 1gb for swap on /dev/sda2[will be type 82] reboot and install

---

### Post by ttk1opc on 2009-04-02
Thanks for the reply, but that is the problem, I don't want to wipe out the other partitions, just install over the linux ones.

---

