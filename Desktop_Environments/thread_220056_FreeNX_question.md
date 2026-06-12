---
title: "FreeNX question"
date: 2006-07-20
forum: Desktop Environments
---

### Post by evillawngnome on 2006-07-20
So, i followed this tutorial verbatim to install FreeNX on my desktop:
[http://applications.linux.com/article.pl?sid=06/05/05/1718238&tid=26&tid=47&tid=29](http://applications.linux.com/article.pl?sid=06/05/05/1718238&tid=26&tid=47&tid=29)
FreeNX installed okay, so installed the client on my WindowsXP Laptop. So far so good. I put in the connection information, and it gets all the way through the handshaking, to the point where its going to draw the display, but it never does. Nothing happens. THe NX box dissapears, but i know its connected to the server. I can run Iptraf on the server and see the connection to my laptop. Like i said, however, there is no display, nothing.

Has anyone had this problem? Where can i start to troubleshoot this?

---

### Post by evillawngnome on 2006-07-20
Abandon'd: I'll just go back to VNC. I know it, and it's easy to set up.

---

### Post by nublie on 2006-07-22
i manage to setup Freenx version 2.0 last nite. I just downloaded three packages from [www.nomachine.com:](www.nomachine.com:) nxnode, nxclient and nxserver. Just install the client first, then nxnode, and finally nxserver. After that, i ran the command: nxsetup --setup-nomachine-key Afterwards, go through the questions. I forgot the question but you could simply figure it out. and try login using a client. But my problem is that, I can create new session(s) but only into xdm. gdm is not working.. i'm not sure why. xdm looks exactly like my desktop tho.. so maybe what happened was i login thru xdm but actually the session is actually a gdm-session. good luck

---

