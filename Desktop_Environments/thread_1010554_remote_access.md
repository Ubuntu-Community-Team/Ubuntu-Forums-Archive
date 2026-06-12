---
title: "remote access"
date: 2008-12-13
forum: Desktop Environments
---

### Post by num on 2008-12-13
hello,

does anyone know a good remote access software where i can access a linux computer from a windows xp computer?

something like teamviewer?

---

### Post by wd5gnr on 2008-12-13
VNC is available across platform. I like UltraVNC on Windows. Also NX works REALLY fast although it can be a pain to configure. Look for freenx or get the "community" edition that has limits (like one user, but for personal use who cares?) and the Windows client is free under similar terms.

---

### Post by num on 2008-12-13
so what should i search for in the application library to get the community? just vnc?

---

### Post by wd5gnr on 2008-12-13
I'm not sure exactly what you are asking. The repos have several flavors of VNC if I recall. Maybe freenx too. [http://www.nomachine.com/](http://www.nomachine.com/) is the site for NX. 

You do have to have network visibility to your machine so if you want to reach over the internet you need to open your router and maybe get a thing like a [http://www.dyndns.org](http://www.dyndns.org)

---

### Post by num on 2008-12-14
im asking what is a good free remote access software that i can access a linux computer from a windows computer.

and what do i need to search for in the reps. to find it?

---

### Post by wd5gnr on 2008-12-14
OK so go to Synaptic and put VNC in the search box. On my machine this gives me:

vnc4server
tightvncserver
x11vnc

And a bunch of other things. x11vnc lets you attach to an existing session. VNC4Server or tightvncserver are more where you want to have a NEW login that is not the same as your desktop (you can use your same ID but you get a new desktop, not a copy of your existing desktop). So take your pick.

If you can't search your package manager for VNC, I'd encourage you not to try to configure NX.  However, if you must, look for package nxserver which will bring in nxnode and nxclient.

Note that VNC is not very secure over the public network. Most people use an ssh tunnel to secure it, although VPN will work too. NX uses ssh by default so if you can set it up, that's one less thing to worry about. 

As for the window side, go to google and enter VNC. There are plenty of options. I like [http://www.uvnc.com/](http://www.uvnc.com/). For NX, use the "nomachine" link I gave previously.

---

### Post by dovalize on 2008-12-14
Definitely, I've been using VNC in most of the time....
and it's stable too.

---

### Post by num on 2008-12-18
so i dont have to use the same vnc program for windows and linux?

---

### Post by wd5gnr on 2008-12-18
No. VNC is a protocol. Think of it like HTTP on the Web. You can use Internet Explorer or Firefox or Konquerer to connect to Apache or IIS or WebLogic and you (at least 99.9% of the time) don't really care that you are on Linux and the server is on a Windows box (haha -- usually the other way around I suppose). 

So if you have VNC on the Windows side and VNC on the Linux side they _should_ be compatible and work with no issue.

---

### Post by num on 2008-12-19
what vnc program for linux would you recommend for a noob? :p

---

### Post by wd5gnr on 2008-12-19
From an earlier post:

x11vnc lets you attach to an existing session. VNC4Server or tightvncserver are more where you want to have a NEW login that is not the same as your desktop (you can use your same ID but you get a new desktop, not a copy of your existing desktop). So take your pick.

So if you want to view your desktop as it looks on your normal monitor x11vnc. If you want to log into a new session either of the other two are about the same from the user's point of view.

---

