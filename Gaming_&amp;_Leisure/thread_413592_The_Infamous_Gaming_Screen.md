---
title: "The Infamous Gaming Screen"
date: 2007-04-19
forum: Gaming &amp; Leisure
---

### Post by Harkainos on 2007-04-19
I have the registered nvidia drivers running.

My Desktop resolution is 1440*900

I am having 2 errors when starting games. 

1. WoW will only play in 800*600. When I start WoW my desktop 'zooms' in (from 1440*900 to 800*600) to make WoW play 'Fullscreen'. When it does this i can literally move my mouse to the right (passed the WoWUI) onto my desktop. What could be causing this?


2. UT2004 (Wine version, I know there is a Linux version) runs at 1240*768 resolution. When i move my mouse far enough left or right my guy will stop turning. Kinda like the mouse hits the edge of the screen. I have configured wine to 'xgrab on' and it is still doing this. What could be causing this?

---

### Post by charlieg on 2007-04-19
Problem (1) is caused by a combination of how X11 works and WoW not accounting for it.  When an application changes the resolution, X11 simply zooms, retaining the extra space.  WoW (or, more specifically, WINE) is not acknowledging this extra space by restricting the cursor.  Think of it has having two monitors and being able to move the mouse cursor from one to the other.  It's up to the application to hold the mouse cursor on a single screen.

---

### Post by Harkainos on 2007-04-19
is there any troubleshooting for x11 then? or is that just how it is? Also why would I not be able to run this game in anything higher than 800*600?

---

### Post by chiefwhosm on 2007-04-19
out of curiosity does it still happen when you run wine in windowed (desktop) mode?

---

### Post by Harkainos on 2007-04-19
yes. I will go home and check through the setting in the .wtf - maybe it is set to 800*600 default and thus causing this. I dont mind it so much.... makes it easier to surf wowhead.com :)

---

