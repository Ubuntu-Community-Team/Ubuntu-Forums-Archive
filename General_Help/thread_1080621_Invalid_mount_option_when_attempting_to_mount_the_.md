---
title: "Invalid mount option when attempting to mount the volume"
date: 2009-02-25
forum: General Help
---

### Post by sojojo on 2009-02-25
Here's exactly what I did to make some of my partitions unable to be mounted. I just don't know how to un-do it. 
I right clicked a partition of sdb on the desktop and selected properties and selected the volume tab. Under settings I typed noauto for mount options, because I didn't want the partition to mounted at start up and I didn't know whether the partition was sdb1, sdb2, etc. Basically I can't change the mount options because there's no volume tab (and its not listed in fstab). Its an external hdd if that changes anything for anyone. Thanks
-sojojo

---

### Post by ddrichardson on 2009-02-26
You can find the device by typing:
```
ls /dev/s*
```
Then connect it and type:
```
ls /dev/s*
```
Again. See which it is and mount it manually, then change the setting that was nadged,

---

