---
title: "Help with installing programs"
date: 2009-06-03
forum: General Help
---

### Post by Ldub314 on 2009-06-03
Ok so I'm new to ubuntu and when i try to install application using add/remove i get Unable to get exclusive lock this usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.So i go to system manger and look for apt-get or aptittude and i dont see it.

---

### Post by michy99 on 2009-06-03
Also, Synaptic Package Manager cannot be running. apt-get and aptitude are terminal (command line) applications.

---

### Post by Soul-Sing on 2009-06-03
```
sudo dpkg --configure -a
``` in the terminal

or system : systemmonitor: processes
you could look if there is proces running on the background like -apt /aptitude....

---

### Post by Ldub314 on 2009-06-03
when i do that i get dpkg: status database area is locked by another process

---

### Post by DeMus on 2009-06-03
> **Ldub314 said:**
> Ok so I'm new to ubuntu and when i try to install application using add/remove i get Unable to get exclusive lock this usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.So i go to system manger and look for apt-get or aptittude and i dont see it.

I have had this as well. When I started a second time all was well. It seems one the installation programs stays "hanging" and is not completely closed after using it. It's not visible in system monitor. A second start of one of the other installation programs worked just fine.
Maybe a bug?

---

### Post by Ldub314 on 2009-06-04
Nothing i do is working all i know is it's some process thats blocking it but i can't end it.

---

### Post by aysiu on 2009-06-04
Only one application can access package management at once.

It could be apt-get, dpkg, aptitude, Synaptic Package Manager, Add/Remove, or Update Manager.

If you have any one of those open, then close it.

If you don't appear to have any of those open, I would do a reboot.

---

