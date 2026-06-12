---
title: "Can't run programs from Windows partition"
date: 2006-06-12
forum: Desktop Environments
---

### Post by jflash on 2006-06-12
Back when I was running Breezy Badger, I mounted my Windows partition in Ubuntu so I could access files, etc. Now, however, I can even read the partition from Ubuntu, much less run programs from it or write to it. I have tried unmounting it and remounting it with the -rw command, but that did nothing to help me. When I look at it's properties, it is shown as root (owner) having read/write permissions, but that's it. Can anyone help?

---

### Post by taurus on 2006-06-12
Did you mount it from /etc/fstab?  What does /etc/fstab look like then?

---

### Post by ayoli on 2006-06-12
your windows partition is mounted as root you can try a line in fstab like:

/your/partition/win    /mount/point  auto user gid=your_group_id   0   0

(my group id is 1001 for ex, you can check it in /etc/group)

---

### Post by davidsxls on 2006-06-12
or... it's an NTFS?

---

### Post by ayoli on 2006-06-12
if it's ntfs CONFIG_NTFS_RW kernel option must be set to yes if ou want to be able to write. this option seems to be unset by default.

---

### Post by jflash on 2006-06-12
It's NTFS. How can I access the CONFIG_NTFS_RW option?

---

### Post by ayoli on 2006-06-12
maybe there is a way with:  echo 1 > /proc/where/the/option/is
the other way is recompiling your kernel after changing the option in config file (with make menuconfig for ex)

---

### Post by bulldog on 2006-06-12
Writing from Ubuntu to a NTFS file system is not something that is common to do.:confused: 
You could make a mess before you know it and I should think twice before I do so.
NTFS read is fully supported however and should be no problem.
Better to make a vFat partition to exange programs or whatever with your Windows Install.

---

