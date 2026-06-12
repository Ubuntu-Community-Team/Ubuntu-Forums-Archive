---
title: "Protech Express Towing Installation Problem"
date: 2009-05-25
forum: General Help
---

### Post by stockbrain on 2009-05-25
Working with a new client - big opportunity (Protech Express Towing)

I thought that maybe the 9.04 would finally includes a good display configuration component... but no. Again, the same s***.

So here we go I've got a lenovo laptop z61m, its a 15' screen and I've got the right resolution for this (1280x800).
Now I have a second 22' screen that I use as an extended desktop.
After upgrade the max resolution I could get was like 1152x852 (or something like that).
After messing with the xorg.cong (****** up, reconfigured) I got a 1280x1024 (5:4) and a 1680x1050 (16:10) options.
1280x1024 looks horribly stretched, and 1680x1050 is out of bounds on left&right side.

The xorg.conf seemed to be different from previous kernel version:

 	Code:
 	Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2960 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection 
I love Linux systems and especially Ubuntu for its ease of use, but this is really annoying, and if I think about someone who would want to try ubuntu for the first time, and then face this kind of problem it would probably turned them down!!

Please help!
Please improve this, make us some good tool to do this! :razz:

So people, do you think the display manager needs improvement?


P

---

