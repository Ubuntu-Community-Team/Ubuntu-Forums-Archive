---
title: "volume osd deleted by"
date: 2011-02-07
forum: Desktop Environments
---

### Post by genjix on 2011-02-07
I installed gstreamer0.10-plugins-bad after firefox asked me to.

Now my volume OSD has been replaced by something else.

Uninstalled gstreamer. OSD hasn't come back :(

Any ideas?

Thanks

---

### Post by genjix on 2011-02-08
bump

---

### Post by Frogs Hair on 2011-02-08
Do you mean the volume on screen display (aka volume applet) ? If so right click the Gnome panel > add to panel > add indicator applet , which includes the volume and mail icon. I use Gstreamer also , but have not experienced any changes on the desktop.

---

### Post by genjix on 2011-02-08
[IMG]http://img810.imageshack.us/img810/4342/screenshotcq.png[/IMG]

I mean that. How do I get back the old volume OSD (on screen display)?

---

### Post by Frogs Hair on 2011-02-08
I use 10.10 from a clean installation and that has never appeared on the screen .

---

### Post by genjix on 2011-02-08
I had set my window manager to awesome,
gconftool-2 --type string --set /desktop/gnome/session/required_components/windowmanager awesome

Seems GNOME + awesome don't work together... :(

Normal volume OSD appears once I unset that.

---

