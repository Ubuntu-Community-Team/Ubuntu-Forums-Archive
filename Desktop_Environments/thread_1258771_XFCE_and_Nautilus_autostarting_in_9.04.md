---
title: "XFCE and Nautilus autostarting in 9.04"
date: 2009-09-05
forum: Desktop Environments
---

### Post by shadarack on 2009-09-05
Okay, I got a bit of a problem. I recently upgraded to Ubuntu 9.04 from 8.10 and was using XFCE at the time. Now I believe I may have had Nautilus running at the time of the upgrade.

To my knowledge, Nautilus is not doing anything to my desktop and it appears I'm using Thunar for everything, but every time I start up XFCE, the splash screen says it's starting up Nautilus, and it hangs there for a good minute or two. I think I got the new version of XFCE with my upgrade, because my desktop settings window looks very different now, and I no longer have the "allow XFCE to manage your desktop" checkbox option, which was the easy old fix.

System-monitor does not list Nautilus as running, but it keeps trying to start up when ever I restart XFCE.

Does anyone know how to fix this, please? Thank you...

---

### Post by coldReactive on 2009-09-05
See if this works,

System > Preferences > Startup Applications/Sessions > Options Tab

Uncheck Automatically remember running applications when logging out.

This checkbox is checked by default in Xubuntu (Unlike in Ubuntu.)

---

### Post by shadarack on 2009-09-07
Well! I was feeling really dumb about not being able to fix this problem on my own. Now I know why I couldn't fix it. For some reason, I do not have preferences listing in my system menu...

Would it make a difference if my original install was Ubuntu, then I switched to Xubuntu, then upgraded probably about 5 times since then?

It seems like perhaps my XFCE menus are messed up somehow. Yay! I found another problem!

---

### Post by kerry_s on 2009-09-07
> System > Preferences > Startup Applications/Sessions > Options Tab

that's for gnome! 
in xfce4 it's:
**menu-> settings-> session & startup** (i think)

---

