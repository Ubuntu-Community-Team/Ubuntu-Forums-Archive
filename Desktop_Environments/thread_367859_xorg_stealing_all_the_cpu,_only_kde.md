---
title: "xorg stealing all the cpu, only kde"
date: 2007-02-22
forum: Desktop Environments
---

### Post by ge5239 on 2007-02-22
so.. a few days ago, i happily ran ubuntu 6.10 with gnome. worked just fine, smooth and everything. 

then i started to see screenshots with kde, i liked it, me liked it very much. so installed kde. me still liked it! was playing with some transparancy and all that. then all of a sudden, out of the blue, computer start chewing, im checking top, and xorg is constantly working with over 50% cpu usage. usually more common to see it working with 95%. 
after a while, when at the same time having problems with my tv-out, i figured that it might have been a problem with going from ubuntu 6.06 - 6.10 -> kde, so downloaded an image and reinstalled the whole thing... and ~20 hours ago, i got things working again. 

but still, that damn xorg. things can work just fine, this time it took ~5 hours before it started chewing, and now it's slooow. i can always relogin, and get things working again, but who wants to do that? and since it worked in gnome, and fluxbox, before, why not kde? 

got 2048 memory, a amd64 3800+, nv-card (XFX GeForce 7600GT 256MB GDDR3 XXX, with drivers via envy, tried installing latest from nv.com manually, plus latest beta, same result). Those things are working, atleast according to cedega. 

anyone got any ideas? love kde, would hate to leave it just cause xorg lags computer to pieces :/

---

### Post by alphamerik on 2007-02-24
This is happening for me too.  AMD64, KDE, NVIDIA dual monitor setup.  Just started happening recently, I am wondering if it is a recent update.  K/Xscreensaver just displays a big X when it turns on, but doing a "test" of a screensaver seems to work mostly.  The first test displays but subsequent tests don't display anything (not even an X).  The logs are devoid of anything useful.  I recently benchmarked a Quadro4 card so that might have something to do with it, but I went through the xorg.conf and didn't see anything weird.  AMD64 support has been really spotty, I am ready to install the x86 version because I am tired of KDE crashing.  The past month has been pretty stable until this past week... when Xorg starts consuming 100% cpu one of the monitors doesn't display the mouse only background and the other is unresponsive.

---

