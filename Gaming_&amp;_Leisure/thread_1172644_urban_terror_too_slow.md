---
title: "urban terror too slow"
date: 2009-05-28
forum: Gaming &amp; Leisure
---

### Post by kvs on 2009-05-28
whenever i run urban terror, it is just too slow! i mean, i cant even navigate the mouse properly. when i run glxgears, it opens a new window with some wheels, and the output is:
unknown chip id 0x95c4, can't guess.
what could this mean?

---

### Post by kvs on 2009-05-28
ok, so i waited for a while and got this output:

1244 frames in 5.0 seconds = 248.786 FPS
1217 frames in 5.0 seconds = 243.352 FPS
1214 frames in 5.0 seconds = 242.787 FPS
1238 frames in 5.0 seconds = 247.447 FPS
1216 frames in 5.0 seconds = 243.172 FPS
1232 frames in 5.0 seconds = 246.374 FPS
1222 frames in 5.0 seconds = 244.206 FPS
1174 frames in 5.0 seconds = 234.766 FPS

---

### Post by kvs on 2009-05-28
ok, its not a problem with urban terror. any 3d game that i install runs very very slowly. what could be the problem?

---

### Post by kvs on 2009-05-29
here are my specifications:
lenovo y330 laptop with 2 gb ram, and my graphics card is [FONT=arial][SIZE=-1][COLOR=#4e4d4d]ATI Mobility RadeonTM HD3450 with 256MB VRAM[/COLOR][/SIZE][/FONT]

---

### Post by K.L. on 2009-05-29
IIRC, I had some problems with Urban Terror while Compiz effects were enabled. Try turning those effects off. Maybe that will help.

---

### Post by kvs on 2009-05-30
how exactly should i do that?

---

### Post by K.L. on 2009-05-30
Right click on desktop.

Choose *Change Desktop Background*.

Click on *Visual Effects* tab and select *None*.

---

### Post by kvs on 2009-05-30
its already checked as none. any other thing that i can try?

---

### Post by K.L. on 2009-05-30
It may sound silly, but do you have video card drivers installed?

Click *System -> Administration > Hardware Drivers* install recommended drivers and reboot.

I'm new to Ubuntu myself, so I can't help you more, sorry.

---

### Post by DrMelon on 2009-05-30
It seems as though your graphics drivers are not being loaded (or you haven't installed them). 

Not to worry, doing what K.L. said should work.

---

### Post by kvs on 2009-05-31
thank you so much! it worked! i had installed ubuntu only about a month ago, seems i had not yet installed the drivers.

---

### Post by K.L. on 2009-05-31
Glad it worked. Happy gaming! :D

---

### Post by cocamoxb on 2009-10-06
I would recommend ATI 9.9 drivers. I've got 9.9 running normally.

---

### Post by myromance123 on 2009-10-07
Oh!
 just a word of advice, :D
but if you find theres a game that still doesn't run well graphic wise even with those drivers listed under hardware drivers installed then try the actual binary drivers from Ati (or Nvidia if you change cards).

 Download the (normally .deb) linux 32 bit or 64bit depending on your specs and it might just give you a nice boost in graphics smoothness :D
 But beware as well as sometimes the latest binary drivers from them may also not work in certain areas or on certain machines :)

It Never hurts (at least not too bad) to try new stuff xD

---

