---
title: "Performance"
date: 2005-10-07
forum: Gaming &amp; Leisure
---

### Post by bugmenot on 2005-10-07
Hi, I'm new to Linux and a little unsatisfied with how UT2K4 plays. It plays better on my dual boot Windows and I was wondering if there were any tricks you guys know to boost the performance a little bit? Also, how can I find the equlivant of an .exe in Ubuntu? I want to make Gaim launch when Ubuntu boots up but it asks me to find it, and I don't even know where it is
Oh and Ubuntu itself feels a little choppy, for instance, when I open a new tab in Firefox it's like the computer freezes for a few seconds or goes VERY slow, not the same in Windows. How come?

---

### Post by Dr. Nick on 2005-10-08
I can try to  help, I run the ut2004 demo fine. What type of video card you have, and have you installed and configured the drivers? About gaim, go to prefrences or administration then sessions than startup and just add gaim. you dont need to know the location of the executable just the command should work, about the general slugishness I cant comment sorry

---

### Post by bugmenot on 2005-10-08
I have a Radeon 9200 with drivers installed and configured correctly

---

### Post by Dr. Nick on 2005-10-08
That should be good enough, Whats the rest of your system like? Do any ohter games play correctly or have you tried yet. I really dont know of anything specifically that would make it real slow

---

### Post by bugmenot on 2005-10-08
I didn't try any other games yet. I have a Celeron 2.5 with 768 MB RAM

---

### Post by Perfect Storm on 2005-10-08
Maybe it's a good idea that you try some other games which requires 3D acc. to eliminate the possibilities if it's the game itself or your OS/3D card

By the way, what's the output when you write 'glxgears' in the terminal? It's well known that the ATI driver for linux sux (blame the ATI staff for that).

---

### Post by Curlydave on 2005-10-08
Oh, this is an easy one. 

Your problem with UT2k4 running much slower in Linux than it does in Windows is because you're using an ATI card. It will simply run much slower than in Windows , and there's nothing you can do about it at the moment. Nvidia users do not have this problem.

Your problem with Ubuntu being slow based on what you see in Firefox is actually Firefox-in-Linux being slow, not Ubuntu or Linux in general. I get the paush in tabs, scroll lag, slow start-up times etc in FF too. This is a known issue that is only present in the Linux version of FF. I would recommend using Epiphany which can be found in Synaptec to correct this. At first I as well thought that Linux was really slow as well, but then I realized that it's because the programs I used most, Open Office and FIrefox are just really slow. (FF is fast in Windows, but OO is just as slow in Windows)

---

### Post by bugmenot on 2005-10-08
I got 1273 frames in glxgears...
Would I get a much better performance boost with FX 5500?

---

### Post by TheIdiotThatIsMe on 2005-10-09
[QUOTE=bugmenot]I got 1273 frames in glxgears...
Would I get a much better performance boost with FX 5500?[/QUOTE]

I have a Geforce FX 5500 AGP and I get in the 1300 range, so not too much of a performance boost. However it should run much better as an Nvidia card.

---

### Post by bugmenot on 2005-10-09
Not sure =(, I switched to nVidia yestarday, I'm getting 23xx in glxgears and ut2k4 has worse performance..

---

### Post by SillyHalfMexican on 2005-10-10
[QUOTE=bugmenot]Not sure =(, I switched to nVidia yestarday, I'm getting 23xx in glxgears and ut2k4 has worse performance..[/QUOTE]


You sure you removed the ATi drivers and have the most recent version of the nVidia drivers?

I read some where on the forums that the newest drivers for Linux only helps out a 7800 series card and that nVidia has dropped support for older cards, not sure if the 5500 was in there.  If it was, thats probably why your getting the performance loss as well.

How many FPS are you getting in UT2k4 in Ubuntu compared to what you get in Windows?

There's also a Linux version of UT2k4 isnt there?  Not emulated in Wine, if so, what are you doing?  Running it through Wine/Cadega or w/e, or running the actual Linux rls?

Nothing else I can really think of though, sorry if that doesn't help at all.

---

### Post by bugmenot on 2005-10-10
Yes I even unisntalled Ubuntu, my card works on those 77's but obviously horribly. I tried setting the 66's but it wouldn't build the kernel module or something. I'm running the native version of ut2k4 and in Windows it's smooth, in Ubuntu it's pretty bad and VERY bad when I look into long distances. I'm extremely disappointed

---

### Post by Curlydave on 2005-10-10
[QUOTE=bugmenot]Yes I even unisntalled Ubuntu, my card works on those 77's but obviously horribly. I tried setting the 66's but it wouldn't build the kernel module or something. I'm running the native version of ut2k4 and in Windows it's smooth, in Ubuntu it's pretty bad and VERY bad when I look into long distances. I'm extremely disappointed[/QUOTE]

UT2k4 is runable in Windows with a 9200, if you use a low res, no AA, no AF and use low settings. Do not attempt in Linux. It's not going to happen until ATI gets better drivers. I'm using an x800 pro and while I do get quite decent performance in UT2k4 even in Linux, it's no where near what it is in Windows.

---

### Post by bugmenot on 2005-10-10
Isn't there any user modified/tweaked drivers around? Windows has a lot of good ones, like [www.dna-drivers.com](www.dna-drivers.com), theyre great

---

### Post by Dr. Nick on 2005-10-10
No tweaked drivers that I know about, So you have a nVidia card in their now?
If so could you check your Xorg.conf file and maybe post it here. I have the ut2004 demo and it is very playable on my card which is basically a gf4 mx440
Im looking for the last 3 "options", mainly the 2nd as the others deal with compositing I believe which isnt a issue here, do you have those? Other places say that they help, I havent tried without them but I get good performance with them.

```

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection
```

About your driver version, I dont know what difference it makes, I have the 7667 from the breezy distro on a card released before the 5000 series of nvidias and I dont have a problem. Of course we all have a different definition of unplayable but yours sounds really unplayable, not just someone whos dissapointed they only get 60ish fps :)

In UT2004 once your in a game of any type hit"~" then "stat fps" for you frame rate if you didnt know how, I average about 20-30

---

### Post by bugmenot on 2005-10-11
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

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
	#Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
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
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"FX 5500"
	Driver		"nvidia"
	Option		"UseFBDev"		"true"
	Option 		"RenderAccel" 		"true" 
	Option 		"AllowGLXWithComposite" "true" 
EndSection

Section "Monitor"
	Identifier	"eView 17f2"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"FX 5500"
	Monitor		"eView 17f2"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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

```

---

### Post by Dr. Nick on 2005-10-12
What happens when you remove the # before glcore and dri, Can you boot up X with them options enabled, It seems that GLcore would help since ut2004 runs in opengl, not sure what all GLcore controls but its worth a try to enable it and see if it works

---

### Post by bugmenot on 2005-10-12
Well actually they were enabled, I disabaled them because someone told me that would help cuz theyre not important and might hurt performance. I didn't see any difference anyway

---

### Post by Dr. Nick on 2005-10-12
I just noticed something in your Xorg.conf that looks interesting, Do you have an onboard video card? I noticed you have no "BusID" set. I heard you must set one if you have multiple video cards, not sure if its a must if you only have a agp and no onboard though.

If that doesnt help I doubt your xorg is the problem.
Also type ```
glxinfo | grep rendering
``` and make sure it says ```
direct rendering: Yes
```

I just started having the opposite problem that you have, my ut2004 runs wayyyy to fast to play. The FPS stayed the same as before appx 24 but everything moves so fast like "fast-foward", interestingly this only happens on the 64bit only demo which is an older version. A newer 32/64 bit demo behaves fine so I am wandering if maybe your 3d accel is good but its a ut2004 config error, I will look at mine but I doubt i'll find a fix as I havent changed any options.

---

### Post by bugmenot on 2005-10-12
There's not BusID because the default busid that was set didn't work and I didn't know what it was so I left it blank, and it worked. and yes direct rendering is on

---

### Post by Dr. Nick on 2005-10-13
Oh, I dont know what the problem is, like I said I just developed a problem with it as well on my computer. Other games using opengl play fine so I assume its a ut2004 problem , I just dont know why it never showed up before now since I didnt change a thing in it or my system in general that I know of. Anyone else have any ideas? Ill mess with it some and if I see anything intresting Ill post back , but to me atleast your system looks capable and configured correctly so I am baffled

---

### Post by DarkManX4lf on 2005-10-13
[QUOTE=bugmenot]I have a Radeon 9200 with drivers installed and configured correctly[/QUOTE]


not dissing your config, but i would think that you need a better video card, something like 9600/5600 or better

---

### Post by bugmenot on 2005-10-13
Umm some people can't really afford a good card? Well I can lol but I don't have an AGP/PCI-E card and my dad is pretty cheap so im not gonna get a new mobo just for a good card. Next year when I can start working I'll get a custom build comp

---

### Post by delirium on 2005-10-16
Uhhh, I kind of think you need the BusID as it gives xorg the location of your graphics card....

Type lspci into console, and then find your graphics card.  It should have an address like: 0000:00:1f.5 or something.  Translate the numbers after the colon from hexademical to decimal, and then use those as your busId.

---

