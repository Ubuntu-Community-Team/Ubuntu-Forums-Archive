---
title: "error exit status 2"
date: 2009-04-29
forum: General Help
---

### Post by toumie on 2009-04-29
hey there, 
im new here and for ubuntu in general
i newly installed ubuntu jaunty 9.04 
while i was adding the gnome-main-menu package from the "synaptic"
the installation was interrupted, and since then i keep getting the following error
on each time i try to install a package

"E: gnome-main-menu: subprocess post-installation script returned error exit status 2"

any ideas?

Thanks in advance,

---

### Post by spiderbatdad on 2009-04-29
try running
```
sudo dpkg --configure -a
```Either that or possibly the package is broken.

---

### Post by toumie on 2009-04-30
thanks for your replay,
i executed **sudo dpkg --configure -a**
it runned ok ,

i tried **sudo dpkg --configure gnome-main-menu**

this is the output
[B]Setting up gnome-main-menu (0.9.12+dfsg-0ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing gnome-main-menu (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 gnome-main-menu
[/B]

---

