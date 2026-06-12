---
title: "I'd like to VNC (Ubuntu &lt;--&gt; Windows)"
date: 2006-08-10
forum: Desktop Environments
---

### Post by mjpatey on 2006-08-10
Does anybody know of a good graphical VNC program that works well both in Ubuntu and Windows?  I'd like to be able to control my Windows desktops from within Ubuntu, and vice-versa.

Thanks for any info you may have!

-Mark

---

### Post by bensexson on 2006-08-10
Well for Ubuntu I would use enable Remote Desktop under Preferences and use tsclient.  With Windows RealVNC is good.

---

### Post by jflash on 2006-08-10
Try [this]("http://ubuntuguide.org/wiki/Dapper#How_to_configure_remote_desktop_.28not_secure.29") (read the following 3 or so entries). It's not secure, but it works just fine for me. In addition, because it's web-based (you do have to use it alongside apache), you can access your desktop across platforms and browsers.

---

### Post by aysiu on 2006-08-10
System > Preferences > Remote Desktop

Set to share, set a password. Find out your IP address by typing ```
ifconfig
``` in the terminal.

Download and install TightVNC for Windows.

---

### Post by mjpatey on 2006-08-10
Aysiu-

So how do I view my Windows desktops from within Ubuntu?

It looks like Remote Desktop will allow others to view my Ubuntu desktop, but what can I run in Ubuntu that will let me view my Windows desktops?

Sorry, I'm a little thick-headed on this.  :-)

---

### Post by murataht on 2006-08-10
try these:

[http://mail.kde.org/pipermail/freenx-knx/2004-October/000287.html](http://mail.kde.org/pipermail/freenx-knx/2004-October/000287.html)

[http://www.ubuntuforums.org/showthread.php?t=150261](http://www.ubuntuforums.org/showthread.php?t=150261)

cheers

---

### Post by aysiu on 2006-08-11
> **mjpatey said:**
> Aysiu-

So how do I view my Windows desktops from within Ubuntu?

It looks like Remote Desktop will allow others to view my Ubuntu desktop, but what can I run in Ubuntu that will let me view my Windows desktops?

Sorry, I'm a little thick-headed on this.  :-)
There's TightVNC for Ubuntu as well. It's in the Universe repositories: ```
sudo aptitude update
sudo aptitude install xtightvncviewer
vncviewer
```

---

### Post by mjpatey on 2006-08-11
Aysiu,

That's perfect!  I just tested it, and I'm able to both biew and be viewed from this machine.

For fun, I set both machines to view each other, and got a nice feedback loop.  :-)

-Mark

---

### Post by Cato2 on 2007-11-25
Aysiu's posting above worked perfectly - just install the tightvncviewer package and run vncviewer from Ubuntu.  I used the Windows TightVNC package with this, and it works pretty well over WiFi.

A couple of tips from 'man vncviewer':

1. Use F8 to bring up the VNC menu within the session, e.g. to go full screen.

2. You can use 'vncviewer -FullScreen hostname' to go directly into full screen mode - useful when you are on a small screen laptop connecting to a PC with larger screen.

3. You can even resize the remote Windows desktop in the normal way (right-click on desktop, properties, etc) while in a VNC session.  Very neat trick!

---

### Post by deserthowler on 2007-11-25
This worked for me on Dapper:

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

I used tightvnc on WinXP and Win2K installed as a service.

I ran xvncviewer on a Tatung/Sun clone using Debian Etch.  A custom FVWM was my window manager.  It ran very well but video was slow.  I think this is, in part, because of the Creator 3D card in my Sun clone.

I found it worked best if I ran XP and 2K and Ubuntu at 1024 x 768 resolution and the Sun as 1240 x 1024.  I ran all 3 machines from the Sun simultaneously with no problems.

Earl

---

### Post by bazzieb on 2007-11-26
Hi there

I can vnc and RDP from my Ubuntu 7.10 to any windows pc but i cant vnc from windows to my Ubuntu. Any suggestions??

Bazzieb

---

