---
title: "Umount problem with Samba"
date: 2005-08-26
forum: Desktop Environments
---

### Post by Lapino on 2005-08-26
I'm using Samba to make a connection between my laptop (hoary) and my desktop (windows xp sp2).
I added the following line to my /etc/fstab file:

```
//bart/share /home/bart/network	smbfs   user,noauto,username=guest,password= 	0	0
```
When I use
```
mount /home/bart/network
``` 
there's no problems, everything works ok, but when I try to unmount the drive using:
```
umount /home/bart/network
``` 
I get an error message saying 
umount: only root can unmount //bart/share from /home/bart/network

Strange thing is, when I use smbumount instead of umount, everything works fine.

I'd like to use mount and umount, so I can easily mount the network drives in rox.

Anyone has an idea?

edit: woops, wrong thread, please move...

---

### Post by amohanty on 2005-08-27
I believe that because smbumount is a suexec-ed helper app for smbmount or somethign to that effect. do an ls -l /usr/bin/smbumount and google for suid bit and smbfs.

HTH
AM

---

