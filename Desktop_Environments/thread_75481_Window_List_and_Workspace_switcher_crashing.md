---
title: "Window List and Workspace switcher crashing"
date: 2005-10-13
forum: Desktop Environments
---

### Post by bryan986 on 2005-10-13
I am running dual monitors with two x servers

My window list and workspace switcher applets seem to be crashing frequently, sometimes they just disappear, other times I get a crash dialog box which refers to wnck-applet

What should I do?

---

### Post by chartek on 2005-10-21
It's happening to me as well and it is really frustrating because it seems to occur randomly. Here are the specs for my computer and then what occurs:

AMD Athlon Thunderbird 1 Ghz
Elsa Gladiac Geforce2 Ultra AGP video card
PNY Geforce4 4000 MX PCI video card (both with 64 MB video ram)
2.6.12-9-k7 kernel with NVIDIA _legacy_ video drivers
* Only occurs with Xinerama turned _off_.

With Xinerama turned off, I have two active workspaces (which I prefer). I have a top and bottom panel on both monitors, with each bottom one containing *Show Desktop*, *Window List*, and *Desktop Switcher* applets. Everytime I try to go to *Preferences* for either Window List applets, an error comes up saying "wnck-applet" has crashed. When I click OK, it proceeds to tell me that all 3 applets on BOTH screens have closed and asks me if I want to reload them. "wnck-applet" also crashes sometimes when I open up and close an application (such as Synaptic) in one screen, then try to open it the the other. Other times "wnck-applet" seems to crash randomly. 

This only occurs with Xinerama turned off. With Xinerama turned on, no crashes take place.

Another issue I've noticed with Xinerama turned off is that my screensaver no longer works. I can preview it just fine, but when the specified time elapses, nothing happens. Again, it works fine when I have Xinerama turned on.

If anyone can help, that would be greatly appreciated. If you need any further information from me, I would be glad to help. Thanks!

---

### Post by chartek on 2005-10-22
I think I've narrowed it down to a problem between the new version on Gnome in Breezy and having Xinerama turned off. When I change the driver in my xorg.conf file from "nvidia" to "nv", the applets I mentioned still crash repeatedly. This issue was never a problem in Hoary; only with Breezy now and having Xinerama turned off has it caused problems.

Here is my xorg.conf file:
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Primary Card - GeForce2 Ultra"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	#VideoRam	64000
	#Option		"UseFBDev"		"true"
EndSection

Section "Device"
	Identifier	"Secondary Card - GeForce4 MX 4000"
	Driver		"nvidia"
	BusID		"PCI:0:15:0"
	#VideoRam	64000
	#Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Primary Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Monitor"
	Identifier	"Secondary Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Primary Screen"
	Device		"Primary Card - GeForce2 Ultra"
	Monitor		"Primary Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
Section "Screen"
	Identifier	"Secondary Screen"
	Device		"Secondary Card - GeForce4 MX 4000"
	Monitor		"Secondary Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Primary Screen"
	Screen		"Secondary Screen" RightOf "Primary Screen"
	Option "Xinerama" "On"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```
Anyone having the same problems? Thanks!

---

### Post by RYX on 2005-10-22
I have a similar problem (so I guess it's not just a Breezy-thing) - sometimes after starting or rebooting the system... everything works just fine, but the window list and the workspace switcher hang up and need a restart... I think this could be a bug in the gnome-panel (I had similar problems under SUSE, where the Update Notifier crashes randomly on system start) ...

---

### Post by kitsos on 2005-10-24
I have exactly the same problem here. 

After spending 1 full day to get my ATI X600 working with fglrx on my 64-bit ubuntu laptop(many thanks to the ubuntu developer that provided a working package and instructions-because ATI $#^$% up) I managed to get a running dual monitor setup.

It seems that when I open an application in one monitor and then try to open another application in the 2nd one, Window List and Desktop switcher crash. This happens regardless of what monitor i start the first application in. It only happens  when i try to open applications in different monitors and not for consequent apps on the same monitor.

It looks as if there's some sort of conflict between the two window lists/Desktop switchers open in two different desktops... Are multiple instances of these apps for the same user known to work ok?

I also don't have Xinerama turned on.

Let me know if you need my xorg.xonf.

Any help would be reeeeally appreciated guys!

Cheers

---

### Post by pauljwells on 2005-10-26
I just changed from BigDesktop (two monitors running off an ATI X600) to Dual Head two monitors with separate X DISPLAY. I'm sure you all know this stuff...
Anyway, with Dual Head I get panel crashes, wnck-applet (I felt like replacing the n with an a...) Back with BigDesktop it all goes away... I still only get the screensaver on the left monitor (better than no screensaver on the dual head) but I can live with that.

---

### Post by kitsos on 2005-10-28
[QUOTE=pauljwells]I just changed from BigDesktop (two monitors running off an ATI X600) to Dual Head two monitors with separate X DISPLAY. I'm sure you all know this stuff...
[/QUOTE]

How did you get Big Desktop working? I use the aticonfig generated file from scratch with the -f option and --dektop-setup=Horizontal and although the second monitor has that gray X server background i can't get anything more on it (the mouse pointer does't even go there). Could you post your xorg.conf plz?

Cheers

---

### Post by hudson on 2005-11-27
[QUOTE=kitsos]I have exactly the same problem here. 

After spending 1 full day to get my ATI X600 working with fglrx on my 64-bit ubuntu laptop(many thanks to the ubuntu developer that provided a working package and instructions-because ATI $#^$% up) I managed to get a running dual monitor setup.

It seems that when I open an application in one monitor and then try to open another application in the 2nd one, Window List and Desktop switcher crash. This happens regardless of what monitor i start the first application in. It only happens  when i try to open applications in different monitors and not for consequent apps on the same monitor.

It looks as if there's some sort of conflict between the two window lists/Desktop switchers open in two different desktops... Are multiple instances of these apps for the same user known to work ok?

I also don't have Xinerama turned on.

Let me know if you need my xorg.xonf.

Any help would be reeeeally appreciated guys!

Cheers[/QUOTE]
I had the same problem for the last month, and finally found the fix - and its not what I thought it would be.

Just registered so I could post it so everyone else can try it (I had the same problem - dual monitors, window list would crash all the time).

Solution: 

Step 1: Even though your monitors appear to work properly at a certain frequency, you will have to experiment with them to find out which frequesncies work properly - in other words, if both monitors don't initialize properly when you log in, then, even after changing the frequency using the caplet and getting it to work doesn't mean anything if it still doesn't initialize properly at the next login.

Step 2: Now that both monitors initialize properly on login, get rid of the Window List capplet (the one that says "switch between open windows using buttons). You can only run 1 instance of it max (and even then its dicey on dual monitors)

Step 3: Now you can add the Window Selector (switch between open windows using a menu) to the bottom panel (I know, most people put it on the top, but you'll find that it works nice on the bottom right beside the workspace switcher).

Ths had been bugging me for the last month. I can live without the "switch between aps by clicking a button on the panel" as long as I have the windows list, and it is a cleaner solution, anyway.

---

