---
title: "Kwin with GNOME"
date: 2012-10-19
forum: Desktop Environments
---

### Post by sienile on 2012-10-19
I really like the layout of GNOME, but hate that Metacity doesn't allow for window tiling. I've installed Kwin and would like to have it as my default window manager, but I can't seem to find the setting that controls this.

How do I set Kwin as my default window manger in GNOME?

---

### Post by sienile on 2012-10-19
Yay! I stumbled on to this page today ([https://blogs.kde.org/2009/01/24/kwin-conqueror]("https://blogs.kde.org/2009/01/24/kwin-conqueror")) and it gives a per-user global solution, which is fine by me.

Add this to your ~/.profile
> export WINDOW_MANAGER=kwin

---

