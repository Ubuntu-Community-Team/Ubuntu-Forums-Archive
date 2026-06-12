---
title: "How to tell xfce to NOT DRAW ANY PIXELS on the edges of the screen."
date: 2011-08-17
forum: Desktop Environments
---

### Post by gangasrotagati on 2011-08-17
I am running Ubuntu Natty with the xfce 4.8 desktop on a tiny computer called a BeagleBoard-xM. My issue is that what I see on my display is partially cut off because the display resolution on the BeagleBoard is set to a resolution that is different from my screen, which is a non-standard size. (wearable computer project)

The BeagleBoard does certain things according to its own specific software, which complicates things. It doesn't seem possible to change this in the xfce Settings Manager (only one setting is allowed, all others are greyed out) nor by changing xorg.conf. (There is no xorg.conf on the BeagleBoard, the Beagle gets this info directly from its display driver. I'm trying to figure out how to fix this problem in the Beagle display driver, but I was thinking that probably a simpler way to fix this problem would be to tell xfce to simply not draw any pixels on the edges of where it thinks the screen is. In other words, how would one tell xfce to draw the screen as a square smaller than the area of the monitor? I could experiment on my desktop machine, and when I saw that xfce was leaving blank space on the borders, I could apply this to my Beagle. But I can't figure out how one would go about doing... I can't think of what I need to google- what would be the proper terminology for this type of task? Any such pointers would be much appreciated.

---

### Post by gangasrotagati on 2011-08-18
Um, sorry, yeah so anyways I just 90% solved my own problem. What I did is I made panels on the edges of the screen where it was cut off. The mouse can still go off the screen, but windows do not open outside of the screen, which was the major problem. Kludge-y but it works.

---

### Post by drawkcab on 2011-08-18
> **gangasrotagati said:**
> Um, sorry, yeah so anyways I just 90% solved my own problem. What I did is I made panels on the edges of the screen where it was cut off. The mouse can still go off the screen, but windows do not open outside of the screen, which was the major problem. Kludge-y but it works.

Wouldn't it be possible to edit the xorg file to a resolution that either matches or is just smaller than your non-standard screen?

I'm surprised you can get xfce running on a beagleboard.

---

### Post by gangasrotagati on 2011-08-18
There is no xorg.conf file on the Beagleboard version of xfce, because the Beagleboard version of xfce gets this information directly from its display driver.

---

