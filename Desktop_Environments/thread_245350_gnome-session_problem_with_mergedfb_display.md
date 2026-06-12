---
title: "gnome-session problem with mergedfb display"
date: 2006-08-27
forum: Desktop Environments
---

### Post by spiregrain on 2006-08-27
I've got two screens of different sizes and resolutions.  I've configured them as a "mergedfb" region.  It works well, but they are slightly out of line.  There is a way to level them up.  My xorg.conf looks like this:

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 7000 (M6) (Primary)"
        Driver          "radeon"
        BusID           "PCI:1:5:0"
        Option         "MetaModes" "1024x768-1680x1050@60 1024x768-1680x1050 1024x768"
        Option          "MergedDPI" "100 100"
        Option "MergedNonRectangular" "true"
        Option "MergedFB" "True"
        Option "MonitorLayout" "LVDS, CRT2"
        Option     "RenderAccel" "true" #works
        Option "AGPFastWrite" "yes"
        Option          "CRT2Position" "RightOf -350"
        Option          "CRT2Hsync" "28-83"
        Option          "CRT2VRefresh" "60"
EndSection

```

The Radeon driver's "CRT2Position" RightOf option should do this.  It works if I start X on it's own.  But in a full GDM-driven Gnome session, it stuffs up.

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ken"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/franklin:/tmp/.ICE-unix/4719
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Value in failed request:  0xcf12
  Serial number of failed request:  12
  Current serial number in output stream:  12

(gnome-panel:4789): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
Initializing nautilus-open-terminal extension

(epiphany:4913): libgnomevfs-WARNING **: Failed to create service browser: Bad state

```

Any thoughts?  It doesn't matter if the offset is 1, -1 or the -350 that I'd really like.  It still fails.

---

