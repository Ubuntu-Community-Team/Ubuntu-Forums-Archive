---
title: "[SOLVED] Very small desktop size"
date: 2007-08-03
forum: Desktop Environments
---

### Post by tekkenlord on 2007-08-03
Hello. I want to install kubuntu feisty in a brand new sony vaio vgn-fz19vn. I load the liveCD and I get a very small desktop size. The resolution seems to be the correct one but the whole desktop seems like a 640x480 window. I tried to use the the xvidtune tool but it says that the video mode can not be changed on this chip. The graphics card is a mobile intel graphics media accelator X3100. Any help is greatly appreciated!

---

### Post by be4truth on 2007-08-09
Did you press F4 to choose the screen resolution when booting the LiveCD?

---

### Post by tekkenlord on 2007-08-10
Thanks for replying. I solved the problem using

sudo dpkg-reconfigure -phigh xserver-xorg

and selected the correct resolution.

---

