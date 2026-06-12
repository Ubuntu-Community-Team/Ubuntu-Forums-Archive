---
title: "[SOLVED] Extra Visual Effects Super Slow and Terrible"
date: 2008-01-19
forum: Desktop Effects &amp; Customization
---

### Post by MountainX on 2008-01-19
A few days ago I installed Ubuntu 7.10 for the first time (on my laptop). Next I installed Ubuntu on my desktop, and this question is about my desktop machine.

First, when I tried to enable extra visual effects I got the message that they couldn't be enabled. The way I solved that was by going to the Synaptics Package Manager and installing xserver-xgl. Then I was able to enable the extra visual effects.

However, the experience was terrible. The wobbly windows effect was so slow that my windows would not even wobble. The whole GUI became unusably slow. That's the first problem.

My video card is a PNY Quadro4 NVS285 64MB 64-bit DDR PCI Express x16 and my computer has 4 GB RAM (and an AMD Athlon 64 X2 3800+ 2.0GHz CPU). I have two HP L2335 LCD monitors running in digital DVI mode at 1920x1200x24 each. I have the nVidia restricted driver enabled.

I thought that maybe I didn't have enough horsepower to run Compiz on two monitors, but other people seem to be doing it. In fact, at [this YouTube link]("http://youtube.com/watch?v=_qddueXkD8E") a guy shows wobbly windows on very old hardware. My windows won't wobble like that!

My second problem is that with xgl installed I lost all the usability features of dual monitors that I depend on. The desktop now spans both monitors and the maximize feature makes windows cover both screens.

Without xgl I had perfect management of the dual monitors without doing anything. I guess it is the nVidia driver, but it worked exactly like I wanted it to OOB.

Is it possible to keep the desktop features I had without xgl, but still get the extra visual effects of Compiz? If so, any ideas what I can do about the performance?

BTW, I don't like the sound of running independent X screens (can't move windows between monitors) and I don't like the sound of Xinerama (can't maximize windows to a single monitor under GNOME, etc.).

I'm really new to Linux, so I don't know what the other options are.

---

### Post by MountainX on 2008-01-19
I would like to have results like this:
[http://youtube.com/watch?v=y7CGLEZXDSM](http://youtube.com/watch?v=y7CGLEZXDSM)

---

### Post by Ub1476 on 2008-01-19
Are you really sure you need restricted driver for such an old graphic card? XGL shouldn't be necessary for nvidia cards, ever. Did you try to enable desktop effects without installing the driver?

---

### Post by MountainX on 2008-01-19
The restricted driver seems to work fine. I like the desktop/windows management features I get with it. When I first installed Ubuntu, only one monitor was enabled. I ended up with the restricted driver in the process of enabling dual monitors. This is the first time I have done any of this with Ubuntu, so I took the advice I found in other posts. Everyone seemed to be recommending the restricted driver, I'm very happy with the way things work - except for the extra visual effects. Without those, everything is quick and well behaved.

Is the graphics card that old? I bought it recently. For a silent card, I thought it was a good one. It is hard to find ***silent*** cards for dual digital DVI monitors at 1920 x 1200 x 24 resolution.

Can expand the memory on this card? If so, what is the max memory for this card? What type of memory do I need to purchase?

Anyway, I've seen [excellent visual effects with Compiz Fusion on 32 MB of video memory]("http://youtube.com/watch?v=_qddueXkD8E"), so I would think I could solve the problems in my original post with my current video card.

---

### Post by Ub1476 on 2008-01-19
Don't worry, Compiz can run on extremely weak hardware, but it's the driver I were referring to. Since the graphic card only had 64mb memory, I just took it for old, and therefore, a good driver would already be available for it. However, since it doesn't appear to be, you might want to install the latest driver from nvidias website. You can use Envy for that, but make sure you have removed XGL and the restricted driver before doing so. Or better, post the result of this (shows the graphic card the Ubuntu way):

```
lspci | grep VGA
```

---

### Post by MountainX on 2008-01-19
lspci | grep VGA

```
01:00.0 VGA compatible controller: nVidia Corporation NV44 [Quadro NVS 285] (rev a1)

```

What's the next step? Thanks.

---

### Post by Ub1476 on 2008-01-19
Remove xgl and the restricted driver, then restart xserver (ctrl+alt+backspace). Now download and install [Envy]("http://albertomilone.com/nvidia_scripts1.html") and run it with:

```
envy -g
```

It will automatically download and install the latest driver, and configure your xserver if you allow it to.

BTW, I think you happen to have a Geforce 6200:p

---

### Post by MountainX on 2008-01-19
xgl is removed now. To remove the restriced driver can I just disable it or do I need to agressively purge it? If I need to purge it, I would appreciate help on the command to use. Thanks.

---

### Post by Ub1476 on 2008-01-19
Just remove from the list. No purging is needed.

---

### Post by MountainX on 2008-01-19
After installing Envy and letting it do its magic, I enabled the driver in the restricted mode drivers dialog. Then I had to manually edit xorg.conf because something in the automatic process inserted virtual resolution modes that shouldn't be there. 

I also saw that xinerama was set to true, so I commented that out because I want to be able to maximize Windows to one monitor. (And if I try to enable xinerama just as a test, I am then unable to turn on the extra visual settings.)

With xinerama not enabled, I could turn on the extra visual effects and the performance is almost OK. My menus are slow to open, but I'll see if that is just a setting or if it is hardware performance. The wobbly windows effect works for the first time. 

However, I have a weird situation where I have two main menu bars - one for each monitor. It looks like I have the two independent X displays I have read about - especially because I can't move windows from one monitor to the other.

I have also lost my sound - at least in YouTube, which is all I have tested so far. (And without any extra visual effects enabled but xinerama turned on, dragging windows across monitors is not smooth like it was before.)

Prior to using Envy, I had exactly the desktop/window management features I like: one main menu bar on the primary monitor, windows maximize to one monitor, dialogs open where expected, and windows can move from one monitor to the other.

I hope to keep those features and still get the extra visual effects. What should I try next? Thanks.

---

### Post by Ub1476 on 2008-01-19
You tell me you let Envy install and configure the driver, then you installed the driver in Restricted Driver Manager?

BTW, you didn't install the driver and configure x with both monitors plugged in, did you? That would answer your mirrored monitors:p

---

### Post by MountainX on 2008-01-19
After I installed with Envy and let it configure the driver, I tried to enable extra visual effects and I couldn't. I got a dialog asking me if I wanted to enable the driver. I canceled that dialog and opened the restricted driver manager to see what was going on. It showed NVIDIA accelerated graphics driver (latest cards) with no check in the enabled box but status showed "in use". I went ahead and added the check to enabled. That allowed me to turn on the extra visual effects.

I did run Envy with both monitors plugged in.

Any suggestions for how I get a fully functional desktop like this one?
[http://youtube.com/watch?v=y7CGLEZXDSM](http://youtube.com/watch?v=y7CGLEZXDSM)

In particular, I want to be able to move windows from one monitor to another and to maximize windows to one monitor only. 

I also lost my sound after running Envy.

---

### Post by Ub1476 on 2008-01-19
Alright, installing and configuring a driver/X with two monitors plugged in will cause the system to think that these two are defaults, meaning you end up as you did.

You will have to revert what you did (if you don't want to mess with the xorg.conf file).. _With only one monitor plugged in. _ In Envy, remember to choose to remove the current driver before installing again, as well as unchecking it in RDM.

Hope it will work better now:)

---

### Post by MountainX on 2008-01-19
I think I'd rather edit xorg.conf if I could get some tips on doing that.

---

### Post by Ub1476 on 2008-01-19
If you post the xorg.conf here I'll look into it.

```
gksud gedit /etc/X11/xorg.conf
```

I gotto go now, but if you want to look around yourself, look for two almost equal sections.

Talk you later.

---

### Post by MountainX on 2008-01-19
Thanks for your help. I decided to follow your recommendation and just uninstall everything, unplug the second monitor and then reinstall with Envy.

After doing that, when I use nvidia-settings to enable twinview, I get this error message:

Failed to set MetaMode (21) 'DFP-0: 1920x1200_60 @1920x1200 +0+0, DFP-1: nvidia-auto-select @1920x1200 +1920+0' (Mode 3840x1200, id: 135) on X screen 0

Anyone have any idea how to correct this? My card and monitors support 1920x1200x24 @60.

Thanks.

---

### Post by MountainX on 2008-01-19
I edited xorg.conf and got twinview working:

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

#--------------------------------------------------------------------------------------------------
# screen 0
#--------------------------------------------------------------------------------------------------

Section "Device"
	Identifier	"nVidia Corporation NV44 [Quadro NVS 285]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	#Screen	0
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"hp L2335"
	Vendorname	"Hewlett-Packard"
	Modelname	"HP L2335 Flat Panel Monitor"
	Horizsync	30.0-107.0
	Vertrefresh	48.0-85.0
  modeline  "1920x1200@75" 246.59 1920 2064 2272 2624 1200 1201 1204 1253 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44 [Quadro NVS 285]"
	Monitor		"hp L2335"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
		Modes		"1920x1200@60"	"1920x1200@75"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NvAGP"	"2"
	Option		"NoLogo"	"1"
	Option		"RenderAccel"	"1"
	Option		"Coolbits"	"1"
	Option		"ConnectedMonitor"	"DFP, DFP"
	Option		"NoPowerConnectorCheck"	"1"
	Option		"TwinView"	"1"
	Option		"Metamodes"	"1920x1200, 1920x1200; 1920x1200, NULL"
	Option		"SecondMonitorHorizSync"	"30-107"
	Option		"SecondMonitorVertRefresh"	"48-85"
	Option		"TwinViewOrientation"	"RightOf"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"UseEdidFreqs"	"True"
	#new stuff from http://www.trevorfitzgerald.com/projects/ubuntu-twinview-monitors-with-an-nvidia-graphics-card/
	#Horizsync	30.0-107.0
	#Vertrefresh	48.0-85.0
	# Option "NoTwinViewXineramaInfo"
EndSection

#--------------------------------------------------------------------------------------------------

Section "ServerLayout"
	Identifier	"TwinView Configuration"
  screen "Default Screen" 0 0
	#screen 1 "screen1" rightof "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Option		"Xinerama"	"Off"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

#--------------------------------------------------------------------------------------------------
# screen 1
#--------------------------------------------------------------------------------------------------

#removed as per http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html

#--------------------------------------------------------------------------------------------------

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "ServerFlags"
	#Option		"Xinerama"	"false"
EndSection

```

unfortunately, when I enabled extra visual effects after that, it was a disaster. I could not give input into any window.

---

### Post by fracturedmorals on 2008-01-20
This is a quick tweak, and I've posted it before.....I'm not guaranteeing results, but it seems to boost things for me.

sudo apt-get install compizconfig-settings-manager

System > Preferences > Advanced Desktop Effects Settings

Go to "General"

Click on the "Display" tab.

Uncheck "Detect Refresh Rate"

Move the refresh rate to 200.

After which: Any time you reactivate the effects, choose "Custom" as opposed to "Extra"

---

### Post by Ub1476 on 2008-01-20
I'm getting a little out of clues now, but you might want to look  [here]("https://help.ubuntu.com/community/NvidiaMultiMonitors?highlight=(monitor)") for Twinview configuration.

I assume you already know there is a graphical interface for monitors in System>Administration>Screens and graphics. 

Let's hope the above post will help you with your frame rate.

---

### Post by MountainX on 2008-01-20
> **fracturedmorals said:**
> This is a quick tweak, and I've posted it before.....I'm not guaranteeing results, but it seems to boost things for me.

sudo apt-get install compizconfig-settings-manager

System > Preferences > Advanced Desktop Effects Settings

Go to "General"

Click on the "Display" tab.

Uncheck "Detect Refresh Rate"

Move the refresh rate to 200.

After which: Any time you reactivate the effects, choose "Custom" as opposed to "Extra"

That's a nice tip. It's good to know about it. But in my case, there is something more serious going on. I need more than a small tweak. I did try this tip, but I get the same result -- the UI becomes completely unfunctional and I either cannot give any input into a window or I can't see the window content at all. (Of course, I can't take a screen shot either. I can't even type into the terminal.) The weird thing is that the main menu does respond to mouse clicks and new apps will open -- you just can't make them respond to any input, nor can you even close them the normal way.

It must be something about my hardware, but I can't figure out exactly what the problem is. At least I have a pretty good understanding of how to edit xorg.conf now. (Hand editing has so far proven to be the only way to deal with the issues I've been having...)

---

### Post by MountainX on 2008-01-20
> **Ub1476 said:**
> I'm getting a little out of clues now, but you might want to look  [here]("https://help.ubuntu.com/community/NvidiaMultiMonitors?highlight=(monitor)") for Twinview configuration.

I assume you already know there is a graphical interface for monitors in System>Administration>Screens and graphics. 

Let's hope the above post will help you with your frame rate.

Thanks for your help. I have used all the GUI tools.

As a next step I think I'll try to uninstall everything related to video and sound. (I installed the OSS sound module in an attempt to restore sound after I lost it with the latest nVidia video driver.) 

How would I remove all that stuff and start fresh? Should I just reinstall Ubuntu?

If I'm going to reinstall, before I completely give up on Compiz, I could try some extreme measures if anyone wants to suggest any. If they mess up my OS, it won't matter at this point.

---

### Post by MountainX on 2008-01-20
Solved! I reinstalled Ubuntu 7.10 completely clean. (I deleted the partition.) I installed everything exactly the same, including the AMD64 version of Ubuntu.

However, this time I had the benefit of a plan. I decided to test Envy right off the bat, before I did anything else. I unplugged my second monitor, installed Envy, installed the nVidia restricted drivers, let Ency do the xorg config settings as recommended, opened RDM and enabled the driver, and rebooted.

First I tested extra visual effects with one monitor (they worked -- for the first time ever, for me!) Then I used sudo nvidia-settings to configure my second monitor. Extra visual effects still worked and they work well. I have wobbly windows and snappy response on dual monitors.

BTW, I also have sound again. :)

I've done all these steps before, and I did them the same way. The only difference I can see is that the first time I tried several solutions before I used Envy. (There must have been some configurations somewhere that were screwed up and nothing I did previously detected or corrected those errors.)

**_[COLOR="Blue"]Question: [/COLOR]_**Windows maximize across both monitors now. I don't want that. This video shows windows maximizing to one monitor. How do I get that?
[http://youtube.com/watch?v=y7CGLEZXDSM](http://youtube.com/watch?v=y7CGLEZXDSM)

 Also, I have not yet installed the 168 updates waiting for me. I assume there is no risk in installing them all. I would hate to find out that something in those updates is responsible for the issues I had before.

Thanks.

---

### Post by MountainX on 2008-01-20
NOT SOLVED! Damn, after I rebooted, the slow and terrible effects are back. I did not change any settings. And I did save the configuration using sudo nvidia-settings. All I did is restart my computer before taking the next step and now the GUI is so slow as to be unusable and no window accepts input. What could be going on??? Thanks.

Oh, btw, after rebooting my main menu bar occupies only one monitor like I wanted it to. That might be a clue about the changes that took place on reboot.

I started a thread here:
[http://forum.compiz-fusion.org/showthread.php?t=6687](http://forum.compiz-fusion.org/showthread.php?t=6687)

---

### Post by lildunn34 on 2008-01-28
> **Ub1476 said:**
> Remove xgl and the restricted driver, then restart xserver (ctrl+alt+backspace). Now download and install [Envy]("http://albertomilone.com/nvidia_scripts1.html") and run it with:

```
envy -g
```

It will automatically download and install the latest driver, and configure your xserver if you allow it to.

BTW, I think you happen to have a Geforce 6200:p\


THANKS this did the trick for me Everything is fine now.

---

### Post by MountainX on 2008-01-28
> **lildunn34 said:**
> \


THANKS this did the trick for me Everything is fine now.

Which video card do you have? I haven't been able to solve my issues.

---

### Post by MountainX on 2008-02-03
I'm still working on this with no solution yet...

---

### Post by MountainX on 2008-03-22
Finally, a solution!

I went with the graphics card described here:

[http://ubuntuforums.org/showthread.php?p=4567681#post4567681](http://ubuntuforums.org/showthread.php?p=4567681#post4567681)

MSI NX8600GT-T2D256EZ GeForce 8600GT 256MB 128-bit GDDR3 PCI Express x16 SLI Supported Video Card

I attached my xorg.conf here:
[http://forum.compiz-fusion.org/showthread.php?p=52502#post52502](http://forum.compiz-fusion.org/showthread.php?p=52502#post52502)

---

