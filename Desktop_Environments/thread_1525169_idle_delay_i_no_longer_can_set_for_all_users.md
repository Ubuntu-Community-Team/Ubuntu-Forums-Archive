---
title: "idle_delay: i no longer can set for all users"
date: 2010-07-06
forum: Desktop Environments
---

### Post by gmoore777 on 2010-07-06
in HardyHeron, I could run this:
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type int --set /apps/gnome-screensaver/idle_delay 15

and this would set the screensaver for all users to 15 minutes.

This no longer works in LucidLynx. 
(it seems that the user can bypass this setting by changing it under
 System-->Preferences-->Screensaver)

If I open `sudo gconf-editor`, I do see that the value is set to "15", but
when I open up System-->Preferences-->Screensaver, it is still set to
the value I had previously, "55".
I have logged out and back in, but that didn't help.

(In HardyHeron, under System-->Preferences-->Screensaver, the idle, acitvate and lock screen setting are all grayed out. User can't even
attempt to change these settings, which is the desired goal.)

Anyone know how to accomplish this in LucidLynx?

---

