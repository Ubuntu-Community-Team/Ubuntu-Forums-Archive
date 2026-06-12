---
title: "[SOLVED] Xubuntu and a FAT32 /home partition"
date: 2006-10-06
forum: Desktop Environments
---

### Post by altonbr on 2006-10-06
Ok.. so here's the deal. I'm installing the Beta2 version of Windows Vista over XP.

At the same time, I'm also installing Xubuntu over Ubuntu.

I tried to install Xubuntu and it couldn't mount my FAT32 data partition as /home... I never did this for Ubuntu.. but I was told I should and it was stupid not to. I originally mounted my data on /media/brett (that was annoying for the defaults in programs.. they always wanted to save to /home/brett)...

so anyway.. is this an irragular thing to do? I thought it's what alot of dual-booters do. Or how can I add Fat32 support into Xubuntu. I'm using the alternative CD for the record.

---

### Post by aysiu on 2006-10-07
You can use FAT32 as an additional *data* partition, but you cannot mount it as /home

/home is a special folder that has a lot of permissions, and FAT32 doesn't support user permissions.

Your best bet is to mount your FAT32 partition as /home/brett/data or /home/brett/storage

---

### Post by altonbr on 2006-10-07
Huh... I never knew. Thanks for the tidbit.

---

