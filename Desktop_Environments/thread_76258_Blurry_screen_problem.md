---
title: "Blurry screen problem"
date: 2005-10-14
forum: Desktop Environments
---

### Post by KDE-fan on 2005-10-14
I just upgraded to Kubuntu 5.10 by using apt-get, and have a serious resolution/display problem. Kubuntu picks the right resolution (1024x768 ), but the display is blurry and doesn't cover the entire screen. I have a Intel integrated graphics card, and a flat-screen monitor (Benq FP531). 

Has anyone else encountered this problem? My screen is blurry, and I am getting a headache from watching it.

---

### Post by KDE-fan on 2005-10-21
[QUOTE=KDE-fan]I just upgraded to Kubuntu 5.10 by using apt-get, and have a serious resolution/display problem. Kubuntu picks the right resolution (1024x768 ), but the display is blurry and doesn't cover the entire screen. I have a Intel integrated graphics card, and a flat-screen monitor (Benq FP531). 

Has anyone else encountered this problem? My screen is blurry, and I am getting a headache from watching it.[/QUOTE]
Solved! I gave 5.10 another shot today! After messing around with the i810 driver and the xorg.conf file for 4 hours, I found an "auto adjust" entry in the menu of my LCD screen. The monitor still complains that it is out of sync or something like that, but other than that it looks perfect.

---

### Post by mforsberg on 2005-11-05
Hi

I have a similar problem. I've just installed Ubuntu 5.10 and my screen is blurry. I have an IBM laptop with an Intel integrated graphics card, but this is my first Linuz installation so I wont be able to solve this problem on my own. 

Do you think your solution may work for me as well, and if so how should I do it. I will need some more detailed information to solve this.

Help is much appreciated!

Martin

---

### Post by linuxted on 2005-11-05
[QUOTE=mforsberg]Hi

I have a similar problem. I've just installed Ubuntu 5.10 and my screen is blurry. I have an IBM laptop with an Intel integrated graphics card, but this is my first Linuz installation so I wont be able to solve this problem on my own. 

Do you think your solution may work for me as well, and if so how should I do it. I will need some more detailed information to solve this.

Help is much appreciated!

Martin[/QUOTE]

I'm having blurry issues too.  Please give us details on how you solved the problem

---

### Post by mforsberg on 2005-11-07
[QUOTE=linuxted]I'm having blurry issues too.  Please give us details on how you solved the problem[/QUOTE]
My problem was that the display resolution was set at the standard 75x75 dpi but after changing that to 96x96 dpi everything is fine.

I got the info on how to do it from this thread:
[http://www.ubuntuforums.org/showthread.php?t=20976](http://www.ubuntuforums.org/showthread.php?t=20976)

Good luck!

---

