---
title: "theme not applied except for &quot;Appearance&quot; app iteself (10.10)"
date: 2010-11-06
forum: Desktop Environments
---

### Post by ZeeGee on 2010-11-06
New 10.10 installation, enabled nvidia proprietary driver. Resolution is fine, but theme is not working except for inside "Appearance" app itself. Please refer to attached screen shot.

When I change theme in "Appearance app", the window title bar decoration did seem to switch for all open windows, but inside the window, all the buttons, toolbars text boxes and menus remained the undecorated grayish Windows 98/2k look. The only place that I can see the theme fully applied is the Appearance app...

I first installed using CD image, then I suspected corrupted files from media, so I reinstalled via net install, but the problem remains.

Tried reinstalling light-themes package, did not seem to help.

Any ideas? Thanks.

---

### Post by snakesqzns on 2010-11-06
Does this happen at first login after a reboot? Or only after you logout?

You can try moving /usr/share/gdm/autostart/LoginWindow/gnome-settings-daemon.desktop.  GDM won't be themed but your desktop should be fine.

---

### Post by ZeeGee on 2010-11-07
Thanks for the tip!

FTR, the gray theme was persistent, e.g. no matter if this is the first login, or if I have logged out and logged back in.

And yes, removing the file did help! Previously GDM was themed, but the session wasn't, not GDM is not themed, but the session is. I guess I can live with ugly login window :)

---

