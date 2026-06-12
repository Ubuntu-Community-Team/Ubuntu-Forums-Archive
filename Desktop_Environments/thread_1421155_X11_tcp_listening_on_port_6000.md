---
title: "X11 tcp listening on port 6000"
date: 2010-03-03
forum: Desktop Environments
---

### Post by paradox_qu on 2010-03-03
I am trying to setup Xdmx on my desktop and an old laptop.  

I need to turn on X11 tcp listening on port 6000.  I commented out -nolisten tcp in /etc/X11/xinit/xserverrc but when I do nmap port 6000 is still not open. 

If I stop gdm and just run X and then do name I can see that port 6000 is open but when I start gdm port 6000 is closed.  I figured that somewhere gdm is closing the port but I can't figure out where.

Any help is appreciated.

-Nick

---

### Post by paradox_qu on 2010-03-04
Never mind I got it working over ssh.  But if anyone know how to speed up Xdmx I would like to know.  I am already using blowfish, if you know anything else please share.

---

