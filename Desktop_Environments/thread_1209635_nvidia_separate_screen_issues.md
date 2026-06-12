---
title: "nvidia separate screen issues"
date: 2009-07-10
forum: Desktop Environments
---

### Post by caradeporra on 2009-07-10
I have had several issues with setting up nvidia on the new ubuntu 9.04

  First, i tried to install the new nvidia drivers, the 180.  After installing, and restarting it works fine.  However, when setting up dual screens as separate x, the second screen is cut off.  i would say it uses about half of the screen but it shows in the top left corner.  so the right 1/3 of the screen is non-existent and the bottom 1/3 as well.  it is not the monitor.  Also, it is not the screen size settings because the screen is setup with the correct settings.  view the screen shot - the screen is cut off instead of just smaller.

  Right now i have installed the nvidia 173 driver which so far is functioning well enough.  There is a bug though where all (or almost all) programs opened through the second screen gnome-panel either open on the primary screen or not at all.  they can be opened through terminal or alt-f2 and will open on the secondary screen.  Some desktop shortcuts created will open on the secondary screen but some even still will open on the primary.  

  I would like to know if anyone else has had issues with the nvidia 180 driver.  I am on ubuntu 9.04 jaunty with a latitude d820 (not sure exactly which video card).

---

### Post by ambercromby on 2009-07-10
This is not a driver issue from what I have found so far. I have an older Nvidia GeForce4 using the 96.43.10 driver. I've tried 96.43.13 as well with the same results.

This seems to have to do with the Glib2 file not handling Screen 0:0 and 0:1 correctly. You can read more here.

[http://bugzilla.gnome.org/show_bug.cgi?id=580103](http://bugzilla.gnome.org/show_bug.cgi?id=580103)

I don't know how to modify that file and I have not seen that file being updated in the updates either.

Update:
Saw there was an X11 component update and had to reboot the computer, but still not working correctly.

---

