---
title: "fsck.ext3: Device or resource busy while trying to open /dev/sda5"
date: 2009-02-15
forum: General Help
---

### Post by JamieKitson on 2009-02-15
Hi,

I canceled a read-only gparted operation and am now getting:

ubuntu@ubuntu:~$ sudo fsck.ext3 -b 32768 /dev/sda5
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?

the drive is not mounted and I've tried rebooting (I'm using a live cd) but to no avail. Any thoughts?

(I am using the -b option as otherwise I get:

ubuntu@ubuntu:~$ sudo fsck.ext3 /dev/sda5
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Superblock invalid, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/sda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

I found the superblock using mke2fs -n)

Thanks, Jamie Kitson

---

### Post by JamieKitson on 2009-02-16
In the end I deleted the partition and then used TestDisk to recover it, which worked. However it shrunk my extended partition to the same size and lost my swap partition which was also in it, so be careful!

---

