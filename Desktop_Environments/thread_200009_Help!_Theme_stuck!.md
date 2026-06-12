---
title: "Help! Theme stuck!"
date: 2006-06-19
forum: Desktop Environments
---

### Post by Jessehk on 2006-06-19
I will first quote somebody else who had this problem (in the Breezy forum)

> 
**gtk2-engines-gtk-qt bug**

When this package is installed, it seems to override the normal gnome
configuration, which is acceptable, but only while it is installed. There seems to be no way to disable this fully while the package is installed, and even uninstalling the package or even the entire KDE system does not return things to their former state. I am now locked into one GTK Style (except for the window borders and icons), changing the setting in gnome theme selector does nothing. So now, I am stuck with a "Fused Lipstik-Human theme". Anybody find a way to fix this?


I am having the exact same problem.

Does anyone have any advice?

---

### Post by bruce89 on 2006-06-19
The only way I know of is removing gtk2-engines-gtk-qt, it's a pretty nasty bug.

---

### Post by ayoli on 2006-06-19
does 
```
rm ~/.gtk* 
```
helps ?

---

### Post by Jessehk on 2006-06-19
[QUOTE=ayoli]does 
```
rm ~/.gtk* 
```
helps ?[/QUOTE]


It does indeed.

Thanks for the quick help. :)

EDIT: I should add that specifically, I rm'd .gtkrc-2.0.

I installed KDE (then promptly removed it ;)), and it had messed with the file. e.g.

*#This file has been edited by KControl Center*

---

