---
title: "ntfs wont mount automatically"
date: 2010-03-30
forum: Desktop Environments
---

### Post by mkartic on 2010-03-30
hi, i recently installed xfce and xmonad in my foray into alternate desktop environments. I have a small issue, hope someone can help me out.

I have a couple of ntfs partitions, they get automatically mounted when i go into gnome. But not in the other two. I have to open thunar and click on their names to mount them. Is there any way to fix this? 'sudo mount -a' doesn't work as they're not in fstab.

---

### Post by TitanusEramius on 2010-03-31
To make "mount -a" and automount work you have to make a line for the harddisk in fstab. If you are in doubt about how to write in fstab, then take a look at this:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

The line you have to make might look something like this:
```
UUID=XXXXXXXXXXXXXXXX /mount/point ntfs-3g defaults 0 0
```You might have to change "defaults", but if I should guess, the harddisk should be automounted with that line. Also, instead of UUID you can use /dev/hd** to point to your harddisk, but UUID will work even if the harddisk changes place in the computer. You can find a harddisks or partitions UUID by using "sudo blkid" in the terminal.

Good luck

---

