---
title: "How to define &quot;when space is restricted&quot;?"
date: 2010-04-24
forum: Desktop Environments
---

### Post by lordL on 2010-04-24
I've been looking at the settings for the window selector on the lower taskbar in Ubuntu. Under "Window grouping" there are three option; 'never group windows', 'group windows when space is limited', and 'always group windows'.

What I'm wondering is whether there is a way to define how limited the space can be before the automatic grouping takes effect? 

With the default I can have something like 15-20 windows open without any grouping taking effect. What I'd like is to be able to define either how many windows can be open before they're grouped, or how small each button on the taskbar can become before grouping occurs.

Does anyone know a way to do this?

---

### Post by davebiffuk on 2010-05-20
I looked at the source code. The criterion for "space is limited" appears to be when the button width would be smaller than a particular value. That defaults to 80 pixels in libwnck (the underlying library) and the window list applet doesn't provide a way to change from the default, as far as I can see.

If you're happy recompiling, then you need to get the source for the libwnck package, edit line 94 of libwnck-2.30.0/libwnck/tasklist.c and change "#define DEFAULT_GROUPING_LIMIT 80" to be something bigger (I used 160).

It'd be nice if there was a GUI (or at least gconf-editor) config option for that...

---

### Post by davebiffuk on 2010-05-20
I reported this as a bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/583418](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/583418)

---

