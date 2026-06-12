---
title: "HDTV Intel 845G"
date: 2006-10-06
forum: Desktop Environments
---

### Post by noeffred on 2006-10-06
Is there a way to get HDTV videos to play on an Intel 845G chip?
I'm always faced with this error (mplayer, VLC, etc.):

```

X11 error: BadAlloc (insufficient resources for operation)

```

Here's my xorg.conf (relevant part)

```

Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

```

Is there a way to get this to work? Is there a way to upgrade the i810 driver? I've been searching the forum and there seems to be no answer which  I refuse to believe.

---

