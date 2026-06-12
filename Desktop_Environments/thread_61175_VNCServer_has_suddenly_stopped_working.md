---
title: "VNCServer has suddenly stopped working"
date: 2005-08-30
forum: Desktop Environments
---

### Post by caspar_wrede on 2005-08-30
My vncserver has suddenly stopped loading a window manager. If I look at the vncserver with a vncviewer I can just see the grey X background and mouse pointer, nothing else. This behaviour seems to have been brought on by me switcing off the computer on which the vncserver runs without shutting it down.

Here are the contents of $HOME/.vnc/$SERVER.log

```
30/08/05 23:19:41 Xvnc version 3.3.7 - built Oct 28 2004 23:57:28
30/08/05 23:19:41 Copyright (C) 2002-2003 RealVNC Ltd.
30/08/05 23:19:41 Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
30/08/05 23:19:41 All Rights Reserved.
30/08/05 23:19:41 See http://www.realvnc.com for information on VNC
30/08/05 23:19:41 Desktop name 'X' (kronos:1)
30/08/05 23:19:41 Protocol version supported 3.3
30/08/05 23:19:41 Listening for VNC connections on TCP port 5901
30/08/05 23:19:41 Listening for HTTP connections on TCP port 5801
30/08/05 23:19:41   URL http://kronos:5801

30/08/05 23:19:55 Got connection from client 0.0.0.0
30/08/05 23:19:55 Protocol version 3.3
30/08/05 23:20:06 Pixel format for client 0.0.0.0:
30/08/05 23:20:06   8 bpp, depth 8
30/08/05 23:20:06   true colour: max r 7 g 7 b 3, shift r 0 g 3 b 6
30/08/05 23:20:06 Using ZRLE encoding for client 0.0.0.0
``` 

Any ideas?

Caspar.

---

