---
title: "Resolution stuck at 640x480"
date: 2005-04-08
forum: Desktop Environments
---

### Post by brymaster on 2005-04-08
Just installed the new Ubuntu 5.04 hoary on my machine and the resolution is stuck at 640x480 and 60hz.  I did NOT have this problem when trying out the 5.04 RC live cd.  Linux for humans? They can't even get Xorg setup right.

Sony Trinitron Multiscan G400
Nvidia Geforce 3 Ti200

Never had such a problem on the numerous linux distros i've tried over the years.  A quick look around the forums suggests that this problem has been around for a while.  

Back to a linux distro that can actually do basic setup correctly.

---

### Post by sparks40 on 2005-04-08
I have the exact same problem! I'm using a using a Gigabyte (845GE) motherboard with a Viewsonic A75f Monitor. 

The kicker is that I had the previous version of Ubuntu "hoary hedgehog 5.04" working perfectly with 1024 x 768 resolution. I downloaded the final version nad installed this morning, but the "only" resolution I can get is 640 x 480... two steps forward and one step back. 

I tried setting up the video several times using xorgconfig but irrespective of the values I entered the output remained at 640 x 480... so something has changed in the hardware detection system or the video card database. I've been working on this for over three hours and thought  that I was the only one experiencing the problem.

If anyone has a solution please post the results.

TNX

---

### Post by Mr Black on 2005-04-08
yeah, I have this same problem.  I was running Ubuntu 4.10 (Warty) and I was able to run at 1024x780, but ever since I installed 5.04 (Hoary) I can't get my resolution any higher than 640x480.  I'm using a Asus motherboard (P4S800) with a ATI Radeon 9200SE video card and a ViewSonic VA520 monitor.

---

### Post by Jezze on 2005-04-08
Perhaps a stupid question but what different Modes exists in your /etc/X11/xorg.conf file? If you know you can set some other resolution just add the resolutions you like for each color depth.

---

### Post by Mr Black on 2005-04-08
Ok, after reading through some other posts people said to add the resolutions to the /etc/X11/xorg.conf file.  The only problem is that when I went to the file all of the resoltuions my monitor supports were already in the file, but I still couldn't use them.  I even tried rebooting, but they would come up.  

Then I saw someone say that they ran the command *sudo dpkg-reconfigure xserver-xorg*.  I ran that, then rebooted and everything was working just fine. You could just restart the windowing system, but I figured I would just reboot.  

This worked for me and hopefully it will help someone else out as well.

---

### Post by brymaster on 2005-04-08
Running sudo dpkg-reconfigure xserver-xorg didn't fix it for me.

---

### Post by sparks40 on 2005-04-08
The xorg.conf file lists the following four modes:
1280x1024
1024x768
800x600
640x480

When I try to adjust the resolution from the main menu the only resolution that shows up is 640x480.

---

### Post by sparks40 on 2005-04-08
The xorg.conf file lists the following four modes:
1280x1024
1024x768
800x600
640x480

When I try to adjust the resolution from the main menu the only resolution that shows up is 640x480.

---

### Post by brymaster on 2005-04-09
Well, I just compared the xorg.conf file generated from the livecd from the one that the install makes and they are identical.  What else is causing this problem then?

I've tried dpkg-reconfigure xserver-xorg 10 times and no configuration works.

---

### Post by sparks40 on 2005-04-09
After a few hours of sleep I decided to try to edit the xorg.conf file. As per a previous respondent's suggestion I added the following two lines to the file in the Monitor section:

HorizSync 31.5-70
VertRefresh 50-100

I rebooted and I finally was able to get  to my preferred resolution of 1024x768. However, I was still unable to adjust the sync rate via the menu item "preferences" aplet... but thats a problem for another day.

Thanks to the previous poster of this information... I appreciate it.

---

### Post by clparker on 2005-04-10
Well, that seemed to do it for me! The Real Solution for this problem seems to be that YOU HAVE TO SPECIFY the frequency of your monitor in the xorg.conf file. I had to tinker with it through trial and error, but i think it's safe to say you should leave a wide margin in there let's say 30-95 and maybey even 60-160 to give you elbow room, i mean it will reset if you got out of range. IM me if you need help.

---

### Post by daniels on 2005-04-10
If your lucky, your monitor picks up on it and tells you that the sync rate is too high.  If you're unlucky, the last thing you hear before your face is sprayed with flying glass shards is 'boom'.

---

### Post by telmo on 2005-04-10
[QUOTE=daniels]If your lucky, your monitor picks up on it and tells you that the sync rate is too high.  If you're unlucky, the last thing you hear before your face is sprayed with flying glass shards is 'boom'.[/QUOTE]

Please say you're joking!  :roll:

---

### Post by trenths on 2005-04-10
You can probably get the resoultion combos and the vertical and horizontal sync frequencies from your CRT manufacturer's website. Load xorg.conf in gedit while you are in root terminal and then just find the section in xorg.conf that cntains that line (or lines). Edit the numbers to correspond to the resolutions sync frequency capabilities of your CRT. I just did it to mine today because Ubuntu fixed my refresh rate at 60 hz. After doctoring the V and H sync frequencies in xorg.conf and rebooting, Ubuntu detected it at 85 hz.

---

### Post by clparker on 2005-04-11
Yeah, just find the model number of the monitor, and google it and find the Vert and Horz frequencies, and then input them.

---

### Post by stoneguy on 2005-04-11
I had this problem with HoaryLive on one system I access. The Samsung monitor wasn't detected properly, and it was labelled "generic". Look at xorg.conf while you're editing it to put in the freq lines to see whether this was your situation too.

Too bad so many people are hitting this problem. It's enough to disqualify the distro from a Grandma's Seal of Approval Award.

---

### Post by trenths on 2005-04-11
Well, I noticed that the Ubuntu post base install setup, unlike Fedora, does not give you an opportunity to choose the make and model number of the CRT from a list. I think that's the problem.

---

### Post by muscl3s on 2005-04-11
I just installed Ubuntu today for the first time and I too have this same problem.  It's stuck in 640x480.  Other than this problem I like hoary thus far  :-?

---

### Post by mstrymn on 2005-04-15
Here's a short guide on the problem.

[http://www.ubuntuforums.org/showthread.php?t=27113](http://www.ubuntuforums.org/showthread.php?t=27113)

---

### Post by Cheizzz on 2005-04-16
i'm having the same problem, when i boot i'm stuck at 640 x 480 with 60 Hz.
when i try to change the resolution via the resolution programme in the preferences tab it says this: (in dutch) 

De X-server ondersteunt de XRandR-uitbreiding niet. Het dynamisch veranderen van de weergavegrootte is niet mogelijk.

(translated to english)

The X-server doesn't support the XRandr-expansion. the dynamical changing of the resolution isn't possible.

i had the problem before, but after a few reboots it just worked again, now i seems to stay

i'm using a Asus radeon 9600xt with the fglrx driver. i'm having some other problems with this card, the colours are sometimes fucked up. for example, my icons in firefox are crap.

my /etc/x11/xorg.conf file:
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Identifier	"ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

could anyone help me?

---

### Post by kromag on 2005-04-16
[QUOTE=daniels]If your lucky, your monitor picks up on it and tells you that the sync rate is too high.  If you're unlucky, the last thing you hear before your face is sprayed with flying glass shards is 'boom'.[/QUOTE]
 OMG I've been picking monitor glass from my face for a week now. LOL! I still never got the resolution fixed even with all the help. Sorry to say I gave up. I do like the Ubuntu distro though and would like to wait until this problem is fixed in the next version. Thankx for the laugh I needed that.

kromag: fedora wearing fool

---

### Post by andlinux21 on 2005-06-18
I just went into the conf file and changed the default depth to 16 and that worked for me.

---

