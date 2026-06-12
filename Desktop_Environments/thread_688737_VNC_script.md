---
title: "VNC script"
date: 2008-02-05
forum: Desktop Environments
---

### Post by peterthewolf on 2008-02-05
If I issue vncviewer 192.168.1.101:0 in a terminal everything works fine.

But if I put the same instruction into a text file and call that text file from a desktop launcher then a terminal is called up and the following display made but is unsuccessful

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Why?

---

### Post by Andrew Stone on 2008-02-07
There's a few possibilities WRT the text file "script" not being set up correctly, or it not having access to your X server.  I don't want to go into them; instead, right click on desktop and select "create launcher", and then for the "command", put in your command "vncviewer 192.168.1.101:0".  Choose a name and also select your icon (on the left).  Click OK and a desktop icon will be created that should work.

---

