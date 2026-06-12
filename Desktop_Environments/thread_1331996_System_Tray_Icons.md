---
title: "System Tray Icons"
date: 2009-11-19
forum: Desktop Environments
---

### Post by captaincrook on 2009-11-19
Annoyance going on here in Kubuntu. In the KDE system Tray, I get garbled icon backgrounds for all GTK apps that have system tray icons. Reproducible by hovering over the icon and waiting for the tooltip to come up. Then, garbled backgrounds!

[img]http://img198.imageshack.us/img198/1452/tooltipbug.png[/img]

Using KDE 4.3.3 from the Kubuntu Backports PPA. Any tips?

---

### Post by captaincrook on 2009-11-19
Hurrah solved. NEEDS to have compositing enabled in xorg. Quite silly.

---

