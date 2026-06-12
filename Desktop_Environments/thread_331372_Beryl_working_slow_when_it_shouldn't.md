---
title: "Beryl working slow when it shouldn't"
date: 2007-01-04
forum: Desktop Environments
---

### Post by Asix on 2007-01-04
After two days of setting up and installing everything, I've managed to install Beryl and Emerald on my Kubuntu Edgy 6.10 box, and I am proud to say that Beryl v0.1.4 is running without any problems on my system.
The problem is that it works kinda... slow. I've properly installed open source drivers for my ATI Radeon 9600 card and set up my xorg.conf file properly (at least I think I did it properly), but Beryl works really slow. Wobbly windows and generally all windows animations work slowly at about 10-15 fps, when rotating the Cube, it's also pretty slow, not to mention extremely slow scrolling in Firefox/Konqueror or any other application where you need to scroll (and I particularly need to scroll often!).
The main thing is that I know that Beryl should work fine on my system (because it worked perfectly on my old Dapper 6.06 box through XGL).
By the way, my system specs are:

AMD Athlon XP 2000+ (working at 1.67 Ghz)
1 GB DDR SDRAM @ 400 Mhz
ATI Radeon 9600 Generic (that's what glxinfo says...)
MSI KT4V (with VIA KT400 chipset on it, horrible thing if you ask me)

When I was running Beryl on Dapper, everything worked fine with the proprietary ATI Driver (fglrx) through XGL, but when I've switched to Edgy and installed open source drivers running through AIGLX, it is really slow. I suspect that I need to add some more values to my xorg.conf file, but I don't want to, because I've screwed it up the first time (found some values on official Ubuntu forums) and then I had to get to recovery mode and use nano to remove those values to get X back to work (otherwise it would just get me to a console login screen and when I type startx it says it cannot connect to X server).

If that will help, I've attached my current xorg.conf file for you to review and tell me what else I should add to it, because I think the problem is in misconfiguration of X server.
Thanks in advance, and sorry for the long post :D

---

### Post by Waappu on 2007-01-04
Hi

Try to change

> Option		"AccelMethod"	"EXA"
to
> Option		"AccelMethod"	"XAA"

or
> Option		"XAANoOffscreenPixmaps"
to
> Option		"EXANoOffscreenPixmaps"

XAA should be faster.

If you having line
> Option		"AccelMethod"	"EXA"
then you should have this
> Option		"EXANoOffscreenPixmaps"
not this one
> Option		"XAANoOffscreenPixmaps"

And disabling blur plugin from Beryl settings might help

---

