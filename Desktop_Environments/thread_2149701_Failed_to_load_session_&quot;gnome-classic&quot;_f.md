---
title: "Failed to load session &quot;gnome-classic&quot; from vnc"
date: 2013-05-29
forum: Desktop Environments
---

### Post by mr746977 on 2013-05-29
Running the latest version (13.04), but installed 12.10 and installed VNC server along this guide: [http://coddswallop.wordpress.com/2012/05/09/ubuntu-12-04-precise-pangolin-complete-vnc-server-setup/](http://coddswallop.wordpress.com/2012/05/09/ubuntu-12-04-precise-pangolin-complete-vnc-server-setup/)

After upgrading, we seem to get the error in the title through a vnc session, surrounded by a blank xserver window.

I should also note we get a similar error when changing the line .vnc/xstartup  to gnome-session --session=ubuntu-2d.

Our .vnc/servername:6.log file reads:
```

Xvnc Free Edition 4.1.1 - built Jan 14 2013 22:28:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc


Wed May 29 14:17:32 2013
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5906
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/, removing from list!
Option "--login" is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new '--profile' option
gnome-session[4993]: WARNING: GSIdleMonitor: IDLETIME counter not found

Wed May 29 14:17:40 2013
 Connections: accepted: 127.0.0.1::45414
 SConnection: Client needs protocol version 3.8
 SConnection: Client requests security type VncAuth(2)

Wed May 29 14:17:42 2013
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565

Wed May 29 14:17:43 2013
 VNCSConnST:  Client pixel format depth 24 (32bpp) little-endian rgb888

Wed May 29 14:20:08 2013
 Connections: closed: 127.0.0.1::45414 (Clean disconnection)
 SMsgWriter:  framebuffer updates 20
 SMsgWriter:    ZRLE rects 16, bytes 7607
 SMsgWriter:    raw bytes equivalent 4186896, compression ratio 550.400421
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":6" 
      after 149 requests (148 known processed) with 0 events remaining. 

(gnome-terminal:4992): Gdk-WARNING **: gnome-terminal: Fatal IO error 11 (Resource temporarily unavailable) on X server :6.

gnome-session[4993]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :6.
```
If you need the text of any other log files, let me know and I'll be glad to help. Thanks.

---

### Post by mr746977 on 2013-05-30
Just for posterity, I found the solution. Turns out .vnc/xstartup contained the line
```
gnome-session --session=gnome-classic &
```
when the command has changed in 13.04 to
```
gnome-session-fallback &
```
The more you know!

---

