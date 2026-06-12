---
title: "Odd Kde Resolution/X Server issues"
date: 2008-09-24
forum: Desktop Environments
---

### Post by rob356 on 2008-09-24
Okay, so I am using Kubuntu 8.04, with KDE 4.1, note, I had these same issues with KDE4. 
My laptop has a maximum resolution of 1400x1050. The screen resolution program can change it to that no problem, but the X server is starting up at a lower resolution. When I log in the program starts and changes the Resolution, the screen goes black then comes back on. I see a white screen, then about 30 second later the desktop shows up. I cannot see the mouse though, after some experimenting I have found that the mouse is "there" but I cannot see it, and after clicking on stuff with the invisible mouse I can see it again.
So I tried to modify my Xorg.conf to say the 1400x1050 res. I added to the screen section,

```
DefaultDepth  24
SubSection  "Display"
   Depth   24
   Modes   "1400x1050"
EndSubSection
```

This does nothing.:( I want the X server to START UP at the 1400x1050 resolution, not have it changed later, as I think that is what is causing all the problems. Any help is greatly appreciated.

---

### Post by rmdegennaro on 2008-09-24
Same/similar issue here, on multiple boxes.  

What I see is that I can set the resolution under "Display" in System Settings, and it changes the resolution for current session.  But the initial login afterwards of KDE always shows default of 1280x10224 on regular screens, and 1280x720 on widescreens.  As soon as I start System Settings up, the resolution changes to what I set it (sometimes larger, sometimes smaller).  

Oh, also the panel stays that the smaller resolution when going bigger.  Strange!  A quick google search shows something similar in Gentoo.  I didn't see a fix, though don't have time to search right now.  Maybe over the weekend.  I will check KDE bugs too...

---

