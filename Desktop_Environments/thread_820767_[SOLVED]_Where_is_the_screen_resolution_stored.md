---
title: "[SOLVED] Where is the screen resolution stored?"
date: 2008-06-06
forum: Desktop Environments
---

### Post by doerings_net on 2008-06-06
While fiddling with the settings in /etc/X11/xorg.conf - to setup a dual monitor scenario on our IBM notebook via DVI-0 and VGA-0 while docked into the minidock - we screwed up something which is obviously not stored in the xorg.conf file itself.

To narrow the issue down, we are wondering where the screen resolution - via KDE [3.5.9] system settings > monitor and display > screen resolution - is saved if not in xorg.conf.

As a user **without** superuser rights is able to change it, the standard file can't be the correct place.

Any ideas?

Thanks in advance.

---

### Post by doorknob60 on 2008-06-07
My best guess would be in ~/.kde/share/config

I looked at some of the files in there, and I can't tell you which oe you need to edit, but it's probably in there somewhere.

---

### Post by doerings_net on 2008-06-07
Got it:

~/.kde/share/config/displayconfigrc

Thanks for the help.

---

