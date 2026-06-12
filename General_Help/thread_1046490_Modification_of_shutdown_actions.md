---
title: "Modification of shutdown actions"
date: 2009-01-21
forum: General Help
---

### Post by grapouitte on 2009-01-21
Hello everyone

I installed Xubuntu on my eeePC 701, with /home mounted on a sd card. All goes well, works fine, except that it is not un-mounted at shutdown time. 

Is there any way I can add something like "umount /dev/sdc1" (the sd card) to the shutdown operation list? I've googled about that, and I couldn't find anything relevant. I also gave a look at pretty much every files in /boot, but couldn't find anything I dared modify. 

In case it is any relevant, I'm using adamm's kernel, [http://www.array.org/ubuntu](http://www.array.org/ubuntu)

Thanx!

---

### Post by HermanAB on 2009-01-21
Shutdown is runlevel 6.  So look in /etc/rc.d/rc6.d for the shutdown scripts.

Cheers,

Herman

---

