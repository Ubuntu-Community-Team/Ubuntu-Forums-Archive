---
title: "Problems running desktop effects in Thinkpad T30 (Feisty &amp; Gutsy)"
date: 2007-11-29
forum: Desktop Effects &amp; Customization
---

### Post by shellhrs on 2007-11-29
I was running Ubuntu Studio Feisty. No desktop effects there, but it ran very well. I have always wanted to have the wobbly windows and cube, but the original package doesn't have it. Until, I found [this]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") great site yesterday. I tried the method described to install Compiz Fusion, but it doesn't work. I thought, maybe that was because it doesn't have desktop effect in the first place (although it will be removed afterwards anyway).

So, I replaced Studio with normal Feisty. Default cube rotation worked, although wobbly windows were very slow. I installed compiz and compizconfig-settings-manager, and voila, no desktop effects at all. I could run the manager, but still no desktop effects.

Then I installed fglrx and Xgl. At last, I got desktop effects. But... new problem appear. Every title bar of maximised windows went blank (maybe the colors just became white, because when I hover the pointer at the top right side, pop-up notification showed up and the buttons still can be used). Also, maximised Firefox window left a 30-pixel-wide full-height white bar at the adjacent workspace on the right.

Following the suggestion in the [site]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion"), I decided to install Gutsy instead. First, Studio Gutsy, then compizconfig-settings-manager. No desktop effects. Appearance Preferences showed NONE, NORMAL, EXTRA, and CUSTOM selection (which can be adjusted using ccsm), but only NONE can be selected. If I select any of the others, a warning window showed up "Desktop effects could not enabled".

I replaced Studio with normal Gutsy, but the desktop effects doesn't run at all. Appearance Preferences showed NONE, NORMAL, and EXTRA. But again, only NONE can be selected without any warning. I haven't installed compizconfig-settings-manager yet (even normal desktop effects doesn't run here).

My system: IBM Thinkpad T30, 1GB RAM, 6GB HDD, Xircom 10/100 Ethernet+Modem PCMCIA.

Can anyone help me? I don't mind reinstalling the full system but I need it to run with full effects. :)

Thanks in advance.

NB: Forlong, if you read this, your [site]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")'s great. Tried to place this message there, but no authentication code appeared (I tried several times), so I post this here. Sorry. :)

---

### Post by javierfh on 2007-11-29
Hi,

i think i have mine working with these effects(at least some, not the cube though), but havent tried much, because it is very very slow.
I think the problem it is in the video card. Not powerful enough.

I cant remember what was the post that helped me, but i can try to find it.

Javi

---

### Post by shellhrs on 2007-11-29
Hi,

Javi, are you running ordinary Feisty or Gutsy? I have the cube on ordinary Feisty, but the wobbly window is so slow there. When I run ordinary Gutsy, none of them run at all.

It'll be great if you can direct me to the post you mention.

Thanks.

---

### Post by javierfh on 2007-12-03
Hi again,

im not sure if that will help you much , but here i have couple of links that were the ones that made the trick (i hope they were :D )
Answering your question, I use fresh installation of gutsy and well havent managed to rotate the cube..eventhough i think it would work, simply doesnt have enought graphic muscle( i can see the corners moving as if it will start rotating)

So the two links i have for you to try are the following:

[https://help.ubuntu.com/community/CompositeManager/CompizFusionATI](https://help.ubuntu.com/community/CompositeManager/CompizFusionATI)

and if that doesnt do the trick try also with this one: 
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon) (this is for feisty and beryl but i guess it will work also for gutsy and compiz fusion).


Hope this helps, let me know if you need anything else or let me know anyway if helped at all.

Javi

---

### Post by shellhrs on 2007-12-03
Javi, thanks for the links. I checked them out, and it seems that they basically use the same technique I used to get the effects.

I assume you have the same box as I do (IBM T30, 1GB RAM). The ATI Radeon Mobility M7 (7500) LW was fully supported by Feisty. By the way, I've checked the Restricted Drivers Manager, and apparently I have none.

I decided to do a clean install of Feisty. After the first reboot post-installation, I can enable the Desktop Effects (wobbly & cube). However, when I restart afterwards, I lost the cube (I deselected wobbly windows).

I guessed that I need to enable Xgl. I installed xgl following the instruction [here]("https://help.ubuntu.com/community/CompositeManager/Xgl"). I used Method A, as suggested by [Forlong]("http://forlong.blogage.de/").

At the login screen, I chose Xgl session. I finally get the cube, but every pop up windows left some thin line artifacts on the screen (I can clear them using F5, but it's annoying nevertheless). I was about to accept the fact the I won't have usable desktop effect, so I undo all the Method A above, but left the xserver-xgl installed. Then I logged out, followed by logging in using Gnome session. And lo and behold, I still have the rotating cube!

So now I have the desktop effects I want, and WITHOUT the annoying artifacts. The only problem is that the title bar of maximised windows completely went blank (there isn't a single button visible -- sometimes I can close the windows by clicking their top right corner). But I can live with this problem (for now :)).

As an added bonus, all the default screensaver run much faster now. I used to get Matrixview running so slow, but now, it ran very swiftly. :lolflag:

If you have the similar box, and you don't mind a clean install, maybe you can try the steps above. May the cube be with you! :)

By the way, I didn't run "compiz --replace".

---

### Post by rahlove on 2008-01-19
if i am not mistaken, ive been through this before, you either have not allowed your restricited drivers properly, or competing drivers, or  both of these process' compete against each other. I am new to this myself.

---

### Post by Ariccanfly on 2008-05-02
> **shellhrs said:**
> I was running Ubuntu Studio Feisty. No desktop effects there, but it ran very well. I have always wanted to have the wobbly windows and cube, but the original package doesn't have it. Until, I found [this]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") great site yesterday. I tried the method described to install Compiz Fusion, but it doesn't work. I thought, maybe that was because it doesn't have desktop effect in the first place (although it will be removed afterwards anyway).)

Working Perfect in 8.04 (had all those wierd issues) search synaptic for xgl, install it.

heres my oxrg. yeah its a mess, you can see all the stuff i tried (in 7.10)
i had it working but with wierd problems. now its fine.

peace

# xorg.conf (xorg X Window System server configuration file)

Section "Device"
Identifier "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
Driver "ati"
BusID "PCI:1:0:0"
Option "GARTSize" "64"
Option "AGPMode" "4"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
Option "AIGLX" "true"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"	
#old 7.10 buggy stuff
#Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	#Driver		"ati"
	#BusID		"PCI:1:0:0"
	#Option "MergedFB" "off"
	#Option "AGPMode" "4" #ok
	#Option "AGPFastWrite" "yes" #ok
	#Option "EnablePageFlip" "on" #ok
	#Option "RenderAccel" "on" #ok
	#Option "AccelMethod" "EXA" # or XXA #ok
	#Option "ColorTiling" "on"
	#Option "OverlayOnCRTC2" "on"

#and more..
#Option "UseFBDev" "true"
#Option "ColorTiling" "true"
#Option "EnablePageFlip" "true"
#Option "AccelMethod" "XAA"
#Option "XAANoOffscreenPixmaps" "true"
#Option "RenderAccel" "true"
#Option "AGPMode" "4"
#Option "AddARGBGLXVisuals" "True"
#Option "DisableGLXRootClipping" "True" 


EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
	#addedthis
	#Option		"XAANoOffscreenPixmaps"
	#Option		"AccelMethod" "XXA" #exa
	#Option		"DRI" "true"
	#Option		"AGPSize"	"32"  #fixes white title bars
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	#addedthistoo	
	#Option		"AIGLX"	"true"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"

EndSection #addedthis too

	#Section "DRI"
	#Mode 0666
	#EndSection


#Section "Extensions"
#	Option  "Composite" "Enable"
#EndSection

---

