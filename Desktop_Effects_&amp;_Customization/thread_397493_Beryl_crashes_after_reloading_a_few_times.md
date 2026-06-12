---
title: "Beryl crashes after reloading a few times"
date: 2007-03-30
forum: Desktop Effects &amp; Customization
---

### Post by Europa2010AD on 2007-03-30
After installing Beryl for the first time, it appeared to be running smoothly. However as I was fiddling with the settings and had to reload it a few times, my computer frozed as Beryl was coming back up on the 3rd or 4th time. Then after rebooting my computer Ubuntu wouldn´t load up properly and I have to go into recovery mode to revert back to the default xorg.conf.

Does anyone know why would this be happening? I followed this guide [here]("http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7").

Btw, is there a way to find out whether I´m running aiglx or xgl?

Below is my original xorg.conf,

> Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

and my modified xorg.conf,
> 
Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver		"radeon"
	Option		¨DRI¨ ¨true¨
	Option		¨ColorTiling¨ ¨on¨
	Option		¨EnablePageFlip¨ ¨true¨
	Option		¨AccelMethod¨ ¨EXA¨
	Option		¨XAANoOffscreenPixmaps¨
	Option		¨RenderAccel¨ ¨true¨
	Option		¨AGPFastWrite¨ ¨on¨
	BusID		"PCI:1:0:0"
EndSection

Thanks a lot for any help and suggestions!

---

### Post by FakeOutdoorsman on 2007-04-01
It could be a number of things but I would recommend a quick reinstall following the instructions on the Beryl Wiki.

1. Read the section on ATI Drivers: [Install Beryl on Ubuntu Edgy with GC Drivers]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_GC_Drivers")

This will give you some basic info on the three ATI drivers: "ati","radeon" and "fglrx".

2. [Install Beryl on Ubuntu Edgy with AIGLX]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX") also on the Beryl Wiki.

---

### Post by Europa2010AD on 2007-04-03
I think I have got Beryl running pretty stable now, after fixing my xorg.conf using the following guides:

[https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy]("https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy")
[http://gentoo-wiki.com/AIGLX]("http://gentoo-wiki.com/AIGLX")

(For some weird reason, I couldn't get it working using only the Ubuntu guide. I had to add in the few lines from the Gentoo wiki that's not contained in the Ubuntu guide.)

Anyway, I've now run into another minor issue:

Whenever I try to play video clips while running Beryl, I only get a blank, black screen. The video would appear for a brief second if I flip to another desktop and flip it back.

The video would work perfectly if I switch back to Metacity using Beryl Manager. So I'm pretty sure it's a problem with Beryl.

Any idea how I can fix this?

---

### Post by FakeOutdoorsman on 2007-04-03
I had this problem when using VLC with Beryl and AIGLX on Edgy.  I fixed it by:

VLC -> Settings -> Preferences -> Video -> Output Modes -> Check "Advanced Options" box -> change video output from "default" to "X11 video output".

Not everyone is satisified with the way X11 makes the videos look since the quality isn't as good as default in Metacity usually.

More info: [Re: cant see video when beryl run]("http://ubuntuforums.org/showthread.php?p=1871612#post1871612")

---

