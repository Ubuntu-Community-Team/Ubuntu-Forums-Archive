---
title: "problem using VNC between Ubuntu and Xubuntu"
date: 2006-06-26
forum: Desktop Environments
---

### Post by teasum on 2006-06-26
I'm trying to VNC from my laptop (Ubuntu Dapper) into my server box, which has Xubuntu installed.  I use PuTTY to turn on the VNC server on my Xubuntu box, and then I try to log in using tsclient.  I get the password box, enter the correct password, and then I get this error message: 

> ** (tsclient:1187): WARNING **:
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
VNC authentication failed

I tried running either vncserver or vnc4server thinking it was a protocol issue, but now I'm not sure how to resolve the problem.  I can do maintenance on my server via the command line with PuTTY, but I prefer a VNC connection.  One other small note: before doing a final upgrade to Dapper, I was able to use VNC to view my server box.

Thanks!

---

### Post by DarthMandeep on 2006-06-26
Have you tried another VNC client, like xtightvncviewer?

---

### Post by teasum on 2006-06-27
I installed xtightvncviewer, as suggested and gave it a shot.  I got the same error message:

>  VNC server supports protocol version 3.8 (viewer 3.3)
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
VNC authentication failed

Any other suggestions?

---

### Post by teasum on 2006-06-27
Never mind... problem solved.  My VNC password file on the server was locked, and therefore no password was set up on the server end for the viewer.  I rebooted and ran vncserver as root, and now the terminal server client logs in just fine.  

Thanks!

---

