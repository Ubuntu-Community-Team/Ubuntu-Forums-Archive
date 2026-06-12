---
title: "Need help to make my Ubuntu partition bigger."
date: 2006-01-14
forum: Desktop Environments
---

### Post by endangst on 2006-01-14
Hi!  Is there an easy to use program to make my Ubuntu partition bigger?

I currently dual-boot with Windows XP, but my Ubuntu partition is running out of space!  I think I don't have enough space in my Ubuntu partition for swap anymore.  I have less than 300MB left I think.

Thanks in advance for your help and suggestions.  I appreciate it very much.

---

### Post by jsmidt on 2006-01-14
If you are willing to back up the files you want to save, the easiest way is to reinstall both OS's with different partition sizes.  I say this is the easiest because if you are not careful you might distroy your computer by mearly changing partition sizes.

---

### Post by j-a-p on 2006-01-14
It sounds as though you need to split up your installation in to more partitions. If you only have a / (root) partition then you should at least create another partition and mount it at /home.

In order to do this you need to:

1. Create a new partition (like /dev/hda3) using fdisk or cfdisk.
2. Make a filesystem on the new partition using mke2fs.
3. Temporarily mount the new partition, at /mnt perhaps.
4. Copy all files under /home to /mnt
5. Edit /etc/fstab to change the filesystem mounted at /home to /dev/hda3
6. Reboot.

This is a bit of  a rough guide, but that is pretty much the gist of it.

Another thing to look at would be Logical Volume Management (LVM2). This allows you to change the size of Logical Volumes on the fly.

---

