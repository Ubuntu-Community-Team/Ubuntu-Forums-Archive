---
title: "Changing drives checked by fsck..."
date: 2009-01-17
forum: General Help
---

### Post by akshay.sulakhe on 2009-01-17
Hello friends,i have installed Ubuntu 8.10 X64 for quite a while...until recently i installed Fedora10 and used one of the drive which was not used by Ubuntu at all and was not assigned a mountpoint...but now when i start up Ubuntu it gives me error saying fsck failed for /dev/sda6..a maintainance schedule is started after which i manually press ctrl+d..and it comes back..no problem then..so how can i tell fsck not to check my /dev/sda6 drive..is there any configuration file which i need to edit...please reply...Thanks...Enjoy life...:guitar:

---

### Post by drs305 on 2009-01-17
> **akshay.sulakhe said:**
> so how can i tell fsck not to check my /dev/sda6 drive..is there any configuration file which i need to edit...please reply...Thanks

Edit fstab and on the line listing /dev/sda6 (or the equivalent UUID) change the last entry to **0**. This will disable fsck checking on that partition.

Example:
```

/dev/sda6  	/mydata  	ext3  	defaults  	0 **0**

```

To edit fstab, make a backup and then open with a text editor such as gedit:
```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```
Edit the file, then save and close.

---

### Post by akshay.sulakhe on 2009-01-17
will surely do that..thanks very much...also where can i get details as to what those 0,1,2 stand for and their combination...Thanks again...

---

### Post by drs305 on 2009-01-18
> **akshay.sulakhe said:**
> ...also where can i get details as to what those 0,1,2 stand for and their combination...

The man pages for stab discuss the fsck check. 1 is for the root filesystem, 2 for other file systems and if 0 or omitted the file system will not be checked.

To read about it (near the bottom of the entry):
```

man fstab

```
If you want to learn more about fsck, it has it's own man page as well.

Welcome to the ubuntu forums.

---

### Post by mcduck on 2009-01-18
> **akshay.sulakhe said:**
> will surely do that..thanks very much...also where can i get details as to what those 0,1,2 stand for and their combination...Thanks again...

"0" means that the partition should not be checked at all.

Other numbers tell the order in which the partitions are checked. "1" should be only used for root partition, for all others use "2" to check them after root.

---

