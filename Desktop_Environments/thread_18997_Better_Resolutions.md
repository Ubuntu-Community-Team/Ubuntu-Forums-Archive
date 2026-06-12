---
title: "Better Resolutions?"
date: 2005-03-09
forum: Desktop Environments
---

### Post by JMY1983 on 2005-03-09
How do I get Ubuntu to a better resolution and refresh rate? This 1024x768 @ 60 is tearing up my eyes!

---

### Post by krusbjorn on 2005-03-10
[QUOTE=JMY1983]How do I get Ubuntu to a better resolution and refresh rate? This 1024x768 @ 60 is tearing up my eyes![/QUOTE]

one way is too add the resolutions you want in /etc/X11/XFConfig-4  using your favourite text editor (you'll see where to type them in, when you open the file)
be sure to only add resolutions you know your monitor and graphics card can handle though ;)

---

### Post by JMY1983 on 2005-03-10
I can open that file with gedit but I can't type anything in for some reason.

---

### Post by eternity on 2005-03-10
[QUOTE=JMY1983]I can open that file with gedit but I can't type anything in for some reason.[/QUOTE]

That's because only root has permissions to edit the file.

Run this command:
sudo gedit /etc/X11/xorg.conf

---

### Post by JMY1983 on 2005-03-10
[QUOTE=eternity]That's because only root has permissions to edit the file.

Run this command:
sudo gedit /etc/X11/xorg.conf[/QUOTE]
 Xorg.conf is blank, what do I put in there?

---

### Post by rosslaird on 2005-03-10
Either you mis-typed the name of the file (on my system, the file is called /etc/X11/xorg.conf) thereby accidentally creating a new (blank) file, or you are using XFree86, in which case the file is called /etc/X11/XFConfig-4 (I think). In either case, the file is there or you wouldn't have a graphical screen.

In a console, type this:

cd /etc/X11
ls

This will show you a file listing, and you will be able to see which file (XF86 or xorg) you want. Then:

sudo gedit xorg.conf
or
sudo gedit XFConfig-4

But don't just go making changes willy-nilly to this file. Do some research (exstensve posts exist on this forum about this subject). If you mess it up, your Gnome session will not start. At minimum, set a default depth, a default refresh rate, and a preferred resolution. For example, the relevant sections on my system look like this:

Section "Monitor"
	Identifier	"Samsung 193P (SyncMaster)"
	Option		"DPMS"
	HorizSync	60
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"Samsung 193P (SyncMaster)"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection

Ross

---

### Post by Azyx on 2005-03-10
In mine Ubuntu  (Warty) i have XF86Config-4, but not XFConfig-4 in that folder. but look in the X11-folder like Ross shown.

But JMY1983. do you have gnome? If so, go to Computer--> System configuration --> Sceen Resolution. There you may change your resolution and refresh-rate.



[QUOTE=rosslaird]Either you mis-typed the name of the file (on my system, the file is called /etc/X11/xorg.conf) thereby accidentally creating a new (blank) file, or you are using XFree86, in which case the file is called /etc/X11/XFConfig-4 (I think). In either case, the file is there or you wouldn't have a graphical screen.

In a console, type this:

cd /etc/X11
ls

This will show you a file listing, and you will be able to see which file (XF86 or xorg) you want. Then:

sudo gedit xorg.conf
or
sudo gedit XFConfig-4

But don't just go making changes willy-nilly to this file. Do some research (exstensve posts exist on this forum about this subject). If you mess it up, your Gnome session will not start. At minimum, set a default depth, a default refresh rate, and a preferred resolution.

Ross[/QUOTE]

---

### Post by matgorb on 2005-03-10
One question first: What is you monitor first?

(I mean 1024*768@60Hz is normal for LCD 15")

---

### Post by rosslaird on 2005-03-10
Mine is a 19 inch LCD.

60 is the normal refresh rate for my monitor. I can set it higher, but then X refuses to fill the entire screen, and the quality of the images does not improve. So 60 is fine.
If you have a 15 inch LCD, 1024x768 is probably the right resolution.

---

### Post by JMY1983 on 2005-03-10
[QUOTE=rosslaird]Mine is a 19 inch LCD.

60 is the normal refresh rate for my monitor. I can set it higher, but then X refuses to fill the entire screen, and the quality of the images does not improve. So 60 is fine.
If you have a 15 inch LCD, 1024x768 is probably the right resolution.[/QUOTE]
 I have a Viewsonic G220fb CRT. I run windows in 1600x1200 @ 85 every day. Linux hasn't recognized my monitor for what it is.

And Azyx, I have tried what you said but I only have 3 low resolution choices and no other refresh choices.

---

### Post by matgorb on 2005-03-10
It is all about the XF86Config-4

The specs of your monitor are I believe:

Frequency Fh:30~110kHz; Fv:50~180Hz

so you need to put this in your XF86Config-4 or xorg.conf

I had the same problem with my 21" Iiyama, it would not take 1600*1200@85 because Ubuntu didn't have the right settings for X, I changed it, and it worked perfectly since then.
I assume you can do this by yourself otherwise post you X config file.

mat

---

### Post by JMY1983 on 2005-03-10
[QUOTE=matgorb]It is all about the XF86Config-4

The specs of your monitor are I believe:

Frequency Fh:30~110kHz; Fv:50~180Hz

so you need to put this in your XF86Config-4 or xorg.conf

I had the same problem with my 21" Iiyama, it would not take 1600*1200@85 because Ubuntu didn't have the right settings for X, I changed it, and it worked perfectly since then.
I assume you can do this by yourself otherwise post you X config file.

mat[/QUOTE]
 What I am wondering is where in the file you enter the actual herz range?? I didn't see that in anyone else's posts.

---

### Post by JMY1983 on 2005-03-10
Here is my config. It still doesn't let me change to my new resolutions in system preferences. 


Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Viewsonic G220fb"
	HorizSync	30-110
	VertRefresh	50-180
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Viewsonic G220fb"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by daniels on 2005-03-10
Just remove the HorizSync and VertRefresh lines altogether, and a world of high refresh rate will be yours (this bug has been fixed in Hoary, largely).

---

### Post by JMY1983 on 2005-03-11
[QUOTE=daniels]Just remove the HorizSync and VertRefresh lines altogether, and a world of high refresh rate will be yours (this bug has been fixed in Hoary, largely).[/QUOTE]
 Thank you, will that work for the resolutions as well?

---

### Post by matgorb on 2005-03-11
Isn't that a little bit dangeroust do that?
I mean how X will know where to sop?


Did you reboot yet, cause I have a smaller range and I still can get it at 75Hz.
Are you using hoary or warty

in warty the file is /etc/X11/XF86Config-4
in hoary it is /etc/X11/xorg.conf

---

