---
title: "KDE screen resolution change crashes xserver"
date: 2007-05-07
forum: Desktop Environments
---

### Post by myoungf1 on 2007-05-07
Ok hopefully this will get me some help.  I have just installed Ubuntu 7.04 and got the core system up with fglrx drivers installed.  Gnome is working wonderfully at the right screen resolution for the monitor that is being used.  I installed the KDE desktop environment and then went to change the screen resolution from the horrid 640x480 default to the correct resolution for the monitor and restarted.  After that X server now crashes and no matter what I do to reconfigure xorg.conf X will not start up again.  I am running an ATI Radeon X1300 256 MB graphics card and a Xerox 19" widescreen LCD monitor.  Again, not to be redundant, Gnome works correctly at the right screen resolution and refresh rate but KDE does not and changing the screen resolution to the correct setting kills X and modifying the .conf file does not bring X back up.

---

### Post by myoungf1 on 2007-05-07
Sorry to bump but could use some advice on this or at least if anyone else has had this problem

---

### Post by myoungf1 on 2007-05-17
Ok bumping this again in hopes of some help.  I have done some additional checking of the forums and have tweaked xorg.conf to exactly what ati needs.  The screen resolution in Gnome desktop environment is great with direct rendering at yes.  But went last night into KDE and the resolution was again 640 x 480 and when I changed the resolution to a higher resolution 1440x900 x once again crashed and didn't come back up until I did the aticonfig --initial and the other command.  Now I am back up in Gnome perfectly but still no change in the KDE resolution.

---

### Post by liassic on 2007-06-28
I get the similar problems but not the crash - I thought that xorg.conf governed both Gnome and KDE but obviously not.  I'm running GDM - Gnome starts fine.  I amended the screen resolution in KDE and now the screen can't display KDE - just clicks away trying to display - obviously the screen resolution/refresh rate is outside the correct range.  But Gnome works OK.
A bit of a pain.
KDE screen resolution in a bit buggy I guess.  Doesn't seem to work well at all.

---

