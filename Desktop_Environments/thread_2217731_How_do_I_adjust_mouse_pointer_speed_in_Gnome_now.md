---
title: "How do I adjust mouse pointer speed in Gnome now?"
date: 2014-04-18
forum: Desktop Environments
---

### Post by paulisdead on 2014-04-18
So I upgraded to gnome ubuntu 14.04, everything else seems fine.  But after I opened the mouse/touchpad settings (didn't actually change anything), my pointer speed got dropped to a slow level, and there are no sliders to change it there.  It was a fine speed until I opened those settings.  I'm on a dual monitor setup, so now I have to pick up the mouse a few times just to move all the way across both monitors.

---

### Post by paulisdead on 2014-04-18
It sounds like the resetting the mouse speed for no reason was fixed upstream awhile ago for gnome-control-center.
[https://mail.gnome.org/archives/ftp-release-list/2013-October/msg00093.html](https://mail.gnome.org/archives/ftp-release-list/2013-October/msg00093.html)
> Mouse:
- Do not reset mouse speed when unset
I've found the settings in dconf and am still tweaking them to my liking.  This is kind of ridiculous that something as basic as slider to adjust acceleration is no longer there.  I mean come on, didn't gnome 1 and windows 95 have this functionality?

In dconf-editor navigate to org > gnome > settings-daemon > peripherals > mouse and adjust the motion acceleration and motion threshold.

---

### Post by beetcom on 2014-07-04
Thanks it works!!, [COLOR=#333333][FONT=monospace]For Unity Authors "Simplicity is not removing things is to make things easier"...[/FONT][/COLOR]

---

