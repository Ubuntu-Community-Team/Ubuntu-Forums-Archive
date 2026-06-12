---
title: "Natty Plasma crash on login"
date: 2011-04-16
forum: Desktop Environments
---

### Post by camper365 on 2011-04-16
I just upgraded to Natty Beta 2, and when I tried to login, I was told that /tmp/2145539930/.kde/share/config/kdedrc is not writable (along with /tmp/2145539930/.kde/share/config/knotifyrc is not writable).  When I run ls -l, I get 
> -rw------- 1 kdm nogroup   39 2011-04-16 19:55 kdedrc

which implies that it is writable.
I can dismiss the dialog box, and after a few seconds of delay, see a crash report that kdeinit4 seg faulted.  I dismiss this and log in to see plasma not running, but I can Alt+F2 any command I wish (except plasma-desktop, it doesn't run).  I already purged kdm and reinstalled, and I'm trying plasma-desktop now.
Any help on how to get kdm and plasma to work would be greatly appreciated. Thank you

---

### Post by camper365 on 2011-04-16
Reinstalling (purging and reinstalling) plasma-desktop didn't solve anything.  Additionally, when I run individual plasma components from an Alt+F2 dialog (type in plasma to a dialog and pick a widget to run) it opens in a window, but not on the desktop.

---

### Post by camper365 on 2011-04-16
Sorry about the constant bumping, but it should be noted that I'm running the proprietary nvidia driver 270.41.03 on an Nvidia Quadro NVS 135M. I also tried running startx from a console login but to no avail, the same problem occurred without the dialog box telling me that /tmp/.../kdmdrc is not writable (which occurs at kdm loading, not login)

---

### Post by Zorael on 2011-04-17
It's not a good permanent solution, but have you tried to (temporarily) rename **~/.kde** and let it start afresh? If kdeinit4 is crashing, perhaps that's what in turn causes plasma to crash.

Also you could try clearing out your **/tmp**, and make sure the directory itself is owned by **root:root** and has a mod of **1777**. Not sure that all that is needed but it's the defaults.

---

### Post by camper365 on 2011-04-17
No, clearing out /tmp doesn't do anything. I also cleared out /var/tmp which was linked to by some of the files in /tmp, and that did nothing.  I'm up to date as of 10 minutes ago, but that didn't do anything. I'll try removing my /etc/kdmrc to see if that does anything (when I upgraded, it asked me if I wanted to keep my old kdmrc and I said yes, so I think the problem might be in there)

---

### Post by camper365 on 2011-04-17
I gave up for a few minutes and decided to try GNOME for the first time in two years, and was quite impressed by Unity, so I think I'll keep it. I think I was able to run kwin from an Alt+F2 dialog, and window decorations would appear, but that was the farthest I got. Good luck to anyone else who might possibly have this problem.

---

