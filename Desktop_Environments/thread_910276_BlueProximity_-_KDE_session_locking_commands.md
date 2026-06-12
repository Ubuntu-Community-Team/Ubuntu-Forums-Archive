---
title: "BlueProximity - KDE session locking commands"
date: 2008-09-04
forum: Desktop Environments
---

### Post by shadowplane676 on 2008-09-04
Ok, im working on getting Blue Proximity to work well on my laptop. i have it interfaced with my phone and it detects the distance and all that. what my issue is, is i cant find the correct commands to either enact a passworded screensaver or do a straight KDE lock session.

the only thing ive been able to find is the kdesktop_lock command (,hich works with blue proximity when i get too far away) but i dont know what the unlock command is.

The other thing is if there is no kdesktop_lock unlock command, what would be the commands to start a screensaver (openGL Euphoria) in KDE running compiz fusion? ive looked for a couple days and havent been able to find anything that works. (xscreensaver and kscreensaver commands dont work)

thanks in advance

---

### Post by Minimouse on 2008-09-12
Hi, 
 
If you use KDE4, I recommand you use the following commands, as D-COP server was replaced with D-BUS within KDE4 : 
 
lock : qdbus org.kde.screensaver /ScreenSaver Lock ; xset dpms force off 
unlock : xset dpms force on ; killall -9 krunner_lock  
 
xset dpms force on/off is used to shutdown/wake up the monitor, so you don't have to wake it up moving your mouse. 
 
It works like a charm. :)
 
Mini.

---

### Post by bongoongo on 2010-07-28
> **minimouse said:**
> hi, 
 
if you use kde4, i recommand you use the following commands, as d-cop server was replaced with d-bus within kde4 : 
 
Lock : Qdbus org.kde.screensaver /screensaver lock ; xset dpms force off 
unlock : Xset dpms force on ; killall -9 krunner_lock  
 
xset dpms force on/off is used to shutdown/wake up the monitor, so you don't have to wake it up moving your mouse. 
 
It works like a charm. :)
 
mini.


my problem is that the unlock command doesn't work i can lock it but that`s it. Any idea what the command would be????

I use kde 4.4.2

---

