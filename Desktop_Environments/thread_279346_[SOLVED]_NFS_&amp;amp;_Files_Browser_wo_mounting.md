---
title: "[SOLVED] NFS &amp;amp; Files Browser w/o mounting"
date: 2006-10-17
forum: Desktop Environments
---

### Post by wieman01 on 2006-10-17
Hey Guys, 

Is there any chance I can access another computer running NFS on the same network w/o having to mount the shared volume? SAMBA lets me do, all I need is a file browser [COLOR="Red"](smb://URL)[/COLOR].

Can I do the same when using NFS? The reason why I don't want to mount all the time is that I want to keep my environment dynamic in the sense that it should not matter which computer I boot first; I should be able to connect to the remote PC on the LAN without mounting & entering my root password.

SAMBA does a perfect job, but is sort of slow. Does NFS offer the same level of convenience?

---

### Post by wieman01 on 2006-10-18
Anybody?

---

### Post by wieman01 on 2006-10-20
Last try... Anybody?

---

### Post by mexlinux on 2006-10-21
There is an NFS kioslave, t should just work with nfs:// from konqueror

---

### Post by wieman01 on 2006-10-21
> **mexlinux said:**
> There is an NFS kioslave, t should just work with nfs:// from konqueror
Thanks a lot. I'll try that.

---

