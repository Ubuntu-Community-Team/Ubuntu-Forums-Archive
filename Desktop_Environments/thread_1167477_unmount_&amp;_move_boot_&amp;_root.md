---
title: "unmount &amp; move /boot &amp; /root"
date: 2009-05-22
forum: Desktop Environments
---

### Post by bradhaack on 2009-05-22
I'm trying to reallocate my hard drive.  I'm using gparted.  I had a large fat32 partition which I have shrunk & would like to mount that unallocated space as /home.  I have 3 primary partitions & 1 extended partition.  I have unallocated space in front of the extended partition which is where linux /boot, /root & swap is.  I need to make that extended partition larger so I can create a /home partition out of the unallocated space.  But I need to unmount the extended partition in order to do that.  Can I unmount /root & the extende partition with crashing the system?  How?
Thanks

---

### Post by GOfree on 2009-05-22
You should probably make a GParted Live cd.

([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/))

That way you can partition your hard drive without mounting any partitions.

How many partitions are you trying to make? I believe there is a maximum of four.

---

