---
title: "Unable to acces external ext3 drive with explore2fs"
date: 2009-06-11
forum: General Help
---

### Post by Metallion on 2009-06-11
I have this 320 gig WD external drive with a tiny windows partition holding ifs driver and explore2fs. In linux everything works just fine but today I tried to use it on windows for the first time using the above programs and it simply doesn't work. the ifs driver says the disk isn't formatted and explore2fs just doesn't show anything when i open the drive. Any ideas?

fdisk -l output:
```
Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3bcdf9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           1        8001    7  HPFS/NTFS
/dev/sdc2               2       38913   312560640   83  Linux

```

and the (i think) relevant part from explore2fs's debug log: (full debug log is attached below)
```
Reading sector 2 count = 2
Found Valid Superblock
4k block size
Inodes count          : 19537920
Blocks count          : 78140160
Reserved blocks count : 3907008
Free blocks count     : 61868469
Free inodes count     : 19501408
First Data Block      : 0
Block size            : 2
# Blocks per group    : 32768
# Fragments per group : 32768
# Inodes per group    : 8192
Mount time            : 1244714478
Write time            : 1244715729
Mount count           : 1
Maximal mount count   : 32
File system state     : 1
Behaviour when detecting errors   : 1
time of last check                : 1244713281
max. time between checks          : 15552000
OS                    : 0
Revision level        : 1
uid for reserved blks : 0
gid for reserved blks : 0
First non-res inode   : 11
Size of inode         : 256
Blockgroup no         : 0
Compatible features   : 0000003C
Incompatible features : 00000002
                      : EXT2_FEATURE_INCOMPAT_FILETYPE
Read only features    : 00000003
                      : EXT2_FEATURE_RO_COMPAT_SPARSE_SUPER
                      : EXT2_FEATURE_RO_COMPAT_LARGE_FILE
uuid                  : 9B09FDE1A5F84633A25302D22F30340C
Volume name           : Kaasje
Last mounted          : 
Compression algorithm : 00000000
No blocks to prealloc : 0
No for dirs           : 0
Revision 1.  This should be OK.
2385 groups of 32768 blocks
Descriptors take 19 blocks
GetBlock 1 len 19
 block 1 starts at sector no 8
Reading sector 8 count = 152
Block bitmap 1 blocks
inode bitmap 1 blocks
inode table 256 blocks
The BlockHeadSize is 258
LockBlockGroup 1
GetBlock 1025 len 258
 block 1025 starts at sector no 8200
Reading sector 8200 count = 2064
INode mode        : 0000
INode size        : 0
dir acl (size hi) : 0
INode uid         : 0
INode gid         : 0
access time       : 0
creation time     : 0
modification time : 0
delection time    : 0
link count        : 0
blocks            : 0
flags             : 00000000
direct blocks     : 0 0 0 0 0 0 0 0 0 0 0 0 
indirect          : 0
double indirect   : 0
tripple indirect  : 0
UnLockBlockGroup 1
Destroying NTDisk
Destroying BlockDevice


```

Attached is a screenshot of what happens in explore2fs. You can see how my internal linux root easily opens but nothing happens when I click this external HD.

This has been reproduced on 2 windows machines with these 3 ext3 readers: [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by Jose Catre-Vandis on 2009-07-20
You need to use Ext2fsd to access ubuntu 9.04 with an inode size of 256
look [here]("http://www.google.co.uk/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fext2fsd%2F&ei=zZ1kStP4BM3RjAfMp_j9Dw&usg=AFQjCNEX7893SYRkZbFlnzq2YRB49yYLDw&sig2=qbEL72IUaJuDkB6TZ5XepQ")

---

