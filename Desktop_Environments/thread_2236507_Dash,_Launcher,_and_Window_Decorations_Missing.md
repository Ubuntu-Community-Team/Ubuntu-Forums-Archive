---
title: "Dash, Launcher, and Window Decorations Missing"
date: 2014-07-27
forum: Desktop Environments
---

### Post by Marshall_Mason on 2014-07-27
Recently I tried to clean up my Acer laptop with Ubuntu 14.04 on it. I rebooted my laptop and Unity had disappeared. I've tried many solutions to no success. I tried doing this in tty1:
```

marshall@Marshall:~$ sudo dconf reset -f /org/compiz
marshall@Marshall:~$ sudo setsid unity
stop: Unknown job: unity-panel-service
start: Unknown job: unity-panel-service
marshall@Marshall:~$ sudo unity --replace
stop: Unknown job: unity-panel-service
start: Unknown job: unity-panel service

```
I set the display variable and even moved some configs around but they still won't appear after I reboot. The guest account works but I need it to work on my account.

---

### Post by deadflowr on 2014-07-27
unity is run by the user, so don't use sudo to start it.
Simply:
```

dconf reset -f /org/compiz
setsid unity

```
should suffice to restart it.

Also, instead of running these from the tty1, try booting in normally and then try ctrl + alt + T to see if you get a terminal, and try running them from there.
See if that helps.

---

### Post by Marshall_Mason on 2014-07-27
The same thing still pops up.

---

### Post by deadflowr on 2014-07-27
Sorry for late reply.

Okay, then step two is to figure out what exactly you where trying to clean up.
Or more to it, how you went about trying to clean.

---

### Post by christopher14 on 2014-07-29
im kind of having the same problem except i updated ubuntu- and installed a few apps vlc chromium etc and now ubuntu only shows a wall paper

---

### Post by christopher14 on 2014-07-29
I did those commands, and when i did the last one it said Unity is not support my hardware-- which is odd because it was working perfectly right before restart

---

### Post by shaansweb on 2014-07-30
I too have the same problem. I also updated ubuntu, making me suspect that there was some bug in the update that is causing multiple people to experience this issue. 

When I run "setsid unity", I get the following error:

"GLib-GIO-ERROR **: Settings schema 'org.compiz.scale' does not contain a key named 'dnd-timeout-spinner' Trace/breakpoint trap"

Does anyone have any suggestions?

---

