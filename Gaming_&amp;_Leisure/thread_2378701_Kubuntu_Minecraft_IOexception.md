---
title: "Kubuntu Minecraft IOexception"
date: 2017-11-26
forum: Gaming &amp; Leisure
---

### Post by xeno42g on 2017-11-26
My problem is that Minecraft optifine does not start. When I join the optifine user, I'll play the game with the following error. What's the problem?

[http://www.kepfeltoltes.eu/images/hdd1/2017/11/23/117IMG_20171122_071852.jpg](http://www.kepfeltoltes.eu/images/hdd1/2017/11/23/117IMG_20171122_071852.jpg)

Sorry for my English!

---

### Post by sgian on 2017-11-27
Something in your optifine user profile got corrupted or removed, as the NoClassDefFoundError seems to indicate.  We could try diagnosing with questions like "Did it ever work?"  "If so, what changes did you make, like maybe switching to java 9 or removing a mod?"  However probably the easiest thing to do is to make a new instance with Optifine,

Personally I use the MultiMC launcher, it even has an Ubuntu .deb file for installation.  Instances are easy to create and alter with mods with MultiMC.

Also I noticed that you only have 1GB of RAM allocated to your minecraft instance.  If your computer has more than 3GB of RAM, you might want to allocate more RAM to minecraft.  Leave 1 or 2 GB for the OS, and the rest can be given to minecraft.  For example, if you have 8 GB of RAM, you can go up to 6 GB of RAM for minecraft without any likely problems if nothing else is running.

---

### Post by xeno42g on 2017-11-27
I use Minecraft 1.12.2. I downloaded optifine from optifine.net also 1.12.2 I tried C5 and C6.The optifine did not work yet. I therefore tried several versions of java.I will try with more memory

---

