---
title: "Can't right click on desktop"
date: 2005-04-12
forum: Desktop Environments
---

### Post by armeck on 2005-04-12
Hey all!

Been lurking around for a few weeks and finally have a need of assitance.  At some point in my upgrade to Hoary (which was before the final release) I lost the ability to right click on the desktop.  I can right click on other items, but for the desktop it just ain't happening.  

Any thoughts?  :neutral:

---

### Post by Xian on 2005-04-12
Check your mouse settings via the Gnome panel menu and see if anything appears disabled, and you also might post the mouse section of your xorg.conf file just to be sure nothing got improperly altered.

---

### Post by armeck on 2005-04-12
Here is the section, apparently one for my mouse and the other for my touchpad:
 ```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
	 Identifier	  "Synaptics Touchpad"
	 Driver		  "synaptics"
	 Option	    "SendCoreEvents"		"true"
	 Option	    "Device"			 "/dev/psaux"
	 Option	    "Protocol"			 "auto-dev"
	 Option 	   "HorizScrollDelta"	"0"
EndSection

```
I also cannot right click with my built in touchpad buttons either, although I can on other items.

---

### Post by chefebe on 2005-06-10
I have the same problem.  I think it is not a mouse issue but a gnome or xorg config issue because the mouse works correctly in all other windows and the panel.  I changed something to cause this because it worked a couple days ago.   For me I lost this ability the same time I noticed my background image was not getting set.  

Any suggestions would be welcome.

---

### Post by Heiny on 2007-11-04
Did someone found a solution for this problem? i'm having the same right now.:(

---

### Post by Heiny on 2007-11-04
ooppss..sorry guys but everything came back just like magic.....don't know what i've done?:confused:

---

### Post by pismikrop on 2007-11-04
try:

sudo cat /dev/input/mice
or
sudo hd /dev/input/mice

and try to right click.

is there any action?

---

### Post by Heiny on 2007-11-04
i don't know for others but for me the only thing i've done to fix this is: ctrl + alt + F1 and i've logged into the console and reboot, after this the system reboot with everything on the desktop working fine...weird?? but that work!

---

### Post by toutatis on 2007-11-11
I had the same problem with right-clicking on my desktop. Also my desktop was empty (no icons) while my ~/Desktop directory was not.
Your solution worked for me too.

Thanks.

---

### Post by TadH on 2007-11-11
this is how to right click on the desktop

alt+f2 type in gconf-editor
go to aps>nautilus>preferences> and click off show desktop and restart x this should solve your problem

---

### Post by TadH on 2007-11-11
alt+ctrl+backspace will restart x when ur done

---

### Post by R3d3y3 on 2008-02-10
This did not work for me, I am still unable to right click on the desktop. I tried deleting all of the .gnome .gnome2 .gconf etc but that did not work either. Any other suggestions?

---

### Post by chiisu on 2008-02-22
Did any of you have this problem after creating another account on your computer?  I've had similar problems, and I'm trying to see if it's related to some kind of config error when another account is created.

---

### Post by chiisu on 2008-02-28
I've re-installed Ubuntu, and I can't seem to reproduce this bug now.  I've gone through the same steps and eveything, but seems to be working fine now.  And this was before Update Notifier showed updated relating to Nautilus...

---

