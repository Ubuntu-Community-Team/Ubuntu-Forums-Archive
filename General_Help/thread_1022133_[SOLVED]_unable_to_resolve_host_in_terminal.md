---
title: "[SOLVED] unable to resolve host in terminal?"
date: 2008-12-26
forum: General Help
---

### Post by abhilashm86 on 2008-12-26
abhilash@abhi:/home$ sudo gedit /boot/grub/menu.lst
sudo: unable to resolve host abhi

i changed my terminal name through /etc/hostname yesterday,from then this error pops up,how to resolve it?

---

### Post by Dr Small on 2008-12-26
> **abhilashm86 said:**
> abhilash@abhi:/home$ sudo gedit /boot/grub/menu.lst
sudo: unable to resolve host abhi

i changed my terminal name through /etc/hostname yesterday,from then this error pops up,how to resolve it?
You need to change the entry in /etc/hosts of the localhost line to match that of your new hostname.

---

### Post by albinootje on 2008-12-26
> **abhilashm86 said:**
> abhilash@abhi:/home$ sudo gedit /boot/grub/menu.lst
sudo: unable to resolve host abhi

i changed my terminal name through /etc/hostname yesterday,from then this error pops up,how to resolve it?

Did you also edit /etc/hosts accordingly ?

---

### Post by abhilashm86 on 2008-12-26
> **albinootje said:**
> Did you also edit /etc/hosts accordingly ?

yes it was desktop early,then i changed it to abhi,so should the name abhilash@abhi:/home$ 
reflect in /etc/hosts?
thats all or anything else?

---

### Post by taurus on 2008-12-26
Boot into recovery mode from GRUB menu and make sure the name in /etc/hostname is the same one that you use in /etc/hosts.

```
nano -B /etc/hosts
```

---

