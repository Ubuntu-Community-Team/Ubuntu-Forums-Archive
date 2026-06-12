---
title: "How do I adjust the resolution of a machine without restarting. . .?"
date: 2007-05-04
forum: Desktop Environments
---

### Post by michwill on 2007-05-04
Hi All,

I'm having trouble with my Ubuntu boxes.  Actually this is a problem I've had for a while.  Basically, I can't adjust a preset resolution without restarting the box.

I have a switchbox with multiple machines connected and if I start a machine up without actually giving it the focus of the switchbox it will start with the most compatible resolution available (which is understandable).  However, when I switch to that box I want to be able to adjust the resolution without hassle and CERTAINLY without a restart.  How do I do this?

Thanks


NOTE:  dpkg-reconfigure does nothing but adjust available resolutions for next restart.  I need immediate results.

---

### Post by ohgod on 2007-05-04
If you're logged into gnome, you can do it via System->Preferences->Screen Resolution.  If you're trying to do it via the gdm window, then I don't know...

If you don't like the resolution you get when you restart, you could edit the /etc/X11/xorg.conf file and remove all the resolutions but the one you want (this is what I do sometimes).

---

### Post by michwill on 2007-05-04
Well the other resolutions aren't even available via gnome when they start without focus.  I only get 640x480.  I'd like to better understand the window manager in order understand why it's so "serial" for lack of a better word.  Any input would be appreciated.

---

### Post by michwill on 2007-05-05
any ideas?

---

### Post by michwill on 2007-05-09
. . .I need to be able to do it on the fly without restarting.  Is there any way to force this?

---

