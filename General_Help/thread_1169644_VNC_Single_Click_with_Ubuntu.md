---
title: "VNC Single Click with Ubuntu?"
date: 2009-05-25
forum: General Help
---

### Post by bronkeydain on 2009-05-25
Hello people,

I am trying to setup a VNC software that will listen to incomming request from VNC Single Click servers and if so ask me for confirmation.

The idea is to have this on my Ubuntu machine permanently and have my clients (Windows Users) download the pre-configured VNC SC application that will request my server to take over their screen and keyboard.

I have this working on a windows computer with Ultra VNC, and I have tested that VNC SC sending the requests to my Ubuntu box. I just do not know which VNC server to use on Ubuntu that will ask me to confirm each connection rather than to prompt my clients for a password.

Any help would be most appreciated as I don't want to use windows for this.
Thanks

---

### Post by bronkeydain on 2009-05-25
Let me try and put it differently:

Does anybody know which Linux VNC software can work with VNC single click just like Ultra VNC does on windows boxes?

---

### Post by bronkeydain on 2009-05-25
I think I have found the answer:
[http://ubuntuforums.org/showthread.php?t=299489](http://ubuntuforums.org/showthread.php?t=299489)

---

### Post by HermanAB on 2009-05-25
This one is easiest to get to work:
[http://www.vncscan.com/vs/oneclickVNC.htm](http://www.vncscan.com/vs/oneclickVNC.htm)

All you need to set is your IP address in one file.

---

### Post by bronkeydain on 2009-05-26
Thanks Herman. I have tried both UtraVNC Single Click and TightVNC Single Click, and both give me the same result. The problem seems to be on my Ubuntu machine rather than the Windows clients (Single Click will connect to a Windows UltraVNC machine no problem).

This is what I get on my Ubuntu machine:
As root:
```
root@buntu:~# vncviewer -listen

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Tue May 26 12:25:27 2009
 main:        Listening on port 5500

vncviewer: unable to open display ""

```
Here it actually drops the connection.

As normal User:
```
taller@buntu:~$ vncviewer -listen

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Tue May 26 12:17:49 2009
 main:        Listening on port 5500


Tue May 26 12:18:07 2009
 CConn:       Accepted connection from 88.6.xxx.yyy::11994
 CConnection: Server supports RFB protocol version 3.16
 CConnection: Using RFB protocol version 3.8
```
Here it stays connected but no screen comes up.

Someone suggested in another thread that the vncviewer software might be buggy and to install xtightvncviewer, and try the following command:
```
taller@buntu:~$ xtightvncviewer -encodings "hextile copyrect" -listen
xtightvncviewer -listen: Listening on port 5500
xtightvncviewer -listen: Command line errors are not reported until a connection comes in.
Connected to RFB server, using protocol version 3.8

```
Again it stays connected but I get no screen.

Any idea's??? 
I am already installing windows on Virtual Box as I am on a deadline. However obviously I do not want to have to use windows each time just to do some reversed VNC connection, this should be possible on Ubuntu.

---

### Post by ubunRyan518824 on 2009-09-15
is there an answer to this??? I have been trying for days now and always getting the same thing

rip@rippc:~$ vncviewer -listen 0
vncviewer -listen: Listening on port 5500
vncviewer -listen: Command line errors are not reported until a connection comes in.
Connected to RFB server, using protocol version 3.8

No windows opens that alows me to view their desktop. Am I doing something wrong or can this just not be done. I would really hate to have a VM or dual boot just to do remote support. Any help would be great!

---

### Post by BelJoost on 2009-11-01
I found a solution in the following thread:
[http://ubuntuforums.org/showpost.php?p=8182096&postcount=3](http://ubuntuforums.org/showpost.php?p=8182096&postcount=3)

I created a script for it and posted it there as well.

---

### Post by labedra on 2009-12-18
Still not working for me on 9.10 so what's the fix any one know, I'm using 64Bit Version of Ubuntu dough

---

### Post by pietro_spina on 2009-12-18
I use Gitso to support my mom and sisters. You have to manage the ports on your side at your router or whatever you use as a gateway.

There is a way to pre-configure their settings as well. I used to just send them an e-mail with the IP. but now I have a domain redirecting to my home computer or laptop if I'm out and about. I don't leave the port open all the time I just open it up when they call and say they want help with something...

[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

The biggest blocker to these reverse VNC solutions is the firewalls  setting off like a million alarms the first time you run it... definitely pays to already be on the phone the first time they run it... haha

regards,
-p

---

### Post by oliver69 on 2010-05-07
The problem is that UltraVNC SC still uses protocol 3.3 whereas the VNC viewer in Ubuntu since Gutsy expects protocol 3.8.

Fortunately the newest RealVNC 4.5 is able again to understand protocol 3.3. But it is not yet available in Ubuntu software sources. You have to download the executable "VNC Enterprise Edition Viewer for Linux (x86)" from [http://www.realvnc.com/cgi-bin/download.cgi](http://www.realvnc.com/cgi-bin/download.cgi)

Then open a terminal, make the binary executable and run it:
```

$ chmod u+x vnc-E4_5_3_r39012-x86_linux_viewer
$ ./vnc-E4_5_3_r39012-x86_linux_viewer -listen -Protocol3.3

```

So now we are able again to help all those still-using-Windows-users :rolleyes:

---

