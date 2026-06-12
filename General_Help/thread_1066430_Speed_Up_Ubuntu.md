---
title: "Speed Up Ubuntu"
date: 2009-02-10
forum: General Help
---

### Post by tacoman359 on 2009-02-10
I've had Ubuntu installed for a few months, and my main problem is speed.  I barely have any programs installed.  I think the only modifications I've made to my computer are adding a few Firefox extensions, installing Pidgin, installing ndiswrapper, and uninstalling Evolution mail.  I've turned my resolution down to 1024x768, but I'd really like to put it back at 1440x900 if it weren't so slow.  I'm using a Dell Inspiron 5100 laptop, so I really don't want to do anything that will cause the laptop's battery to run out faster.

Are there any programs that I can uninstall or other things that I can do to improve performance?

---

### Post by lavinog on 2009-02-10
What is slow...is the video slow? What video card do you have? Do you have the correct video driver installed? If using nvidia or ati you may want to enable the restricted driver.

How much memory is installed
can you post
```
free -m
```

---

### Post by personjerry on 2009-02-10
installing most programs should not slow your computer down, unless you have a hard drive problem with lack of free space in which case you couldn't install much at all. log in in recovery mode and see if that is faster e.g. lag when you type a letter. if there is, it might not be a video card problem

---

### Post by HermanAB on 2009-02-10
Run 'top' to see what is chewing resources and kill it.

Cheers,

Herman

---

### Post by personjerry on 2009-02-10
hermanAB: telling someone to kill processes you are not sure of is not wise.

you should not kill a process unless you know what it is. if unsure, ask here.

again, you should determine the true problem first.

---

### Post by 2hot6ft2 on 2009-02-10
Here are some performance tweaks for you. Many of which I have done on my installs. BE VERY CAREFUL as some can be dangerous (when turning off services and such). There are warnings... best thing is if you're not sure what one is leave it alone. That being said have fun.

These 2 are pretty much the same I forget which one is newer but they give a lot of services info.
[http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html](http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html)
[http://forumubuntusoftware.info/viewtopic.php?f=42&t=894&sid=b0234a8891bbfb37ee63c45d986485bb](http://forumubuntusoftware.info/viewtopic.php?f=42&t=894&sid=b0234a8891bbfb37ee63c45d986485bb)

[http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/](http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/)
[http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_](http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_)

These are a bit old
[http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)
[http://ubuntuforums.org/showthread.php?t=107856](http://ubuntuforums.org/showthread.php?t=107856)

Enjoy.:guitar:

---

### Post by tacoman359 on 2009-02-10
Here's the output of "free -m".

             total       used       free     shared    buffers     cached
Mem:           501        323        177          0         13        145
-/+ buffers/cache:        165        336
Swap:         1427          0       1427

I have a bit of a problem with space, but it's not a big deal.  My Ubuntu partition is only 10GB and I have 3.5GB left, but that probably doesn't matter.  I forgot to mention I have a P4 at 2.6GHZ (I think, I don't know how to check in Ubuntu).  I'm sure my main problem is my graphics card. It's an ATI Mobility Radeon 7500c.  I'm getting about 120fps from glxgears at 1024x768, but only about 20fps at 1440x900.  The drivers for my graphics card appear to be working fine and direct rendering is working.  What would enabling restricted drivers do?

I just noticed, but there was a massive speed boost when I changed my resolution.  In XP, I have it set at 1440x900 and it definitely doesn't effect speed that much when I put it down to 1024x768.  By massive, I mean my problem is basically fixed, but I'd still like to know how to speed Ubuntu up a bit and possibly set it to a higher resolution without the massive speed decrease.

Thanks 2hot6ft2, that helped me disable a few services.

Thanks for the fast replies.

---

### Post by lavinog on 2009-02-10
> **tacoman359 said:**
> 
I have a bit of a problem with space, but it's not a big deal.  My Ubuntu partition is only 10GB and I have 3.5GB left, but that probably doesn't matter.  I forgot to mention I have a P4 at 2.6GHZ (I think, I don't know how to check in Ubuntu).  I'm sure my main problem is my graphics card. It's an ATI Mobility Radeon 7500c.  I'm getting about 120fps from glxgears at 1024x768, but only about 20fps at 1440x900.  The drivers for my graphics card appear to be working fine and direct rendering is working.  What would enabling restricted drivers do?

I just noticed, but there was a massive speed boost when I changed my resolution.  In XP, I have it set at 1440x900 and it definitely doesn't effect speed that much when I put it down to 1024x768.  By massive, I mean my problem is basically fixed, but I'd still like to know how to speed Ubuntu up a bit and possibly set it to a higher resolution without the massive speed decrease.

Thanks for the fast replies.

120fps is extremly slow for glxgears.
my laptop gets 1000fps (mobility radeon express 200m)
and my desktop gets 3200fps (radeon HD3650)
the problem is your video drivers, but give me a sec to look up something on your card.

---

### Post by 2hot6ft2 on 2009-02-10
> **tacoman359 said:**
> What would enabling restricted drivers do?

Thanks 2hot6ft2, that helped me disable a few services.

Thanks for the fast replies.
You're welcome and I would install the restricted graphics driver. But let lavinog check on your card first.

---

### Post by personjerry on 2009-02-10
for ATI cards there is the open source default drivers of the propriety, much faster driver known as fglrx. go to System - Administration - Hardware Drivers and select the ati driver if you want to install fglrx.

---

### Post by 2hot6ft2 on 2009-02-10
> **personjerry said:**
> for ATI cards there is the open source default drivers of the propriety, much faster driver known as fglrx. go to System - Administration - Hardware Drivers and select the ati driver if you want to install fglrx.
I agree and you may find this informative too on that.

Ubuntu Intrepid - Clocksource Fixed, System Still Hangs, AND No Videos - FGRLX Fixes It
[http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubuntu-intrepid-clocksource-fixed-system-still-hangs-and-no-videos-fgrlx-f](http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubuntu-intrepid-clocksource-fixed-system-still-hangs-and-no-videos-fgrlx-f)

---

### Post by lavinog on 2009-02-10
fglrx (the restricted driver) does not support the radeon 7500
It looks like the open source driver is the only option...but it should still be better than plain mesa.

---

### Post by tacoman359 on 2009-02-10
Great, thanks for all your help guys.  I wasn't expecting to find a driver better than my current one... last time I tried that I ended up having to wipe my computer.

---

### Post by lavinog on 2009-02-10
can you post your /etc/X11/xorg.conf
and /var/log/Xorg.0.log

---

### Post by personjerry on 2009-02-10
idk, perhaps try installing fglrx, the worst thing that can really happen is having to uninstall it (package xorg-driver-fglrx for apt-get)

and if I remember correctly xorg conf gets autoupdated by apt-get in ubuntu 8.x

---

### Post by 2hot6ft2 on 2009-02-10
I think I found a post with a solution here [http://ubuntuforums.org/showpost.php?p=6243258&postcount=3](http://ubuntuforums.org/showpost.php?p=6243258&postcount=3)
> **davient said:**
> Thanks for that, it was close but not quite for me. I had a few more issues but I've now got everything working perfectly!

I found a post mentioning that compiz works perfect on knoppix, with a T30. I promptly got the latest cd version and put loaded up knoppix compiz :) 

It worked, so I grabbed the xorg.conf and I've now modified it to get to work under ubuntu.  Here is the minimal version for anyone else with this issue :)
```

Section "ServerLayout"
	Identifier     "Xorg"
	Screen      0  "T30 Screen" 0 0
	InputDevice    "Configured Mouse"
	InputDevice "Generic Keyboard"	
        InputDevice    "Synaptics Touchpad"
        Option         "AIGLX"     "true"
EndSection

Section "ServerFlags"
	Option "AllowMouseOpenFail"  "true"
	
EndSection



Section "Module"
# Comments: see http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=346408
	Load  "dbe" # Double Buffering Extension, very important.
	Load  "dri" # This shouldn't be available choice if user has selected driver vga, vesa or nv.
	Load  "glx" # GLX Extension.
	Load  "freetype" # Freetype fonts.
	Load  "type1"  # Type 1 fonts
	Load  "record" # Developer extension, usually not needed
	SubSection      "extmod"
		Option          "omit xfree86-dga"
	EndSubSection
EndSection

Section "Extensions"
	# beryl and compiz need this, but it can cause bad (end even softreset-resistant)
	# effects in some graphics cards, especially nv.
	Option "Composite" "Enable"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection


Section "Monitor"
	Identifier	"T30 LCD"
	Option	"DPMS"	"true"

EndSection

Section "Device"

	Identifier  "ATI Radeon 7500M"
	Driver      "ati"
	VendorName  "All"
	BoardName   "All"
	Option "GARTSize" "64"
	Option "AGPMode" "8"


	Option "XAANoOffscreenPixmaps" "true"
	Option "AllowGLXWithComposite" "true"
	Option "EnablePageFlip" "true"

        Option  "XaaNoScanlineImageWriteRect" "true"
        Option  "XaaNoScanlineCPUToScreenColorExpandFill" "true"
EndSection

Section "Screen"
	Identifier "T30 Screen"
	Device     "ATI Radeon 7500M"
	Monitor    "T30 LCD"
	DefaultColorDepth 16
	Option "AddARGBGLXVisuals" "true"
	Option "DisableGLXRootClipping" "true"

EndSection

Section "DRI"
	Mode 0666
EndSection


```

I'm guessing this may also work in Ibex...?  I'll try this later and let you know :)

From this thread [http://ubuntuforums.org/showthread.php?t=986026&highlight=radeon+7500+driver](http://ubuntuforums.org/showthread.php?t=986026&highlight=radeon+7500+driver)

---

### Post by lavinog on 2009-02-11
That looks like a good way to go

---

### Post by tacoman359 on 2009-02-11
I replaced that with my xorg.conf file, but it didn't work.  Everything took longer to load, I was missing things (like the exit and minimize buttons), the terminal appeared white when I launched it and I couldn't run anything from it.  I just restored a backup of that file and everything is working now.  Was this made for Intrepid or a different version?

By the way... I have a 7500c, not a 7500.  I don't know if it makes a difference, but it definitely could.

---

