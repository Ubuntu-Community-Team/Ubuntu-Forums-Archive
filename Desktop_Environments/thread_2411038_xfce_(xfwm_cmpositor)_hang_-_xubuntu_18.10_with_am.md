---
title: "xfce (xfwm cmpositor) hang - xubuntu 18.10 with amdgpu and ryzen 2600"
date: 2019-01-23
forum: Desktop Environments
---

### Post by tigerdog on 2019-01-23
Background:  I have used Xubuntu for many years, and run 18.10 successfully in the past.  I built a new machine over the holidays, switching to AMD graphics after many years with nVidia.  

The Problem:  the xfce interface becomes unresponsive after the system sits idle for approx 1 hour.  I can no longer scroll the browser window and the system sits for 30-60 seconds before responding to a mouse-click to switch desktops.  Sometimes other apps work, but dragging the unresponsive browser window onto a different desktop freezes this desktop also.

Attempts to resolve:  try newer kernel 4.20, with newer amdgpu (no change.)  disable compositor from control panel (still hung.)  try to install amdgpu-pro proprietary driver (not supported in 18.10, only 18.04).

Workaround:  disable native compositor, install compton.
Once compton was installed and system restarted, I have had no more issues.  I think this points to something in the native xfce/xfwm compositor but don't know the system structure well enough to pinpoint further.

For now, I'll live happily with my workaround but I thought I should report this issue somewhere.  If this is not the best forum, please tell me what is.

---

### Post by DuckHook on 2019-01-24
Thanks for the info and workaround, tigerdog.

This is as good a place as any for your workaround. But you've probably been around long enough to know that the forums are basically run by fellow Ubuntu user enthusiasts like you and me, and the developers rarely, if ever, visit here.

The best (only?) place to get action on a bug is to report it in Launchpad. That's the formal avenue for getting the developers' attention on bugs. Try searching their database first. Someone else may already have reported it, in which case, you should me-too the existing bug report instead of starting a duplicate (the devs don't like that).

Cheers and good luck!

---

### Post by slickymaster on 2019-01-24
I'd advise you to report a bug againts the xfwm4 package in [https://bugs.launchpad.net/ubuntu/+source/xfwm4/+filebug](https://bugs.launchpad.net/ubuntu/+source/xfwm4/+filebug) and even upstream: [https://bugzilla.xfce.org/enter_bug.cgi](https://bugzilla.xfce.org/enter_bug.cgi)

---

### Post by tigerdog on 2019-01-24
Thanks for the direction.  DuckHook, you are correct that I've been around a while, but am fortunate that I have never really needed to pay much attention to bugs.  Stuff has "just worked" for me.  I'll consider myself lucky.  I'll head over to launchpad now.

---

