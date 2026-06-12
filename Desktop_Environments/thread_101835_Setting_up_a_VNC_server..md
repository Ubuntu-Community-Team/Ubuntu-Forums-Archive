---
title: "Setting up a VNC server."
date: 2005-12-10
forum: Desktop Environments
---

### Post by UltraSonicSite on 2005-12-10
edit

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=UltraSonicSite]I bet you guys are tired of people asking these questions, but I still haven't found the answer to get things working.

My friend has windows xp.
I want him to connect to my computer.
He has a vnc viewer.
Ubuntu has a vnc server.

Now, how do I start this server?

In System/Preferences/Remote Desktop there is a screen.

It says something along the lines of 'vncviewer localhost.localdomain:0'

What is localhost?
What is localdomain?
The port stays as 0?

Sorry if I sound like I think you guys are stupid, your not, it's just I want to make it pretty clear on what I want. (since the other posts I searched didnt have responses)[/QUOTE]

The server should already be running.  It is called "vino" if you look for the running process.

If your friend is trying to connect over the Internet, he needs to have the Internet address your computer can be reached at.  If your home computer is plugged directly into the Internet, that is just your normal IP address.  If you are going through a router, you need to have the router forward the correct port (5500 for display 0, 5501 for display 1, etc.) to your Ubuntu computer.

Say your address is 192.168.0.2 (this cannot be a routable Internet address, since it is reserved for home use, but I will use it for the example).  Your friend could connect to you with something like 192.168.0.2:0.  That means IP address 192.168.0.2, display 0.

---

### Post by arnieboy on 2005-12-10
[QUOTE=UltraSonicSite]I bet you guys are tired of people asking these questions, but I still haven't found the answer to get things working.

My friend has windows xp.
I want him to connect to my computer.
He has a vnc viewer.
Ubuntu has a vnc server.

Now, how do I start this server?

In System/Preferences/Remote Desktop there is a screen.

It says something along the lines of 'vncviewer localhost.localdomain:0'

What is localhost?
What is localdomain?
The port stays as 0?

Sorry if I sound like I think you guys are stupid, your not, it's just I want to make it pretty clear on what I want. (since the other posts I searched didnt have responses)[/QUOTE]
try following this howto:
[http://ubuntuforums.org/showthread.php?t=76638](http://ubuntuforums.org/showthread.php?t=76638)

---

### Post by UltraSonicSite on 2005-12-15
So for the sake of argument, lets pretend this is my ip 

12.75.31.5

if i'm on another linux, I just type this in the console?

```
vnc 12.75.31.5:0
```

---

### Post by soulestream on 2005-12-15
vncviewer ip:0


or use realvnc


soule

---

### Post by curtis on 2005-12-15
[QUOTE=cwaldbieser]The server should already be running.  It is called "vino" if you look for the running process.

If your friend is trying to connect over the Internet, he needs to have the Internet address your computer can be reached at.  If your home computer is plugged directly into the Internet, that is just your normal IP address.  If you are going through a router, you need to have the router forward the correct port (5500 for display 0, 5501 for display 1, etc.) to your Ubuntu computer.

Say your address is 192.168.0.2 (this cannot be a routable Internet address, since it is reserved for home use, but I will use it for the example).  Your friend could connect to you with something like 192.168.0.2:0.  That means IP address 192.168.0.2, display 0.[/QUOTE]
5900 for display 0, 5901 for display 1 etc.

---

### Post by UltraSonicSite on 2005-12-16
I suspect I can't connect to my computer by that form cause when I type my own Ip it says: 
```

VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

```
 (btw, I know that to connect to my computer all i have to do is type vncviewer and thats it)

---

