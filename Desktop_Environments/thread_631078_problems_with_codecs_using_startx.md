---
title: "problems with codecs? using startx"
date: 2007-12-04
forum: Desktop Environments
---

### Post by COner on 2007-12-04
ubuntu 7.10

everything worked fine until i changed the startup mode:
sudo update-rc.d -f gdm remove

so it loads just fine to ttyl mode

but after i type startx everything appears to load just fine, until i try to open any videos using vlc or totem

if i do a sudo gdm from ttyl mode everything runs just fine..... except that by running gdm i have to login again, which is kinda stupid considering that i would then have to enter my password 3x to load.  i still want it to go to text mode initially

is there any way to make sure that startx is loading the codecs? or is that not the problem.  i could get the error messages from vlc or totem if it would help

---

