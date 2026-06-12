---
title: "Drive space &amp; tune2fs"
date: 2008-12-04
forum: General Help
---

### Post by Aenima99x on 2008-12-04
I recently installed a second HDD in my HTPC for all my movies. Both drives in the system are Western Digital 1 TB. I've formated the new drive as ext3 with Gparted showing the available space as 931.51 GB - ok looks good. 
When I create the single partition using all drive space, it changes to 931.51 GB total with 14.81 GB used and 916.70 Unused.
Ok I thought it was the 5% being reserved for the super user, so I run ```
sudo tune2fs -m 1 /dev/sdb1
``` 
It says it changes the reserved amount and does show the reserved block count now at 1%, however Gparted still shows that 14.81 GB used. There is nothing on the drive except for the Lost+Found folder, which is completely empty (no hidden files). 
Any ideas where this 14.81 GB has gone???

---

### Post by TeXtonyx on 2008-12-04
Could it be one of those GB versus GiB, 1024 or 1000, discrepancies?

---

### Post by Aenima99x on 2008-12-04
That would account for the 1 TB drive showing as 931.51 GB, but not for the 14.81 GB of used space on an empty drive. :confused:

---

### Post by jayaprakash_ece on 2008-12-18
> **Aenima99x said:**
> I recently installed a second HDD in my HTPC for all my movies. Both drives in the system are Western Digital 1 TB. I've formated the new drive as ext3 with Gparted showing the available space as 931.51 GB - ok looks good. 
When I create the single partition using all drive space, it changes to 931.51 GB total with 14.81 GB used and 916.70 Unused.
Ok I thought it was the 5% being reserved for the super user, so I run ```
sudo tune2fs -m 1 /dev/sdb1
``` 
It says it changes the reserved amount and does show the reserved block count now at 1%, however Gparted still shows that 14.81 GB used. There is nothing on the drive except for the Lost+Found folder, which is completely empty (no hidden files). 
Any ideas where this 14.81 GB has gone???
I just bought a Samsung F1 spinpoint 1 TB drive yesterday and have the same problem.. Don't know why I am still missing around 15 GiB despite reclaiming the lost space using tune2fs command. If you managed to find a solution, please do let me know.. Thanks.. :)

---

