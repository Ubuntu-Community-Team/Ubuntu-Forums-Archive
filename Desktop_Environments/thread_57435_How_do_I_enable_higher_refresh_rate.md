---
title: "How do I enable higher refresh rate?"
date: 2005-08-16
forum: Desktop Environments
---

### Post by Dolphin on 2005-08-16
X is stuck at 60hz and won't go any higher.
My LCD is capable of 75hz.  I tried editting my xorg.conf with the correct refresh ranges and it didn't work.  Ideas?

---

### Post by GreyFox503 on 2005-08-16
This is copied from one of my responses in another thread:

[QUOTE=GreyFox503]I had a similar problem with my login screen being at the wrong refresh rate than my desktop.  The solution involved adding custom lines to my xorg.conf file, at /etc/X11/xorg.conf

There are several threads on this forum on how to do that.  You might be able to fix it the easier way by running this:

```
sudo dpkg-reconfigure xserver-xorg
```

this is a way to configure your xserver by choosing options about your graphics card and monitor.

When it gets to the part about choosing resolution, there will be three choices, something like:

Easy
Medium
Advanced

I don't remember the exact wording.  If you choose medium, then you can specify your monitor's resolution and refresh rate.[/QUOTE]

---

