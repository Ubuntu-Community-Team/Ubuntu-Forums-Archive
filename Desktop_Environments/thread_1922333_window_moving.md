---
title: "window moving"
date: 2012-02-08
forum: Desktop Environments
---

### Post by Rahabib on 2012-02-08
been having this issue the last few days. I havent seen another thread about this.

I am running unity on a macbook pro with a second monitor.  first monitor is the lcd of the laptop is running at 1440x900 and the second monitor is running at 1920x1200.

Everything worked great until yesterday, where for no reason when I drag a file in nautilus (or some other programs), the macbook lcd moves up.  As soon as I let go of the file it goes back to its original location.  I assume this is a bug introduced in an update in the last few days since no settings were changed on my end, but I am not sure and dont want to file a bug when there is a known work around (nothing appears with my search criteria on this forum or bugzilla).

This happens infrequently dragging emails around in thunderbird.  It happens all the time in nautilus when in "icon" mode.  List mode, it happens infrequent.

my thought is that this is related to nvidia x server display settings and the difference between the resolutions.  its strange that it happens only when dragging files around.

---

### Post by Rahabib on 2012-02-09
update. Unity 2D doesnt have this problem.  only Unity 3D.

---

### Post by Rahabib on 2012-02-09
I have deleted the monitor.xml and removed and re-installed the  nvidia 173 drivers to no effect.  I can minimize the effect by enabling  "Force full screen redraws (buuffer swap) on repaint" in "Work Arounds"  in CCSM.

gnome classic and unity 2d work fine.  My thoughts are that either CCSM, Nvidia, or a unity update has caused this.

---

### Post by Rahabib on 2012-03-08
ok. bug filed. more info given.  its apprently linked to an update with Unity and panel opacity in CCSM.  I hope at some point it gets fixed.  I am not sure why I even bother reporting bugs since nothing gets looked at.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-driver-nv/+bug/932229](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-driver-nv/+bug/932229)

---

