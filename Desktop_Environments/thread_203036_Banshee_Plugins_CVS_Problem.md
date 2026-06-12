---
title: "Banshee Plugins CVS Problem"
date: 2006-06-24
forum: Desktop Environments
---

### Post by bebe on 2006-06-24
hi,

I compile Banshee 0.11 from CVS which gone just fine. But there is a problem with plugins. When i do ./autogen.sh --prefix=/usr i get that 

Running intltoolize...
intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite

--force is not working or i do it wrong.

How can i fix it?

---

### Post by rekahsoft on 2006-06-24
You could try my script...i have attached it...use the following command:
```
sudo sh ./banshee-installer -u
``` Report back with the results. 

Note: the script is still in development but is pretty stable and **_WILL NOT_** damage anything. I used it on two sysems and it worked great :)

---

### Post by tronica on 2006-06-24
can you explain how to compile banshee from cvs

---

