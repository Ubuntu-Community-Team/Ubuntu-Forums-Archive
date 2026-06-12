---
title: "NX doesn't display custom theme after system updates."
date: 2009-08-02
forum: Desktop Environments
---

### Post by ponx on 2009-08-02
Hi,

I run Ubuntu 9.04 with !Machine NX to remotely access my machine from work.  After installing recent system updates, all of a sudden my NX window fails to show the icons and menus for my custom desktop theme, resorting to GTK defaults (I think).  Oddly enough, the window decorations are ok, it's just the rest of the theme...

My theme's are fine when I log in locally.  I also tried re-installing NX, but to no avail...

Any ideas how to resolve this..?

ponx.

---

### Post by ponx on 2009-08-03
Looks like it may be linked to this (newly introduced) bug:
[https://bugs.launchpad.net/freenx-server/+bug/399758]("https://bugs.launchpad.net/freenx-server/+bug/399758")

---

### Post by rabbitofdeath on 2009-08-03
I think you are right - I have the same problem. I can't wait for this to get fixed!

---

### Post by Nickular on 2009-08-03
My NX desktop used to look like default Ubuntu, but now looks funny (see attached).  I am wondering if this is the same problem you are describing or something different.  

To my knowledge, I haven't changed any visual settings.  As I recall, the desktop started to look different after I used "ssh -X" to login from a different linux distro.  When using the computer locally (not through NX), everything looks normal.

---

### Post by rabbitofdeath on 2009-08-04
Yeah, this is the same problem as described. I've seen it happen on 3 different machines. Unfortunately there seems to be no workaround (that I can find atleast). Hopefully it will get fixed soon, I hate that blue :-/

---

### Post by Aaron44126 on 2009-08-04
Wow, [another](http://ubuntuforums.org/showthread.php?t=1231195) [one](http://ubuntuforums.org/showthread.php?t=1227186).  Glad I'm not the only one with this problem.  Hope someone finds a fix soon...

---

### Post by Aaron44126 on 2009-08-04
Fixed.  gnome-settings-daemon was crashing, see [this bug](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245).

Run gconf-editor.
Navigate to /apps/gnome_settings_daemon/plugins/keyboard.
Uncheck the "Active" box on the right.
Log out and log back in.

This disables the "keyboard" plug-in for gnome-settings-daemon.  I'm not exactly sure what this plug-in does at the moment, but my keyboard is still working fine.  :-P

---

### Post by Nickular on 2009-08-05
Just confirming that this fix works.  Thanks Aaron44126!

---

### Post by DrClaw27 on 2009-08-05
It doesn't seem to fix it for me.

---

### Post by Aaron44126 on 2009-08-05
Try disabling the "mouse" plug-in as well.  (Some people in the bug were commenting that they had to also disable the "mouse" plug-in to keep gnome-settings-daemon from crashing.)

---

### Post by thebigkevdogg on 2009-10-01
> **Aaron44126 said:**
> Fixed.  gnome-settings-daemon was crashing, see [this bug](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245).

Run gconf-editor.
Navigate to /apps/gnome_settings_daemon/plugins/keyboard.
Uncheck the "Active" box on the right.
Log out and log back in.

This disables the "keyboard" plug-in for gnome-settings-daemon.  I'm not exactly sure what this plug-in does at the moment, but my keyboard is still working fine.  :-P

That did the trick for me...thanks Aaron!

---

