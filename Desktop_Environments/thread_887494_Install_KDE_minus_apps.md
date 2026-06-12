---
title: "Install KDE minus apps"
date: 2008-08-12
forum: Desktop Environments
---

### Post by RedPandaFox on 2008-08-12
I have Ubuntu 8.10 alpha installed on my EeePC, I like gnome apps but I like the feel of KDE 4, is it possible to install KDE without installing all the KDE apps?

---

### Post by Seisen on 2008-08-12
Try installing ```
kde4-core 
```and see if that is what you are looking for.

---

### Post by kerry_s on 2008-08-12
> **RedPandaFox said:**
> I have Ubuntu 8.10 alpha installed on my EeePC, I like gnome apps but I like the feel of KDE 4, is it possible to install KDE without installing all the KDE apps?

you'll have to do a custom install, use the alternate disk to install a command line system, then build up from there:

sudo apt-get install xorg kdm kde-core

---

