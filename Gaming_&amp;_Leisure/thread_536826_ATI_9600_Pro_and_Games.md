---
title: "ATI 9600 Pro and Games"
date: 2007-08-28
forum: Gaming &amp; Leisure
---

### Post by whistlerspa on 2007-08-28
Am unable to get the following games to play properly

Nexuiz - freezes to black screen almost as soon as I start to play
Open Arena - between 10  - 30 seconds before the same
Sauerbraten - same as Nexuiz

Alien Arena works OK though

I'm using the propriety ATI drivers so gl is active - I have an Acer 1714 LCD monitor and an Athlon 2400 chipset on a Gigabyte motherboard with 1,260 Mb of SD-DDR RAM (333MHz).

Frame rates are good for the seconds or so the games run. The ATI control panel says I'm in clone mode.

I wonder why am I unable to run these games successfully?

---

### Post by whistlerspa on 2007-09-01
Solved I myself in the end thanks to a posting I found here

[http://en.opensuse.org/Using_Xgl_on_older_versions_of_SUSE_Linux](http://en.opensuse.org/Using_Xgl_on_older_versions_of_SUSE_Linux) and another source for one line so I'll post in case any one else has the problem. 
        
In etc/X11/xorg.conf under 

Section    "Device"
               "Identifier"     "ATI Radeon 9600" 

change the first option below from "yes" to no" and then insert the next two lines

        Option 		"EnablePrivateBackZ" "no"
	Option          "VideoOverlay"          "on"
	Option 		"AGPv3Mask"	 "0x00000002"

Then in 
Section    "Extensions"    add the line
                 Option 		"DAMAGE" 	"no"

Worked for me anyway.

---

