---
title: "Everything is HUGE, how to shrink it?"
date: 2007-03-03
forum: Desktop Environments
---

### Post by stupidlongname on 2007-03-03
I'm a new Ubuntu user and using it seems to be quite a shock after using Windows, at least visually. Currently I'm using 1024x768 as the display resolution (couldn't get it to work on 1152x864 as I use in Windows, even after installing nVidia drivers for my Geforce2 400), but everything is way too big. For instance, the tab names in Firefox are displayed in a font that, to me, looks like a size 16 at least. Every window is huge, every dropdown menu is huge.

Can I do anything about it or should I just learn to cope with this space consuming interface?

Thanks.

---

### Post by teaker1s on 2007-03-03
terminal 
sudo ```
dpkg-reconfigure xserver-xorg
```
use spacebar to select/tab to move to ok etc
select resolutions you know your hardware supports

---

### Post by Kumagoro on 2007-03-03
That's what Ubuntu stands for, it should be usable for people with worser eyes.

Mess around with the settings or try out KDE (suda apt-get kubuntu-desktop)

---

### Post by stupidlongname on 2007-03-03
> **Kumagoro said:**
> That's what Ubuntu stands for, it should be usable for people with worser eyes.

Mess around with the settings or try out KDE (suda apt-get kubuntu-desktop)

Won't KDE eat loads of my hardware resources? I don't really want that :-/

---

### Post by Kumagoro on 2007-03-03
I don't have any huge performance issues on KDE.

Sempron 3000+
512mb RAM
GeForce 6100 integrated (uses me 128mb for itself, so i have actually 384 RAM)

Plus some eye-candy like kbfx, ksmoothdock (no XGL/AIGLX)

Or simply tru fluxbox/xfce

Or be a 1337 user and use console

BTW: if Windows XP runs smoothly for you, so will KDE

---

### Post by stupidlongname on 2007-03-03
Thx Kumagoro, I'll give it a shot I guess.
I managed to get my resolution to 1152x864, things are much better now :)

---

### Post by elmerfud on 2007-03-03
I had the same huge screen issue you did.  I had to remove all resolutions larger than my desired resolution from my xorg.conf file.

---

