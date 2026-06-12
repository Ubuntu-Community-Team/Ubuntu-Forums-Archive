---
title: "Search not working in Gnome Shell"
date: 2013-11-03
forum: Desktop Environments
---

### Post by dbland2263 on 2013-11-03
I'm running Ubuntu 13.10 64bit with Gnome Shell installed, and I'm not sure if perhaps I uninstalled a package I needed or my configuration is screwed up, however anytime I attempt to use the search in the shell, for example to try to load an application, it just shows "No Results". Some things do show up, for example rhythmbox, but things like Firefox don't. Most of the things that will show up are control applications, such as printers, display, manage online accounts, etc.

If anybody could give any advice to help me fix this, I'd be greatly appreciative.

---

### Post by BrunoLotse on 2013-11-04
Hi:) execute this code to check whether Firefox is installed```
dpkg -l | grep firefox
```Cheers,Bruno

---

### Post by dbland2263 on 2013-11-04
```
dennis@mp-desktop:~$ dpkg -l | grep firefox
ii  firefox                                   25.0+build3-0ubuntu0.13.10.1        amd64        Safe and easy web browser from Mozilla
ii  firefox-locale-en                         25.0+build3-0ubuntu0.13.10.1        amd64        English language pack for Firefox



```

But yeah, it's not just firefox, even typing in things like gedit and calculator (or even gnome-calculator) don't yield any results.

---

### Post by BrunoLotse on 2013-11-05
Hi:)I've got a bit different output
```
ii  firefox    25.0+build3-0ubuntu0.12.04.1 Safe and easy web browser
ii  firefox-globalmenu    25.0+build3-0ubuntu0.12.04.1     transitional package
ii  firefox-gnome-support   22.0+build2-0ubuntu0.12.04.2  GNOME support
ii  firefox-locale-en  25.0+build3-0ubuntu0.12.04.1 English language pack for Firefox
```

See? GNOME support package. May be that make a trick?

Cheers,
Bruno

---

### Post by dbland2263 on 2013-11-05
Hm, that could be related, but that wouldn't explain why things like gedit and gnome-calculator don't show up either. I would expect it to be some package unrelated to any application or a setting, or perhaps just needing to reconfigure something.

At any rate, I kind of gave up and just downloaded and installed Ubuntu Gnome edition, and it seems to be working fine there, so I guess it's not solved but I don't need the answer anymore, thanks for your help though.

---

### Post by BrunoLotse on 2013-11-06
Hi:) The best I could. Glad that your Ubuntu Gnome edition is working. I am running stock GNOME Shell on precise and no complaints yet :)Cheers,Bruno

---

