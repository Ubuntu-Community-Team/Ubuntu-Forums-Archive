---
title: "Screwed up my fstab..."
date: 2008-02-24
forum: Desktop Environments
---

### Post by burgerearl on 2008-02-24
I was trying to make my windows and dell utilities partitions disappear by mounting them to /mnt instead of /media (changed the mount point in fstab).

Now I can't find (in places, computer, /dev) or mount (mount /dev/sda2 /mnt doesn't return an error or mount that partition) some of my partitions. I thought I made a backup of fstab, but changing fstab back to the backup doesn't change anything. I'm not 100% confident my backup is correct as I started editing before backing up (subsequently undid all changes and saved a backup).

Is there any way I can regenerate a default fstab to get my system back to the previous state?

Thanks for any help, next time I'll make sure to backup correctly...

---

### Post by rapiscan on 2008-02-24
If you have the live cd, you can try booting into the live cd and copying the fstab from there.

---

