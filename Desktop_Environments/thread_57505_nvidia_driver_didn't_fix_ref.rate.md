---
title: "nvidia driver didn't fix ref.rate"
date: 2005-08-16
forum: Desktop Environments
---

### Post by yeonil on 2005-08-16
I am having issues with low refresh rate, i cannot set it higher than 60hz @ 1024*768 (my monitor is capable of maintaining at least 75, or 80Hz) i have installed nvidia drivers + settings, but in the configuration program there is no option to alter the refresh rate. i have GeForce FX 5200, ubuntu hdd install (dual boot)
Thanks in advance,


Yeonil
edit: ah, and hello there :D
edit: did I mention that I am a noob?  :grin:

---

### Post by GreyFox503 on 2005-08-16
This is one of my responses from another thread:

[QUOTE=GreyFox503]I had a similar problem with my login screen being at the wrong refresh rate than my desktop.  The solution involved adding custom lines to my xorg.conf file, at /etc/X11/xorg.conf

There are several threads on this forum on how to do that.  You might be able to fix it the easier way by running this:

```
sudo dpkg-reconfigure xserver-xorg
```

this is a way to configure your xserver by choosing options about your graphics card and monitor.

When it gets to the part about choosing resolution, there will be three choices, something like:

Easy
Medium
Advanced

I don't remember the exact wording.  If you choose medium, then you can specify your monitor's resolution and refresh rate.[/QUOTE]

---

### Post by yeonil on 2005-08-17
thanks a lot, i did it, and it really asks for the refresh rate now, but when i logged again to gnome the refresh rate stayed the same (60Hz) (i chose 75Hz) (and in the resolution window there is only one choice still)

Yeonil

---

### Post by GreyFox503 on 2005-08-17
If you know the exact specs of your monitor (you can look them up from the manufacturer's website), then you can enter then specifically in your xorg.conf file, like I had to do.

Here's how to backup and edit your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```

Once you're in there, look for the section called "Section 'Device'".  Here's what mine looks like:

```
Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	262144
	Option		"UseFBDev"		"true"
[B]	Option "HSync2" "63.80"
	Option "VRefresh2" "60.00"[/B]
	Option "NvAGP" "3"
	Option		"NoLogo"
EndSection
```

You don't need all that stuff, but the bolded parts show where I specified my Horizontal and Vertical refresh rates.

My Vertical refresh rate (the one you probably care about) is at 60Hz, but you can change yours to 75Hz or whatever you want it to be.

To find out the correct values, though, I would see the manufacturer's website and find your monitor for its exact specs.

---

### Post by yeonil on 2005-08-17
Hey, thanks, GreyFox503, this one helped, i changed the rates in my monitor tab. I wasn't sure at all before your post, that the "refresh rate" in general is practically the same as vertical refresh (rate).

Yeonil

---

### Post by GreyFox503 on 2005-08-17
Glad to know it worked  :)

---

