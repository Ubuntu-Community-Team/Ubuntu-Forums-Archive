---
title: "Another &quot;Desktop effects could not be loaded&quot; thread!"
date: 2007-10-29
forum: Desktop Environments
---

### Post by Krunk_Kracker on 2007-10-29
I know theres a few of these already, but non with a definite answer.

I've only been using Ubuntu and Linux for like 3 days now, and really want to to try out Compiz, but cannot get it to load. 

When I type "compiz" in terminal I get this:

> Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity 

Looks to me like all the drivers are loaded, but I do not have xgl supported yet.

This is the video section of my xorg file:
> Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
EndSection


So I know a 9000 is supported, I've seen Beryl and Compiz ran on much less than that.

So, now I did research and tried to download xgl, and this is the outcome:
> sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl


Any help would be extrememly appreciated! Also, what the hell are the copy/paste shortcut keys on Linux? lol

---

### Post by oldos2er on 2007-10-29
Look in your Software Sources to be sure all repositories are enabled.

 I've always used Ctrl-Ins and Shift-Ins for copy and paste.

---

### Post by Krunk_Kracker on 2007-10-29
> **oldos2er said:**
> Look in your Software Sources to be sure all repositories are enabled.

 I've always used Ctrl-Ins and Shift-Ins for copy and paste.
Hmmm....nothing was checked...I checked everyhting and now it's downloading some updates.....

What to do after this?

Thank you very much :D

---

### Post by Krunk_Kracker on 2007-10-29
Uhoh, now that I activated everything, and did "sudo apt-get install xserver-xgl" now it get to the login screen and after I sign in, goes right back in. I can however sign in under failsafe-gnome....any ideas?

---

