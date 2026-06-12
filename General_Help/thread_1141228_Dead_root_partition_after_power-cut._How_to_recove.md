---
title: "Dead root partition after power-cut. How to recover?"
date: 2009-04-28
forum: General Help
---

### Post by yesint on 2009-04-28
Dear All,
I've got a power-cut during boot-up. After that "the root partition could not be mounted". Rescue mode does not help. It seems that the file system in the root partition is completely dead. 
Reinstall is not really a problem because all data are in a separate /home partition, which is alive, but I'd like to do something more smart than this. Is there any way to recover without reinstalling the system?

---

### Post by zeex on 2009-04-28
> **yesint said:**
> Dear All,
I've got a power-cut during boot-up. After that "the root partition could not be mounted". Rescue mode does not help. It seems that the file system in the root partition is completely dead. 
Reinstall is not really a problem because all data are in a separate /home partition, which is alive, but I'd like to do something more smart than this. Is there any way to recover without reinstalling the system?

Hi, 

Boot from a live CD and see if you are able to mount the root partition. Run fsck on /. See the manual for fsck ( **$ man fsck **) if you need more info. 

Post the content of /etc/fstab 

fsck should repair any damage to filesystem. Try it and post the contents of fstab.

---

### Post by yesint on 2009-04-28
Thanks! I'll try

---

