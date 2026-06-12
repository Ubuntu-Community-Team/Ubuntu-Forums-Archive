---
title: "command line partitioning"
date: 2006-09-05
forum: Desktop Environments
---

### Post by pwrstick on 2006-09-05
Hello,

I installed a USB2.0 HD and it seemed to go over just fine, mounted it ok and everything.  I could even browse to the directory where it was mounted and see "lost+found" and write to it (with sudo only, another story).

For fun I ran 'fdisk -l' and got the following:
```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table
matt@cottage:/mnt$
```

I'm confused because I can browse to and write to the drive, and I'm wondering if I need to run parted.  I'm command line only because it's a server install, and I'm also wondering if I properly partition it if I'll get to write to it without using 'sudo'.

Cheers!
-Phil

---

### Post by ciscosurfer on 2006-09-05
You can used fdisk to do what you want or parted or cfdisk or a bunch of other command-line tools.  To start, read the manual page for fdisk```
man fdisk
```

---

### Post by pwrstick on 2006-09-30
So I figured out what I was doing wrong.  I actually created a file system on a device without actually partitioning it first.  I'm a WinNub so my thinking wasn't clear.

Anyway, you have to first make a parition, and then create a file system, and finally mount the file system on that partition.

My new drive was '/dev/sda' so I ran 'sudo cfdisk /dev/sda' and created a primary partition.  So now I have a /dev/sda1

THEN I ran 'mkfs.ext3 -b 4096 /dev/sda1' which actually formats the new partition with a (suprise) ext3 file system.

After that you mount it as always.  I hope this is helpful to someone else that can't run gparted because they're ssh'ing in too :)

---

### Post by CatKiller on 2006-09-30
In addition to the fdisk programs, there is a program called parted that runs from the command line. I suspect, although I don't know for sure, that Gparted is a Gnome front-end for this program.

---

