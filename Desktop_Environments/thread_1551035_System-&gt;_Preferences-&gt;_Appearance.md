---
title: "System-&gt; Preferences-&gt; Appearance"
date: 2010-08-11
forum: Desktop Environments
---

### Post by SoFl W on 2010-08-11
I selected none for "Visual Effects" because I don't care for eye candy, today I went in that option and everything is grayed out.  It looks as though it is set to "none" but the page is grayed out and I can't select anything.

Everything else in Appearance seems to work.  Is there a reason why this would no longer let me change anything?

---

### Post by SoFl W on 2010-08-11
I am attempting what I found in this thread and rebooting.
[http://ubuntuforums.org/showthread.php?t=1113355](http://ubuntuforums.org/showthread.php?t=1113355)


EDIT:  Tried removing that file, menus options still grayed out.

---

### Post by SoFl W on 2010-08-11
I tried "gnome-appearance-properties %F" from the command line and received the following error(s)
```
name-desktop:~$ gnome-appearance-properties %F

(gnome-appearance-properties:2427): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2427): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

```

---

### Post by SoFl W on 2010-08-11
From my ".xsession-errors" file

```
Window manager warning: Failed to read saved session file /home/walt/.config/metacity/sessions/10878c8ba3da4ca246128157063847795100000016200035.ms: Failed to open file '/home/walt/.config/metacity/sessions/10878c8ba3da4ca246128157063847795100000016200035.ms': No such file or directory

(polkit-gnome-authentication-agent-1:1696): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1696): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:1695): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x12685f0'
Unable to find a synaptics device.
Initializing nautilus-gdu extension
```

---

### Post by linux18 on 2010-08-11
gksudo gnome-appearance-properties

---

### Post by SoFl W on 2010-08-11
Thanks,  same thing, Visual effects grayed out, with the following error on the command line

desktop:~$ gksudo gnome-appearance-properties
(gnome-appearance-properties:8665): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

---

### Post by SoFl W on 2010-08-11
Now I am trying to think back, seems I remember something in a "speed up your boot" and turning off these options but I can't remember.

---

### Post by linux18 on 2010-08-11
make sure gnome keyring daemon is not turned off at boot up

---

### Post by SoFl W on 2010-08-11
It is checked in the start up aps.

---

### Post by colin.p on 2010-08-12
I seem to remember, when I had the same issue, it was because I had removed compiz. I had to re-install it to be able to select anything in the visual effects. I could be wrong of course.

---

### Post by SoFl W on 2010-08-14
Thank you, I am not sure, I really don't like any of the fancy eye candy effects so I might have removed the compiz package but if I did it was a while back.  I reinstalled compiz and the options are back.

I don't remember installing compiz in the first place, is it part of a normal install?

---

### Post by SoFl W on 2010-08-14
Although I am not sure if I am 100% satisfied with the answer, I am going to mark this solved.  I still don't know why it happened in the first place... but it could have been me.

---

