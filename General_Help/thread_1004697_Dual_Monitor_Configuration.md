---
title: "Dual Monitor Configuration"
date: 2008-12-07
forum: General Help
---

### Post by grantmeaname on 2008-12-07
I don't know which forum to put this in, so I'll just put it here.

I have a Toshiba Satellite L35 laptop from two years(ish) ago. It has an ATi Mobility Radeon X300 IGP. I'm currently running Ubuntu 8.10 with the fglrx driver, X, and GNOME. I have an old CRT connected to the laptop's VGA-out port. The CRT is lacking EDID, the chip that contains the file stating what resolutions and refresh rates the monitor is capable of.

I would like to run both the laptop's panel (1280*800 60Hz) and the CRT (via VGA-0 at 1600*1200 85Hz, which it is capable of in Windows). Additionally, I would like to be able to move windows between the two screens. If this isn't possible, I'd like to configure it with two different refresh rates and give up the ability to move .

I don't know if the problem is in X or if it is in the driver, and beyond that I have no idea how to deal with it. The most similar post to my problem is _[unanswered]("http://ph.ubuntuforums.com/showthread.php?t=861608")_.

Thanks!! If this is in the wrong place, sorry.

---

### Post by NT4usB on 2008-12-07
ed: Been poking around my ATi box. Found a menu item under 'Other', Screen and Graphics Preferences. You tried that?

Do you have ATi Catalyst Control Center installed?
Easiest to hardest:
Install envy or envyng, depending on which supports your card, and use it to install The ATi driver (includes ATi Catalyst Control Center.) I chose uninstall first to clean out the old stuff. I had to use the manual install option to get my 9600 to work.

Install ATi Catalyst Control Center Linux flavor from the ATi site.

If you're savy in such things, you could build a xorg.conf manually. That's what I do when all else fails...

---

### Post by grantmeaname on 2008-12-08
> **NT4usB said:**
> ed: Been poking around my ATi box. Found a menu item under 'Other', Screen and Graphics Preferences. You tried that?

You lost me.

> **NT4usB said:**
> Do you have ATi Catalyst Control Center installed?

Yes. Edit: The best it will let me do is specifying that my CRT is left of my laptop. It sets them both to run at 1280*800@60Hz, so I have a 2560*800 screen now.

> **NT4usB said:**
> Install envy or envyng, depending on which supports your card, and use it to install The ATi driver (includes ATi Catalyst Control Center.) I chose uninstall first to clean out the old stuff. I had to use the manual install option to get my 9600 to work.

Envy NG's GTK mode doesn't do anything anymore, and all Envy NG's text-based does is install the driver.

> **NT4usB said:**
> If you're savy in such things, you could build a xorg.conf manually. That's what I do when all else fails...

I'm proficient enough to be comfortable with editing it (I've edited both it and grub.conf before) but I don't know what to actually put.

ED: I've tried to use aticonfig to help me... no beans.
Here's my shot at [pairmodes]("http://http://gagravarr.livejournal.com/114618.html"), which I gather are somewhat new...
```
grant@grant-laptop:~$ sudo aticonfig --add-pairmode=width1280xheight800+width1600xheight1200
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-6
grant@grant-laptop:~$ sudo aticonfig --list-pairmode
Get pair modes : 2
 0    1280x800 + 1280x800 --> 2560x800 
 1    0x0 + 0x0 --> 0x0 
```
I'm reluctant to remove pairmode 0 because it's the one I'm using at the moment.

I went into xorg.conf ```

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "EnableMonitor" "crt1,lvds"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "PairModes" "1280x800+1280x800,0x0+0x0"
	BusID       "PCI:1:5:0"
EndSection
```
and changed it to
```
Option	    "PairModes" "1280x800+1280x800,1280x800+1600x1200"
```

--list-pairmode still shows the same old thing after saving, but I guess that's because Xorg.conf is lower in the stack than aticonfig. I'm gonna reboot and post what happens.

Edit:it said the two pairs of dimensions can't be greater than 1280*800 and 1024*768. No pairmodes, I guess...

---

### Post by grantmeaname on 2008-12-11
bump...

can anybody tell me what to put in xorg.conf?

---

### Post by Forge on 2008-12-18
Fglrx was always pretty fiddly with multi-monitor IME, and it may not be possible to do what you want to do.

I haven't messed with fglrx multi-mon in quite some time, but in Ye Olden Days, there were multiple ways to configure multi-mon. The one they seem to still be using used to be called Big Desktop, where the two screens are seen by the OS/apps as one big desktop, on one virtual monitor. This constrained resolution support as you've seen.

They had another option called Extended Desktop that would see the two screens as separate and independent, and would allow independent res/refresh as well.

I'll have to poke at Intrepid+fglrx and a spare monitor when I get home. I'll also poke at bridgman to see what's up if the options have changed.

---

