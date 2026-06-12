---
title: "Xubuntu 9.10 w/ openbox"
date: 2009-11-28
forum: Desktop Environments
---

### Post by dmsynck on 2009-11-28
Hi all,

Since I have a pretty low memory system (512) MB, I wanted to try replacing the xfwm4 window manager with openbox to see if I could reduce the memory usage. Installed openbox and obconf, checked memory usage to get a baseline, killed xfwm4 and started up openbox. Upon checking the memory usage the second time, I found to my astonishment that the memory usage had actually increased. Has anyone seen this and how can it be ? I thought openbox was supposed to be lighter.

---

### Post by hirnwurscht on 2009-11-28
Hello,

Afaik, xfwm4 does start a few processes like xfce4-panel etc., those won't get killed with xfwm4.

The best way is to log-out and change the session-type to openbox, no xfce4 apps are started that way.

If anything goes wrong, log out and change the session-type back to whatever you have now.

---

### Post by urukrama on 2009-11-29
Xfwm4 is much heavier than Openbox on my computer. How big is the difference on your computer?

Xfce is that it is very modular, so you can easily load parts of the Xfce DE without using others. What you could do (and what I generally prefer) is to just load Openbox and add all the Xfce modules I like to Openbox' autostart (xfce4-panel etc.). Perhaps that will make a bigger difference on your computer?

---

### Post by XubuRoxMySox on 2009-11-29
A really awesome implementation of Openbox on an Ubuntu base is [Crunchbang Linux]("http://crunchbanglinux.org"). It flies on my old laptop. Definitely worth a look.

-Robin

---

