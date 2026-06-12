---
title: "XGL/Compiz on GNOME in Ubuntu 6.06"
date: 2006-07-12
forum: Desktop Environments
---

### Post by narandill on 2006-07-12
Hi,

I have Radeon 9200 SE, on ATI 8.26.18 drivers (with fexes libGL.so.1.2 [changind to older version], and sim-link fix in libGL.so.1 on boot)
In GNOME and XGL Direct Rendering=YES...

I have installed xgl and compiz just like in this howto: [xgl](https://help.ubuntu.com/community/CompositeManager/Xgl) / [compiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz).
I have chosed method A (in installing xgl)

When i login into XGL server all looks like gnome session, that is corect?
What about script startxgl.sh ? :
```

#!/bin/sh
**Xgl :1** -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
**DISPLAY=:1**
exec gnome-session

```
That was bad on my pc, so i have changed **DISPLAY=:1** to **DISPLAY=:0**, but, when i logged in the xglx starts in own window, whed I edited **Xgl :1** to **Xgl :0** - then all still looks that same like old gnome... :/
All the effects, that we can see in Novell demo about xgl - this should work in fresh install of xgl ? Or with Xgl+compiz ?

When i executed compiz i have this error:
```

root@mieszko:/home/mieszko# compiz --replace gconf
root@mieszko:/home/mieszko# compiz.real: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
compiz.real: Connection Error (No reply within specified time)
compiz.real: Couldn't initiate D-BUS connection
compiz.real: Disabling D-BUS Service
compiz.real: No composite extension

```
So i edited the xorg.conf and add this, to repair this error:
```

Section "Extensions"
    Option "Composite" "true"
EndSection

```
After restart of X on xgl server XGL in the fglrxinfo was been mesa drivers! and Direct Rendering = NO :(

This is logs from xorg:

This log is before add "Extensions":
```

root@mieszko:/home/mieszko# cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Specified desktop setup not supported: 8
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used

```

And that with new "Extensions" in xorg.conf:
```

root@mieszko:/home/mieszko# cat /var/log/Xorg.0.log.old | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Specified desktop setup not supported: 8
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used

```

Anyone have this problem ? I don't know what to do now......

---

### Post by rjwood on 2006-07-12
see here:
[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

---

### Post by narandill on 2006-07-12
This is topic for nvidia...

Also nothing else has changed:
When dri is not loaded as module there is Mesa in fglrxinfo and no direct rendering...

---

