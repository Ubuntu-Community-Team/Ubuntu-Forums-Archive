---
title: "mount.nfs: internal error - any solutions?"
date: 2009-01-05
forum: General Help
---

### Post by bluepowder7 on 2009-01-05
desktop running recently updated 8.04-64, and file server running updated 7.10-32 (both updates done as "sudo aptitude safe-upgrade" two days ago).

when trying to mount the file server's drive to my desktop (using "sudo mount server:/storage_drive /desktop_mount_point"), i get the now-infamous

**mount.nfs: internal error**

message.

i haven't done any specific updates to nfs, or config changes, so should i be doing something to enable the nfs'ing to work?  or can i install an older version of nfs on either the server or desktop (or both)?  or is it a kernel issue?

---

### Post by bluepowder7 on 2009-01-06
.

---

### Post by bluepowder7 on 2009-01-07
eh bump?

---

### Post by bluepowder7 on 2009-01-11
last kick at the dog?

---

### Post by ille on 2009-01-22
Yesterday I've done an upgrade om my laptop to 8.10 and I also get the nfs internal error when trying to mount my mythbuntu 7.10 nfs share. 

Another laptop (eeepc 901) running xandros mounts the share without problem.

Googling around I found this bug, [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/213444](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/213444)

Seems alot of people have problem with nfs in ubuntu.

---

