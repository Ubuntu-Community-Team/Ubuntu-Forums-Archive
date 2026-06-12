---
title: "Orphaned inodes on EXT4"
date: 2010-12-28
forum: Desktop Environments
---

### Post by saltydog on 2010-12-28
Each time I start my Ubuntu 10.10, I notice this messages in dmesg:

[    3.133178] device-mapper: dm-raid45: initialized v0.2594b
[    3.249339] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    3.249346] EXT4-fs (sda6): write access will be enabled during recovery
[    3.551766] EXT4-fs (sda6): orphan cleanup on readonly fs
[    3.551779] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 524784
[    3.551869] EXT4-fs (sda6): 1 orphan inode deleted
[    3.551875] EXT4-fs (sda6): recovery complete
[    3.729759] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)


Each time the inode number is different. I made SMART tests on the disk, and all went fine. Do I have to worry? Could it be something related to a wrong shutdown?

**Update**: I have just ran an fsck at boot, but when I logged in, the same orphan_cleanup was in dmesg.

---

### Post by beruic on 2011-02-01
Don't know if you have to worry, but check bug [https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/672177](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/672177)

---

### Post by mikechant on 2011-02-25
I've been getting this issue on 10.04 (lucid) ever since I installed it, and although I guessed it wasn't due to 'real corruption' and carried on, it's always made me a bit uneasy.
I previously found all sorts of bugs/posts relating to orphan inodes but I couldn't really say which were relevant. 
The above link is quite reassuring - confirms that the orphan inodes are really a cleanup, not corruption issue, and that the problem is being worked on actively and is very near to being fixed in 10.04

---

