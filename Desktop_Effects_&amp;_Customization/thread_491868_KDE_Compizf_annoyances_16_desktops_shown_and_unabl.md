---
title: "KDE Compiz/f annoyances: 16 desktops shown and unable to configure"
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by Zeroangel on 2007-07-04
Hey all, I have a few things that are bothering me. I am a **Kubuntu** Feisty Fawn user. And a fan of Beryl, but lately I have tried Compiz and am not liking it so much. Compiz is much smoother animation-wise than beryl, but the cube is so slow. Additionally My issues are....

Even though I'm only using four desktops, whenever compiz (and sometimes beryl) is enabled. Kicker shows a total of 16 desktops! This is quite space consuming and weird since clicking on desktops 1,5,9,13 sends me to face 1 of the cube. 2,6,10,14 send me to face 2, etc.

Also, how do I go about configuring Compiz Fusion? Beryl had a nifty configuration applet in the taskbar. I tried installing compiz-settings, but changing things there doesnt seem to work either....

---

### Post by Happy_Man on 2007-07-04
Try installing compizconfig-settings, going to the cube plugin, and changing the number of vertical desktops and horizontal desktops to 1 and 4, respectively. I am a Kubuntu/Fusion user too, but have never had this problem. Perhaps this will work for you....

---

### Post by Zeroangel on 2007-07-04
Thanks! :KS

I found the configuration applet. And your settings seem to work for me. Additionally the slow performance of the cube was fixed by disabling transparancy on the cube. Loving Compiz-Fusion, especially the new plugins like Expose. :)

---

### Post by Zeroangel on 2007-07-04
No good! Whenever I restart compiz-fusion, the 16 desktops on my kicker reappear. :(

---

### Post by Happy_Man on 2007-07-05
For me, this happens too, but i generally wait a few seconds and they go away and only the usual four appear. I wonder why.....

---

### Post by warp99 on 2007-07-06
Had the same problem but solved it by editing the kwinrc and changing the number of desktops from 4 to 1. The kwinrc file is located in ~/.kde/share/config. ;)

---

