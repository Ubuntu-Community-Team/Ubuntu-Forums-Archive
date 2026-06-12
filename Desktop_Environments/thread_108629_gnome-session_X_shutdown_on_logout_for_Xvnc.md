---
title: "gnome-session X shutdown on logout for Xvnc"
date: 2005-12-26
forum: Desktop Environments
---

### Post by jek on 2005-12-26
I manually start Xvnc using vncserver and start gnome-session from the ~/.vnc/xstartup file.  

When I logout from gnome, I would like the Xvnc to exit.  Currently it just sits there with an empty X window.

I have tried adding the -once flag manually to the /usr/bin/vncserver file but that didn't do it.

What is the magic incancation to get gnome-session to exit on logout?

---

### Post by sciurus on 2005-12-26
What configuration did you use in *~/.vnc/xstartup* to start Gnome? I have *exec gnome-session* but I only get a gray screen when I start vncserver and try to connect.

---

### Post by jek on 2005-12-27
The xstartup file is trivial:

#!/bin/sh
gnome-session

---

### Post by sciurus on 2005-12-27
I thought it would be be, but that does not work for me. Still a gray, banded screen. I tired putting in the name of an application, thinking perhaps it would launch windowmanagerless, but even that didn't cause anything to happen.

[email]user@machine:~/.vnc[/email]$ vncserver
Found /usr/share/vnc-java for http connections.

New 'X' desktop is machine:1

Starting applications specified in /etc/X11/Xsession
Log file is ~/.vnc/machine:1.log

[email]user@machine:~/.vnc[/email]$ more machine:1.log
27/12/05 23:13:19 Xvnc version 3.3.7 - built Sep 27 2005 11:14:24
27/12/05 23:13:19 Copyright (C) 2002-2003 RealVNC Ltd.
27/12/05 23:13:19 Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
27/12/05 23:13:19 All Rights Reserved.
27/12/05 23:13:19 See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC
27/12/05 23:13:19 Desktop name 'X' (machine:1)
27/12/05 23:13:19 Protocol version supported 3.3
27/12/05 23:13:19 Listening for VNC connections on TCP port 5901
27/12/05 23:13:19 Listening for HTTP connections on TCP port 5801
27/12/05 23:13:19   URL [http://machine:5801](http://machine:5801)

---

### Post by jek on 2005-12-28
Hm.  My version is 4.0 with Breezy up to date:


Xvnc version 4.0 - built Apr 19 2005 04:26:49
Underlying X server release 40200000, The XFree86 Project, Inc

---

### Post by sciurus on 2005-12-29
[QUOTE=jek]Hm.  My version is 4.0 with Breezy up to date:
Xvnc version 4.0 - built Apr 19 2005 04:26:49
Underlying X server release 40200000, The XFree86 Project, Inc[/QUOTE]

I think the difference is I have vncserver 3.3.7-7ubuntu1 installed from main, whereas you must have vnc4server from universe. I'll try that.

---

### Post by DaMasta on 2005-12-29
There is a -once option when running the vncserver command. Once that server is used and exited, it'll end.

---

### Post by jek on 2006-01-27
[QUOTE=sciurus]I think the difference is I have vncserver 3.3.7-7ubuntu1 installed from main, whereas you must have vnc4server from universe. I'll try that.[/QUOTE]

True, I'm using the universe/vnc4server install.  I tried downgrading to the one in main, and that made it work.  There is obviously something in the vnc4 version that has changed in a way that broke this.

---

