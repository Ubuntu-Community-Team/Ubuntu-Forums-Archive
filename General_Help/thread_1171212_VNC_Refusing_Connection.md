---
title: "VNC Refusing Connection"
date: 2009-05-27
forum: General Help
---

### Post by warnox on 2009-05-27
Hey!

Alright so I've been trying to get this to work for a decent few hours now and haven't got far.

I've got Debian 5.0.1 installed on a machine. I want to get VNC working on it the same way as it does in windows - to be able to connect to the machine when the computer is sitting on the logon screen.

What does work:
Setting up Remote Desktop in Debian and connecting to it that way, but this doesn't work on the logon screen.

What doesn't work:
I followed this guide: [http://ubuntuforums.org/showthread.p...c+gnome&page=1](http://ubuntuforums.org/showthread.p...c+gnome&page=1)

All went ok and the computer is listening on port 5901 but I get a connection refused whenever I try to connect to the vnc server.

I can "_telnet 192.168.1.250 5901_" and "_netstat -ab_" shows _0.0.0.0:5901_ but whenever I try and vnc in I get:

> 
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

Anyone have any idea why Debian is refusing the connection?

PS: I've tried this on two completely different systems, one with Debian 5.0.1 and one with Ubuntu 8.01, get the same result on both.

Thank you,



Gregor

---

### Post by warnox on 2009-05-27
Anyone have any idea?

---

### Post by XCan on 2009-05-27
The guide you're referring to puts me on the forum's main page. :( 

I guess you manually changed the port since the default is 5900?

---

### Post by HermanAB on 2009-05-27
"...haven't got far..."

That is a good thing actually.  Don't use VNC.  It is a insecure.  Use SSH instead, since it can do much more than VNC and is much easier to get to work.

---

### Post by jonobr on 2009-05-27
I would recommend installing and running wireshark.
Capture traffic leaving your source machine and see if they are responded to.

That should give you an idea if this is an application issue or other and may give you a better clue on where the problem lays

---

### Post by warnox on 2009-05-27
The connection must be refused on the Server end, since I can't even connect to 'localhost'. Yes the port is set to 5901 and that's what I am trying to connect to.

Not sure why that link didn't work, but try this:

[http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc+gnome&page=1](http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc+gnome&page=1)

---

I could try SSH, but do you know a good guide for that? And will it still give me an actual desktop rather than just a command line?

Thanks,



Gregor

---

