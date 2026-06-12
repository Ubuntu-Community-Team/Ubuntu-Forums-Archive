---
title: "KDE startup difficulties"
date: 2009-12-12
forum: Desktop Environments
---

### Post by Kensey on 2009-12-12
So, having decided to give KDE a shot, I immediately ran into two issues:

1) On login the desktop is initially very laggy.  I have Compiz chosen as the default window manager but it was laggy under KWin too.  With either KWin or compiz selected as the WM, if I open a terminal and type:

compiz --replace &

everything becomes much more responsive.  I could just add a startup task to do that, but that seems hackish.  Is there a cleaner way to fix this?

2) KDM just plain doesn't work (GDM works fine).  If I switch to KDM with dpkg-reconfigure gdm, then reboot, I get white and dark bars across the width of the middle third of the screen.  Moving the mouse causes a smear of pixels to move coherently, and typing likewise causes things to change, so the system appears responsive, just with a corrupted display.

I read about a bug where using KDM with desktop effects on causes a corrupted display on certain hardware, but turning off desktop effects didn't fix my issues like it did for others.  (My hardware is a Dell Latitude D610 with Intel 915GM graphics.)  For now I'm just living with GDM (and the face browser coming back after every round of updates)...

---

