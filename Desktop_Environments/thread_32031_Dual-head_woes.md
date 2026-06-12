---
title: "Dual-head woes"
date: 2005-05-05
forum: Desktop Environments
---

### Post by OwlManAtt on 2005-05-05
Greetings! I'm trying to set up a dual-head display for my box, but I'm having some trouble.

See, I've got an nVidia GeForce FX 5200 with two ports for monitors. I hooked an old Dell screen up to the second port, installed the nVidia driver, and started playing with the xorg config. After a /etc/init.d/gdm restart, both monitors displayed part of the login screen (the screen was massive, but I just thought "I'll fix that later" when I saw it). I logged in, and as soon as GNOME started loading, the second monitor powered down and stopped displaying anything. I can't move the mouse over there anymore, either.

So, where did I go wrong? I'm using TwinView. Here is my xorg config:

[http://owly.homelinux.net/~owlmanatt/upload/xorg.conf](http://owly.homelinux.net/~owlmanatt/upload/xorg.conf)

Thanks!

---

### Post by OwlManAtt on 2005-05-05
Ah, after some tweaking, I got it to work. The problem was one of the resolutions I wanted the monitors to run at. 

With that fixed, I just have one small issue left. My desktop background.

See, I've got this 1024x768 desktop image that I've been using for years. As it stands, gnome thinks I'm using one really weird monitor (1024x768 plus 800x600), and tries to put it on both. Center/scale image splits it across the two screens and leaves blue to both sides of it (undesierable), full screen streches and mangles it, and tile tiles it funny and cuts it oddly so I don't get the whole thing on my big monitor. 

Is there any way for me to left-align it or fix it? I really don't want to part with it. =/

Thanks!

---

