---
title: "Where can I change GMT / Local time ?"
date: 2005-12-23
forum: Desktop Environments
---

### Post by Azmodan on 2005-12-23
I installed Kubuntu on my father's computer but he uses Windows too.  By default, the install set the clock to GMT but Windows doesn't like it.  Is there some file I can modify so Kubuntu sets the hardware clock to local time instead ?

Thanks

---

### Post by wylfing on 2005-12-23
The short answer is Yes, this is possible. I don't know how to make it happen inside KDE, because it's been a few years since I used it and all my KDE knowledge is out of date. However, see here:

[http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-time.html](http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-time.html)

Specifically, this:
> To change the computer to use UTC after installation, edit the file /etc/default/rcS, change the variable UTC to no. 

HTH

---

