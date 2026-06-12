---
title: "Remove startup apps"
date: 2010-04-23
forum: Desktop Environments
---

### Post by matroshka on 2010-04-23
Hi,

Sorry if I might asking a question which already been answered previously, however I cannot find a suitable answer for my problem...

I'm using both GNOME and KDE on my Ubuntu, and in GNOME I'm using Cairo-Dock which I want to remove when I use KDE.. 

But I can't find a so-called Startup Manager in KDE.. I've read people talking about Autostart, but I think it's for configuring new startup application not removing it..

how can I remove my Cairo-Dock upon starting the KDE then? 

Thank you!

---

### Post by Zorael on 2010-04-25
In KDE, apps start upon login if they have a link or .desktop file in **~/.kde/Autostart**, **/etc/xdg/autostart**, **/usr/share/autostart** and potentially **~/.config/autostart** (I think).

What you can do is to find what file is autostarting it and hope it's a .desktop file (which it likely is), and if so add the line **OnlyShowIn=GNOME;** to it. As a side-effect it will probably disappear from the menu in KDE (and not just cease to autostart). Another solution is to remove any mention of autostarting in said .desktop file, and use some GNOME-specific way of getting it to autostart there.

---

