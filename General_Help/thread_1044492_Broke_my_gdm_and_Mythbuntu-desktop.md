---
title: "Broke my gdm and Mythbuntu-desktop"
date: 2009-01-19
forum: General Help
---

### Post by orduek on 2009-01-19
after trying to fix the sound in my system I uninstalled and re-installed gdm and mythbuntu-desktop.
But, I get error when trying to reinstall packages,
when trying to install anything else I get an error also (error no.2)

when writing:
sudo dpkg --configure -a i get:
```
ormetal@ormetal-desktop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of mythbuntu-desktop:
 mythbuntu-desktop depends on gdm; however:
  Package gdm is not configured yet.
dpkg: error processing mythbuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythbuntu-desktop
```

needless to say it brokes many things in my system, although I can use it (but barely).
I really need some help here, I don't want to re-install everything

Thanl you

---

### Post by orduek on 2009-01-19
any idea will be extremly helpful.

---

