---
title: "Firefox + Compiz = High CPU and Bad Performance"
date: 2007-12-11
forum: Desktop Effects &amp; Customization
---

### Post by Windsurfer619 on 2007-12-11
Hi guys, new to the boards, but I've been using Ubuntu for about 2 weeks. Very very happy with it, even with bugs considered!

_Problem:_Ever since I turned on Compiz, any web browser I have open is very slow. I've tried Firefox, Swiftfox, and Opera, and they are all considerably lagging when I have effects turned on. And when I mean lagging, I mean having to hold the mouse button down so it registers a click, and it takes half a second to "finish" scrolling. Sometimes, the browsers (Or more likely the system) doesn't register that a key has been *unpressed*.
The CPU hovers between 70 and 100% when I'm using the effects and any browser.
When I am not using effects, both firefox and Opera are very quick, and CPU hardly goes higher than 20%.

_My system:_** P4 2.8 Ghz w/HT.  Radeon X700 pro (256MB). 2 GB RAM**

_What I've tried:_ Many, many posts about Firefox being slow. And almost none of them solved.
Originally, I had the default drivers that Ubuntu installs. I've installed the new ATI drivers. I've followed a tutorial to do that, and enable AIGLX.
I get about 1200 FPS with fgl_glxgears no matter if I have the desktop effects on or off, or if I have a browser window open or not.
I've tried having different amounts of effects enabled, and I still get the same CPU usage and performance problems.
If it's any help, here's my xorg.conf file:
```
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "VW222"
	Option	    "DPMS"
EndSection

Section "Device"

	#Added from the compiz.org/ATI site
	Identifier  "ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]"
	Driver      "fglrx"
	Option	    "DRI" "on"
	Option	    "VideoOverlay" "on"
	Option	    "ColorTiling" "on"
	Option	    "EnablePageFlip" "true"
	Option	    "AccelMethod" "XXA"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "AGPMode" "8"
	Option	    "AGPFastWrite" "yes"
	Option	    "RenderAccel" "on"
	#Some experimental options!
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]"
	Monitor    "VW222"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1680x1680" "1680x1050" "1600x1200" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Group        0
	Mode         0666
EndSection

Section "Extensions"
	Option	    	"Composite" "Enable"
	Option 		"DAMAGE" "true"
	Option 		"RENDER" "true"
EndSection

#Added as per 
# http://linux.wordpress.com/2007/11/22/update-running-compiz-fusion-using-ati-cards-and-aiglx/

Section "ServerFlags"
  	Option 		"IgnoreABI" 	"on"
	Option 		"AIGLX" 	"true"
EndSection

```

Help would be greatly appreciated, thanks :)
I really enjoy the effects, but I also enjoy browsing the internet (hehe, don't we all?)

And yes, I've seen [this thread]("http://ubuntuforums.org/showthread.php?t=589332"), but it's more than a year old, and I haven't been seeing any newer posts. If I'm simply lacking Googlefu, please let me know!

---

### Post by smartboyathome on 2007-12-11
Compiz requires **at least** 512 mbs of ram, and this is what is causing your slowdown. You won't be able to run it on a machine with less without serious performance problems. :(

---

### Post by Windsurfer619 on 2007-12-11
I have **2 GB of RAM**. My **video card** has 256 MB. I think that's plenty :)

---

### Post by screaminj3sus on 2007-12-11
yeah dude, I've seen people running compiz on geforce 4's and less ram fine...

---

### Post by new2*buntu on 2007-12-11
I run compiz fun, without too much lag. I just had to disable cube transparency, since that would lag somewhat. :)

---

### Post by screaminj3sus on 2007-12-11
I had a problem with my old PC (3.0 Ghz p4 w/HT/2GB RAM/7600GS 256MB) with compiz being sluggish especially with firefox. The most intensive effects like cube and fire and crap all ran prefectly but stuff like minimize animations would often be the most problemetic. Firefox would always be slow and flciker balck when uniminizing and slow in general. I haven't tried linux on my new pc yet though. (Now I have an x1950 which will probably be a bitch to get compiz running on anyway) that old PC ran aero on vista Flawlessly though. (Which is supposedly has much higher requirements than compiz but I've only had problems with compiz.

---

### Post by Windsurfer619 on 2007-12-12
Okay, to bump my post, and to summarize:

Compiz works great! My computer *tears it to shreds!*

Firefox works great when compiz isn't turned on! It's even faster than windows!

The problem comes up, however, when compiz effects are turned on (even just minimal effects!). Then Firefox gets very very slow. All browsers get slow. But no other programs!

---

### Post by Windsurfer619 on 2007-12-20
So it's still unsolved. I'm sorry if this counts as a double post.

With some playing around, it seems that the larger my firefox window, the slower it is. In fact, if I make any application have a large area that needs to update, my entire computer gets very slow. Is this really a hardware problem?

I have a laptop with an intel 945GM that is able to pull better performance out of the same pixel-size windows.

EDIT: It's the ATI driver, right? What driver is the best, would you say? I have AIGLX working with this driver...

---

### Post by curumbao on 2007-12-27
Uhm, I have your same problem, firefox and opera both get very slow when compiz effects are enabled, don't know why.

Anyway, you sure have a problem with your ATI drivers, as with that card you should get more fps. In my laptop computer (ATI mobility Radeon 9700, 64MB) I get 1250 fps, and in my ATI 9600 PRO 256 MB more than 2000.

So check your drivers. I personally recommend you using envy to install them if you haven't tried.

---

### Post by thefirstM on 2007-12-27
I also have a problem with Firefox and Compiz.  When I am running firefox and compiz at the same time, the speed of Firefox is fine, but if any effect tries to take place in front of the firefox window, it is jerky.  If I try to minimize or close firefox itself, it is perfectly smooth.  I have a GeForce 6600gt AGP.

---

### Post by Windsurfer619 on 2007-12-27
Awh. I tried using Envy, and now I can't get any GUi working. It only boots in recovery mode. :(  boo.

---

### Post by Gigamo on 2007-12-27
I also have this problem. Switching tabs takes like 2 seconds when compiz is enabled and using firefox. I don't think my system's causing it, I have a T7700 CPU and 2GB RAM with 8600M GT card.

---

### Post by drawkcab on 2007-12-31
> **Gigamo said:**
> I also have this problem. Switching tabs takes like 2 seconds when compiz is enabled and using firefox. I don't think my system's causing it, I have a T7700 CPU and 2GB RAM with 8600M GT card.

Yeah, same here (IFL90).  It's annoying to have to wait months for adequate drivers.

---

### Post by ycason on 2008-01-01
This is a known problem with the newest ATI drivers.  You'll just have to wait for a fix or try running with the open source drivers.  XGL could also be a solution.

Check the Phoronix forums for updates on the ATI drivers.  [http://www.phoronix.com](http://www.phoronix.com)

Sorry I couldn't be more help but at least you know the source of the problem now.

:guitar:

---

### Post by Windsurfer619 on 2008-01-01
Thank you for letting me know :)
I guess I'll be leaving Compiz off until ATI decides to fix this.

---

### Post by Gigamo on 2008-01-01
I fixed this by upgrading to Hardy's kernel. See the Tutorials subforum. :)

---

### Post by Borbus on 2008-01-01
I have this problem running compiz-fusion on latest nvidia drivers. My PC has 2GB of ram and 512MB of vram and x86_64 Ubuntu 7.10.

Firefox isn't quite as slow as the OP described but it is noticeably slower with compiz enabled. Stuff like closing tabs always lags, I click to close and the page disappears but the tab bar lags for a considerable time before the tab disappears. Javascript animation and stuff is super slow.

edit: Actually I'm not sure... I did more testing and it seems Firefox is slow with or without compiz :/

---

### Post by samosamo on 2008-01-26
> **Gigamo said:**
> I fixed this by upgrading to Hardy's kernel. See the Tutorials subforum. :)

Can anyone verify this guys claim and explain why Hardy's kernel with the same ATI drivers and Firefox will fix this issue ?

---

### Post by curumbao on 2008-01-31
I tried Hardy's Kernel in my laptop computer and it's all the same. Still slow.

Maybe it fixes the stuff on some computers....

---

### Post by curumbao on 2008-02-12
I solved my problem. I read somewhere that another person had problems with the propietary drivers and just returned to the Mesa one (can't remember where).

So I removed with envy the drivers I previouslly installed, edited the whitelist of compiz, and know I have compiz perfectly running and with my firefox as smooth as when not using compiz. And whit direct rendering and the same rate of fps (around 1900).

It may the same problem with some of you, if you don't specifically need the ATI drivers you could go back while they don't release new ones.

---

### Post by gekaare on 2008-02-13
> **Borbus said:**
> I have this problem running compiz-fusion on latest nvidia drivers. My PC has 2GB of ram and 512MB of vram and x86_64 Ubuntu 7.10.

Firefox isn't quite as slow as the OP described but it is noticeably slower with compiz enabled. Stuff like closing tabs always lags, I click to close and the page disappears but the tab bar lags for a considerable time before the tab disappears. Javascript animation and stuff is super slow.

edit: Actually I'm not sure... I did more testing and it seems Firefox is slow with or without compiz :/

I too experienced similar problems. I almost gave up Ubuntu at one point there. But then i realized, flash was the problem... So, i installed Flashblock Add-on to firefox and my computer is faster than ever! :) Could be irrelevant, hope it is helpful

---

### Post by pythonusr on 2008-02-19
I had this issue not five minutes ago, but I upgraded to the development version of Hardy's kernal and it was fixed.

---

### Post by tdayal on 2008-02-22
I have the same problem on my Compal IFL90. I don't really want to upgrade to the hardy kernel just yet... anyone find any fixes?

---

### Post by laborg on 2008-02-24
Under Hardy Alpha5 owning a intel 950 graphic card I am having the same problems.

---

### Post by marscay on 2008-02-28
i had this problem for awhile, for me the problem was fixed through the 8.2 ATI proprietary driver.

although i'm now using compiz in Arch and it's amazingly fast and stable.

not bad mouthing ubuntu because it's a great distro but if you're after more performance on the desktop, specifically with firefox and compiz then Arch is a great dist to use if you like to mess with the guts of linux a bit more.

---

### Post by ellalan on 2008-03-01
I do have same problem, my PC has become slow since I have updated yesterday.
Could some one tell me how to turn off compiz please. Thanks in advance.

---

### Post by Melcar on 2008-03-01
FF (especially with smooth scrolling on) is very CPU hungry.  This is even more true when you turn on Compiz and happen to be using fglrx (the ATI Linux driver).  The ATI devs. have been blaming Compiz, and their explanations have been few but make sense.  
When you engage Compiz, it seems that certain tasks that would normally be  off loaded to the GPU or that only use a small amount of CPU power, get routed to the CPU; this is very noticeable on older single core CPU (my laptop 2GHz Sempron gets chewed up by Compiz).  Also, with fglrx, Compiz itself becomes very CPU hungry, which only adds to the problems, especially if you're running a slower single core CPU.

---

### Post by maarten12 on 2008-03-01
You can use overlay types so it eats less CPU
like: [SIZE=-1]sudo aticonfig --overlay-type=Xv
where you can replace 'Xv' for 'opengl' or 'disable'
you also might want to check if you use direct rendering, which I had alot of problems with until I turned it on
you can check with: [/SIZE]glxinfo | grep rendering

---

