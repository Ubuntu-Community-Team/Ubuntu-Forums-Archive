---
title: "Minimal install of xfce"
date: 2010-03-19
forum: Desktop Environments
---

### Post by Clivest on 2010-03-19
Hi

I've just done a minimal install of ubuntu using the Karmic Minimal CD Image and would like to use xfce4.

What packages are needed? I would rather not install any unnecessary stuff because it is a slow computer anyway. Is it possible just to use the xfce4 package rather than the full xubuntu-desktop package?

Oh and: would you recommend gdm or wdm as a window manager?

Thanks

Clive

---

### Post by nothingspecial on 2010-03-19
> **Clivest said:**
> Hi

I've just done a minimal install of ubuntu using the Karmic Minimal CD Image and would like to use xfce4.

What packages are needed? I would rather not install any unnecessary stuff because it is a slow computer anyway. Is it possible just to use the xfce4 package rather than the full xubuntu-desktop package?

Oh and: would you recommend gdm or wdm as a window manager?

Thanks

Clive

If you install xubuntu-desktop you may as well have installed xubuntu.

Yes just install xfce4, it will pull in a few dependencies including thunar but no way near as much a xubuntu-desktop.

If you want something even faster than xfce try openbox.

---

### Post by cascade9 on 2010-03-19
You will need (AFAIK) xorg as well. GDM/XDM/WDM is optional (startx from the command will start the desktop). Personally I prefer XDM. You could install xfce-goodies as well, but I wouldnt, its probably easier to just install stuff as you need it (I dont install xfce4-goodies myself) 

The most I would reccomend is- 

sudo apt-get install xorg xdm xfce4 xfce4-goodies

---

### Post by Clivest on 2010-03-19
Thanks. 

I've just done xorg and xfce4 for the moment. It's running pretty fast :D. I might add xdm, or try openbox or fluxbox tomorrow.

---

### Post by nothingspecial on 2010-03-19
Cool, openbox takes a bit of configuring but once you have it`s smooth as a sausage.

---

### Post by Harry James on 2010-03-20
I don't know how to do it on the main menu, but i know how to make a  link.
Make a launcher  and set the command to this:
gksudo shutdown now
however, this requires a password.

---

### Post by Rodney9 on 2010-03-20
Fluxbox is terrific, very fast and you can configure it just by text files to your hearts content.

Here is a very good guide by Narada - 

[http://ubuntuforums.org/showthread.php?t=1236329&highlight=conky+fluxbox](http://ubuntuforums.org/showthread.php?t=1236329&highlight=conky+fluxbox)

Here is a wiki -

[http://fluxbox-wiki.org/index.php?title=Fluxbox-wiki](http://fluxbox-wiki.org/index.php?title=Fluxbox-wiki)

Then just search this site for Fluxbox for more hints.

Rodney

---

