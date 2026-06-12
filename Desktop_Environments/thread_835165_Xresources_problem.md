---
title: "Xresources problem"
date: 2008-06-20
forum: Desktop Environments
---

### Post by giorgio.p on 2008-06-20
I am using vnc to connect to Ubuntu 7.1 from windows xp.

It was working fine but something I have done must have broken some settings and the keyboard is jumbled up (types the wrong characters).

A terminal connection through putty is fine.

Connecting directly onto the Ubuntu box is also fine except that I do get a message saying X settings are different from Gnome settings every time I log in.

My logfile in ~.vnc is:
20/06/08 13:11:06 Xvnc version 3.3.tight1.2.9
20/06/08 13:11:06 Copyright (C) 1999 AT&T Laboratories Cambridge.
20/06/08 13:11:06 Copyright (C) 2000-2002 Constantin Kaplinsky.
20/06/08 13:11:06 All Rights Reserved.
20/06/08 13:11:06 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
20/06/08 13:11:06 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
20/06/08 13:11:06 Desktop name 'X' (george-ubuntu:2)
20/06/08 13:11:06 Protocol version supported 3.3
20/06/08 13:11:06 Listening for VNC connections on TCP port 5902
xrdb: No such file or directory
xrdb: can't open file '/home/george/.Xresources'
Window manager warning: Log level 32: could not find XKB extension.

I dont know what should be in .Xresources which appears to be missing nor how to rectify the x versus Gnome difference every time I log in.

I hope someone can point me in the right direction.

Thanks
George

---

