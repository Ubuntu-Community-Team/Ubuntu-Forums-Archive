---
title: "Mesa3D DRI with propriety drivers possible?"
date: 2012-02-20
forum: Desktop Environments
---

### Post by ultiphoenix on 2012-02-20
Hey guys,

i've been trying to figure out if this is possible but its really difficult to find a proper answer. This is basically the situation, i love the way the default display stack handles multi monitor support etc. I use my laptop alot to move around so i need it to be intelligent and dynamic. I'm currently using a macbook pro (early 2011) with osx lion (which is crap by the way) and i want to go back to ubuntu, but at the same time i dont want to lose on the display side.

I know the radeon opensource drivers are pretty solid at the moment, but i'd like the piece of mind that the propriety drivers offer. If i need to use the opensource driver so be it, but i've always been curious about the propriety drivers. Why does it have to be the one or the other? Or am i just completely wrong? please shed some light on this.

Basically i do not want the catalyst control center or any of the other radeon crap, i just want to use the normal display manager for configuration, i dont want to create xorg.conf files with static configurations.

---

### Post by HavarN on 2012-02-20
Installing the proprietary AMD Radeon drivers is just a matter of going to System Settings->Additional Drivers to install the fglrx driver. This will provide you with hardware accelerated OpenGL libraries. And in my experience, both the fglrx drivers and the open source radeon drivers have become much better in later years.

You should not install Mesa3D in addition. Mesa3D is a *software* implementation of OpenGL 3.0 with some OpenGL 4 extentions. Which would be way slower than using the fglrx provided OpenGL libraries.

---

