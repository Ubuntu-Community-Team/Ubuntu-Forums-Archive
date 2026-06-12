---
title: "Backup Solution - Partition Images"
date: 2008-03-29
forum: Desktop Environments
---

### Post by explosive on 2008-03-29
Hi,

I am looking for suggestions for a good backup solution.

I have just implemented software RAID 1 on my Ubuntu 7.10 installation to guard against hard disk failure. Previously I did weekly partition images of my /home partition using partimage and stored them on a removable hard disk. 

Does anyone have any suggestions of the best way of backing up my files? If I unmount my /home and then take an image with partimage will this mess up the running RAID config?

---

### Post by trippinnik on 2008-03-30
You could use something like Keeper.  It doesn't backup to partition image, but it will automatically grab all the files and back them up at specified intervals.  It uses rdiff-backup so it will save changes so you can revert back to a certain backup.

---

### Post by explosive on 2008-03-30
Do you have a link to keeper? I cant seem to find any info on google.

---

