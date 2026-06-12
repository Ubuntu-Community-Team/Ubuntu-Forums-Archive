---
title: "vnc4server Ubuntu 8.10 with twm color issues"
date: 2008-11-14
forum: Desktop Environments
---

### Post by SkeebZ on 2008-11-14
Hi all,

  I am trying to run vnc4server on Ubuntu 8.10, and I just want to sue twm, I don't need kde or gnome.  I have installed vnc4server, xterm, and twm.  After I start a new vnc session I can connect to it, but I get the grey tweade twm.  I have no color, and whenever I try to kick off an application like firefox or even aptitude inside the vnc session I obviously can't see any text because the colors are not working.

Anyway, here is the vnc log file:  (Any help would be greatly appreciated)


Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Fri Nov 14 22:44:17 2008
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5903
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/Type1/, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
xsetroot:  unknown color "grey"
twm:  invalid color name "black"
twm:  invalid color name "white"
twm:  invalid color name "slategrey"
twm:  invalid color name "gray85"
twm:  invalid color name "gray85"
twm:  invalid color name "gray85"
twm:  invalid color name "slategrey"
twm:  invalid color name "gray70"
twm:  invalid color name "gray85"
twm:  invalid color name "gray85"
twm:  invalid color name "gray85"

Fri Nov 14 22:44:27 2008
 Connections: accepted: 192.168.1.101::50447
 SConnection: Client needs protocol version 3.8
 SConnection: Client requests security type VncAuth(2)

Fri Nov 14 22:44:29 2008
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 8 (8bpp) rgb max 3,3,3 shift 4,2,0

Fri Nov 14 22:46:57 2008
 Connections: closed: 192.168.1.101::50447 (Clean disconnection)
 SMsgWriter:  framebuffer updates 1018
 SMsgWriter:    ZRLE rects 4605, bytes 218545
 SMsgWriter:    raw bytes equivalent 11320114, compression ratio 51.797634
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":3.0"^M
      after 14927 requests (14904 known processed) with 0 events remaining.^M
xterm:  fatal IO error 11 (Resource temporarily unavailable) or KillClient on X server ":3.0"^M
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":3.0"^M
      after 137 requests (137 known processed) with 6 events remaining.^M
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":3.0"^M
      after 377 requests (374 known processed) with 0 events remaining.^M

---

