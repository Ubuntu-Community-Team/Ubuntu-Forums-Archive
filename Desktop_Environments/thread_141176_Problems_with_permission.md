---
title: "Problems with permission"
date: 2006-03-07
forum: Desktop Environments
---

### Post by ubuntukid on 2006-03-07
Ok. I`ve got a second harddrive mounted on my desktop in a folder called HDB. Now for some reason only the root user. So how do I change the permission so that I can use it without being root?

---

### Post by Sutekh on 2006-03-07
Is it a Windows formatted hard drive?  (NTFS and FAT)

[http://www.psychocats.net/linux/mountwindows.php]("http://www.psychocats.net/linux/mountwindows.php")

Will change the permission to allow full access for FAT partitions and read/execute access for NTFS partitions

---

### Post by ubuntukid on 2006-03-07
It's Extended 3 but theres nothing on it so I can easily reformat it if I need to. I just want to be able to access it as my own disk.

---

### Post by aysiu on 2006-03-07
If it's Ext3, just mount it using defaults and then either *chown* or *chmod* it. For example, if it's mounted at /extra_drive, type ```
sudo chown -R ubuntukid:ubuntukid /extra_drive
```

---

