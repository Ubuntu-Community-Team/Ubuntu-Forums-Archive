---
title: "Easy way to rewrite CD/DVD (umount problem)"
date: 2007-02-25
forum: Desktop Environments
---

### Post by ildella on 2007-02-25
I need to format and rewrite a DVD. Gnomebaker fails cause it cannot umount the rewritable drive cause:
1. it is not in fstab
2. process is not runned by root. 

BTW, It was easy to run gnomebaker from sudo and make everything works, but I am wondering about people who does not know what that message means and simply tell "this does not work". 

It is true that it is not in fstab. My dvd are automounted from default and Control Center options just allow me to open some program or natuilus. 
I do not want to disable automount, but there should be a way to format a RW disc without running gnomebaker or such as sudo or, worsk, umounting it. 

anyone knows?

---

### Post by shareMenaPeace on 2007-02-25
On a sidenote as gnome baker is a graphical interface it should be

```
gksudo 
```i think ...

And soud slike a permission think, well i have not much of idea maybe you need to chown the DVD device to your username.
> 
sudo chown username /media/DVDDEVICE

No idea if this would work or is a security think maybe someone else can commet on this.

---

