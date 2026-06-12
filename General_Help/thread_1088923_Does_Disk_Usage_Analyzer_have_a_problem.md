---
title: "Does Disk Usage Analyzer have a problem?"
date: 2009-03-06
forum: General Help
---

### Post by desconocido on 2009-03-06
My hard disk is 80 GB nominal. The line in the attached screenshot that says "Total filesystem capacity" seems to double the actual numbers.

---

### Post by mªrty on 2009-03-06
"Total" means everything connected to the system. do you have another hard drive, internal or USB, connected?

---

### Post by blackened on 2009-03-06
On my machines it includes mounted network drives in the total as well.

---

### Post by desconocido on 2009-03-09
> **mªrty said:**
> "Total" means everything connected to the system. do you have another hard drive, internal or USB, connected?

No, no other drives, no network. Default install of Hardy Heron with security updates.

df output:
```
df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             74551324   9966076  60828048  15% /
varrun                  512916       116    512800   1% /var/run
varlock                 512916         0    512916   0% /var/lock
udev                    512916        52    512864   1% /dev
devshm                  512916        12    512904   1% /dev/shm
lrm                     512916     39788    473128   8% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon      74551324   9966076  60828048  15% /home/bob/.gvfs
```

---

### Post by Yashiro on 2009-03-09
Remove gvfs-fuse-daemon from the scan. It's a virtual mirror of your current file system but the Disk Analyzer does not know this in advance.

---

### Post by desconocido on 2009-03-11
> **Yashiro said:**
> Remove gvfs-fuse-daemon from the scan. It's a virtual mirror of your current file system but the Disk Analyzer does not know this in advance.

Hmmm, as both gvfs-fuse and Disk Analyzer came as standard in the default installation of Ubuntu, it's a pity they don't know about each other.

---

### Post by desconocido on 2010-08-14
Disk Usage Analyzer fixed in Karmic 9.10.

---

