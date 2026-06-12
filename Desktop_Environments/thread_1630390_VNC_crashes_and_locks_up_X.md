---
title: "VNC crashes and locks up X"
date: 2010-11-25
forum: Desktop Environments
---

### Post by dargaud on 2010-11-25
Hello all,
that's a recent problem. I use VNC daily to connect to various machines (to and from Kubuntu, all 10.10). On one of them, when I get a VNC crash, not only I cannot reconnect, but also when I physically go in front of the machine, the screen is black and won't turn on.
Here's some code:
```
local $ ssh -L 5900:localhost:5900 remote
remote $ x11vnc -auth guess -find -localhost -once -nopw -nodpms
25/11/2010 09:28:51 x11vnc version: 0.9.10 lastmod: 2010-04-28  pid: 5817
25/11/2010 09:28:51 
25/11/2010 09:28:51 wait_for_client: WAIT:cmd=FINDDISPLAY
25/11/2010 09:28:51 
25/11/2010 09:28:51 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
25/11/2010 09:28:51 
25/11/2010 09:28:51 Autoprobing TCP port 
25/11/2010 09:28:51 Autoprobing selected port 5900
25/11/2010 09:28:51 Listening also on IPv6 port 5900 (socket 4)
25/11/2010 09:28:51 

The VNC desktop is:      remote:0
PORT=5900
25/11/2010 09:28:58 Got connection from client 127.0.0.1
25/11/2010 09:28:58   other clients:
25/11/2010 09:28:58 check_access: client 127.0.0.1 matches host 127.0.0.1
25/11/2010 09:28:58 incr accepted_client=1 for 127.0.0.1:57603  sock=5
25/11/2010 09:28:58 wait_for_client: got client
25/11/2010 09:28:58 client progressed=0 in 15/10 0.010446 s
25/11/2010 09:28:58 client_set_net: 127.0.0.1  0.0006
25/11/2010 09:28:58 wait_for_client: running: env X11VNC_SKIP_DISPLAY=''  /bin/sh /tmp/x11vnc-find_display.fBLsaC
25/11/2010 09:28:58 wait_for_client: find display cmd failed.
25/11/2010 09:28:58 wait_for_client: bad reply '
'
```

While on the local machine I run:
```
local $ vncviewer localhost:0

VNC Viewer Free Edition 4.1.1 for X - built Apr  9 2010 18:41:55
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Thu Nov 25 08:45:51 2010
 CConn:       connected to host localhost port 5900
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8

Thu Nov 25 08:45:54 2010
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding

Thu Nov 25 09:15:06 2010
 CConn:       Throughput 1007 kbit/s - changing to full colour
 CConn:       Using pixel format depth 24 (32bpp) little-endian rgb888
 DesktopWindow: attempting to render invalid local cursor

Thu Nov 25 09:28:11 2010
 main:        End of stream

```

At this point the ssh connection is still open on the remote, but even doing 'service kdm restart' doesn't improve the situation. All apps seem to keep running normally in the meanwhile.

Any pointers, at least on how I can restart X, short of a reboot ?

---

### Post by krunge on 2010-11-25
Have you tried the x11vnc -noxrecord option? There is yet another fatal bug in Xorg released in ubuntu. -noxrecord works around it.

Search these forums for "x11vnc noxrecord" for more info.

---

### Post by dargaud on 2010-11-26
Thanks. So far so good.

---

### Post by krunge on 2010-11-26
> Thanks. So far so good.
Very good. Please report back here when you are sure that the x11vnc "-noxrecord" option has solved the problem for you.

---

