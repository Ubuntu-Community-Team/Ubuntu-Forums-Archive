---
title: "Problem mounting system partitions in rescue mode"
date: 2021-12-11
forum: Fedora/RedHat and derivatives
---

### Post by uaj380 on 2021-12-11
I have a serious problem.
Server crashed and not returned, disk problems.
I'm trying to mount `/dev/vg/root` partition
to access and remove the files but it's giving me a superblock error.


Until yesterday I was able to access it in read-only mode
using the command below.
```
mount -o ro,noload /dev/vg/root /mnt
```
But now not even this command works anymore because of the error.
I tried to recover the corrupted block without success.
The operating system know that all I need is access to the location -/dev/vg/root to remove our data.


Doing some checks at least the files are still allocated on the disk;
the problem is to access the location that is no longer visible for mounting.
```
mount /dev/vg/root /mnt
mount: /mnt: wrong fs type, bad option, bad superblock on /dev/mapper/vg-root, missing codepage or helper program, or other error.


mount -o ro,noload /dev/vg/root /mnt
mount: /mnt: mount(2) system call failed: Stale file handle.
```
LVM used partition system


System where the server was installed: CentOS 6.9.


System I'm currently accessing in rescue mode.
```
Linux rescue 5.13.13 #1 SMP Thu Oct 28 09:11:58 UTC 2021 x86_64 GNU/Linux
```
partition scheme (output from `lsblk`):
```
NAME          MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
loop0           7:0    0  2.9G  1 loop
sda             8:0    0  2.7T  0 disk
&#9500;&#9472;sda1          8:1    0    2G  0 part
&#9474; &#9500;&#9472;md0         9:0    0    2G  0 raid1
&#9500;&#9472;sda2          8:2    0  2.7T  0 part
&#9474; &#9492;&#9472;md1         9:1    0  5.5T  0 raid0
&#9474;   &#9500;&#9472;vg-root 253:0    0  5.4T  0 lvm
&#9474;   &#9492;&#9472;vg-swap 253:1    0    4G  0 lvm
&#9492;&#9472;sda3          8:3    0    1M  0 part
sdb             8:16   0  2.7T  0 disk
&#9500;&#9472;sdb1          8:17   0    2G  0 part
&#9474; &#9500;&#9472;md0         9:0    0    2G  0 raid1
&#9500;&#9472;sdb2          8:18   0  2.7T  0 part
&#9474; &#9492;&#9472;md1         9:1    0  5.5T  0 raid0
&#9474;   &#9500;&#9472;vg-root 253:0    0  5.4T  0 lvm
&#9474;   &#9492;&#9472;vg-swap 253:1    0    4G  0 lvm
&#9492;&#9472;sdb3          8:19   0    1M  0 part
```


Tried solutions like recovering bad blocks
```
sudo mke2fs -n /dev/xx


Failed attempt to recover bad blocks
sudo e2fsck -b 32768 /dev/vg/root
```
Location I am trying to access,
which is where CentOS 6.9 is installed: `/dev/vg/root` 
The backup data I need is in this location.

---

### Post by howefield on 2021-12-11
Thread moved to the "*Fedora/RedHat and derivatives*" forum.

---

