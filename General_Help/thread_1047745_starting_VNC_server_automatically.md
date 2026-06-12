---
title: "starting VNC server automatically"
date: 2009-01-22
forum: General Help
---

### Post by tmetzcc325 on 2009-01-22
Hey all,

This is going to be a bit long, but I like to give as much info as I can right up front.  I have a PC running Ubuntu Ibex.  This one is connected to a monitor.  I have another PC running Ubuntu Ibex.  This sits in another room, and is completely headless, but it is not a server, so it has the Gnome desktop.  It has a network connection, and that is all.

I am currently able to ssh into the box with no problems.  What I want to do is be able to VNC in and control it graphically.  I have set up the GDM Login to automatically log me in upon startup, and configured the Remote Desktop preferences to allow remote control of the desktop.  I need the graphical environment so my wife can take control from her Windows laptop on occasion (but she is too graphical to simply use PuTTY like I do).

The problem is thus: For some reason, we cannot VNC into the box at all, unless I use XDMCP and manually log in graphically from the Ubuntu box with the monitor.  Obviously, this isn't ideal.  I'd like to be able to VNC in, even without logging in XDMCP.  Shouldn't the automatic login setting allow us to VNC in as soon as the user is automatically logged in upon reboot?  Or is there something I am not understading about how the Remote Desktop works?

Any help is appreciated.

Thanks,
Tom

---

### Post by dcstar on 2009-01-22
> **tmetzcc325 said:**
> 
.........
I am currently able to ssh into the box with no problems.  What I want to do is be able to VNC in and control it graphically.
.........

There are HOWTOs in the forums on how to do this.

---

### Post by tmetzcc325 on 2009-01-23
Yes, I know how to set up VNC.  I have a specific problem that I am referring to, regarding the automatic login, and only being able to use VNC after I log in through XDMCP.

I have tried searching for help before posting, but couldn't find anything about this specific issue, which is why I posted.

How about this question: Is there a way to have the built-in VNC server start automatically without requiring a user to login?  Something like XDMCP, but that can be used by a VNC client (especially on Windows)?

---

### Post by tmetzcc325 on 2009-01-24
Okay, I was able to set this up using this howto:

[http://ubuntuforums.org/showthread.php?p=4963842](http://ubuntuforums.org/showthread.php?p=4963842)

Turns out I wasn't aware that XDMCP could be used in this way.

Thanks for your help,
Tom

---

### Post by graysky on 2009-01-24
Thanks for the link, that is interesting.  I've been doing it from a script that runs:

vncserver -geometry 1650x1030 -alwaysshared :1

---

