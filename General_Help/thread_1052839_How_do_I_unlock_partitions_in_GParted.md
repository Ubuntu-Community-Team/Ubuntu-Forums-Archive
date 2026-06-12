---
title: "How do I unlock partitions in GParted"
date: 2009-01-28
forum: General Help
---

### Post by ozguitarplayer on 2009-01-28
Been looking at how to create partitions however GParted shows that all partitions in 3 hard drives are locked, even a 1 Gig flash/usb drive is locked,
how do I unlock them?

---

### Post by todak on 2009-01-28
Right click on the partition you want to unlock and then click **Unmount** in the menu that appears.

---

### Post by ozguitarplayer on 2009-01-28
many thanks, a simple fix, 

when I was looking around I saw the unmount but was too cautious to click it in case it had bad results...still haven't got mount/unmount sorted in my head,thought mounted was when the file was in use and unmounted the opposite...thanks again

---

### Post by ozguitarplayer on 2009-01-28
ummm how do I lock them again if I want to....?

---

### Post by todak on 2009-01-28
Mount them again. **Locked** does not necessarily mean that you cannot write to or alter any files in that partition, permissions takes care of that. A locked partition means you cannot do any partition operations on that particular partition. It means that it is locked by the system for use.

---

### Post by drs305 on 2009-01-28
> **ozguitarplayer said:**
> ummm how do I lock them again if I want to....?

In gparted, just select the partition, then Partitions, Mount (or Mount On). Any time the partition is mounted it is 'locked'.  So any way you can mount the partition it will be mounted and thus 'locked'. 

Other ways to mount the partition would be through the command line (if it's listed in fstab and not "noauto" you can simply run "sudo mount -a" to mount all partitions) or by clicking on a device in nautilus or another file browser.

---

### Post by ozguitarplayer on 2009-01-28
that's explained it, thankyouu both...

---

