---
title: "Anyone got Fn+F8 working? (CRT/LCD button)"
date: 2008-04-10
forum: Dell  Ubuntu Support
---

### Post by Kiri on 2008-04-10
I would like to be able to switch between my laptop display on my m1210 and an external LCD monitor connected via VGA cable. 
Pressing FN+F8 (the key that should be assigned to switch between displays) seems to try to refresh the screen (it goes blank for a second then comes back on), but nothing is actually changed...

Anyone got this working?

---

### Post by LMP900 on 2008-04-10
I probably can't be of too much help, but I can answer your question:

Fn+F8 works just fine for me; I have a 1420n (Intel video) with Ubuntu 7.10 (Dell custom image).

---

### Post by Kiri on 2008-04-11
If possible, could you post your xorg.conf?
(its located at /etc/X11/xorg.conf)

---

### Post by LMP900 on 2008-04-11
As requested:

```
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x822" "593x1072" "0x0"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by KimH on 2008-04-11
Hi, I am using Hardy beta at the moment, if that should make a difference.... A few weeks ago when I connected a monitor via a VGA cable Fn+F8 worked out of the box. I could switch between the laptop screen, external monitor and dual view without any problems. Since then I have switced to a HDMI/DVI cable and noticed that Fn+F8 does not work anymore :-( I don't know if this related to using the HDMI output now or if something changed in Hardy in one of the updates that comes pretty frequently theese days.

Regards
Kim

---

### Post by Kiri on 2008-04-11
Thanks LMP900, 
I dont see anything special in your xorg.conf file, so I wonder why yours works and mine doesnt.. hmm

Question for both of you, when you press fn F8 and switch to dual view, how is it setup? Is it twin view or cloned?

---

### Post by aidave on 2008-04-11
Oddly enough I have just tried this an hour ago, attempting to clone output from my laptop onto a larger screen for work.

The Fn-F8 seems to do nothing (on Hardy Beta w/1420).

Using the NVIDIA XServer settings applet that came from installing via Envy, I was able to detect and clone to the second monitor!  The utility is very useful actually.  Hope that helps someone.

---

### Post by supercheetah on 2008-04-11
I have an M1330, and it seems to work just fine for me.

What's the output of /var/log/Xorg.0.log right after you plug in the other monitor?  Actually, save a copy before you plug it in, and do a *diff* with it right after you plug in the second monitor.

From what I can see in my own logs is that X should automatically detect the second monitor and its capabilities.

---

### Post by LMP900 on 2008-04-11
> **Kiri said:**
> Thanks LMP900, 
I dont see anything special in your xorg.conf file, so I wonder why yours works and mine doesnt.. hmm

Question for both of you, when you press fn F8 and switch to dual view, how is it setup? Is it twin view or cloned?

It's cloned. The LCD television I connect it to has a native resolution of 1366x768. It automatically detects the resolution and the taskbar+windows+icons are rearranged accordingly on the notebook display. Then the notebook display shuts off after a while...

What video card does your m1210 have? Apparently, another user cannot get it to work either:

[http://ubuntuforums.org/showthread.php?t=632832](http://ubuntuforums.org/showthread.php?t=632832)

> **HDave said:**
> 

External Monitor (with Laptop Screen Off, not Dual-View):
	Did not work, had to use "nvidia-settings" program to enable
	NOTE: don't install nvidia-settings package...program is available with restricted drivers
	NOTE: Screens and Graphics applet will break xorg.conf and set you back big time!
	**NOTE: Fn-F8 key could not get to work, have to reboot to switch modes**

---

### Post by KimH on 2008-04-19
As mentioned earlier, I remember that  FN+F8 worked just fine with a VGA cable, but after I switched to HDMI/DVI i noticed that i couldn't switch anymore..... Today I tried with the VGA cable again just for testing. To my big surprise FN+F8 did not work on the VGA cable anymore :confused: It seems that something has changed in Hardy over the last couple of weeks or maybe I have messed up some settings. I don't know :confused:

I hope this is solved n the final release of Hardy next week.

---

### Post by steveneddy on 2008-04-19
I hate those Fn keys.

---

### Post by atlas95 on 2008-04-19
This doesn't work for me too, but this had work in hardy !
Please see this bug and +1 it :)

[https://bugs.launchpad.net/dell/+bug/218062](https://bugs.launchpad.net/dell/+bug/218062)

---

### Post by KimH on 2008-04-20
> **atlas95 said:**
> This doesn't work for me too, but this had work in hardy !
Please see this bug and +1 it :)

[https://bugs.launchpad.net/dell/+bug/218062](https://bugs.launchpad.net/dell/+bug/218062)

You have got my +1 on this :)

---

### Post by thecure on 2008-04-20
> **KimH said:**
> You have got my +1 on this :)

Have Dell 1420, running Hardy 64 bit version. Function keys work sporadically but have Nvidia card and so I just use Nvidia's configuration tool and that works fine.

---

### Post by fnielsen on 2008-05-07
Fn+F8 does not work for me with Hardy and Dell Latitude D420. It did work with gutsy.

---

