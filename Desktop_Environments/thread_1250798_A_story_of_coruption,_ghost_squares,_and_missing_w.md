---
title: "A story of coruption, ghost squares, and missing window dressing."
date: 2009-08-26
forum: Desktop Environments
---

### Post by SacValleyDweller on 2009-08-26
Background: 
One week ago, my XP-running desktop, AKA The Dinosaur, went BSOD. All I had time to read when I returned to my keyboard was that there was a problem with my windows kernal. It rebooted itself and come up with a black screen and a line of text at the top reading "no operating system found." After some consultation with the tech support guy from my ISP, my 50-year old distant cousin, and the friend that introduced me to Ubuntu, I decided on the advice that my freind gave; run Ubuntu on The Dinosaur and see if I can access my HD. Accessing the HD was a no go due to corruption, so my freind and I decided to install Ubuntu on Dino.

The Issue;
Ubuntu, even from the disc, ran with some problems; ghost squares of missing pieces of window or half-higlighted button where I clicked with the cursor, and a lack of window title bar (see attatched screenshot)

In effort to fix this, I, at the direction of my friend checked that we had the right video card drivers. I did.
We uninstalled compiz and metacity.
we then run this in terminal:
```
sudo nano /etc/X11/xorg.config
```

to try to reconfigure the color depth to 16 bit color.

none of those things fixed the issue

The Dumb fix:
Nosing around on my own upon my friend's sugestion, I went to the "appearence prefferences" window, and found that visual effects were set to normal. I tuned them to off, and PRESTO! All was fixed!

My friend and I guess that my 8-year-old video card couldnt handle the effects.

*sigh* Trials and tribulations of the transition from Windows to Ubuntu. :rolleyes:

---

