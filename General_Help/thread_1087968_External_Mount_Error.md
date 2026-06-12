---
title: "External Mount Error"
date: 2009-03-05
forum: General Help
---

### Post by hismindkills on 2009-03-05
So, I'm having problems mounting my external HD.  I get the following when I put in ```
sudo fdis -l
df -h 
```:

```

mhundley@mhundley-laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x475a4759

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux
mhundley@mhundley-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  7.7G   26G  24% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  220K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  976K  500M   1% /dev/shm
lrm                   501M  2.0M  499M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1             230G   60M  218G   1% /media/disk

```

So, it's mounted (I think) but it says I don't have permissions to add/edit/do anything to files on there.  Not sure what to do to resolve the issue.

---

### Post by taurus on 2009-03-05
You just need to change the ownership of /media/disk from root to your login name, mhundley.

```
sudo chown -R mhundley:mhundley /media/disk
ls -la /media
```

---

