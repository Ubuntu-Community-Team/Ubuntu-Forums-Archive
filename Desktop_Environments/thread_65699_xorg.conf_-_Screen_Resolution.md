---
title: "xorg.conf - Screen Resolution"
date: 2005-09-14
forum: Desktop Environments
---

### Post by mumebuhi on 2005-09-14
Hi,

Every time I restart my Ubuntu box, the screen resolution is always reverted back (from 1600x1200) to 640x480. Moreover, I can not change it back to 1600x1200 through the Screen Resolution Preferences. The /etc/X11/xorg.conf (i.e. Section "Screen", Subsection "Display") shows 1600x1200 modes for every color depth available.

The typical workaround that I do is to '$ dpkg-reconfigure xserver-xorg' and restart my machine. After this, the 1600x1200 option shows up the Screen Resolution Preferences.

Is there a better way to solve this problem?

Thank you.


Buhi

---

### Post by mlomker on 2005-09-14
That's peculiar because the reconfigure simply writes a new xorg.conf file, I think.  I can't imagine why it would be overwritten at bootup.

What type of video card do you have?  Perhaps a newer driver would help.

---

