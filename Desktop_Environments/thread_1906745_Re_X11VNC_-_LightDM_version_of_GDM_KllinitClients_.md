---
title: "Re: X11VNC - LightDM version of GDM KllinitClients = false?"
date: 2012-01-09
forum: Desktop Environments
---

### Post by danielvds on 2012-01-09
Hi guys, newbie to the forums here.

I've been turning my old Lenovo ThinkPad into a uPnP server for my Xbox 360 for a few days now trying different distros, apps and servers to see what fits with what. I've decided Xubuntu is easiest to get started and I've managed to auto-mount the shared media USB hard drive and set up a startup entry for ushare in rc.local but the thing I can't crack is getting the 'X11VNC' Server to run at boot...

I've been following this great guide:
[http://ubuntuforums.org/archive/index.php/t-488207.html](http://ubuntuforums.org/archive/index.php/t-488207.html)

But there's a vital step to stop X11VNC from closing the VNC Session as soon as you log in from another client (am I correct?) 
- **You need to set KillInitClients=false in /etc/X11/gdm/gdm.conf**

But as I'm running a newer install of Xubuntu, the Default Window Manager is in fact _LightDM_ which doesn't let me do the same as the above. Is there any solution similar to the above that works with LightDM- or should I rather switch to GDM - isn't that heavier on a light server setup... and a bit drastic for such a small tweak though?

Without the above GDM tweak, when I try to log in from a client [RealVNC Viewer for Windows] on another pc, it never asks me for my set password, it just straight away says Connection Ended Unexpectedly.... It seems that X11VNC does successfully run at startup as the ':0' screen is indeed in use, but unaccessible. 

Could it be that I HAVE to log in with SSH? I don't know where to start with a SSH VNC client connection though, I tried to use PuTTY but it also ended unexpectedly... Furthermore I did try to set the -reopen parameter in x11vnc but it doesn't change much.

What does work is when I am logged in on the host computer, I'm able to simply type 'x11vnc' without sudo and it works on my client computers straight away... I always have to restart the application though beforehand to do so because of this pre-set during boot ':0' screen that doesn't let you access it.

Problem is I want to be able to turn the laptop on and have it working without touching it after turning it on, and be able to access it with a VNC client at any time during it's uptime- through at least password protection or SSH if I can get it working. It's not exactly in the best place to fiddle with things on the actual computer itself, I'd prefer to gain access from another computer in the house.

Hope I put this in the right forum!
Thanks in advance guys!

---

### Post by krunge on 2012-01-10
GDM removed the KillInitClients feature some years ago. So now it always kills them.

x11vnc now tries to avoid being killed by GDM and it usually does.

Collect the x11vnc output using the -o /path/to/logfile option, recreate the failure, and attach the logfile to this thread.

BTW, 

Thanks

---

### Post by irvin on 2012-02-11
Here's something that will work !

before login screen, secure, with password and numeric keys are working !

[http://www.dannratemal.de/?p=450](http://www.dannratemal.de/?p=450)

---

