---
title: "Unbuntu and FlightGear on Dell Inspiron 8500"
date: 2007-07-29
forum: Dell  Ubuntu Support
---

### Post by ruarymac on 2007-07-29
Hello Forum viewers,

I am having trouble with FlightGear running on Ubuntu 7.04 installed on a Dell Inspiron 8500.  All seems to work in the small startup screen but as soon as I maximize the window it slows down to an extremely slow rate and is unusable.  The GLXGears demo yields a frame rate of about 300 FPS when its window is maximized, I have loaded new drivers from nvidia and I have also tried setting Environment variables but still it is slow.  I installed FlightGear from the Ubuntu Synaptic Package Manager.  I have not tried building it myself as that seemed rather difficult when i read about it.  I would like to hear from anyone one with any ideas or solutions.  Ubuntu is great and my main aim is to use FlightGear so I can sever my last tie to XP.  Thanks to anyone who can help.

Ruary

---

### Post by Paul S on 2007-07-30
I've got a core 2 duo here and flightgear consumes about 75% of the 2 1.60 Ghz processors in small screen.  I don't know how to go to full screen mode and don't have the time to learn flightgear, but suspect you may be running out of cpu.  Try running "top" in a terminal when you have it running, and check it's usage.

regards,

---

### Post by ruarymac on 2007-07-30
Thanks Paul,

I checked the CPU usage and yes it was using >90% when in full screen mode.  What I have discovered is that by reducing the screen resolution and then returning back to the origonal screen resolution again FlightGear functions well in full screen mode.  I will have to check the CPU usage again to see if there is any great difference.  I have yet to figure out what caused (or causes) it to crash in the first place and will cross that bridge when or if I need to.  So now that I am able to get it to function I am on to the next stage of the FlightGear learning curve - seting up my joystick.  My ultimate goal is to interface it with external home made controls ie. com and nav radios etc.  This is a project I started with MS Flight Simulator and XP for a freind but I have grown to dislike MS so much I have converted to LINUX.

Thanks again,

Ruary

---

### Post by stbub on 2007-08-02
> **ruarymac said:**
> Thanks Paul,

I checked the CPU usage and yes it was using >90% when in full screen mode.
Ruary

FlightGear uses LOTS of different OpenGL functions.  Depending on the graphics card you have, it may be that not everything is done in hardware.  If some effects involve software rendering, then you'd want to disable those effects.

Good luck.

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

