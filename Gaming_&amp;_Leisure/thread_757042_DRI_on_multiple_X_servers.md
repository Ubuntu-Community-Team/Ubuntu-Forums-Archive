---
title: "DRI on multiple X servers?"
date: 2008-04-16
forum: Gaming &amp; Leisure
---

### Post by bluefish86 on 2008-04-16
I'm trying to set up a second X server on which to play games.  So far I have it working for non-OpenGL games.  I just run the games through the following script:

```
#!/bin/sh

sudo xinit /usr/bin/sudo -u chris -H `which $@` -- /usr/bin/X :1 -br -layout "Game640 Layout"
```

The problem is the second server fails to enable DRI with the following errors:
```

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) I810(0): [drm] DRM interface version 1.0
(II) I810(0): [drm] drmSetBusid failed (8, pci:0000:00:02.0), Permission denied
(EE) I810(0): [dri] DRIScreenInit failed. Disabling DRI.

```

Any opengl games will only work in indirect mode, making them unusably slow.  I've done a bunch of searching, but can't find any info on it.

My first server is running DRI without problems, but it's current dual head MergedFB setup prevents all full screen OpenGL games from working at all.  Most windowed OpenGL games also glitch out in weird ways.

---

### Post by bluefish86 on 2008-04-18
I feel stupid for not trying this earlier, but it turns out that my second X server fails to grab DRI even if it's the only one running.  I know DRI works because my gdm-controlled server has no trouble with it.  What am I doing wrong with my command?

---

### Post by rumblered on 2008-04-29
I believe you're not getting access to the dri device because of the way you're starting X. Try putting this in your xorg.conf:

```
Section "DRI"
    Mode 0666
EndSection
```

---

### Post by dennisn on 2009-03-19
As far as I can tell, it's currently not possible to have DRI on multiple X servers -- only the first one will be able to access this :S.

I hear rumors about this being possible in the future via "kernel modesetting"; not sure when or if this will occur.

[http://sourceforge.net/mailarchive/message.php?msg_name=634973.48914.qm%40web44910.mail.sp1.yahoo.com](http://sourceforge.net/mailarchive/message.php?msg_name=634973.48914.qm%40web44910.mail.sp1.yahoo.com)

:'(

---

