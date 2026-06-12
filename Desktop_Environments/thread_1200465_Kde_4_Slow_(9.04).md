---
title: "Kde 4 Slow (9.04)"
date: 2009-06-30
forum: Desktop Environments
---

### Post by jure1873 on 2009-06-30
I recently upgraded from kubuntu 8.04 to 8.10 and then to 9.04 and now I have KDE 4.2.2 and everything is soooo slow. 

I just switched to gnome because of this (firefox and thunderbird are gtk apps anyway). The problem is that I also use krusader and digikam a lot and they are still slow. What could be wrong? 

Unfortunately kde 3.5's repository is down. Do you think this can be fixed somehow or is it better if I compile kde 3.5 from sources?

---

### Post by RJARRRPCGP on 2009-07-01
I dunno. Because KDE is slow for me, too, even with another distro and PCBSD.

---

### Post by aged hippy on 2009-07-01
Open a terminal and run ***top*** - that will show you what is hogging your resources. :)

---

### Post by RJARRRPCGP on 2009-07-06
I dunno what the problem is, but KDE is slow when my hardware exceeds the minimum requirements! And I also made sure to use the Nvidia proprietary driver. 

Even when I tested with at least a 2.1 Ghz processor, it feels like it's only a Pentium I 133 Mhz LOL.

---

### Post by ssri on 2009-07-06
You might have to switching your rendering from opengl to xrender.  I heard that uses your video card's graphics acceleration to render things fast.  If direct rendering is not enabled, that might explain why the draw times are laggy.

---

### Post by RJARRRPCGP on 2009-07-06
> **ssri said:**
>  If direct rendering is not enabled, that might explain why the draw times are laggy.

Direct rendering was on. And I made sure, because I game.

---

### Post by Khrimzunn on 2009-07-06
I've noticed the slow performance of KDE while I was on vbox, I haven't tried it fully installed on my desktop yet. 
Also how can you check if direct rendering is on? (Sorry but I was wondering.)

---

### Post by ssri on 2009-07-07
> **Khrimzunn said:**
> I've noticed the slow performance of KDE while I was on vbox, I haven't tried it fully installed on my desktop yet. 
Also how can you check if direct rendering is on? (Sorry but I was wondering.)

~$glxinfo | grep direct

---

