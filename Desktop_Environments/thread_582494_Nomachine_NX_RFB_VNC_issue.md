---
title: "Nomachine NX RFB VNC issue"
date: 2007-10-19
forum: Desktop Environments
---

### Post by boogieman75 on 2007-10-19
Hey all, I have been lurking around here for awhile and I haven't found a solution to this problem. 

I am running debian and I just installed the latest nomachine client/node/server from tutorial i found in another thread. Everything works great except vnc. When I try to connect to a VNC session through nx i get this message...It connects find and looks as if X is going to launch, get the black screen, logo and...

"Cannot find the RFB client. Please contact your system administrator."

here's the log from NX session administrator


NXPROXY - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '5201'.
Session: Starting session at 'Fri Oct 19 22:11:54 2007'.
Info: Connection with remote proxy completed.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using pack method 'adaptive-9' with session 'vnc'.
Info: Using product 'LFE/None/LFEN/None'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':0.0'.
Info: Listening to font server connections on port '11009'.
Session: Session started at 'Fri Oct 19 22:11:54 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 1/2048K.
Session: Terminating session at 'Fri Oct 19 22:13:19 2007'.
Session: Session terminated at 'Fri Oct 19 22:13:19 2007'.

Your help is greatly appreciated!

Thanks!


J

---

### Post by boogieman75 on 2007-10-21
Bumparino

---

### Post by wolfc on 2008-05-23
To make an old thread complete:

You need to install vncviewer.

(and continue reading here: [Cannot set RFB password]("http://ubuntuforums.org/showthread.php?t=615017"))

---

### Post by BuddyHall on 2008-06-05
I've encountered same problem.  I found a fix.. in config file on server:  /usr/NX/etc/node.cfg

It should read:

# Specify path and name of the command to start the RFB Client.
#
CommandStartRFB="vncviewer -fullscreen"

However for some reason my config file didn't have a space after vncviewer so the cmd was being executed as "vncviewer-fullscreen" which of course is a problem. 

Correct this and I think you'll find your problem solved.

---

