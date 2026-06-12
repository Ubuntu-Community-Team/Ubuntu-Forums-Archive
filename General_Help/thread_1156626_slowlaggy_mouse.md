---
title: "slow/laggy mouse"
date: 2009-05-11
forum: General Help
---

### Post by jjblackfox on 2009-05-11
Hi, I just convinced my brother to switch over from XP to Ubuntu and everything is running smoothly except for his mouse. The cursor moves very slowly, which is very annoying. 

He has an nVidia GeForce 6200 LE graphics card and we tried two different usb mice, but both of them have the same problem.

I enabled the NVidia Accelerated Graphics Driver v.180 and rebooted, to no avail.

---

### Post by Tipped OuT on 2009-05-11
Try to configure it. Go to System< Preferences< Mouse.

---

### Post by jjblackfox on 2009-05-11
I tried that, it just changes the acceleration of the already laggy mouse. Basically, the problem is that the mouse pointer's movements are jerky and it isn't one smooth motion, like the mouse pointers refresh is too low.

---

### Post by Tipped OuT on 2009-05-11
I've had this problem in Ubuntu 8.10...I'm guessing that's what you're using? Good news, it was fixed in Ubuntu 9.04. Time for an upgrade my friend. :)

If you are using Ubuntu 9.04 then..ouch. I don't know.

---

### Post by jjblackfox on 2009-05-11
I used a fresh install of Ubuntu 9.04, unfortunately, it's not fixed for him.

---

### Post by Tipped OuT on 2009-05-11
Has he installed all of the updates? Has he tried using another kernel at boot? Has he tried editing Xorg? Is it a mouse or a touch pad?

---

### Post by jjblackfox on 2009-05-11
> **Tipped OuT said:**
> Has he installed all of the updates? Has he tried using another kernel at boot? Has he tried editing Xorg? Is it a mouse or a touch pad?

He has installed all the updates, it's a mouse, haven't tried using another kernel or editing Xorg, but I'm not sure how it works.

---

### Post by Tipped OuT on 2009-05-11
To edit Xorg, open Terminal and type: dpkg-reconfigure xserver-xorg 
or for the manual way: nano /etc/X11/xorg.conf

---

### Post by jjblackfox on 2009-05-11
doesn't look like that did anything

---

### Post by Tipped OuT on 2009-05-12
Sorry, I don't know then.

---

### Post by jjblackfox on 2009-05-12
The xorg seems to be really short, perhaps the problem is in here:


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

There isn't a refresh rate or screen resolution, and it seems a lot shorter than other xorg lists.

---

