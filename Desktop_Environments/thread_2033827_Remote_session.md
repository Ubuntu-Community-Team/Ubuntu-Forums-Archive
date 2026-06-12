---
title: "Remote session"
date: 2012-07-27
forum: Desktop Environments
---

### Post by Priyank Kaushal on 2012-07-27
hi, I want to know how to start remote session on ubuntu ..what rae the commands..I have recently installed xllvnc software on my 11.10 ubuntu desktop...

---

### Post by markbl on 2012-07-27
> **Priyank Kaushal said:**
> hi, I want to know how to start remote session on ubuntu ..what rae the commands..I have recently installed xllvnc software on my 11.10 ubuntu desktop...
Type [FONT="Courier New"]man x11nvc[/FONT] and read away. The man page is full of examples and options. Tells you everything you need to know, how to use it with ssh etc.

---

### Post by Priyank Kaushal on 2012-07-27
But how to get look of files in remote computer..what are commands..it is not asking for remote computer ip or username..how to connect??

---

### Post by steeldriver on 2012-07-27
If both machines are on your own LAN and you are behind a NAT then you can just start the x11vnc server and point your VNC client at it. Otherwise I would recommend using SSH tunneling (both for security and for ease of routing through firewalls).

To set up a basic non-tunneled connection, you can use something like:

```
x11vnc -rfbauth /home/*user*/.vnc/passwd -rfbport 5900 -shared -forever -nowf -norc -notruecolor -bg -xkb
```(I copied this from the default mythtv setup) where the /home/*user*/.vnc/passwd is created by running

```
vncpasswd
```You can then point your VNC client at *your-remote-server*:5900 where *your-remote-server* is the hostname (if you have working DNS resolution) or IP of the remote machine.

If you want to use SSH tunneling then you would add '-localhost' to the x11vnc command, and then set up an SSH tunnel - something like

```
ssh *user*@*your-remote-server.com* -L 5900:*your-remote-server*:5900
```and then point the VNC client at localhost:5900 instead.

---

### Post by Priyank Kaushal on 2012-07-27
from windows the ubuntu can be connected but how to connect windows from ubuntu....I want to know the commands sir..

---

### Post by steeldriver on 2012-07-27
For that case, you can install a remote desktop client on Ubuntu that supports the Windows native RDP protocol (such as vinagre) and then simply enable remote desktop connections on the Windows box. Or you can install a 3rd party VNC server on Windows and use any VNC client on Ubuntu.

---

### Post by longfeltwant on 2012-07-31
Is there a way to get a complete desktop X session over a remote connection? I have Ubuntu running on a Linux box and I would like to be able to connect to it from my Mac. Here is what I've done:

> open X11 on my Mac
> ssh -Y servername
> log in, then on remote Ubuntu machine:
> xeyes &
> nautilus &
> unity &

Xeyes and Nautilus both work as I would expect, but Unity does not. What I don't know is, is that supposed to work? Is that how I would do it? I also tried some variants. If I start unity-2d-shell, then the desktop background from Ubuntu will draw underneath my Mac windows, but nothing else will start. I could also call unity-2d-panel and the menu bar appears right underneath my Mac menu bar. So I feel like I must be close. When I call unity I get this:

```
username@servername:~$ unity &
[2] 3856
username@servername:~$ unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Fatal: No composite extension
compiz (composite) - Error: initScreen failed
compiz (core) - Error: Couldn't activate plugin 'composite'
compiz (core) - Error: Plugin 'composite' not loaded.

compiz (core) - Error: InitPlugin 'opengl' failed
compiz (core) - Error: Couldn't activate plugin 'opengl'
compiz (core) - Error: Plugin 'composite' not loaded.

compiz (core) - Fatal: No composite extension
compiz (core) - Fatal: No composite extension
Segmentation fault (core dumped)

```

The first thing it says is that unity-panel-service is not found. I haven't dug into that error message yet, but I will now, and I'll report back if I figure things out.

---

