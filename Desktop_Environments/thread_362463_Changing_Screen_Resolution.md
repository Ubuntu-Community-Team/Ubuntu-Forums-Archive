---
title: "Changing Screen Resolution"
date: 2007-02-15
forum: Desktop Environments
---

### Post by ubix on 2007-02-15
I'm running GNOME on Ubuntu 6.10, and would like to change my screen resolution to a size other than one of those displayed in the **"[COLOR="Blue"]Screen Resolution Preferences[/COLOR]"** window. I've added the appropriate entry into **SubSection "Display"** in **/etc/X11/xorg.conf**, but this is not reflected when restarting X.

After installing Ubuntu I can select between 3 different resolutions, as they are defined in on the line
```
**Modes "1024x768" "800x600" "640x480"**
``` in **/etc/X11/xorg.conf**. To the above **Modes** line I added new resolution **"1280x1024"**, so now it reads ```
**Modes "1280x1024" "1024x768" "800x600" "640x480"**
``` When I restart the X, the new resolution does not show up in **"[COLOR="Blue"]Screen Resolution Preferences[/COLOR]"** window.

If I remove the old and leave only the new resolution so it reads ```
**Modes "1280x1024"**
``` the **"[COLOR="Blue"]Screen Resolution Preferences[/COLOR]"** window shows incorrectly the resolutions [list][*]**1280x800** [*]**1280x768** [*]**800x600** [*]**640x480** :(  (there should have been only the [COLOR="Red"]**1280x1024**[/COLOR] resolution set at this point)[/list]The problem seems to be in GNOME not in X11 setup, namely, **"Screen Resolution Preferences"** choices window never gets correctly updated. :confused:

Can someone please point me in the right direction. _*But please do not talk about the [COLOR="Red"]driver,[/COLOR] *_because the problem clearly is not in that area!

---

### Post by Scooter7 on 2007-02-16
ubix, try my suggestion here:

[http://ubuntuforums.org/showthread.php?p=2163641&posted=1#post2163641](http://ubuntuforums.org/showthread.php?p=2163641&posted=1#post2163641)

I hope this helps,

   ~Teh DS (Scooter7)

---

### Post by ubix on 2007-02-16
> **Scooter7 said:**
> ubix, try my suggestion here: [http://ubuntuforums.org/showthread.php?p=2163641&posted=1#post2163641](http://ubuntuforums.org/showthread.php?p=2163641&posted=1#post2163641)
I hope this helps...I am sad to report to you it does not! :(

Also, ```
sudo dpkg-reconfigure xserver-xorg
```doesn't to anything else but but writes a new **/etc/X11/xorg.conf**, indeed, providing you supply to it the correct parameters, it should be more reliable than what one can do manually. Unfortunately, if you do not know what you are doing you can burn your monitor!

Some people talk about having problems with NVIDIA graphic board, and drivers. Though I was sure this was not the case, after all the troubles I went through so far, I started to doubt my earlier beliefs.

---

### Post by veloce on 2007-02-16
So is it the nvidia card you are using?  There are several issues with different graphics cards that cause the exact symptoms you report.

---

### Post by ubix on 2007-02-16
> **veloce said:**
> So is it the nvidia card you are using?  There are several issues with different graphics cards that cause the exact symptoms you report.Yes, I use **Nvidia** graphic card. Here 's the relevant info from my **xorg.conf** file:```
Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
#		Modes		"1280x1024"		"1024x768" "800x600" "640x480"
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
```This problem didn't exist in the earlier Ubuntu releases. I tested exactly the same hardware with a two years older Ubuntu, and it worked just fine! Why would the newer driver be such a nuisance?

---

### Post by Scooter7 on 2007-02-16
Perhaps you could try this:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29)

Although I can't say it will help, but it might.   I don't have experience with nvidia cards, as I've always used ATI, so I can't be much help here.   Good luck.

   ~Teh DS (Scooter7)

---

### Post by ubix on 2007-02-18
I have spent two days playing and tweaking the graphic driver installations and testing, only to at the end in frustration over the wasted time decided to wipe out all the changes by reinstalling the vanilla Ubuntu from the CD, and reinstall and reconfigure my system to the state before the useless exercise.

Though many diligent people, of whom Alberto Milone is a shinning star, have spent enormous amounts of time and extraordinary efforts trying to bypass the obstacles proprietary hardware and Licenses  create for the Open System, the **nVidia driver** example clearly demonstrates, that the available solutions are nor adequate or appropriate because in some cases they simply do not work.

The generic **nv driver** has a minor problem, which in fact even works under **xorg's** configuration file, with the older **XF86Config**. The business of installing a new driver clearly does not call for recompilation of entire kernel, nor for over hundred of updates for a not so long ago released version of OS. This is where Linux with its modular design shines, and yet the **nVidia/ATI driver** installations make it look incomparably worse than Micro$oft or Apple. 

If you are just trying to get your resolution to work for the legacy **[COLOR="DarkGreen"]NVIDIA GeForce2 MX/MX 400[/COLOR]**, because it used to work before you updated to newer Ubuntu, [COLOR="Red"]_do not bother getting a new **nVidia** driver_[/COLOR],  ](*,)  simply copy the old **[COLOR="Blue"]XF86Config-4[/COLOR]** over **[COLOR="Blue"]xorg.conf[/COLOR]** and restart the server (rebooting will do).

---

### Post by cmavr8 on 2007-02-21
I have a similar problem. My laptop has a 1280x800 wide display so I got a 19" TFT display of the same aspect ratio (widescreen, 1440x900).

When reconfiguring xorg I select 1280x800, 1280x1024 and 1440x900.

Inside xserver, in screen resolution preferences I can select: 1280x1024, 1280x800, 1024x768, 800x600, 640x480.


1280x1024 works, image stretched but fully viewable. TFT recognizes it as 1280x1024.


1280x800 results in normal image (not stretched) but trimmed top and bottom. TFTrecognizes it as 1280x768.

What the f*** is going on? I've been reading and playing with xorg.conf all day...

Please note that I have the TFT connected all the time, even when reconfiguring xorg. So the gpu thinks there is no laptop's display (remains turned off all the time). If I get the TFT right I will make mods to xorg.conf to clone image to both monitors...

Also, for reference, laptop is a Lenovo 3000 V100 with Intel 945GM Express graphics card.

Any ideas?

Thanks

EDIT:
Better description of the issue here: [http://ubuntuforums.org/showthread.p...81#post2191281](http://ubuntuforums.org/showthread.p...81#post2191281)

---

### Post by punkybouy on 2007-02-21
I can only add my experience.  Having done several Edgy installs I find if the Live CD does not run at 1280 X 1024 it will not add that resolution to your setup.   I have to reboot once or maybe more until the Live CD is running at the higher resolution then it will install the higher resolution.  Very odd.
Anybody have any experience using the DVI connector instead of VGA?

---

### Post by veloce on 2007-02-21
> **cmavr8 said:**
> I have a similar problem. My laptop has a 1280x800 wide display so I got a 19" TFT display of the same aspect ratio (widescreen, 1440x900).

When reconfiguring xorg I select 1280x800, 1280x1024 and 1440x900.

Inside xserver, in screen resolution preferences I can select: 1280x1024, 1280x800, 1024x768, 800x600, 640x480.


1280x1024 works, image stretched but fully viewable. TFT recognizes it as 1280x1024.


1280x800 results in normal image (not stretched) but trimmed top and bottom. TFTrecognizes it as 1280x768.

What the f*** is going on? I've been reading and playing with xorg.conf all day...

Please note that I have the TFT connected all the time, even when reconfiguring xorg. So the gpu thinks there is no laptop's display (remains turned off all the time). If I get the TFT right I will make mods to xorg.conf to clone image to both monitors...

Also, for reference, laptop is a Lenovo 3000 V100 with Intel 945GM Express graphics card.

Any ideas?

Thanks

EDIT:
Better description of the issue here: [http://ubuntuforums.org/showthread.p...81#post2191281](http://ubuntuforums.org/showthread.p...81#post2191281)

Aah, Intel graphics card.  You need to install "915resolution".

Check out the page on the wiki:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by cmavr8 on 2007-02-22
Thanks for your replys...

I did have 915resolution but the desired mode (1440x900) was not listed when tried 915resolution -l.

This means my laptop is incapable of 1440x900?
Maybe I'll just use 1280x800 to the TFT, too... I'll try that and keep you posted.

(I use RGB connection because that's the only one my laptop has)

---

### Post by cmavr8 on 2007-02-22
Update!
By using 915resolutions again, I found out what I've been doing wrong. I forced mode 50 to be 1440x900 by setting it in  "/etc/default/915resolution" conf file!

It works!!!
When I boot with TFT plugged in, it works in 1440x900 perfectly. (Well, login screen is a bit too long for this screen but it doesn't bother me)

When I boot with TFT not plugged in, default laptop panel works in 1280x800!

This is NICE, but not enough for me. It's just the first step.

Now I want to set up the "clone". I mean, I want the LapPanel to show at 1280 and the TFT at 1440 AT THE SAME TIME. This way I won't have to reboot every time I take my laptop away from the tft...

I'm working on it but if you have something to suggest...

Anyway, you've been so helpful! Thank you!

---

### Post by cmavr8 on 2007-02-22
I added the following lines in the "monitor" section in my xorg.conf:
Option   "MonitorLayout" "CRT,LFP"
Option   "Clone" "true"

So now If I reboot with tft plugged, I get correct res in tft but a strange white screen with colored stripes on the LFP (laptop flat panel for newbies like me).

If I reboot with tft unplugged, the lfp works fine. If I hot plug tft in, after logging in, TFT shows in wrong res...

Do I need to set two "monitor" and "screen" sections in my xorg???

---

### Post by veloce on 2007-02-22
> **cmavr8 said:**
> I added the following lines in the "monitor" section in my xorg.conf:
Option   "MonitorLayout" "CRT,LFP"
Option   "Clone" "true"

So now If I reboot with tft plugged, I get correct res in tft but a strange white screen with colored stripes on the LFP (laptop flat panel for newbies like me).

If I reboot with tft unplugged, the lfp works fine. If I hot plug tft in, after logging in, TFT shows in wrong res...

Do I need to set two "monitor" and "screen" sections in my xorg???

You could try the laptop's "switch monitors" key combination and reset the resolution for the monitors you are using.

Alternatively, yes, set up xorg with two monitors, screens, **and device** sections.

---

### Post by cmavr8 on 2007-02-25
(Stupid forum didn't notify me for new post... And now I'm on a trip, so no experimenting...)

The switch screen combo only works on login screen. Actually it doesn't even work there most of the time... I had it working once, but then there where keyboard problems so I reseted xorg and both the problems and the function were gonne.

It's strange though, because the only difference was made to the mouse input device... (also, keytouch program was installed while having the old xorg...)

Complicated situation.

If I try two monitors, screens and devices sections, won't I have a dual head setup? I have set dual head in the past and it's not what I want... 

I want clone and if possible in different resolutions...

Thanks for answering though!
Any more ideas? Can't I just make two monitors?

---

### Post by veloce on 2007-02-26
There's two different ways I'd try to get the clone setup you want:

[LIST=1]
[*]Install i810switch - I believe it is supposed to enable the monitor switch

[*]Full dual head setup BUT with "clone" enabled rather than "xinerama"
[/LIST]

---

