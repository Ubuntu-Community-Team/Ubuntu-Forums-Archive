---
title: "Gkrellm, Gkrellmms, and xmms"
date: 2005-04-09
forum: Desktop Environments
---

### Post by Mlehliw on 2005-04-09
I've installed these three apps and when I launch up xmms and gkrellm, if I have the xmms plugin for gkrellm on then gkrellm immediately freezes. Gkrellm won't crash though if xmms is playing and the xmms plugin is off. When I tested the crash the terminal spit out this message.
```
libmikmod.so.2: cannot open shared object file: No such file or directory
``` 
I tried installing libmikmod but gkrellm simply crashed without the error. Anyone else having this problem? This worked just fine in Warty, needless to say I'm a little disappointed to find out it doesn't in Hoary.

---

### Post by Gentist on 2005-05-07
The error message has nothing to do with gkrellm freezing up (or shouldn't have). My guess is that the plugin is at fault. If you're having them all start at the same time, try to start xmms via gkrellmms instead and see if it crashes. I've had gkrellm freeze up when starting xmms at times (on my Gentoo box), and to have it unfreeze, I simply had to kill xmms. Gkrellmms is nice, but a little buggy it seems.

---

### Post by Mlehliw on 2005-05-07
Are your mp3 files stored under a windows partition? If so try adding "nls=utf8" to the options for your windows filesystem in your fstab file.

---

### Post by thedruid on 2006-08-01
I have the same problem.
gkrellmms crash when xmms is running. If i exit xmms and load gkrellmms then it dosn't crash but as soon as i open xmms from gkrellm then it freeze. I think it have something to do with xmms.

And no i don't have my files on a ntfs partion.

---

