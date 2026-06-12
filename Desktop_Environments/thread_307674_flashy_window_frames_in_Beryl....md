---
title: "flashy window frames in Beryl..."
date: 2006-11-26
forum: Desktop Environments
---

### Post by nickstatus on 2006-11-26
hello... When I am in a xgl session, all the window frames are constantly flickering in and out of existance. This is really irritating, because how am I supposed to close or move said windows? also, applications seem to take longer to start up, and it was not like this previously. this may stem from an issue with my video card or driver. I have a ati radeon xpress 200m, and the driver is the most current xorg fglrx ati driver. although not by any means urgent, any advice is welcome. 
 ***edited to say: I forgot to tell y'all that I am running the drake. the DAPPER drake.***

---

### Post by BuRn_sLuG on 2006-11-27
Hey, I occasionally have the same problem as you do. To fix it, I right click the beryl-settings icon in the taskbar, and select *Emerald Theme Manager*. Then select Edit > Frame Engine > Vmrunner.

That usually fixes it, though if anyone knows what causes our problems and could sort out a permanent fix, help would be greatly appreciated :mrgreen:

---

### Post by nickstatus on 2006-11-27
much thanks mr BuRn_sLuG... I will try this... This forum thing is really handy... If it wasn't for resources such as this, linux would be a territory for cs majors only...

---

### Post by NikoC on 2007-01-14
Have the same problem on my lappy with a Nvidia Geforce Go 6200 graphics card... the strange thing is though that when I boot up the first time beryl gives these flickering frames but when I end a session and log in again, the problem seems to be gone... gonna try the Frame engine solution tomorrow at work ;)
I'm running Freespire 1.0 at the moment, it is one of the few debian based distro's that I've tried that actually manages to shut down my laptop 'normally'.

---

### Post by kuripot on 2007-01-14
I get this problem sporadially as well, and is an ongoing problem. What I usually do is right click on the Beryl gem in the panel and select quit. Beryl continues to work but the icon is gone from the panel. Still looking for a permanent fix too

---

### Post by NikoC on 2007-01-15
Well it's not a complete fix but a good workaround that does the trick for me:
after getting into KDE I opened a console and typed 'sudo killall emerald' after which I chose the Run Program option and typed 'emerald'... no more flickering here now! I wrote these two simple lines in a script and added that to my KDE Autostart programs.

---

