---
title: "Controlling Volume in Fluxbox"
date: 2007-01-27
forum: Desktop Environments
---

### Post by teejay17 on 2007-01-27
I'm still learning all about Fluxbox, getting my bearings straight, figuring it out, etc. Anyway, I'm just wondering how to control my computer's volume; I've looked in the menus, etc. but nothing is striking me as being volume-oriented.

---

### Post by blackcrow on 2007-01-29
You can probably get a system tray app or a dockapp that controls the volume, [www.dockapps.org]("http://www.dockapps.org/") would be a good place to start looking.

I use keyboard shortcuts, enabled by adding the following two lines to ~/.fluxbox/keys:
```
yourkeys :ExecCommand amixer -q set PCM 2- unmute
yourkeys :ExecCommand amixer -q set PCM 2+ unmute
```
Replace "yourkeys" with any key name or key sequece of your choice, eg "Control plus" etc. If you have multimedia keys on your keyboard, then the volume up/down keys are usually called "XF86AudioLowerVolume" and "XF86AudioRaiseVolume".

Hope this helps :)

---

### Post by Ramses de Norre on 2007-01-29
I've put kmix in my startup file, it then loads the kde volume thingy in my notification area. I'd rather use gnome's but I couldn't figure out how to start that without gnome-panel. You can also easily modify kmix' icon, it's somewhere in a directory.

---

### Post by teejay17 on 2007-02-05
Both of you, thanks for your help. I actually discovered, quite by accident, that the shortcuts I use for Gnome actually work in Fluxbox. I guess they successfully carried over.

---

