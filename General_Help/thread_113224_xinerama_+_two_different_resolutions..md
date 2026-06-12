---
title: "xinerama + two different resolutions."
date: 2006-01-05
forum: General Help
---

### Post by bannerboy on 2006-01-05
is there any way to set up xinerama or a similar system, so that I can drag windows between two monitors that are running at different resolutions?

---

### Post by Leif on 2006-01-06
absolutely. it's no different than using xinerama in any other setup.

---

### Post by mgchan on 2006-01-10
Anyone have a link to a guide to setting this up?  I have one 1600x1200 LCD and a 1280x1024 LCD hooked up to an NVidia 6600GT.  The 1600x1200 is connected via DVI and the other is connected via VGA.  I've been able to get one running at 1600x1200 but the other would be stuck with the wrong resolution, or I can get both running at 1280x1024 sharing one desktop.

---

### Post by mntbighker on 2006-01-11
Look here:

[http://www.interparse.com/debianmultihead/](http://www.interparse.com/debianmultihead/)

There are some interesting options available in such an arrangement. Some cards will only offer 3D accel on the main display (whichever one that is). I had issues with my GT6600. Either the card or the driver limited certain features to the main display so the TV output had limitations. I never figured out how to make the TV the primary (HD Myth setup). There options regarding rotation, mirroring and virtual view port. xinerama generally thinks it's one giant space so annoyingly, new windows may open straddling the two displays :-( My ultimate plan is to have 2 Dell 2005's connected to my dual DVI GT6600 :-) I need a dual DVI kvm that costs less than a small car so my Mac and PC can share though.

--MM

---

### Post by mgchan on 2006-01-11
I followed the instructions here but still have both running at 1280x1024, even though I only have 1600x1200 listed in the "Modes" section of my larger monitor.  Any ideas on how to troubleshoot this?  The Xorg log file just stated that it was setting the monitor to mode 1280x1024 without trying 1600x1200.

[QUOTE=mntbighker]Look here:

[http://www.interparse.com/debianmultihead/](http://www.interparse.com/debianmultihead/)

There are some interesting options available in such an arrangement. Some cards will only offer 3D accel on the main display (whichever one that is). I had issues with my GT6600. Either the card or the driver limited certain features to the main display so the TV output had limitations. I never figured out how to make the TV the primary (HD Myth setup). There options regarding rotation, mirroring and virtual view port. xinerama generally thinks it's one giant space so annoyingly, new windows may open straddling the two displays :-( My ultimate plan is to have 2 Dell 2005's connected to my dual DVI GT6600 :-) I need a dual DVI kvm that costs less than a small car so my Mac and PC can share though.

--MM[/QUOTE]

---

### Post by mntbighker on 2006-01-11
Post your xorg.conf

---

