---
title: "GTK+ Setuid login problem?"
date: 2007-11-18
forum: Desktop Environments
---

### Post by chaosrl on 2007-11-18
Hello everybody.

I'm running Gutsy and recently I haven't been able to log in. The error file read as follows:

```
(process:5757): Gtk-WARNING **: This process is currently running setuid or
setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

  [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5761): Gtk-WARNING **: This process is currently running setuid or
setgid.
this is not a supported use of GTK+. You must create a helper
program instead. For futher details, see:

  [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to
/etc/X11/xinit/xinput.d/default.
Checking for nVidia: not present.
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp
-fullscreen -br +xinerama
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1;
fixing.
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
```

As far as I can tell, the main problem that caused it seems to be that my computer didn't like the fact that I had forgotten that I had put Windows Vista on hibernate and tried boot into Gutsy and mount the drive. Does anyone have any idea as to how to solve this? Thanks!

---

### Post by theRightNee on 2008-01-04
you haven't bumped this, so i am assuming you've given up on the question. anyway, for me i had to uninstall xsever-xgl to get the gnome session to work. perhaps that  is realted to the Vista issue? i do not know. hope this helps

---

### Post by mattym76 on 2008-01-18
> **theRightNee said:**
> you haven't bumped this, so i am assuming you've given up on the question. anyway, for me i had to uninstall xsever-xgl to get the gnome session to work. perhaps that  is realted to the Vista issue? i do not know. hope this helps

I got this, and in the end made sure my /mnt was drwxr-xr-x and my /tmp was drwxrwxrwx

that seemed to fix it.

---

### Post by Arcege on 2008-01-24
I just got the same error after trying one of the xfce4 tips&tricks.  It seems that putting a bash while loop that called xfdesktop (none of which was setuid) into $HOME/.config/xfce4/xinitrc caused the problem.  When I removed the file, the symptom went away.

---

