---
title: "VNC authentication fails localhost:1 test on 6.06"
date: 2006-07-01
forum: Desktop Environments
---

### Post by transistor on 2006-07-01
I'm working on installing Hamachi on my father's (75) laptop so I can remotely help him surf. I've been following [KingOfNowhere's (very clear) howto]("http://doc.gwos.org/index.php/VNC_and_Hamachi#Enabling_XDMCP_in_Gnome") and think I have Hamachi set up properly.

Now I'm working on VNC. I've installed vnc4server and xinetd, set the vncpasswd, edited /etc/xinetd.d/Xvnc and restarted xinetd. When I run "vncviewer localhost:1" I get ...
```
~$ vncviewer localhost:0
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
VNC server supports protocol version 3.7 (viewer 3.3)
Password:
VNC authentication failed
```
I *am* entering the vnc password (and have double-checked by entering it again).

One possible problem is that 6.06's Login Window Preferences dialog seems to be different to that described in the howto.

Can anyone give me some guidance?

By the way, what does xinetd stand for? X is for X-windows, I presume.

Many thanks.

---

### Post by transistor on 2006-07-02
I checked xinetd on [Wikipedia]("http://en.wikipedia.org/wiki/Xinetd") and learned ...
*xinetd, the eXtended InterNET Daemon, is an open-source daemon which runs on many Unix systems and manages Internet-based connectivity. It offers a more secure extension to or version of inetd, the Internet daemon.*

Now what about my VNC problem. Anyone got any ideas?

---

### Post by gurgle on 2006-07-14
i get password failed as well. i know i am enterring in the correct password. Anyone got an idea on why this is happening?

---

