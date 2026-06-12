---
title: "Desktop Effects not enabling"
date: 2007-05-08
forum: Desktop Effects &amp; Customization
---

### Post by jroque on 2007-05-08
I was working find with Ubuntu 7.04 desktop and the desktop effects until I install Beryl. I remove all package related to Beryl and re-install all related to Compiz to see if I could get my 3d effects back, but it is giving me the error message that "Desktop Effects could not be enable"

Any idea how can I restore my original configuration?

Thank you.

---

### Post by rufius on 2007-05-08
What kind of video card do you have and is acceleration enabled?

---

### Post by jroque on 2007-05-08
Section "Device"
	Identifier	"Intel i810"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel i810"
	Monitor		"Generic Monitor"
	DefaultDepth	24

SubSection "Display"
		Depth		24
		Modes		"1152x768" "1024x768" "800x600" "640x480"
	EndSubSection

---

### Post by jroque on 2007-05-08
I fix it.

I whent to Systems | Administration | Synaptic Package Manager | File | History 

and noticed that I removed the following files, so I reinstalled them:

compiz-extra (0.3.6.1-0ubuntu2)
gnome-games (1:2.18.1-0ubuntu1)
libcm7 (0.1.1-0ubuntu2)
ubuntu-desktop (1.43)
desktop-effects (0.7.1-0ubuntu4)
gnome-compiz-manager (0.10.3-0ubuntu1)
libgnome-compiz-manager0 (0.10.3-0ubuntu1)

then I removed:

xserver-xgl
libglitz-glx1
libglitz1
xorg-driver-fglrx

I did logout and press Clt. Alt. Backspace

And Desktop Effects works

---

### Post by Goldnblazer on 2007-05-30
I am stoked that I ran across this thread. I had the exact same problem with the exact scenario.
I added the items from your list and deleted the others and it works again.
This was the first time that I really needed help on this and the community came through.
This place rocks!

---

