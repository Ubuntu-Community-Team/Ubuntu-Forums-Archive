---
title: "Google Earth problem"
date: 2007-04-06
forum: Desktop Environments
---

### Post by geovino on 2007-04-06
I recently installed Google Earth via Automatix2 and when it started up the globe would not stop zooming in and it was just very jittery. it just kept blinking and zooming in an out. I have a Nvidia video. since it wouldn't work I uninstalled it. 

What would cause this problem?

I'm using 6.10

---

### Post by benerivo on 2007-04-06
This sounds exactly like a graphics card problem. Are you sure you have the nvidia drivers installed? You can do this through automatix.

---

### Post by homerhomer on 2007-04-07
This fixed my google earth splash screen issue. I use the fglrx driver for my crappy ATI card for my laptop. recently I installed Googleearth and couldn't get past the splash. 


I changed my xorg.conf  ati section to look like this and it worked. 



Section "Device"
	Identifier  "Generic Video Card"
	Driver "fglrx"
    	Option "VideoOverlay" "on"
    	Option "OpenGLOverlay" "off"
    	Option "DRI" "true"
    	Option "ColorTiling" "on"
    	Option "EnablePageFlip" "true"
    	Option "AccelMethod" "EXA"
    	Option "XAANoOffscreenPixmaps"
    	Option "RenderAccel" "true"
	Option "AGPFastWrite" "on" 
    	BusID  "PCI:1:5:0"
EndSection


Hope this helps 

:D

---

### Post by geovino on 2007-04-10
I installed the Nvidia Settings and it's all checked except X display which is says to leave unchecked. I then installed Google Earth again and I get a message that my video card is not configured. How do I configure it?

I have a MSI motherboard K8N Neo4-F Nvidia nForce4

---

### Post by Hampster on 2007-08-14
I am using edgy 6.10 and would very much like to install Google earth.  I downloaded what I thought was the program but got      "GoogleEarthLinux.bin"  on my desktop.  Trying to open that was a dead loss.  I have searched for the prog in the repositories or at least I think I have  but I can't find the next step.  I have spent hours reading forum threads and have only learnt that I have a lot to learn.  Can anyone suggest what my next step should be? (After the coffee fix)

Forget this.......  found a thread  got it installed and almost working..  Crashes when I move the mouse.   More research...     [http://ubuntuforums.org/showthread.php?t=195335](http://ubuntuforums.org/showthread.php?t=195335)

---

### Post by geovino on 2007-08-14
Google maps work so well that I have no need to try to configure Google Earth.

---

