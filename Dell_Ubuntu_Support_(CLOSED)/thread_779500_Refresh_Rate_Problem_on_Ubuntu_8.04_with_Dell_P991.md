---
title: "Refresh Rate Problem on Ubuntu 8.04 with Dell P991"
date: 2008-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Joshgo on 2008-05-02
Hi, I'm a beginner. I installed ubuntu about 2 weeks ago and am getting used to the fact that I am not using windows xp anymore. I began using ubuntu because I messed up windows xp (long story) and my problem is that I usually get a refresh rate of 120hz in 1024x768 in windows xp (My Dell P991 is capable of it). Now that I use ubuntu, the max refresh rate I get is 85hz even in low resolutions such as 800x600. Anyone know what my problem is?

Note: My graphics card is a nVidia GeForce 5200 fx and I am using the nvidia-glx-new drivers from the list of software packages.

---

### Post by Joshgo on 2008-05-04
Anyone???  :confused:

---

### Post by NakedSnake on 2008-05-05
try

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Joshgo on 2008-05-05
When I typed that this is what I got:

jogo@J2D2:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for jogo: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080505151453

---

