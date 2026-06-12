---
title: "How do i create a FAT32 disk in Gnome"
date: 2005-12-13
forum: General Help
---

### Post by skivan on 2005-12-13
Hi!

Does anyone know how to create or edit a FAT32 disk in Gnome, when I installed Ubuntu I had 2 discs in the computer and after the installation I reallised that it would have been better if one of them was a FAT32 disc so that windows can read and write to it.

Thanks!

// Magnus

---

### Post by kosmic on 2005-12-13
If you want an easy way, just fire up synaptic and install Gparted, it's a very good partitionig program and can do what you are asking :)

---

### Post by Leif on 2005-12-13
try gparted

---

### Post by skivan on 2005-12-13
Thanks! I will try that! :D

---

### Post by Thunk on 2005-12-13
Anyway, you can always install this driver in windows:

[URL="http://www.fs-driver.org/"]
http://www.fs-driver.org/[/URL]

It will enable windows to access your EXT2/EXT3 partitions.

This might be easier than re-partitioning.

---

### Post by frodon on 2005-12-13
yes, but only the read support is reliable with ext2/ext3 windows drivers, so it's not a complete solution.

---

### Post by Thunk on 2005-12-13
You're right about that. It all depends on the level of access you need...

Correction:
the driver in [www.fs-driver.org](www.fs-driver.org) will enable BOTH reading and writing.

---

