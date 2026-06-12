---
title: "Win4Lin runs slow as crap."
date: 2007-08-12
forum: Desktop Environments
---

### Post by tamirtoad on 2007-08-12
Hey everyone, I'm having a big, bad problem with win4lin. First of all, i'm on a sony vgn fs550 laptop. I installed xp pro sp2 flawlessly, but when I actually opened a guest sessions, it took forever to load and then i got a framerate of about one per second when i was in the actual windows environment.

Windows also didnt recognize any mouseclicks. (I had to navigate EVERYTHING using the keyboard--not fun.) The first thing i did was shut down and go to a config file in the win4lin installation and change the available RAM from 128mb to 500mb. I ran win4lin again, and went to the system manager in windows. It recognized that there was 500mb of memory, but still ran slow as ever.

So I tried downloading the drivers and installing them. I got to the installation wizards, but they all failed because the 'drivers werent meant for my hardware'.

I even restarted my computer and tried to run it again, but no luck.

Anyone have any ideas?

---

### Post by llamakc on 2007-08-12
[http://www.win4lin.com/smf/index.php](http://www.win4lin.com/smf/index.php)

---

### Post by tamirtoad on 2007-08-12
Ok, so here's what i've got so far:

Use sudo /etc/init.d/powernowd stop to turn off powernowd. This increases win4lin's speed quite a bit, but still nowhere near native. (replace 'stop' with 'start' to start it back up)

This fixes some of the mouse woes:
Adding the line 
MRGPRO_OPTIMIZED_MOUSE="off"
to /etc/default/mergepro.

And apparently tinkering around with win4lin's memory usage has results. I have been doing this, but without many results. 

Also, I have read stuff on the win4lin forums about versions of win4lin above 2.8 or so not working well on laptops (specifically pentium M architecture)

That's all for now; i'll post more if i get any significant results.

---

