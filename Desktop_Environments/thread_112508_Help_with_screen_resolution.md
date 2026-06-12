---
title: "Help with screen resolution"
date: 2006-01-04
forum: Desktop Environments
---

### Post by HokeyFry on 2006-01-04
i am using a laptop that is currently using a screen resolution of 800 x 600. I want to get it to 1024 x 768, but I can't figure out how. I have gone thru a HOWTO and a wiki on it, but to no avail. Can someone help me?

---

### Post by sharpenyourteeth on 2006-01-04
i dont mean to hijack this thread or anything, but i'm having a similiar problem so i didnt see a point in starting another thread with the same title. i'm trying to run my resolution at 1600x1200 but nothing i've tried works. the highest resolution it's letting me choose is 1024x768. here is my xorg.conf file: 


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31-80
	VertRefresh	56-76
	# V-freq: 60.00 Hz  // h-freq: 74.69 KHz
	Modeline "1600x1200" 170.89  1600 1688 1896 2288  1200 1200 1203 1244 
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800]"
	Monitor		"Generic Monitor"
	DefaultDepth	24	
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


thanks for the help

---

### Post by thekiller on 2006-01-04
[QUOTE=sharpenyourteeth]i dont mean to hijack this thread or anything, but i'm having a similiar problem so i didnt see a point in starting another thread with the same title. i'm trying to run my resolution at 1600x1200 but nothing i've tried works. the highest resolution it's letting me choose is 1024x768. [/QUOTE]

Are u using nvidia or nv in the graphics cards' driver section ? And make sure you did install nvidia driver cos seems like you have an nvidia graphics card.

And HockeyFry, what graphics card are u using ? Did u specify horizontal and vertical refresh rates correctly for your monitor ? try changing driver to vesa in your xorg.conf under graphics card device.

---

### Post by sharpenyourteeth on 2006-01-04
[QUOTE=thekiller]Are u using nvidia or nv in the graphics cards' driver section ? And make sure you did install nvidia driver cos seems like you have an nvidia graphics card.[/QUOTE]

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

nvidia, and yeah i did install the drivers

---

### Post by thekiller on 2006-01-04
by pressing ctrl+alt+backspace, do u see Nvidia splash screen on your desktop ? And can u tell me the make and model of your monitor please ?

---

### Post by Lord Illidan on 2006-01-04
Try this link : [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by sharpenyourteeth on 2006-01-05
[QUOTE=thekiller]by pressing ctrl+alt+backspace, do u see Nvidia splash screen on your desktop ? And can u tell me the make and model of your monitor please ?[/QUOTE]

sorry for the late response, but yes i do see the splash screen, and i have a dell 2001fp


[QUOTE=Lord Illidan]
Try this link : [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)
[/QUOTE]

i've tried that already, no luck

---

### Post by HokeyFry on 2006-01-05
[QUOTE=thekiller]And HockeyFry, what graphics card are u using ? Did u specify horizontal and vertical refresh rates correctly for your monitor ? try changing driver to vesa in your xorg.conf under graphics card device.[/QUOTE]

I don't know how to check my graphics card, as it is an old laptop and I don't feel comfortable opening it up (last time I almost couldn't close it, long story). I know there is something you type in the shell and it will tell you but I do not know what it is. Also, I do not really know what the refresh rates do, but here they are (i think these are what you are talking about):

HorizSync     31-101
VertRefresh    60-160

And I will try changing the driver to "vesa" and see what happens.

---

### Post by HokeyFry on 2006-01-05
I changed the device name to "vesa" and it changed nothing. Also, I think after paying more attention to the xorg.conf file that my graphics card is by someone named Neomagic, although it could just be the driver for the screen, which is a Neomagic screen.

---

