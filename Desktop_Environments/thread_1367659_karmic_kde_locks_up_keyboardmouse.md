---
title: "karmic kde locks up keyboard/mouse"
date: 2009-12-29
forum: Desktop Environments
---

### Post by maestrobwh1 on 2009-12-29
I have an issue with karmic on a t43 Thinkpad where the keyboard and mouse buttons (the cursor still can move) stop responding.  Pressing the powerbutton prompts a logout and I wait for the 30 seconds to go by and logout restarts the login dialog.  Logging back in solves the problem.  THIS IS NOT A HARD LOCKUP THEN.

This is a thinkpad that has upper and lower mouse buttons on the touchpad.  At some point, there was no support for the lower set (stopped working).  I am not sure if this is related.

[edit]
Running Kubuntu, but _I find other posts similar to this issue that also happen in gnome and they seem to involve laptops_.  **_Please read below and if you see something like I listed in the next post and you have a usb mouse you can plug in and this lets you regain access to the desktop, post back.  _**I want to gather info to file a bug.

**I did a fresh install since this became so annoying.  I am now seeing the same exact thing!**

Help?

---

### Post by cybergalvez on 2009-12-29
I don't think its your think pad, I am having the very same issue with the gnome desktop on my desktop

---

### Post by maestrobwh1 on 2009-12-31
The only think that I can do other than hit the power button to logout **_is unplug or replug a usb mouse.  This also seems to "fix" the issue temporarily._**

I also installed "gsynaptics" and deactivated the touch pad when I am using the mouse.

[I think] There is something recent with something to do with the touchpad and a recent update.*  The bottom 2 buttons on the thinkpad are inoperable most of the time (when the pad is activated via gsnaptics), however sometimes one or the other will work.  The upper two always work.

*I have an IDENTICAL machine that I have not "updated" in several weeks, and that one works fine and all touchpad hardware works as expected all of the time.

I think I should report a bug if others are seeing something like this.

[edit]
Bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/501942](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/501942)

---

