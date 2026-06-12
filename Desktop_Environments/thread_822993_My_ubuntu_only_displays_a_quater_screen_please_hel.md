---
title: "My ubuntu only displays a quater screen please help"
date: 2008-06-08
forum: Desktop Environments
---

### Post by Sexysexter7 on 2008-06-08
I just finished downloading ubuntu today using the program that lets you install it inside of windows and choose it on boot up, any ways i was downloading some stuff updating it whatever shut it off and i came back after dinner and windows booted so i shut down and choose ubuntu and some how i got only a quarter screen but i can still click my buttons just i cant see any but the top left corner any help would be appreciated thank you

---

### Post by sammi.jo on 2008-06-08
Sounds like your resolution is too high. 

First, back up your xorg: sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

If you can get to a terminal, type in 'sudo gedit /etc/X11/xorg.conf and scroll down til you see your screen resolutions. Fix accordingly.


Alternatively, try > sudo dpkg-reconfigure xserver-xorg and going through the options til you can set a resolution.

If you can't get into a terminal manually, press alt+f2 and type that in the box, and click 'run in terminal' underneath it. Here is a copy of my xorg screen section, just for reference.

> Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
	Depth 1
	Modes "1280x800" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 4
	Modes "1280x800" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 8
	Modes "1280x800" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 15
	Modes "1280x800" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 16
	Modes "1280x800" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 24
	Modes "1280x800" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

If all goes wrong when you restart x (ctrl+alt+backspace) then go into recovery mode and type in > sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf and restart

---

### Post by Sexysexter7 on 2008-06-08
sorry, i probobly sound like an idiot but whats a zorg and whats a terminal and how do i get to it

---

### Post by sammi.jo on 2008-06-08
It's alright, I'm a noob too!

xorg is what manages your whole display thing. Follow these steps:

Press alt+f2 together

Type 'sudo cp /etc/X11/xorg.conf', **don't do the next step without doing this; you could mess up your graphics!** [without the ' '] press 'run in terminal' and enter.
put in password if needed.

Press alt+f2 together again.
 
Type in the box 'sudo gedit /etc/X11/xorg.conf', click 'run in terminal' and press enter. Put in your password if requested.

When you get the box full of writing, scroll down until you see 'Section "Screen". It'll look like this:

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

If it does, then copy and paste this under 'Device' and on top of 'EndSection':

SubSection "Display"
Depth 1
Modes "1280x800" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x800" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x800" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x800" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x800" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x800" "1024x768" "800x600" "720x400" "640x480"
EndSubSection


**Make sure you change the resolutions to ones that your screen can handle. If in doubt, do 1024x768 at first, then change it to a higher one if you realise that's too small!**

When you've done that, save it, and press ctrl+alt+backspace together. It should bring you back to a login screen that you can see!

---

### Post by Xiong Chiamiov on 2008-06-09
Just a note that it's a good habit to get into using gksudo instead of sudo for graphical apps.  There are some odd things that can happen with permissions if you don't.

---

### Post by oleksus on 2008-06-10
Well, I edited the file as you said, but didn't see any added resolutions in a graphic display selection menu. And after a couple reboots, I found that all those changes were deleted by system, and I can't see any modes there.

How do you set in this conf file, which resolution to actually set the screen to?
Because I edited the file, then reboot, but nothing changes, and I still don't see the resolutions in the list of available ones!

And maybe I should add something in the "Device" section as well?

---

### Post by Zorael on 2008-06-10
Please post the contents of the file after having changed it, so we can see how it now looks. Again, **/etc/X11/xorg.conf**.

---

