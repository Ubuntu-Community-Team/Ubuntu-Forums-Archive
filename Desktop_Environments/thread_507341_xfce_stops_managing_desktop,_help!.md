---
title: "xfce stops managing desktop, help!"
date: 2007-07-22
forum: Desktop Environments
---

### Post by gotonpo on 2007-07-22
I'm having a strange issue, and I can't seem to figure out a fix..

I'm running Xubuntu 7.04, and I had everything running perfectly.  I recently installed nautilus (as I prefer it to thunar), and now xfce turns off the "allow xfce to manage the desktop" setting the first time I run nautilus after a login.

The setting is also turned off any time I run a fullscreen wine application.  This didn't use to happen before I installed nautilus.

Anyone have any ideas on how to prevent this from happening?

Much appreciated!

---

### Post by tbroderick on 2007-07-23
It's nautilus that is messing things up. When using nautilus outside of GNOME, you need to start it with --no-desktop option. You can edit your menu or launcher.
```

nautilus --no-desktop

```

---

### Post by gotonpo on 2007-07-23
Thank you!  Fixed the issue w/ wine too.  I'm not sure why nautilus got it's hands in wine, but glad this works! :)

---

