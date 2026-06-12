---
title: "Strange window behavior in Breezy"
date: 2006-04-01
forum: Desktop Environments
---

### Post by thebasard on 2006-04-01
Hi all,
My wife is a mostly happy convert from Windows to Ubuntu.  But we've been having this annoying problem with her Breezy install on a Dell Latitude D600.  This laptop has the Radeon 9000 and we have the Radeon driver loaded.

The problem we have is this: She might have serveral windows open and for some reason the computer goes into a state where the mouse works and the keyboard functions but she is unable to minimize, maximize or close any of the open windows.  The only way we've found to gain control over her computer again is to hit ctl+alt+backspace.  Sometimes, alt+f4 will work.

She's starting to mention going back to Windows if this problem doesn't get fixed so any help would be greatly appreciated!

Thank you in advance,
Clay

---

### Post by taurus on 2006-04-01
Maybe it has something to do with the ATI driver for your video card!  If she doesn't need the 3D capability, switch the driver in /etc/X11/xorg.conf to "vesa" and see if she still experiences the same problem...  Why go back to Windows when there is a solution to a problem!!!

---

