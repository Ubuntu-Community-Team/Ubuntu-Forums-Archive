---
title: "How do I mount drives as read/write ?"
date: 2005-04-12
forum: Desktop Environments
---

### Post by Rockrol913 on 2005-04-12
I am having a problem mounting my removable drives as read / write. I can read and play the files on both of my external drives, but I can't delete a file if I want. All the files are mounted as read only and that's it ...
THANX in advance for any help :)

---

### Post by abhaysahai on 2005-04-12
Unmount the device.
mount -o rw /device /mountpoint. 
This should work.

---

### Post by devil28 on 2005-04-13
you could also edit etc/fstab as root. you have to change the argument "ro" to "rw" in the lines for your partitions. that will make it permanent. (I hope this works for removables as well,but it should.) If the drive is ntfs,writeing is not such a good idea, because still unstable due to ms .

---

