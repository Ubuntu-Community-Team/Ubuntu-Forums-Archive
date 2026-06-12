---
title: "Gnome blank screen and power management with nvidia weirdness"
date: 2012-12-24
forum: Desktop Environments
---

### Post by paulisdead on 2012-12-24
I've been having this issue on a couple systems, both using the nvidia proprietary drivers and the 12.10 gnome remix.

The screen will go blank even when the power management is set to not shut off the monitor for an hour.  It will still try to blank the screen if smplayer is playing a video.  The other stupid thing is, about 90% or so of the time, it just blanks the screen and doesn't actually shut off the monitors.  

My 2 i7 systems have this issue, one with a Geforce 460 the other with a 560 448 core both experience this issue.  The one with the 560 is dual monitors with twinview, but the 460 box only has 1 monitor.

I've been using the 310 drivers, but had this problem on the older drivers.  I forget which version Ubuntu wants to install, it's the set not marked as experimental.  I needed the 310 drivers for the Steam beta, and they don't seem to have helped or hurt the situation.

Oddly enough I don't get this on my netbook using an nvidia ion GPU and the proprietary drivers.

Anybody have any ideas?  FC17 wasn't having this issue, back when I was running fedora.  So I know it's not the hardware.

---

### Post by Bobhuber on 2012-12-25
> **paulisdead said:**
> I've been having this issue on a couple systems, both using the nvidia proprietary drivers and the 12.10 gnome remix.

The screen will go blank even when the power management is set to not shut off the monitor for an hour.  It will still try to blank the screen if smplayer is playing a video.  The other stupid thing is, about 90% or so of the time, it just blanks the screen and doesn't actually shut off the monitors.  

My 2 i7 systems have this issue, one with a Geforce 460 the other with a 560 448 core both experience this issue.  The one with the 560 is dual monitors with twinview, but the 460 box only has 1 monitor.

I've been using the 310 drivers, but had this problem on the older drivers.  I forget which version Ubuntu wants to install, it's the set not marked as experimental.  I needed the 310 drivers for the Steam beta, and they don't seem to have helped or hurt the situation.

Oddly enough I don't get this on my netbook using an nvidia ion GPU and the proprietary drivers.

Anybody have any ideas?  FC17 wasn't having this issue, back when I was running fedora.  So I know it's not the hardware.
Edit the xorg.config and disable the power saving modes there. I'm on a different computer right now but if you look at the options posted on Nvidia's site under driver installation it will give you the correct settings and where to put them.

---

### Post by paulisdead on 2012-12-26
I could do that, but I'm actually looking to have this work properly, like it did in 11.10 and fc17.  It didn't used to try and just blank the screen while a video was playing, and the monitors turned themselves off when scheduled, like they were supposed.

---

### Post by paulisdead on 2012-12-26
I found this bug report, and am trying some stuff reported there.  We'll see how this works.
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/1062166](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/1062166)

---

### Post by powerpcliberation on 2012-12-27
In all the years I have been using Linux the one negative constant has been issues with Nvidia GPU.  There are generally always fixes but only because there are almost always issues.  Sad but true.

---

### Post by paulisdead on 2013-01-16
I'm going to give this a bump since it's been a couple weeks and no activity here or in the bug report I linked to.  Tweaking with the dconf settings mentioned in the bug report didn't help either.  I'm fully up to date.

I'm almost tempted to see if the problem is present in fedora 18 on one of the boxes.

---

### Post by BicyclerBoy on 2013-01-16
If you're not attached to it try remove gnome-screensaver & install Xscreensaver.

The gnome-screensaver is known on have problems from before 10.04 & it was generally blamed on gnome.

---

### Post by paulisdead on 2013-01-26
> **BicyclerBoy said:**
> If you're not attached to it try remove gnome-screensaver & install Xscreensaver.

The gnome-screensaver is known on have problems from before 10.04 & it was generally blamed on gnome.

That's been working much better.  I waited so long to really make sure I was aware of the exact behavior.  It's no longer blanking every few minutes, and the monitors shutdown properly at the specified time.  It still tries to blank the screens while smplayer's playing a video, though.  This is a big help, since I like to pass out watching something, so my monitors aren't glaring at me all night.

I've tried adding the following to the mplayer options
heartbeat-cmd="xscreensaver-command -deactivate >&- 2>&- &"

Caffiene set to monitor for smplayer/mplayer doesn't help either.

---

