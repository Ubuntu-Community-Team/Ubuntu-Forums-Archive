---
title: "gdmflexiserver hangs (when switching users)"
date: 2008-02-23
forum: Desktop Environments
---

### Post by neutro on 2008-02-23
I don't have much hope to fix this as googling the problem returns only a single relevant result. The problem I have is exactly [[COLOR="Blue"]this bug[/COLOR]]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=319345") dated from 2005 and marked "unreproducible" in the Debian database.

The symptoms are simple: the switch user and fast user switching features do not work on my fairly standard Gutsy install. It simply does nothing; no, there's no login screen waiting for me on VT9. I have exactly the same gdm.conf (and a fairly similar Gnome desktop) on another computer on which user switching works very well.

On this reference computer, switching users can be performed on the command line by issuing ```
gdmflexiserver --startnew
```. On my problematic setup the same command does nothing. I can see gdmflexiserver in the process list, apparently just sitting there, waiting. I must kill the processmanually to be able to launch an application or even click on the log off / suspend / switch user button in the system tray.

So I tried running ```
gdmflexiserver -d --startnew
``` (debug flag on) on both systems to see the difference. On the reference system the last command sent to gdm by gdmflexiserver is ```
FLEXI_XSERVER Standard
``` and gdmflexiserver gets response ```
OK :20
``` On the problem setup the FLEXI_XSERVER Standard command is sent but there's simply no response.

I think the only difference between the two systems that could have something to do with that problem is the fact that I'm using the proprietary nVidia drivers on the problem setup, whereas I'm using an intel driver on the working system.

If anyone has a hint or something else to suggest, I'd be grateful.

---

### Post by neutro on 2008-02-23
Of course, hours after posting I finally solve my problem. Here's the solution in case someone else gets there.

It happens that I had not lo network interface defined in my /etc/network/interfaces file after playing with it trying to get my wireless network up and running. I just added 
```
auto lo
iface lo inet loopback
```
then I ifup'ed lo and that did the trick: the Xserver just needs a loopback interface.

This [more subtle bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/108761") led me to light.

---

