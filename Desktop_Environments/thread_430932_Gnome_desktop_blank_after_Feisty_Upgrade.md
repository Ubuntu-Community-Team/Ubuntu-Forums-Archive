---
title: "Gnome desktop blank after Feisty Upgrade"
date: 2007-05-02
forum: Desktop Environments
---

### Post by Deadl0ck on 2007-05-02
Hi all,

I'm using VNC to access my Ubuntu box - I just upgraded to Feisty and now when I log in all I have is a blank screen.

I get the following in my VNC Log:

```

Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
02/05/07 20:34:56 Xvnc version 3.3.tight1.2.9
02/05/07 20:34:56 Copyright (C) 1999 AT&T Laboratories Cambridge.
02/05/07 20:34:56 Copyright (C) 2000-2002 Constantin Kaplinsky.
02/05/07 20:34:56 All Rights Reserved.
02/05/07 20:34:56 See http://www.uk.research.att.com/vnc for information on VNC
02/05/07 20:34:56 See http://www.tightvnc.com for TightVNC-specific information
02/05/07 20:34:56 Desktop name 'Martin's Linux Box (VNC)' (martin-linux:1)
02/05/07 20:34:56 Protocol version supported 3.3
02/05/07 20:34:56 Listening for VNC connections on TCP port 5901
02/05/07 20:34:56 Listening for HTTP connections on TCP port 5801
02/05/07 20:34:56   URL http://martin-linux:5801
SESSION_MANAGER=local/martin-linux:/tmp/.ICE-unix/5801
Error: Cairo 1.4.2 does not yet support the requested image format:
        Depth: 8
        Alpha mask: 0x00000000
        Red   mask: 0x00000007
        Green mask: 0x00000038
        Blue  mask: 0x000000c0
Please file an enhancement request (quoting the above) at:
http://bugs.freedesktop.org/enter_bug.cgi?product=cairo
gnome-session: /build/buildd/libcairo-1.4.2/src/cairo-image-surface.c:199: _cairo_format_from_pixman_format: Assertion `NOT_REACHED' failed.
Error: Cairo 1.4.2 does not yet support the requested image format:
        Depth: 8
        Alpha mask: 0x00000000
        Red   mask: 0x00000007
        Green mask: 0x00000038
        Blue  mask: 0x000000c0
Please file an enhancement request (quoting the above) at:
http://bugs.freedesktop.org/enter_bug.cgi?product=cairo
gnome-panel: /build/buildd/libcairo-1.4.2/src/cairo-image-surface.c:199: _cairo_format_from_pixman_format: Assertion `NOT_REACHED' failed.
Window manager warning: Log level 32: could not find XKB extension.

(nautilus:5837): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-volume-manager:5838): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
Initializing gnome-mount extension
Error: Cairo 1.4.2 does not yet support the requested image format:
        Depth: 8
        Alpha mask: 0x00000000
        Red   mask: 0x00000007
        Green mask: 0x00000038
        Blue  mask: 0x000000c0
Please file an enhancement request (quoting the above) at:
http://bugs.freedesktop.org/enter_bug.cgi?product=cairo
nautilus: /build/buildd/libcairo-1.4.2/src/cairo-image-surface.c:199: _cairo_format_from_pixman_format: Assertion `NOT_REACHED' failed.
02/05/07 20:35:46 Got connection from client 192.168.1.101
02/05/07 20:35:46 Protocol version 3.5
02/05/07 20:35:46 Ignoring minor version mismatch
02/05/07 20:35:48 Full-control authentication passed by 192.168.1.101
02/05/07 20:35:48 Pixel format for client 192.168.1.101:
02/05/07 20:35:48   8 bpp, depth 8
02/05/07 20:35:48   true colour: max r 7 g 7 b 3, shift r 0 g 3 b 6
02/05/07 20:35:48   no translation needed
02/05/07 20:35:48 Using tight encoding for client 192.168.1.101
02/05/07 20:35:48 rfbProcessClientNormalMessage: ignoring unknown encoding 8
02/05/07 20:35:48 Enabling X-style cursor updates for client 192.168.1.101
02/05/07 20:35:48 Enabling cursor position updates for client 192.168.1.101
02/05/07 20:35:48 Using image quality level 6 for client 192.168.1.101
02/05/07 20:35:48 Enabling LastRect protocol extension for client 192.168.1.101
02/05/07 20:35:48 rfbProcessClientNormalMessage: ignoring unknown encoding -223

```

Anybody got any ideas ?

Thanks !

---

### Post by MCrusty on 2007-05-22
I'm having the same issue. This applies to ALL users of my system. I've tried using vncserver and tightvncserver with the same problems. I have also removed the .gnome .gnome2 .gconf .metacity directories of a user and tried VNC again with no luck.

Any ideas?

---

### Post by loathsome on 2007-05-22
Does this happen if you create a *new* user?

---

### Post by MCrusty on 2007-05-22
Yes it does. I just created a whole new user and I get the same issues.

---

### Post by loathsome on 2007-05-22
Are you able to do a reinstallation of GNOME? I had the same problem and did 1) reinstall 2) new user. It solved the problem (not sure exactly which one, though)

Good luck!

---

### Post by c960657 on 2008-01-07
Try raising the color depth to more than 256 colors. Apparently Cairo doesn't like only 8 bit colors. [credit]("http://www.linuxquestions.org/questions/debian-26/debain-etch-remote-server-xfce4-setup-488860/#post2449943")

---

