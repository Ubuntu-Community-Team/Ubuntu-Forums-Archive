---
title: "Problems Installing Banshee"
date: 2008-09-24
forum: Fedora/RedHat and derivatives
---

### Post by leipzigzag on 2008-09-24
I'm new to fedora and linux. When I install banshee, this error shows up: 

Transaction Check Error:
  file /usr/share/desktop-directories/Internet.directory from install of gnome-menus-2.20.1-1.fc8 conflicts with file from package xfdesktop-acer-lp-1522.no_spot.mcs_patched
  file /usr/share/desktop-directories/Settings.directory from install of gnome-menus-2.20.1-1.fc8 conflicts with file from package xfdesktop-acer-lp-1522.no_spot.mcs_patched

Error Summary
-------------

I'm not sure what that means, or what to do... 

Thanks.

---

### Post by igknighted on 2008-09-25
This is a forum for Ubuntu Linux.  While some might have knowledge of your problem in Fedora, you will have much better luck at [http://forums.fedoraforum.org](http://forums.fedoraforum.org).

When you post there, also tell them how you are trying to install banshee - repo's (yum install banshee), RPM (.rpm file), source (.tgz file), etc.  It will help get more accurate advice.

Also, Fedora recently shut down their update servers and actually switched to new ones due to a security compromise.  Thus your system may not be using the newest update servers and cannot get the proper packages.  Try doing a full system update (yum update) first.

---

