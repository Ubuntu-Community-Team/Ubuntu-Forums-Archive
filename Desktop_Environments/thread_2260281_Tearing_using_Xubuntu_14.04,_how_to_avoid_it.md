---
title: "Tearing using Xubuntu 14.04, how to avoid it?"
date: 2015-01-10
forum: Desktop Environments
---

### Post by fkervin on 2015-01-10
Hi All,

I'm using Xubuntu 14.04 and I've tearing on videos EVEN when I disable compostite (I can live with this, it's not a problem). I've look for info but all I read says that the problem should get solved by not using compositing.

The graphics card is an integrated Intel.

Any help?

Many thanks in advance

---

### Post by fkervin on 2015-01-10
Hi Again,

I've just try to create a folder called xorg.conf.d inside /etc/X11 and then create file "/etc/X11/xorg.conf.d/20-intel.conf" with this code:

```

Section "Device"
Identifier "Intel Graphics"
Option "SwapbuffersWait" "true"
Option "AccelMethod" "sna"
Option "TearFree" "true"
EndSection
```

Then if I play a video on plex in fullscreen, when exiting fullscreen computer crashes in blank screen.

The most weird is that after removing this file I've try to enable composite and a check that contains that makes tearing dissapear.

As a result, I can have composite activated with no tearing, but when I disable compositing I have tearing.

I want NO composite and NO tearing, hehe

Any help

Regards

---

