---
title: "resize ext2 inode size"
date: 2009-04-20
forum: General Help
---

### Post by dnaxx on 2009-04-20
Hello!

I have created a ext2 partition with gparted but the inode size is 256. I need to change the size to 128, so that I can access the partition from Windows XP with the ext2 driver.

How can the inode size be changed (if possible, without data loss on the partition)?

Regards,

---

### Post by harlock592 on 2009-05-24
Hello,
 
i also need to do that.

---

### Post by ihatethetv on 2009-07-08
me three. i need that too

---

### Post by ihatethetv on 2009-07-08
It looks like this can't be done in-place, i.e. without destroying the partition and reformatting...but that's fine with me

I moved my data off and then did this:

1> figure out mount point of device

I went into gparted and noted the mount point and the device.  

Note: this isn't ideal, I'd like to hear a better way to do this, I can't think of one off the top of my head.

2>unmount partition

sudo umount /dev/sd(whatever)

3> use mkfs.ext3 to recreate a ext3 partition on the partition

sudo mkfs.ext3 -I 128 /dev/sdb1

note: the -I 128 is the important part, it says to create 128-sized inodes.  I fooled around with the damned -i option and couldn't figure that one out.

found the info here:

[http://handyfloss.net/2009.07/accessing-linux-ext2ext3-partitions-from-ms-windows/]("http://handyfloss.net/2009.07/accessing-linux-ext2ext3-partitions-from-ms-windows/")

---

