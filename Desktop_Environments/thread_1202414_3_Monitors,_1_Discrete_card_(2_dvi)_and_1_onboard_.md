---
title: "3 Monitors, 1 Discrete card (2 dvi) and 1 onboard (1 dvi), Xinerama crashing X"
date: 2009-07-02
forum: Desktop Environments
---

### Post by lightfoot256 on 2009-07-02
I've been trying to get Ubuntu working on my 3-monitor dev machine for a while now and recently compromised by having 3 X-displays joined by Xinerama; There was a bit of a hit every time you drag a window from one monitor to another but I don't do it very often and I like to keep my windows within a screen anyway so it's not a biggie.

Anyway, I recently down-graded my graphics card from an over clocked 9600GT to a very low power, _silent_ 7600GS (both XFX) as I hardly ever used the power of the 9600 and it was making way too much noise and using up over double the amount of electricity. The motherboard is an XFX 9300 providing onboard graphics for the final monitor. (Intel Socket 775)

Anyway, since swapping the cards Xinerama fails to work. Enabling it causes X to crash and go into an annoying loop trying to relaunch - after about 2 minutes it gives up and tells me to wait some more... 

I can get twin view working on it's own, and that works quite well, I can also then enable X on the 3rd screen but it's completely seperate (bar copy/paste and mouse/keyboard) so I can use it but I can't drag anything accross to it - Firefox also whines if I try to open it while its running on the other screens.

I've tried the nvidia 177, 180 and 185 drivers and neither fix the issue - 177 actually wouldn't work at all.

Are there any alternatives to Xinerama or another way to get this setup to work. I want all 3 monitors active and able to drag windows between them _but_ when I maximise I'd like them to behave as seperate regions - When using twinview and a third monitor it thinks the first two screens are one and maximising stops working; I guess nvidia are fudging somthing that gets cancelled out when you enable another screen.

I also don't use composite or any desktop effects, but do want hardware acceleration and ability to run OpenGL apps in any of the screens.

Many thanks,
Chris

---

