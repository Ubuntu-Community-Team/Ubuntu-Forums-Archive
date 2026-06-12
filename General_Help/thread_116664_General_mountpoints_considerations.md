---
title: "General mountpoints considerations"
date: 2006-01-13
forum: General Help
---

### Post by pt78 on 2006-01-13
Hallo all,

as I'm more linux advanced user than export I would like to share my situation and ask other users and experts for their opinion. 

I installed Ubuntu jest recently and I'm quite satisfied with it. Even despite missing synchronization tools with Pocket PCs this is finally distribution worth using instead of windows. 

I installed Ubuntu on 80GB drive. I deleted 15GB primary WXP partition and created partitions for /, /boot, /home and swap partition in this 15 GB space. I left extended partition untouched. After trying Ubuntu and configuring necessary tools I would like to delete convert logical drives to ext3 and mount them somewhere. And this is the point. Rest of hard drive should contain files accessible for all computer users. I was thinking about mounting to /home/public and /home/multimedia. However these are not usual mount points. As I'm not expert I would like to ask others about their pros and cons of doing so.

Thanks for ideas.

---

### Post by kosmic on 2006-01-13
How can mount them em /media and make it Read, Write, Execute to everyone with the comand chmod 777

---

### Post by pt78 on 2006-01-13
[QUOTE=kosmic]How can mount them em /media and make it Read, Write, Execute to everyone with the comand chmod 777[/QUOTE]

Of course I could do so... But my question was more about "Why shouldn't I mount it to /home/multimedia or /home/public?"

---

### Post by aysiu on 2006-01-13
As long as you chmod the folder properly, it really doesn't matter where you put the mount point.

---

