---
title: "NAS Permissions"
date: 2009-04-21
forum: General Help
---

### Post by bgotro on 2009-04-21
I have a D-Link DNS323 on my network and have been able to create a volume that is seen by Ubuntu 8.10. This NAS is also successfully accessed by a Windows Vista laptop and another laptop in the house running Windows XP. My problem in Ubuntu is that, while I can access all the files, I am unable to save a file after modifying it. I believe the problem has something to do with permissions. When I run 'ls -l' (without the quotes, here is what I get:

drwxr-xr-x 2 bill bill 4096 2009-04-20 20:02 Desktop
drwxrwxrwx 9 root root    0 2009-04-18 20:49 DNS323

I believe I need to change the 'root root' to 'bill bill' to allow me to fully access this volume. Is that correct and, if so, how can accomplish this? Thanks for any help!

---

### Post by StuartN on 2009-04-21
chown bill:bill DNS323

---

### Post by bgotro on 2009-04-21
> **StuartN said:**
> chown bill:bill DNS323

Thanks, Stuart, but this command doesn't work as, for some reason, Ubuntu doesn't see DNS323 as a directory even though it's displayed as a folder in the File Browser!

Is anyone running a NAS with Ubuntu 8.10?

---

### Post by jeremy on 2009-05-23
DNS-323 1.08 beta firmware at:

[http://forums.dlink.com/index.php?topic=5485.0](http://forums.dlink.com/index.php?topic=5485.0) 

Lots of fixes and features including NFS support!

---

