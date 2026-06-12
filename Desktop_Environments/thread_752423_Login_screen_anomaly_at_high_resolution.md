---
title: "Login screen anomaly at high resolution"
date: 2008-04-11
forum: Desktop Environments
---

### Post by peeple on 2008-04-11
I'm running the hardy beta fyi

normal desktop resolution: 2048 x 1536 @ 67hz
NVidia 6800GT

Has anyone figured out how to fix this without going to 16 bit color mode?

I don't really want to edit my xorg.conf if i don't have to.

This is the problem: 

[IMG]http://www.psu-clan.com/images/login%20screen%20anomaly.JPG[/IMG]

the monitors display settings arent the issue, its a video card resolution issue.

I'd like not to have to change my xorg.conf but...

if you wanna give me suggestions on what to change in my xorg.conf...
```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 8 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Dell"
	Modelname	"Dell P1110"
	Horizsync	30.0-121.0
	Vertrefresh	48.0-160.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
```
...
```

  modeline  "2048x1536@75" 340.48 2048 2216 2440 2832 1536 1537 1540 1603 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes		"1600x1200@60"	"1600x1200@75"	"1600x1200@65"	"1600x1200@70"	"1400x1050@75"	"1600x1200@85"	"1400x1050@60"	"1792x1344@75"	"1280x960@75"	"1792x1344@60"	"1280x1024@60"	"1856x1392@60"	"1280x1024@85"	"1856x1392@75"	"1280x960@85"	"1920x1440@60"	"1280x960@60"	"1920x1440@75"	"1280x1024@75"	"2048x1536@60"	"1152x864@75"	"2048x1536@75"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

Once it logs in everything is fine.

(anyone else update compiz-fusion and get 50% cpu usage?)


Thanks in advance and I apologize for probably beating a dead horse.

---

### Post by Merovius on 2008-04-13
I had this for two days. Mine was worse because the login box was only slightly visible in the lower right corner of the screen.  I fixed it by rebooting into recovery mode and selecting try to fix xorg or something to that effect. (third choice down the list) It fixed it right up. Only drawback was I had to re run Envyng to reinstall my nvidia driver. All is now perfect. :popcorn:

---

### Post by Baul on 2008-04-13
Same here - using a higher resolution than default i.e.640x480 at 50 Hz such as 1024x768 at 66 to 75 Hz caused the login window to become non-centred as you discribed.  (goes off screen bottom right hand corner).

I have had also have problems with compiz enabled with maximise/minimise panels in Open Office and Inkscape (most other applications seem to be okay) - Also emerald does not seem to work at all on my system.  Have tried various suggestions given on the forums but with no luck as yet.

However I should add that I using Hardy Beta (latest update) so it's not so much a complaint as an observation.   However any suggestions always very welcomed!! 

My Machine specs are

AMD 64 Dual Core 4200+
Magic View Plug and Play (quite old from my first computer!)
and
Gainward Nvidia 7800 GS AGP
on a ASRock 939A8X-M motherboard

---

### Post by warp99 on 2008-04-14
Add the resolution to you modes line:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		**Modes		"2048x1536@75" "1600x1200@60"**	
	EndSubSection
EndSection
```

The login screen bases it's mode on 1600x1200, but you have a virtual desktop size of 2048x1536. So add the resolution to your modes line.

---

### Post by captainneb on 2008-04-14
I have this same issue with login screen being a higher resolution than it should be.  In my case, however, the monitor doesn't suppor the output resolution at all and so it goes into standby.  I have been loging in blindly which I really don't want to have to do permanantly. My xorg.conf file doesn't have a 'mode' section in the 'screen' section at all, when I add it and reboot I can see the login page OK as it completely corrupts the video driver and runs a standard driver instead.  I have tried running 
sudo dpkg:reconfigure xserver.xorg   which was suggested elsewhere.  Then it suggested selecting the proper video driver and removing unsuported video modes.  Problem is, when I try this option, there are no options to chose anything for video.  It only makes configureation changes to my keyboard.  Any other solution I have tried results in system not loading video drivers properly.  Does anyone have any other fix's for this problem???

---

### Post by warp99 on 2008-04-14
> **captainneb said:**
> I have this same issue with login screen being a higher resolution than it should be.  In my case, however, the monitor doesn't suppor the output resolution at all and so it goes into standby.  I have been loging in blindly which I really don't want to have to do permanantly. My xorg.conf file doesn't have a 'mode' section in the 'screen' section at all, when I add it and reboot I can see the login page OK as it completely corrupts the video driver and runs a standard driver instead.  I have tried running 
sudo dpkg:reconfigure xserver.xorg   which was suggested elsewhere.  Then it suggested selecting the proper video driver and removing unsuported video modes.  Problem is, when I try this option, there are no options to chose anything for video.  It only makes configureation changes to my keyboard.  Any other solution I have tried results in system not loading video drivers properly.  Does anyone have any other fix's for this problem???

Recently I learned that Hardy doesn't keep the monitor setting in xorg.conf anymore, but in ~/.gnome2/monitors.xml. So you could add a modeline and a monitor mode to your xorg.conf as I suggested in this post:

[http://ubuntuforums.org/showpost.php?p=4712241&postcount=14](http://ubuntuforums.org/showpost.php?p=4712241&postcount=14)

Just replace the input with the resolution and refresh rate you want to run at.

---

### Post by dontgetshocked on 2008-04-14
As an alternative you can always use another login screen Window, this solved my problem meanwhile back at the ranch.

Good Luck,

---

### Post by mposisil on 2008-04-30
I have this same problem.  My monitor's default resolution is 1680 X 1050, but the login screen is not centered, it is slightly to the right.  It appears to be running at a different resolution.  After I login everything is running fine at 1680 X 1050.  I've altered the screen section in the xorg.conf and it kinda worked but not really.  If I change the resolution to 1600 X 1024 the login screen looks perfect, but then after I login in everything is fuzzy because it stays on this resolution.  Is there a way I can have the login screen be 1600 X 1024 and then after I login go back to 1680 X 1050?  Also what login screen worked the best for you?

---

### Post by dontgetshocked on 2008-04-30
I solved my pr0blem by installing the new os instead of using the beta.Otherwise if you use one of the other login screens, it will work.it is ALWAYS in my opinion better to backup your data and install a fresh copy of your new os.
Good luck or else wait for an update to Ubuntu.

---

### Post by KillaW0lf04 on 2008-05-03
hey guys, im having the exact same problem. Im using the hardy heron official release which i upgraded from Ubuntu 7. Any help solving this problem for a noob?

---

