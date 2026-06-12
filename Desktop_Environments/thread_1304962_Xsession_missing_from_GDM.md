---
title: "Xsession missing from GDM"
date: 2009-10-29
forum: Desktop Environments
---

### Post by Ambush Commander on 2009-10-29
This is a continuation of [http://ubuntuforums.org/showthread.php?t=1299248](http://ubuntuforums.org/showthread.php?t=1299248)

The relevant bugs are:

[https://bugs.launchpad.net/ubuntu/karmic/+source/gdm/+bug/398300](https://bugs.launchpad.net/ubuntu/karmic/+source/gdm/+bug/398300)
[https://bugzilla.gnome.org/show_bug.cgi?id=589544](https://bugzilla.gnome.org/show_bug.cgi?id=589544)

I am trying to cook up a workaround, but haven't been having much luck. Anyone else?

---

### Post by Ambush Commander on 2009-10-29
Aha, I got it to work. Add a file named "Xsessions.desktop" to /usr/share/Xsessions with the contents:

[Desktop Entry]
Name=Xsession
Comment=This runs ~/.xsession
Exec=/etc/X11/Xsession

---

