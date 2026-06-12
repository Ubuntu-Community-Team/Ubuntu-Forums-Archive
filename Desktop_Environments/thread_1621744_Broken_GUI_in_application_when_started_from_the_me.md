---
title: "Broken GUI in application when started from the menu"
date: 2010-11-14
forum: Desktop Environments
---

### Post by aamikkelsen on 2010-11-14
I have problem regarding when a application is started from the menu-line. If I for example start wxmaxima though Menu -> Science -> Wxmaxima, then the menu-bar is gone. I can access the menu-bar by pressing F10, but the menubar never shows up!

I have the same experience with emacs 23, where the menu-bar starts as it should, but whenever I change major (or minor) mode, the new menu-item appears, but I cannot access the menu-item (it is just blank). As before, whenever I go though F10 the menuitem shows up as it should.

Same goes for eclipse.

Instead of starting the applications though the Menu -> ..., I tried to start them in the terminal instead. Then the applications do not suffer from this menubar behaviour.

Do anyone have a solution for this?

---

### Post by aamikkelsen on 2010-11-15
I found a solution to my problem. I removed the **appmenu-gtk**-package and the menubar back.

sudo apt-get remove appmenu-gtk

The problem was also described in [https://bugs.launchpad.net/appmenu-gtk/+bug/667611]("https://bugs.launchpad.net/appmenu-gtk/+bug/667611")

---

