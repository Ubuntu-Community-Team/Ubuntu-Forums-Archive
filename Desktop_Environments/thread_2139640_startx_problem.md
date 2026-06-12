---
title: "startx problem"
date: 2013-04-27
forum: Desktop Environments
---

### Post by Maloy14 on 2013-04-27
Hi!
I've been running Ubuntu 10.04.3 for over a year now. Yesterday morning, I installed some updates, then turned my machine off. After turning it on again, I discovered that I was not able to log in; my computer gets stuck at the ubuntu loading screen (the one with the word 'ubuntu' with the five dots underneath). Pressing any button/key does not work, but the machine shuts down when properly when I press the power button.

I restarted the machine and went to the recovery mode. When I run 'startx', I get this message:

```
Fatal server error:
Could not create server lock file: /tmp/.X0-lock

Please consult the The X.Org Foundation support
 at http://wiki.x.org 
for help.

 ddxSigGiveUp: Closing log
giving up.
xinit: Permission denied (errno 13): unable to connect to X server
xinit: No such process (errno 3): Server error.
```

I tried to access the /etc/X11/xorg.conf file, but this is what I get:

```
gksudo gedit /etc/X11/xorg.conf

(gksudo:1774): Gtk-WARNING **: cannot open display:
```


Furthermore, I cannot mount my external hard drive for some reason, so I cannot backup my files. But I do have access to them when I do ls or cd.

I really need your answers and support for this, as I am doing my undergrad thesis now. I need to have my machine fixed. Thanks. 

PS: here is my uname -a output: 
Linux maloy-laptop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64 GNU/Linux

---

### Post by steeldriver on 2013-04-27
If you need to edit files in a CLI terminal you will need to use nano / vi / vim (gedit is a GUI application)

Not sure about 10.x, but newer versions mount the filesystem read-only when you're in recovery mode - that would explain why X can't create the lock file - it may also explain why you can't mount your drive. If you post the exact error message it will be easier to help.

---

