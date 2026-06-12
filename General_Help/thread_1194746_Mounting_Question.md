---
title: "Mounting Question"
date: 2009-06-23
forum: General Help
---

### Post by measekite on 2009-06-23
I have a 2 partition on 2 separate drives.  I would like to mount both of them so I can see the data of both under /home.

Can I do this or will the second mount wipe out the first one?

---

### Post by rushikesh988 on 2009-06-23
why dont u try to go in  /media   or in /mount

---

### Post by Bucky Ball on 2009-06-23
You can't mount two partitions to the same mount point, as it is the DIRECTORY /media/your_mount_point_name, just as it would be /boot/grub/. It's treated pretty much the same. Consequently, if you had a /grub directory on another partition called /grub_other, you would wipe the first.

A partition is treated like a directory. You could put a short cut to the other partition on the second drive into the mounted /home on the first, or you may be able to wangle something with Symlinks. Or, you could just copy what you want into your /home directory and have a spare partition on the other drive!  Interested to see what people suggest.

---

### Post by 7raTEYdCql on 2009-06-23
You can probably figure out the name of the hard-drive which is mentioned in grub.

Then in home make a new dir say abc, 
then use 
mount abc "drive", which is what you should get in Grub. Don't remember the name of the file where it is mentioned(Because i am on a win machine now :( ). But it is a config file somewhere in /grub.

---

