---
title: "VNC Server on Ubuntu Server 8.10 - Works Local, not across network"
date: 2008-12-30
forum: General Help
---

### Post by vipernicus42 on 2008-12-30
Hey Folks,

So I've installed Ubuntu Server 8.10, then installed xfce on it, and got a vnc server setup using the tutorial I found here:

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

(and along the way I installed vnc viewer so that I could test)

Locally, I can do vncviewer localhost:1 and it works just beautifully

However, if I move to the other computer that's on my desk and try to VNC into my ubunTest box it says Connection Refused.

Both are connected to the same switch, both have IPs from my DHCP server and I can ping and PuTTY from my XP  box into my ubunTest box. 

I'm not sure what other info you guys need to give me a hand with this, but at this point I don't know what to look at. I'm guessing my ubunTest box isn't accepting connections from other machines on whatever port VNC is listening on but I have no idea how to troubleshoot that.

Be kind, I'm a relative newbie when it comes to Linux.

Jon

---

### Post by vipernicus42 on 2008-12-30
Wow... I hate bumping things after such a short time but my post fell to page 3 within an hour so I figured it needed a bit of help before it got lost to the sands of time... 

Jon

---

### Post by vipernicus42 on 2008-12-30
Alright.... so problem #1 is solved. 

As it turns out, vnc4server was listening on port 5901, but my RealVNC Windows client expects to find VNC servers on a different port, so I had to specify the port when connecting.

BUT.... now that one problem is solved I have another. Even if I specify :0 at the end, I can't seem to get a window to the console desktop. What I mean is, if I sit down at my ubunTest box and log in, I want to be able to VNC from another machine on the network into *that* session and control the mouse and keyboard, not log into a second session on the same machine. 

Any ideas how to make that happen?

Jon

---

### Post by rjmoerland on 2009-01-04
x11vnc allows you to log in via VNC to an existing real X display, that is, one that is driven by hardware. It is in the repositories and you can read about it here: [http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/) and [http://www.vincentkong.com/2008/02/remote-desktop-on-xubuntu/](http://www.vincentkong.com/2008/02/remote-desktop-on-xubuntu/)

I hope this is what you seek.

---

