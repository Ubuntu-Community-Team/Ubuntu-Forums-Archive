---
title: "Uninstalling kubuntu"
date: 2005-05-09
forum: Desktop Environments
---

### Post by mariuss on 2005-05-09
Hi,

I installed Kubuntu on top of a clean Ubunut Hoary install using the kubuntu-desktop meta package.

How can I remove KDE/Kubuntu now?

Removing kubuntu-desktop apparently removoes only that package and leaves all the KDE packages there.

Thanks,
Marius

---

### Post by philipacamaniac on 2005-05-09
**sudo apt-get remove kdebase kdelibs**

should kill off any KDE apps and Kubuntu-related packages.

---

### Post by mariuss on 2005-05-09
In Synaptic I maked **kdebase** and **kdelibs4** (**kdelibs** was not installed) for removal and this did the trick.

Thanks a lot,
Marius

---

