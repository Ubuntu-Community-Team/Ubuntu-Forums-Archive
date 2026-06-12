---
title: "vncsevrer font path problem"
date: 2012-05-02
forum: Desktop Environments
---

### Post by Skaperen on 2012-05-02
When I try to start vncserver, I get the following error messages:
```
lorentz/root /root 92# vncserver -geometry 960x600 -depth 32
[B]Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.
Couldn't start Xtightvnc process.[/B]

02/05/12 18:16:31 Xvnc version TightVNC-1.3.9
02/05/12 18:16:31 Copyright (C) 2000-2007 TightVNC Group
02/05/12 18:16:31 Copyright (C) 1999 AT&T Laboratories Cambridge
02/05/12 18:16:31 All Rights Reserved.
02/05/12 18:16:31 See http://www.tightvnc.com/ for information on TightVNC
02/05/12 18:16:31 Desktop name 'X' (lorentz:3)
02/05/12 18:16:31 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
02/05/12 18:16:31 Listening for VNC connections on TCP port 5903

Fatal server error:
Couldn't add screen
02/05/12 18:16:32 Xvnc version TightVNC-1.3.9
02/05/12 18:16:32 Copyright (C) 2000-2007 TightVNC Group
02/05/12 18:16:32 Copyright (C) 1999 AT&T Laboratories Cambridge
02/05/12 18:16:32 All Rights Reserved.
02/05/12 18:16:32 See http://www.tightvnc.com/ for information on TightVNC
02/05/12 18:16:32 Desktop name 'X' (lorentz:3)
02/05/12 18:16:32 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
02/05/12 18:16:32 Listening for VNC connections on TCP port 5903

Fatal server error:
Couldn't add screen

lorentz/root /root 93# 
```Shouldn't the package have at least enough fonts?  And I'd think these would be the same fonts for a normal hardware video X server.  I looked in the vncserver script and 4 paths are listed inside, and those do exist.  Is something else needed?  Another package?

---

