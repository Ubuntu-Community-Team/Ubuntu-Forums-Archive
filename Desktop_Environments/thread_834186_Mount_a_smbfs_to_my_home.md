---
title: "Mount a smbfs to my home"
date: 2008-06-19
forum: Desktop Environments
---

### Post by Heiliger on 2008-06-19
Hi,

I have mounted a SMBFS (samba share) to my /home/xxx directory.
(done via fstab)
For some reasons the desktop environment does not run properly any more after doing this.

There seems to be issues reading or writing the .xxx config files via SMB.

File access works fine but when I start GDM I get several errors. And some applications do not work properly (e.g. firefox).

After 2 days of investigation I still have no idea what went wrong.

Any help?

This seems to be not an access right problem since access rights are the same in the network drive as in the original /home/xxx directory.

RGDS

Christian

---

### Post by drrob1 on 2008-06-19
My experience is slightly different.  I mount smbfs that points to a windowsXP share.  I do this from a command prompt.  I have found that it only works as root, that is, the mount command only works as root and I have to be root to access the share.  

I suggest you change fstab back and not automount it in fstab.

---

