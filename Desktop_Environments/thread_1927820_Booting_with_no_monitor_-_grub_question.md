---
title: "Booting with no monitor - grub question"
date: 2012-02-18
forum: Desktop Environments
---

### Post by fmouse on 2012-02-18
I'm running Ubuntu 11.04 on a desktop system.  If my monitor is on, everything boots nicely as it's supposed to.  

When I'm away from home I turn off everything including my monitor, my Ubuntu desktop system - everything except my Linux in-house router/gateway.  I have a VPN to said router/gateway, and can run a wake-on-LAN command to bring up my desktop box so I can get to files I need on it.  If my monitor is on, this works fine, the system comes up, and I can ssh into the desktop box and do what I need to do.  If my monitor is off, however, the system won't boot.  I found out that in this state, grub has presented a text-mode menu to what it thinks is the effective terminal, and is waiting for a response, which it won't get since the network isn't up at that point.  It's either hung, or waiting with a very long timeout.

I used to configure grub all the time, but don't have the bandwidth to figure out the rather complex bootloader file collection use by the grub-pc installed in Ubuntu 11.04.  Can anyone tell me how I can tell grub-pc in this Ubuntu to boot normally if there's no monitor connected to the box?

---

### Post by SteveDee on 2012-02-19
> **fmouse said:**
> I'm running Ubuntu 11.04 on a desktop system.... Can anyone tell me how I can tell grub-pc in this Ubuntu to boot normally if there's no monitor connected to the box?

No, but I did have a similar problem prior to version 10.10.

So this may be a long shot, but I created a simple configuration like this:-
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection


Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync 31.5-48.5
	VertRefresh 50-70
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24
	SubSection "Display"
	Depth 24
	Modes "800x600"
	EndSubSection
EndSection

```
...and put it in /etc/X11/xorg.conf

If you don't have a /etc/X11/xorg.conf it should be safe to create one with the above text. If you do have one, save a copy as /etc/X11/xorg.confOld or something.

---

