---
title: "DV1394 and RAW1394 permissions"
date: 2006-03-12
forum: Desktop Environments
---

### Post by phitilip on 2006-03-12
hi all ,


just switched my desktop to ubuntu a few days ago and i have to have say i am really swept of my feet on how nice this total environment "feels".

I have got almost everything that was on my Windows box working (without the virusses that is of course ;-) ) but there is one thing that does not work.

When i launch kino or dvgrab they provide following error.
raw1394 - failed to get handle: Permission denied.

Looking at the forum i noticed that this is probably due to wrong permissions on 
dev/dv1394
dev/raw1394

below the permissions i currently have ? What should i change and how ? Thnx


hombre@ubuntu:~$ ls -l /dev/raw1394
crw-rw----  1 root disk 171, 0 2006-03-12 06:18 /dev/raw1394
hombre@ubuntu:~$ ls -l /dev/dv1394
total 0
crw-rw----  1 root video 171, 32 2006-03-12 06:18 0
hombre@ubuntu:~$

---

### Post by Teren on 2006-03-12
sudo chmod a+rw /dev/raw1394 /dev/dv1394

---

### Post by phitilip on 2006-03-12
Seems to work thanks a lot !!

---

