---
title: "Screen resolutions in Gnome not available in KDE"
date: 2006-10-26
forum: Desktop Environments
---

### Post by raymacey on 2006-10-26
I'm running Edgy, and I've installed the kubuntu desktop as well.  I've installed the nvidia beta drivers to get Beryl working, and that's going fine.

The problem is, when I load KDE instead of Gnome, I get a 65Hz, small resolution on my monitor.  The higher resolutions are working fine at 85Hz in Gnome though.  To the best of my knowledge, they both get these details from xorg.conf, so I'm kinda at a loss as to where to look.

Any ideas would be greatly appreciated...

---

### Post by tagginannie on 2006-10-27
> **raymacey said:**
> I'm running Edgy, and I've installed the kubuntu desktop as well.  I've installed the nvidia beta drivers to get Beryl working, and that's going fine.

The problem is, when I load KDE instead of Gnome, I get a 65Hz, small resolution on my monitor.  The higher resolutions are working fine at 85Hz in Gnome though.  To the best of my knowledge, they both get these details from xorg.conf, so I'm kinda at a loss as to where to look.

Any ideas would be greatly appreciated...

Try running 'krandr' in a terminal it should already be in kdebase if it is not there you can install it I believe by using this command 

sudo apt-get install krandr 

You can also use "krandr" as try icon and than use CTRL,ALT and the +/- signs from your number pad to increase/decrease resolution that are configured in the /etc/X11/xorg.conf

Hope this helps
Suzy

---

### Post by raymacey on 2006-10-27
Well, I can see all of my higher resolutions using krandtray, so thanks for that tip.  Unfortunately, it didn't solve my problem though, as all of the refresh rates listed are 54Hz, 55Hz etc. For some reaon I can't get my regular 85Hz, though I can in Gnome...

---

### Post by raymacey on 2006-10-28
And now it gets even stranger.  Using krandtray, when I change to 50Hz, my monitor uses 85Hz, avoiding the problem, in spite of the fact there is no option to actually select 85Hz as a refresh rate...

Another question, is this thread in the right subforum, or is there a more appropriate one?

---

### Post by chaosgeisterchen on 2006-10-28
You may rather post it in the hardware-sector. But it's obviously a display problem of KDE.

---

