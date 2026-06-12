---
title: "Total Ubuntu Noob Accident..."
date: 2009-04-05
forum: General Help
---

### Post by EvilFunnyBunny on 2009-04-05
So, being the total ubuntu noob that I am, I was reading the ubuntu pocket guide. Page 57 specifically. 

So I was like, oh noes, my graphical settings are off! A quick click, and Ubuntu asks me if I want to install a driver (which I guess I don't have installed yet) for my ATI radeon HD 4870. So I click yes and stuff, and then it tells me to restart.

Restart = Bad.

So I restarted. And then it couldn't load the graphics and I am now stuck at non graphical interface.

Anyway to fix this? *other than reinstalling*

---

### Post by Maheriano on 2009-04-05
You can probably edit your xorg.conf file to put in the default ATI driver and then reboot. Once you get everything installed and working, then you can try your proprietary ATI driver again. It should be located in /etc/X11/xorg.conf I think. Either that or Google the default xorg.conf settings and just copy/paste those for now. Fix it later.

---

