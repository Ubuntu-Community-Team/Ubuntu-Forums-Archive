---
title: "Blank screen at start up for Inspiron 2500"
date: 2008-12-24
forum: General Help
---

### Post by omikun on 2008-12-24
It has a 700mhz PIII, 256megs of ram, 40 gig hd, and 815 intel chip. It was running XP fine but slow, so I wanted to install 8.10 on it and see how it performs. Then the problems started:

It hangs when I try to boot off of the live CD. It gives me the pretty ubuntu logo and the orange progress bar and once it fills up it does nothing else (even after an hour or two).
I get a blank screen when I installed with WUBI and tried to boot off of that. (same as above except I get a blank screen after the progress bar fills)

Alternate cd approach:
Another blank screen when I reformatted it and installed Ubuntu and tried to boot off of that. (progress bar fills and then the whole screen goes blank)
When I go to recovery console and continue boot, it hangs at Starting GNOME Display Manager.

I looked for my X11 xorg.conf in recovery mode but there is no such folder under /etc/ and the only xorg I found (with "find . -name xorg" at root dir) is for the keyboard under /usr/

Is there a way to still salvage this?

Oh and both CDs worked on other computers so it's only this pos that the problem manifests.

Another piece of info: I tried to install xp pro w/ sp2 after all of this and it doesn't go pass 'loading up drivers' or whatever. 

Yet another piece of info: after I tried to adjust the partition size the first time I tried to install with the regular ubuntu cd while the XP parition was still there and failed (due to some directory mismatch) I would get a blank screen after the Windows load screen trying to boot into XP. I got rid of that by booting in safe mode and disable the video driver fixed that. Afterwards I could boot in XP normally but the resolution was stuck at 800x600 and I couldn't find a newer driver than the one already installed so I figured Ubuntu would be a better alternative.

---

### Post by namdung on 2008-12-24
I suggest you try Xubuntu instead.

---

### Post by omikun on 2008-12-24
Sweet that worked! Thanks! I wonder why XP setup doesn't load though. Oh well. Thanks again!

---

### Post by namdung on 2008-12-24
Glad to be of help. You may mark the thread as solved if you're satisfied and thank me to help boost my ego :-)

---

### Post by omikun on 2008-12-25
I don't know if I should start a new thread, but I can't get my resolution up beyond 800x600 (it should go up to 1024)

Here's what my xorg.conf says:

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"

Do I just change UseFBDev to vesa or something? I researched it but I am not exactly sure what to do...

---

