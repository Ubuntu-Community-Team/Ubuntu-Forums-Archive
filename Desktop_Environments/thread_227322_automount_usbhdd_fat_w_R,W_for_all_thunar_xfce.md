---
title: "automount usbhdd fat w/ R,W for all thunar xfce"
date: 2006-08-01
forum: Desktop Environments
---

### Post by sbmd on 2006-08-01
Hello I have xubuntu installed on an older p3 800mhz 384mb ram works great with xubuntu, but i am having some problems mounting it. and having read and write access. Can anyone shed some light on this? I have added an entry in fstab but i think I need some of the sets set right. I added my usrs gid and uid. Thanxk for all your help in advance.

---

### Post by encho on 2006-08-02
I thing problem is that in xfce pmount is in charge of handling the mounts. I do not think you need entry in fstab. Try to uncomment it, than type
> sudo chown sbmd:sbmd /media/sda1
and restart.

Of course, change sbmd with your user name, if different, and /media/sda1 with /media/smbd_usbdrive or similar if you labeled it.

---

### Post by sbmd on 2006-08-02
Thankx that did help. I guess I am needed to read more on thunar and xfce. Thankx alot.

---

