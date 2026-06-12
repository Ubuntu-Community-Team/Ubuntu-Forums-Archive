---
title: "Flight gear with ati card?"
date: 2007-04-20
forum: Gaming &amp; Leisure
---

### Post by stbub on 2007-04-20
Anyone having any success with flight gear flight simulator?

I've got an asus x300 video card (i.e. ati r300 chipset). 

I get about 1000fps with glxgears, but 1fps with the simulator :-(

I use the open source driver, and am on ubuntu 7.04.

Any hints as to what you are doing to get this running would be much appreciated.

---

### Post by stbub on 2007-04-20
To answer my own questions, I did 2 things:

1) use driconf to disable low-impact fallback so that flight gear doesn't fall back on software rendering of unimportant visuals

2) mv /usr/share/games/FlightGear/Textures.high /usr/share/games/FlightGear/Textures.high.hide

   to use less details


That way, I can get a reasonable frame rate.

---

### Post by ruarymac on 2007-08-02
G'day Mate,

Just a suggestion - check my post on similar problem - search using 'ruarymac'.  It might help you.

Regrads
Ruary

---

### Post by leobuntu on 2007-08-17
Using driconf to disable low-impact fallback bumped my frame rate per second from 1 to 14 on a Latitude D810 with ATI Mobility X600

---

### Post by jelofson on 2007-10-22
> **stbub said:**
> Anyone having any success with flight gear flight simulator?

I've got an asus x300 video card (i.e. ati r300 chipset). 

I get about 1000fps with glxgears, but 1fps with the simulator :-(

I use the open source driver, and am on ubuntu 7.04.

Any hints as to what you are doing to get this running would be much appreciated.

If I use the ATI opensource driver, then I get a situation like you. 2000+ fps glxgears and crap in flightgear. There is some r300 error that comes up in the terminal regarding fallback. I haven't tried driconfig.

If I use the restricted ati driver, flightgear works fine, but I lose all ability to enjoy desktop effects.

---

### Post by visionary on 2008-01-13
Maybe you could try the following which i harvested from some other websites which helped me greatly with Flightgear in Gusty....

1)When you start flight gear, consider starting with the following options in your command.... (You can read more from here [http://mail.flightgear.org/pipermail/flightgear-users/2005-May/010980.html](http://mail.flightgear.org/pipermail/flightgear-users/2005-May/010980.html) )

> --control=mouse
> --disable-intro-music
> --disable-random-objects
> --disable-sound
> --disable-hud-3d
> --disable-specular-highlight
> --fog-fastest
> --model-hz=60
> --geometry=800x600
> --visibility=10000.0
> --fov=50
> 
> --prop:/sim/rendering/static-lod/detailed=500
> --prop:/sim/rendering/static-lod/rough=5000
> --prop:/sim/rendering/static-lod/bare=15000
> --prop:/environment/clouds/layer[1]/coverage="clear"
> --log-level=alert

That actually improved a little.....Now for the biggest improvement i go was to to do the following.....

2) downloaded driconf (sudo apt-get install driconf)

3)Then edit device section of /etc/X11/xorg.conf to show as

Section "Device"
Identifier "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
Driver "ati"
[B]BusID "PCI:1:0:0"
Option "AGPMode" "4"
Option "EnablePageFlip" "true"
Option "AGPFastWrite" "true"
Option "EnableDepthMoves" "true"
Option "GARTSize" "64"
Option "AGPSize" "64"
Option "backingstore" "on"
Option "UseInternalAGPGART" "no"[/B]
EndSection


Though i am using Nvidia card, i added those lines (in bold)  in my xorg.conf file.

Now restart your system and enjoy your flight gear.
Hope that helps!

Cheers!

---

