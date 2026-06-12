---
title: "UT2004 will no longer start"
date: 2006-04-13
forum: Gaming &amp; Leisure
---

### Post by WillFerrellLuva on 2006-04-13
Hey,

Had UT2004 playing for a while.  Didnt change anything, then one day it stops working.  I see the splash screen then it just disapears.

Looking at the other related posts i tried deleting the UT2004.ini file but that didnt work.  Then I tried deleting the entire ~/.ut2004 folder but that didnt work either.

I always get the following error in the UT2004.log:
...
Log: OpenGL
Critical: Couldn't set video mode: Couldn't find matching GLX visual

Exit: Executing UObject::StaticShutdownAfterError
Exit: Executing USDLClient::ShutdownAfterError
...

From the terminal it looks like this:
chris@ubuntu:~$ ut2004
WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error
chris@ubuntu:~$

Any Ideas?

---

### Post by WillFerrellLuva on 2006-04-13
Nevermind......I guess

After a reboot it is working now.

Hopefully it wont happen again.

---

