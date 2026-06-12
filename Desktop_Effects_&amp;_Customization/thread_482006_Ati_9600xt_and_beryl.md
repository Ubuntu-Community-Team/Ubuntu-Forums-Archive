---
title: "Ati 9600xt and beryl"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by Zsigee on 2007-06-23
Hi guys! I installed beryl on ubuntu 7.04, and it worked fine, when i enabled the ati accelerated graphic driver, it falls back to the metacity window manager. So i tried to find a solution for this. I did an XGL session, and when i started beryl it crashed to a white screen, I edited my xorg.conf and it crashed to a black screen. I downgraded the beryl to a previous version. Tried to install a driver from ATI homepage, tried to install a driver with envy. I tried a lot of things to get it work. Now i reinstalled ubuntu with no beryl and no accelerated graphic driver. Now i ask for your help to get it work :(. Im new to linux things, and pls help:(.

---

### Post by Zsigee on 2007-06-23
Now i got beryl works again, but when i try to play a movie, i cant see it. Only i can see it when i move the movie player window.

i made beryl from [https://help.ubuntu.com/community/RadeonDriver#head-180e7f8934082e4a506ce23130b024b773218317](https://help.ubuntu.com/community/RadeonDriver#head-180e7f8934082e4a506ce23130b024b773218317)

when i do glxinfo | grep vendor in terminal i got:
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

and glxinfo | grep "direct rendering" :
direct rendering: Yes

in xorg.conf i got:

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AR [Radeon 9600]"
        Driver		"ati"
        BusID		"PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option		"AGPMode"			"4"
        Option		"AGPFastWrite"			"true"
        Option		"DisableGLXRootClipping"	"true"
        Option		"AddARGBGLXVisuals"		"true"
        Option		"AllowGLXWithComposite"		"true"
        Option		"EnablePageFlip"		"true"
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

So this is weird. pls help

---

### Post by zero244 on 2007-06-23
I ran beryl with a 9600 card very well with XGL in a session.
In your driver section for Driver you have ATI. I always used fglrx for my driver.

---

### Post by zero244 on 2007-06-23
Also in your ServerLayout I see you have aiglx enabled. I didnt think you could run XLG and aiglx at the same time.

---

### Post by whistlerspa on 2007-06-24
I have the same card. I found that the ATI proprietary (fglrx) driver would not run up until yesterday when I was 'told' by the restricted drivers manager [it popped up] that a new version was available when I booted up. 

I'd wanted to try this as games like prboom and nexuiz or open arena freeze on startup or crash. I was using Ubuntu default drivers previously I guess. Beryl worked OK with this but often defaulted back to metacity on boot.

Once installed Beryl was very shaky, Swiftfox or Firefox did weird things and any attempt to change desktop settings resulted in black screen of death. The computer also lost all functionality on standby if I left it after the default time for screensaver to kick in. Alas games were no better either. 

So I ditched it. It seems to me that the problem lies with the card. My other machine with Intel graphics experiences none of this.

:(

---

