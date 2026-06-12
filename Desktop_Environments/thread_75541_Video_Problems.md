---
title: "Video Problems"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Georgie-o on 2005-10-13
When I boot-up with the monitor turned on, my screen has verticle thin blue lines and sometime the monitor goes crazy and gets stuck on different parts of the screen and freezes in an unusable state.  When I leave the monitor off during the boot-up process, I get no distortion problems, but the monitor is stuck in a resolution of 640x480.  The Resolution options pull-down menu doesn't show any other options.
Is this a video card driver issue?  If so, whats the fix?

Thanks

---

### Post by Ampersand on 2005-10-14
You'll have to open a terminal, (or press Ctrl, Alt and F1 if the screen is unusable at the time) and then run 

```
sudo dpkg-reconfigure xserver-xorg
```

You'll probably find it useful to have the documentation for your monitor around for the horizontal and vertical sync settings. If you've not got them, just select the Simple or Medium monitor setup.

---

