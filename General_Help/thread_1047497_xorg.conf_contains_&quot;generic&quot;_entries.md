---
title: "xorg.conf contains &quot;generic&quot; entries"
date: 2009-01-22
forum: General Help
---

### Post by robwencke on 2009-01-22
Hello,

I am fairly new to Ubuntu.  I have a Cisco MCS 7825 H3 Server on which I am running Intrepid Desktop amd64.  I have a Samsung SyncMaster 2032nw (20") monitor which has a 1680 x 1050 native resolution.

I am not able to choose my native resolution from the available GUI.  The highest available resolution is 1440x900.

The posts I have found addressing this issue instruct you to find the section called "Display" and add your native resolution to "modes".  I cannot find the "Display" section in my xorg.conf file.  Here is what my xorg.conf file looks like:

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

That is the only uncommented section in the file.  I'm sure I am going to kick myself when I learn of what I am missing.  Thank you for your help.

Rob

---

