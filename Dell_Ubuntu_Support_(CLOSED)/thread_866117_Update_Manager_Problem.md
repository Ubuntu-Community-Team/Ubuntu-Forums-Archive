---
title: "Update Manager Problem"
date: 2008-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by darkmire on 2008-07-21
Hi

When I run Update Manager, I get a list of updates.  When I click on Install I get the following error message.


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E:_cache->open() failed, please report.

When I open a root terminal and run dpkg --configure -a I get the following.   

root@dell:/home/mark# dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-19-386 (2.6.24-19.34) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-386

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-386
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-19-386 (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.24-19-generic (2.6.24-19.34) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-386:
 linux-image-386 depends on linux-image-2.6.24-19-386; however:
  Package linux-image-2.6.24-19-386 is not configured yet.
dpkg: error processing linux-image-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.19.21); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-386:
 linux-ubuntu-modules-2.6.24-19-386 depends on linux-image-2.6.24-19-386; however:
  Package linux-image-2.6.24-19-386 is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-386 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: subprocess post-installation script returned error exit status 1

Does anyone know what the problem is?  How would I go about finding out what the dependency problems are and rectifying the problem?

I'm running Ubuntu 8.04 on a Dell Inspiron 6400

Thanks

Mark

---

### Post by Potatoj316 on 2008-07-21
I doubt it will work but try this instead.  In a normal (non root) terminal type ```
sudo dpkg --configure -a
```

---

### Post by darkmire on 2008-07-21
Same result again I'm afraid.

---

### Post by falcon61102 on 2008-07-21
Run and post this:
```
sudo fdisk -l
```

That will list your partitions and sizes.  The way that it keeps giving you an error about not enough space, it sounds as if you are running low on disk space for that partition.

---

### Post by darkmire on 2008-07-22
Details are as follows:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2              12         273     2104515    b  W95 FAT32
/dev/sda3   *         274         298      200812+  83  Linux
/dev/sda4             299       12161    95289547+   f  W95 Ext'd (LBA)
/dev/sda5             299         619     2578401   82  Linux swap / Solaris
/dev/sda6             620       12161    92711083+  83  Linux
mark@dell:~$

---

### Post by bapoumba on 2008-07-22
> gzip: stdout: No space left on device

Please run df -H to see which partition is full.

---

### Post by darkmire on 2008-07-25
OK I've done that and found that sda3 is the one that's full.  I presume that to free up space that I need to remove old kernel stuff.   I'm currently running the following:

Linux version 2.6.24-19-386 (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 Wed Jun 18 14:09:56 UTC 2008

I presume that I can't take on the kernel update because the disk space is full of older kernels.  Persumably I need to remove all kernel versions prior to 2.6.24-19-386 to free up the space?   Please could you give me some hints and tips on this.  I'm more comfortable using Synaptic tor remove old packages than the command line.

Thanks  
Mark

---

### Post by bapoumba on 2008-07-25
I suppose this is your root (/) partition. You can start with 
```
sudo apt-get clean
```
That will remove the downloaded packages files that have been installed (see man apt-get). It may free enough space. If not, you can remove kernels with synaptic (I usually keep one previous working kernel in addition to the current one).

---

### Post by darkmire on 2008-07-27
> **bapoumba said:**
> I suppose this is your root (/) partition. You can start with 
```
sudo apt-get clean
```
That will remove the downloaded packages files that have been installed (see man apt-get). It may free enough space. If not, you can remove kernels with synaptic (I usually keep one previous working kernel in addition to the current one).

I've tried that and no luck.  When I launch synaptic all I get is the error message I mentioned in my first post. I can't use synaptic until I solve the disk space problem but I can't solve the disk space problem because I can't use synaptic.   How else do I remove old kernels?

The problem is that Dell have installed Ubuntu so that all kernel files are in a different partition (sda3 which functions as /boot in the filesystem and is only 152 MBytes) to everything else which is in sda6.  This is irritating as other ubuntu setups I've done myself have always had /boot contained within the root partition.

All advice appreciated.  At least I'm learning something here!

Thanks

Mark

---

### Post by darkmire on 2008-07-30
> **darkmire said:**
> I've tried that and no luck.  When I launch synaptic all I get is the error message I mentioned in my first post. I can't use synaptic until I solve the disk space problem but I can't solve the disk space problem because I can't use synaptic.   How else do I remove old kernels?

The problem is that Dell have installed Ubuntu so that all kernel files are in a different partition (sda3 which functions as /boot in the filesystem and is only 152 MBytes) to everything else which is in sda6.  This is irritating as other ubuntu setups I've done myself have always had /boot contained within the root partition.

All advice appreciated.  At least I'm learning something here!

Thanks

Mark


OK all sorted.   I just deleted all the backup files for the old kernels which freed up some space, ran dpkg --configure -a which tidied everything up, then ran Synaptic to remove older kernels (there were five there - and four of them since I upgraded to 8.04) and now I'm down to two.

Many thanks to all who helped.

Mark

---

