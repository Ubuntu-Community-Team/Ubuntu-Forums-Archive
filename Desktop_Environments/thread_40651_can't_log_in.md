---
title: "can't log in"
date: 2005-06-09
forum: Desktop Environments
---

### Post by tikal26 on 2005-06-09
Hi I started my computer and isntead of launching KDM I ended up in a terminal. I logged in and then I put my password. i typed sudo KDM but no kdm. how do I get to KDE ](*,) . thanks for you replies

---

### Post by kvidell on 2005-06-09
[QUOTE=tikal26]Hi I started my computer and isntead of launching KDM I ended up in a terminal. I logged in and then I put my password. i typed sudo KDM but no kdm. how do I get to KDE ](*,) . thanks for you replies[/QUOTE]
 If you're already signed in then just type "startx" (No sudo required)

How'd you end up runlevel 3 anyway?
- Kev

---

### Post by tikal26 on 2005-06-09
ok i did that, but I get the following message
(EE) Nvidia(0): failed to load Nvidia Kernel module
(EE) Nvvidia(0): **Aborting**
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by kvidell on 2005-06-09
[QUOTE=tikal26]ok i did that, but I get the following message
(EE) Nvidia(0): failed to load Nvidia Kernel module
(EE) Nvvidia(0): **Aborting**
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found[/QUOTE]
 oo.. your problem is much deeper than a simple runlevel issue. You're having kernel module difficulties.

Did you recently patch or otherwise update your nVidia drivers?
- Kev

---

### Post by tikal26 on 2005-06-09
[QUOTE=tikal26]Hi I started my computer and isntead of launching KDM I ended up in a terminal. I logged in and then I put my password. i typed sudo KDM but no kdm. how do I get to KDE ](*,) . thanks for you replies[/QUOTE]
 No I didn't it, but then just to try I did and apt-get update and then a apt-get --fix-missing upgrade and I was able to log in. I am about to log out and see if it works. I don't know what was wrong. any ideas


IT WORKS NOW!!!

---

