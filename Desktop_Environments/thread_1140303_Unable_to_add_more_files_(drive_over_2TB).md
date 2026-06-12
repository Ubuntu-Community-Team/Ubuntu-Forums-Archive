---
title: "Unable to add more files (drive over 2TB)"
date: 2009-04-27
forum: Desktop Environments
---

### Post by nosebreaker on 2009-04-27
This is on kubuntu 7.10 (LinuxMCE, but I stopped the services for now)
100GB for OS (sda)
2.7TB for media (sdb)

I've got a strange problem, I have about 350GB of media, and for some reason I can't copy more files due to an IO error.  I also cannot run fsck on the volume because it is over 2TB, and it has issues with that apparently.  For some reason, I couldn't copy more files onto the volume.

So I backed up the data from the 2.7TB volume, and reformatted it as ext3 (it was ext2).

When I copy the data back, I get about 30% through before it fails due to the I/O device error.  The error is very generic, I will update once I get the exact message.  Any thoughts?

This is what it says in dmesg:
> 
[ 9014.104000] EXT3 FS on sdb1, internal journal
[ 9014.104000] EXT3-fs: mounted filesystem with ordered data mode.
[ 9123.320000] attempt to access beyond end of device
[ 9123.320000] sdb1: rw=0, want=1195900944, limit=1144934334
[ 9123.320000] EXT3-fs error (device sdb1): read_inode_bitmap: Cannot read inode bitmap - block_group = 4562, inode_bitmap = 149487617
[ 9123.324000] EXT3-fs error (device sdb1) in ext3_new_inode: IO failure

In the above instance, sdb1 is the 2.7TB volume and sdc1 is the 500G usb drive.

And if I run fsck:
> 
e2fsck 1.40.2 (12-Jul-2007)
The filesystem size (according to the superblock) is 679987703 blocks
The physical size of the device is 143116791 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no


---

### Post by Flareside on 2009-04-27
Nevermind, I just finished reading your post.

---

### Post by nosebreaker on 2009-04-29
I figured it out.  The reason why I couldn't add more files was due to a filesystem error, I ran e2fsck and it fixed it.  But before I could run e2fsck I had to change the label type from msdos to gpt with parted and I reformatted it as ext3 again.

---

