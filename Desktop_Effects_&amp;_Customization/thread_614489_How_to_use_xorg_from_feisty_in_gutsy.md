---
title: "How to use xorg from feisty in gutsy"
date: 2007-11-16
forum: Desktop Effects &amp; Customization
---

### Post by doggiedoll on 2007-11-16
I used radeon 9200 and I love my xorg in feisty. AIGLX work fine with radeon driver.  After I install gutsy, everything is broken. I want to upgrade but xorg is not yet ready. XGL will make my machine slow, but fglrx will not support my old card.

Can I use my old xorg from feisty in new gutsy? Mix and match. :D :confused:

---

### Post by Inxsible on 2007-11-16
if you have saved a backup then you could always try. although i would suggest you also make a backup of the current gutsy xorg.conf, just in case things go from bad to worse ;)

---

### Post by kelvin spratt on 2007-11-16
I had the same problem as you when i tried the live disk so i locked the Xorg drivers and did distro upgrade to 7.10 clicked ok to the over writes, now have 7.10 with feisty xorg drivers. it seems to work fine for me.

---

### Post by rsambuca on 2007-11-16
Yes, it worked for me as well.  I had just saved my Feisty xorg, and then copied it to gusty and it works perfectly (albeit I am using nVidia).

---

### Post by doggiedoll on 2007-11-17
Thank you you all but at first I did not mean the /etc/xorg.conf. I mean xorg xserver. Can we put xserver from feisty in to gutsy?

But puting feisty xorg.conf in to gutsy gives me idea too. I did try it unfortunately. It does not work for my system. :(

---

