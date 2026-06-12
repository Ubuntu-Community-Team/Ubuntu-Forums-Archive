---
title: "Cannot open System Settings"
date: 2013-10-24
forum: Desktop Environments
---

### Post by bswilson on 2013-10-24
So, for some strange reason I cannot open the gnome-control-center (a.k.a. System Settings applet). 

This is what I see in the syslog file:

```
Oct 24 17:03:23 kernel: [17986.819005] gnome-control-c[10051]: segfault at 20 ip 000000000040a371 sp 00007fff54ef03b0 error 4 in gnome-control-center[400000+e000]
Oct 24 17:03:35 whoopsie[1214]: online
Oct 24 17:04:37 whoopsie[1214]: last message repeated 2 times
```

And when I try to run gnome-control-center from a command line, I see this:

$ gnome-control-center

```
(gnome-control-center:10902): GLib-GObject-WARNING **: cannot derive 'GnomeControlCenter' from non-fundamental parent type 'CcShell'
(gnome-control-center:10902): GLib-CRITICAL **: g_once_init_leave: assertion 'result != 0' failed
(gnome-control-center:10902): GLib-GObject-CRITICAL **: g_object_new: assertion 'G_TYPE_IS_OBJECT (object_type)' failed
Segmentation fault (core dumped)
```

Does anyone know how to overcome this problem? A reboot does not help.

---

### Post by bswilson on 2013-11-03
Long story, but I ended up reinstalling Ubuntu to solve other more pressing problems.

---

### Post by ahamdi on 2014-02-22
Hi
I have the exact same problem. And I don't want to re-install everything unless there is no more solution.
Could someone help me diagnose the issue ?

Thanks

---

### Post by ahamdi on 2014-02-23
Should I open a new thread to get help on this issue ?

---

### Post by QIII on 2014-02-23
Yes, please.

This one is marked as solved, so it's not likely it will be looked at.

---

