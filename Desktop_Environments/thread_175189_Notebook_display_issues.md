---
title: "Notebook display issues"
date: 2006-05-12
forum: Desktop Environments
---

### Post by tcarter on 2006-05-12
Hello everyone, I'm a long time Fedora/ Redhat user and I just downloaded ubuntu. I downloaded it initialy on one of my desktops and I like it so much that I decided to put it on an old Dell insiron 1100 notebook. The installation went fine, but for some odd reason, the display is'nt working corrctly. The display looks like a picture that has been matted, with a 3 inch black border around it, and I cant seem to get the thing to stretch out all the way. The display on the notebook is 14", but the desktop looks like it's running in a window.
If anyone has some suggestions on how to fix this, I'd be appreciative of the help. I've tried everything I know to do and no luck. Thanks in advance.
Just for the record, I searched the forums for an hour before asking this.

---

### Post by tcarter on 2006-05-17
Bump.

---

### Post by durableapostle on 2006-05-26
Modify your xorg as follows (sudo gedit /etc/X11/xorg.conf):

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
	HorizSync 31.5 - 48.5
	VertRefresh 59.0 - 75.0
EndSection

Section "Monitor"
	Identifier 	"Monitor0"
	VendorName "Monitor Vendor"
	ModelName "Dell 1024x768 Laptop Display Panel"
	HorizSync 31.5 - 48.5
	VertRefresh 59.0 - 75.0
	Option 		"DPMS"
EndSection


You may have to configure it so that this will load earlier in the start up process--unfortunatly, this is beyond my ability.  Maybe you won't need it, though....

---

