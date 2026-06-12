---
title: "how to delete GNOME??"
date: 2005-07-09
forum: Desktop Environments
---

### Post by Digitallysick on 2005-07-09
ive put up several posts, for some reason, my ubuntu box wants to log straight into GNOME , when KDE has always been my default, anyway to fix this?? when i logout, and go to session "last" it goes back to GNOME instead of KDE, any way to get rid of gnome alltogether and have my linux box boot straight into KDE??

---

### Post by art on 2005-07-09
Did you do dpkg-reconfigure kdm? It should fix it...

---

### Post by kvidell on 2005-07-09
To remove GNOME try sudo apt-get remove ubuntu-desktop
Since I'm assuming you've already done sudo apt-get install kubuntu-desktop

I'm not sure how to operate KDM, so that's my suggestion...
- Kev

---

