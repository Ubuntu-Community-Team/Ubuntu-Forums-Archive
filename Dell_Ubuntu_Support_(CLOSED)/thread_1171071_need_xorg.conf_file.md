---
title: "need xorg.conf file"
date: 2009-05-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by provomike on 2009-05-27
If you have the Dell 530N with the integrated graphics and are using the Dell S2409 LCD monitor, could you please send me a copy of your /etc/X11/xorg.conf file?

It's a long story. Suffice it to say it got trashed and the expert support people at Dell have no idea what the settings should be for the graphics and monitor they sold me. Go figure.

---

### Post by b@sh_n3rd on 2009-05-27
If your video isn't working or something like that..try;
```
# sudo dpkg-reconfigure -phigh xserver-xorg
```in a terminal to get the default xorg.conf file. To setup X to find your card, it'll be easier if you told me what your video card is? Then you'll get faster results than anything :D...

PS: I love dell's :D, I've got two...one an 11yr old Dell OptiPlex GXa and a 9/10 yr old Dell Dimension XPS D266...They are the best in my "fleet" :D

---

