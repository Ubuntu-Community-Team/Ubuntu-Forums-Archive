---
title: "Unable to unmount ext3 partition w/ gparted livecd"
date: 2006-07-02
forum: Desktop Environments
---

### Post by zahidism on 2006-07-02
Hi, I'd like to remove ubuntu from my laptop and I'm going to put it on my desktop but I'd like to revert back to the XP on my laptop.  My hard drive has a windows ntfs partition and a linux extended partition w/ an ext3 and a fat32 drive partition.  so i fixed the MBR to load windows, and now i want to run gparted off the livecd to basically whipe out the other partitions and resize my windows to the max hard drive capacity.  only problem is when i use gparted on livecd it says my ext3 and swap are "in use" and they have a lock next to them and i cant unmount them.

---

### Post by Jagot on 2006-07-02
In terminal you could try this:

```
sudo umount /dev/hda3
```

Changing the hda3 as appropriate.

---

