---
title: "openGL apps crash xserver"
date: 2007-04-14
forum: Desktop Environments
---

### Post by farruinn on 2007-04-14
Whenever an app that uses openGL is run (eg xscreensaver, blender, etc) xorg crashes on me with the following error in the log. This started occurring after a recent update to edgy eft.

```
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting
```

Thanks, hopefully that's enough info.
-farruinn

---

### Post by farruinn on 2007-04-15
In the meantime, how can I simply disable xscreensaver? I can't open the screensaver preference in Gnome and there I don't have the ~/.xscreensaver file.

---

### Post by jbeiter on 2007-04-18
just to chime in, I just applied the latest crop of patches and now xscreensaver crashes xserver.

---

### Post by newtonfn on 2007-04-18
May be it is unrelated, but I had a similar problem that was solved reinstalling the nvidia drivers.

---

### Post by jbeiter on 2007-04-18
That worked, I reinstalled/recompiled nvidia and that fixed it. 

Thanks!

---

