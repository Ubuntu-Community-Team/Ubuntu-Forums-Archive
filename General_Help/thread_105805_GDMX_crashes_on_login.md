---
title: "GDM/X crashes on login"
date: 2005-12-19
forum: General Help
---

### Post by vortura on 2005-12-19
Hi all...

I'm having trouble with Breezy on a new PC.

It appears to have installed fine and X starts and prompts me for a login.  However as soon as I put in my username and password and click the login button, it just hangs.  Clicking the language button also causes it to hang.  Interestingly, the mouse still works, but there's nothing to click on, and apparently no system activity

I can't switch to another console... I haven't tried to ssh to the box in the hung state as I don't have another computer to try this with.  

The hardware is a Epox Nforce4 based motherboard, an amd64 3700+, and a geforce 7800GT based video card.  20" widescreen apple monitor.

I've grabbed the latest nvidia video card driver, but I haven't got that installed yet because I've been having a few problems compiling it.  I'm not sure that it is the driver though, given that X starts fine in the first place.

I'm kinda stuck.  Does anybody have any ideas?

Richard

---

### Post by BathroomNinja on 2005-12-19
First, you probably didn't need to make 2 threads about this; I'm sure you probably hit Submit twice, no big deal.

Did you install x86 or the 64bit version of Ubuntu?
Have you ever been able to log into X?
Do you have any USB devices plugged in?  If so, unplug them all and reboot, try logging in again.  Let me know those 3 things.

---

### Post by tlc on 2005-12-19
I have similar hardware and had the same problem. I solved it by booting into recovery mode, and changing the "nv" driver to "vesa" in /etc/X11/xorg.conf. This at least allowed me to log in. Make sure you've got your kernel headers installed before trying to install nvidia driver, or it won't work. Or if you can live with the 7676 driver, just use arnieboy's automatix script - it's in the customisation, tips'n'tricks forum.

EDIT: I recommend the latest 8174 driver, as the 7676 version wouldn't recognise the coolbits option or display temperatures in nvidia-settings, and the fan stayed at full ear-splitting shreik at all times. Everything works perfectly with 8174 though. (POV 7800GT) - Just remember to remove the nvidia-legacy package(s) via Synaptic before you install it.

---

### Post by vortura on 2005-12-19
Hi there...

Thanks for replying and sorry about the double post.  I clicked the post button and got an error saying I wasn't logged in, so I logged in and posted again.  2 posts... damn.

Anyway... The good new for me is that I got it working.  The nvidia drivers did the trick.

thanks,
Richard

---

