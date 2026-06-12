---
title: "2nd monitor does not dispaly"
date: 2009-03-11
forum: Desktop Environments
---

### Post by luke0927 on 2009-03-11
Hello just installed Kubuntu on a dell laptop everything is fine I attached a external monitor....and went to configure dislpay to try and enable it but it never comes on I tell it to set the VGA0 resolution and it applies the settings but it never comes on.....is there something else i need to do...

thanks

---

### Post by ubudog on 2009-03-11
There should be a button on your keyboard, I think F4 or something that has a picture of a monitor on it.  Press fn and then press that and maybe it will work.  You may have to push it a couple of times though.

---

### Post by luke0927 on 2009-03-11
F8 is the CRT/LCD button but it does not work i tried that earlier.

---

### Post by warp99 on 2009-03-11
> **luke0927 said:**
> Hello just installed Kubuntu on a dell laptop everything is fine I attached a external monitor....and went to configure dislpay to try and enable it but it never comes on I tell it to set the VGA0 resolution and it applies the settings but it never comes on.....is there something else i need to do...

thanks

Which drivers are you using?

---

### Post by luke0927 on 2009-03-12
I have not loaded any other drivers i thougt it was fine since my LCD display was fine...its a standard intel integrated laptop video card......any commands i can run to show anyone to help me figure out if is should load a different driver?

---

### Post by flying_icarus on 2009-03-17
I got my secondary display to work (a SD TV on tv-out) on a nvidia graphics card, but it was necessary to use the nvidia-settings program first, which configured the Xorg settings for the second display (easier than doing it manually, although that works too).

Inside KDE 4.x.x the display settings program (system settings->display) does nothing - it just crashes the whole system settings application.

So, what programs have you tried to use to set up the secondary screen? Maybe try googling up some info on a more basic way to set up the screen with intel drivers?

Oh and yes, one more observation - on a laptop with an old ati card, the secondary display wasn't detected if it was plugged in after the laptop booted. Only when connecting it while the laptop was powered off, did it come up while booting.

Hope this helps somewhat. ;)

---

### Post by dbaas41 on 2009-03-17
I'm using a dell Inspiron 1525 laptop with Ubuntu and ran into largely the same problem as you.  The solution for me involved altering my xorg.conf file.

The main issue seemed to be setting the virtual screen size...before I did that, the external monitor would not do anything.

---

### Post by dbaas41 on 2009-03-17
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	Option		"monitor-VGA" "laptop"
	Option		"monitor-LVDS" "external"
EndSection

Section "Monitor"
	Identifier	"laptop"
	Option		"PreferredMode" "1024x768"
EndSection

Section "Monitor"
	Identifier	"external"
	Option		"PreferredMode"	"1024x768"
	Option		"LeftOf"	"laptop"
	#Option		"Enable"	"true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"laptop"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Virtual		2048 768
	EndSubSection
EndSection

```

This is part of the altered xorg.conf...the main section I had to fix was the "Screen" section.  Set the virtual screen size to the sum of your two resolutions in both the x and y directions.  Unfortunately, some issue results in my hardware only supporting 2048 X 2048...  So there's the possibility that you can run into the same issue.  Otherwise you should be able to go up to 4096 if I remember correctly.

---

