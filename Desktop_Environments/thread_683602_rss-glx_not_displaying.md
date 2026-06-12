---
title: "rss-glx not displaying"
date: 2008-01-31
forum: Desktop Environments
---

### Post by pormogo on 2008-01-31
I was trying to enable the slick looking rss-glx screen saver on a basically new version of ubuntu 7.10 however it's not showing up in the screen saver menu. dpkg shows that I have it installed

[i]root@superb-odifference:~# dpkg -l|grep rss
ii  rss-glx                                    0.8.1-6ubuntu5                      Really Slick Screensavers GLX Port[/i]

however it doesn't show up. I tried running rss-glx_install and it still doesn't show up. I was going to remove the package and reinstall it, but when I try and use apt to remove it it wants to remove gnome-desktop, not something I'm interested in doing. Why is this not showing up? Am I missing a config or anything?

---

### Post by kuja on 2008-01-31
rss-glx isn't just a screen saver, it's a whole bundle of screen savers. Included are things such as Hufo's smoke, a tunnel screensaver, a fireworks screensaver, and my personal favorite - Euphoria.

---

### Post by pormogo on 2008-01-31
All of those others screensavers appear to be there and are working. I have 1 screesaver that just doesn't seem to work. This screen saver is named helios, is that supposed to be it? Is there a way I can remove and reinstall the package without totally breaking dependencies?

---

### Post by kuja on 2008-02-02
Running something like sudo apt-get install --reinstall rss-glx should be able to do the trick ...... I don't think it has any reverse dependencies anyway ... or does it?

---

