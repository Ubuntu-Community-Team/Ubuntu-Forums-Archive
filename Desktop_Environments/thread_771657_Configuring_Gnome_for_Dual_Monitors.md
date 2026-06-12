---
title: "Configuring Gnome for Dual Monitors"
date: 2008-04-27
forum: Desktop Environments
---

### Post by theburningor on 2008-04-27
I just finished installing Hardy Heron on a machine with an nVidia GeForce 9 series and dual monitors.  I got the drivers and TwinView set up ok so that the desktop expands across both screens.  However, I'd like to have it set up so that the panels only display across the top of one monitor rather than both and so that dialog boxes and new applications appear centered on one monitor rather than right in the middle of the two.  This behavior is equivalent to the 'Extend my windows desktop on to this monitor' functionality in XP

I'm not sure if this is a Gnome proglem, an X problem, a TwinView problem or what but I figured I would start here.

---

### Post by Person98 on 2008-04-27
if you use xinerama instead of twinview you can do what you want, although it is getting kinda outdated now( I don't know why I personally think it is the best out of all the multimonitor options) you can find some how-to's around the net, it might take a little more effort and patiance on your part though.

---

### Post by theburningor on 2008-04-27
It appears that in Hardy, Xinerama is being deprecated in favor of XRandR which has a GUI.  I'm still not clear on exactly how its supposed to be configured.  Will post back here when I figure it out.

---

### Post by RAOF on 2008-04-27
> **theburningor said:**
> It appears that in Hardy, Xinerama is being deprecated in favor of XRandR which has a GUI.  I'm still not clear on exactly how its supposed to be configured.  Will post back here when I figure it out.

For you, it can't (unless you're using the free, 3d-less 'nv' drivers, or the experimental maybe-3d-capable 'nouveau' drivers).  The nvidia proprietary driver doesn't support XRandR (1.2, the version required for the GUI).

This is something that annoys me about TwinView.  You can enable it in xorg.conf (by running *sudo nvidia-xconfig --twinview*) and then you'll get the behaviour you want as long as all your screens are plugged in when you boot (or technically when you start X).  It doesn't seem to work correctly when you dynamically add or remove monitors.  Logging out and logging back in again should make it work properly once you've changed your monitor setup, though.  To do these dynamic changes, you can use the 'nvidia-settings' program, which is in the 'nvidia-settings' package (would you believe? :)).

---

### Post by mriedel on 2008-04-28
theburningor, TwinView provided me with the setup you're looking for by default (or rather after enabling it).

It's kind of annoying that there's no console-based equivalent of nvidia-settings (that i know of) though. Causes [this]("http://ubuntuforums.org/showthread.php?p=4810361#post4810361") problem for me.

---

