---
title: "MultiDisply for dual head GeForce FX 5950 Ultra"
date: 2007-02-15
forum: Desktop Environments
---

### Post by increment on 2007-02-15
Greetings all, 
   
  First post! Just decided to make the switch to Ubuntu from Gentoo, and I'm having a little trouble getting my dual display working. (I'm an idiot for not copying my old config before wiping the old install!). Anyway, the box is an AMD64 box and i installed Ubuntu 6.10. 

   I have done some messing with my xorg.conf file and it is currently as it appears below.  As it stands now, my first monitor is the only one showing good output. It looks as though all the info is present (e.g. i move my mouse to the corner of the screen and it doesn't go off), on the other monitor. Meanwhile, the other monitor is showing an amalgamation of colors and pixilation, it looks like buffer garbage or something.

   On the Gentoo box it was working using XFree86 and Xinerama with the nvidia driver.  Any help will  be greatly appreciated! :)

---

### Post by increment on 2007-02-15
Solved! alright, here is the deal, needed to change to the nvidia driver, and just leave the same BusID in each of the "Device" sections. below is the working config.

---

