---
title: "Power Management-This program cannot start..."
date: 2006-07-30
forum: Desktop Environments
---

### Post by EdThaSlayer on 2006-07-30
So i just came back from vacation. So i start up my Ubuntu Linux Dapper Drake as usual. The log in screen works fine. But then randomly while it was still loading my desktop environment...the screen suddenly goes blank and returns to the log in.So i tried doing a diagnostic...
but i havent heard of this before
(below is the pop up message i got in the failsafe GNOME option)

"Power Manager:This program cannot start the dbus session service. This is usually started automatically in X or Gnome start up when you start a new session"

So iam not really sure where to go next.
1:Where to find the dbus session service?
2:How to install it back to the gnome startup manager...


Thanks to anyone that replies ^_^

---

### Post by EdThaSlayer on 2006-07-30
also now...
when i try to log in using the
GNOME session the screen turns black and
it says something about 

***libc corrupt***
(it dissapears very fast...so i cant read everything...that it says)

---

### Post by erdalronahi on 2006-08-30
I got the same problem. Cannot log into GNOME, though XFCE and KDE run fine.

---

### Post by xtknight on 2006-08-30
Can you guys post this file here immediately after GNOME startup failure?  After it happens go to a virtual terminal (Ctrl+Alt+F2), and type this after logging in to the same user as you used to log into GNOME.

**cp ~/.xsession-errors ~/Desktop/xsession-errors**

Then bootup to something that does work and open that file off your desktop, and post it here.  If it's big post a pertinent part of it.

---

### Post by erdalronahi on 2006-08-30
I haven't told you that the virtual terminals do not work anymore, have I :) I'll find another way...

---

### Post by erdalronahi on 2006-08-30
Here is the file: 
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "erdal"
/etc/gdm/Xsession: Beginning session setup...

(gnome-session:15477): Gdk-WARNING **: locale not supported by Xlib

(gnome-session:15477): Gdk-WARNING **: cannot set locale modifiers
SESSION_MANAGER=local/erdal-laptop:/tmp/.ICE-unix/15477

(metacity:15546): Gdk-WARNING **: locale not supported by Xlib

(metacity:15546): Gdk-WARNING **: cannot set locale modifiers

(gnome-panel:15551): Gdk-WARNING **: locale not supported by Xlib

(gnome-panel:15551): Gdk-WARNING **: cannot set locale modifiers

(nautilus:15553): Gdk-WARNING **: locale not supported by Xlib

(nautilus:15553): Gdk-WARNING **: cannot set locale modifiers

(gnome-panel:15551): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-volume-manager:15555): Gdk-WARNING **: locale not supported by Xlib

(gnome-volume-manager:15555): Gdk-WARNING **: cannot set locale modifiers
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
gnome-volume-manager: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
nautilus: Fatal IO error 104 (Connection reset by peer) on X server :0.0.


```

I think the relevant line is this:
```

(gnome-panel:15551): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

```

---

