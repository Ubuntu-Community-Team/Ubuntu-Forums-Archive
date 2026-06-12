---
title: "disabling animations in gui"
date: 2013-06-07
forum: Desktop Environments
---

### Post by cheeseburger38 on 2013-06-07
Is there any way to disable the GUI animations like sliding pop up menu, fades? This is usually done on Win machines by tweakers to speed things up a bit.

---

### Post by zombifier25 on 2013-06-07
It's really hard to disable all of Unity's animations because it's Unity's core, being a compositing window manager. There used to be a Unity 2D project, which is a lighter Unity without compositing, but it was discontinued, instead the work is focused on making regular Unity faster (and they have done a good job)

You can disable some of them though. Many of the animations are provided by many of Compiz's plugins, so it can be hard to pin down all. The opening, closing and minimizing animations are provided by the Animations plugin. The Aero-snap-like animations are provided by the Grid plugin. The fading windows animation is provided by the Fading Windows plugin. To disable them, first install CompizConfig Settings Manager, by installing the package compizconfig-settings-manager via the SOftware Center or via the command line:
```
sudo apt-get install compizconfig-settings-manager
```
Then open ccsm, search for those plugins (note: **BE VERY CAREFUL**), and untick them to disable them. Compiz will freeze for a moment, but then it will be fine.

---

