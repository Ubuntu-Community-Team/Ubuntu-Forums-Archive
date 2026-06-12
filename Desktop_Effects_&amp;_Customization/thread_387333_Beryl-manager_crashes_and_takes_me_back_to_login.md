---
title: "Beryl-manager crashes and takes me back to login"
date: 2007-03-18
forum: Desktop Effects &amp; Customization
---

### Post by PolitikerNEU on 2007-03-18
Hello!

I have got the following problem:
I have installed beryl like it was described on this page: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#Kubuntu ](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#Kubuntu ) but whenever I want to start beryl or beryl-manager I get a black screen and immediately log off.

System:
- Kubuntu 7.04 Feisty Herd 5
- Amd64
- Nvidia Geforce 7 series

---

### Post by MoonRise on 2007-04-27
Has anybody a clue on this? My system is a Dell Inspiron 1000 with a SiS 650L display adapter.

---

### Post by Smuve on 2007-04-27
I'm not sure about Kubuntu Feisty, but I (and several others) had the same problem just a short time ago with Ubuntu Edgy.  It happened after a xorg update.  We all reinstalled nvidia drivers and the problem was fixed.

Our/my issue was with GL.  I was dropped back to login whenever my screensave start up as well.  Try to run a GL screensaver and see if the same thing happens.

---

