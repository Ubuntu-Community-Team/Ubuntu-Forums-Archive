---
title: "gnome-display-properties does not open"
date: 2009-08-22
forum: Desktop Environments
---

### Post by HuoMaKe on 2009-08-22
I'm running a fully-updated Karmic system (newly installed), and I'm having issues with my displays. See, I have a 40-inch television (brand new! I'm bragging, sorry) that I tried hooking the box up to. The TV said the display was unusable, so I said, fine, I'll fix the resolution with the other monitor. I hooked said monitor up to the computer, logged in, and opened Display properties from GNOME. It flashed that the app was loading, then flashed that a window was about to pop up, then crashed. I tried from the terminal:

```
mark@grom-hellscream:~$ gnome-display-properties 

(gnome-display-properties:3582): Gtk-WARNING **: Ignoring the separator setting

(gnome-display-properties:3582): Gtk-WARNING **: No object called: 
**
display-properties:ERROR:xrandr-capplet.c:684:rebuild_resolution_combo: code should not be reached
Aborted (core dumped)

```

To no avail. I did this same process earlier today (had MBR issues, needed a reinstall) and it worked fine, after an update, but it was doing the same thing at first.

If anyone has an idea what's going on...please help.

---

### Post by HuoMaKe on 2009-08-22
Also, apparently in Karmic, the xorg.conf file has been phased out. Great job, now I have to restart in recovery mode or stop X to fix the problems with your buggy properties manager. *sigh* this alpha is getting me very angry, probably more than any other before it.

---

