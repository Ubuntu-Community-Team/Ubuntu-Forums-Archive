---
title: "Multiple monitors on Samsung N130 netbook?"
date: 2009-12-30
forum: Desktop Environments
---

### Post by Doggonit on 2009-12-30
So, I'm running Ubuntu 9.04 (not the Netbook Remix edition)

When I plugged in a Dell LCD into the VGA port, Ubuntu automatically set it to "mirror" mode, making both displays run at 800x600.

I cannot actually set the resolution in the display preferences any higher in that mode, but I actually want to have the netbook's display at the normal 1024x600 and the external LCD at it's native 1280x1024. But when I set the resolutions to that (having deselected mirror mode), and hit apply, I get the following error message:

> Your settings cannot be applied because the virtual resolution is not big enough to contain your screens

Do I have to mess about in the xorg.conf file or some such? And if so, what should I put in there basically? How do I identify the devices (internal LCD and external) if I were to name them and give them seperate resolutions in the .conf file? I guess that this is a xorg and not a gnome problem, or isn't it?

Basically, I'm lost, well out of my comfort zone, and the only things I found on Google regarding this problem didn't really apply or work.

Thanks in advance,

D.

---

### Post by Doggonit on 2009-12-30
Here is my current xorg.conf from /etc/X11/  [Minus the comments section - I cut that out as it's the default one, and is just long and adds nothing)

> 
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


I checked in the synaptics package manager, and it seems that all the X.org X server driver things were downloaded already, so how come the Mobile Intel 945GM Express Chipset isn't recognized as the proper "Device"? This really worries me.

---

### Post by Doggonit on 2009-12-30
So, apparently I could run multiple X servers? That is: One for the netbook LCD and one for the external LCD? How do I determine which display is which? And can I start a second X server simply from the terminal? Or do I have to do that outside of a current X session? I might be talking utter garbage, I'm really foreign to this aspect of things in Linux (heck, I'm a newbie, really)

---

### Post by cleggton on 2010-01-01
I seem to recall that the Intel Drivers in 9.04 had a bug that didn't allow you to run with a (combined) screen res of >2048 on the horizontal axis if you had 3d acceleration running, I can't remember the work around (but it did mean no 3d) 

There should be plenty of documentation as this was a massive problem for intel users on 9.04.

Alternatively you could upgrade, as the drivers were fixed in 9.10

---

