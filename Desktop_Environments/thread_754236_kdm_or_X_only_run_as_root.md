---
title: "kdm or X only run as root"
date: 2008-04-13
forum: Desktop Environments
---

### Post by H4rm0ny on 2008-04-13
I have a Kubuntu 7.10 installation that has had this problem since installation: KDM crashes on startup, or perhaps it is the X server (I don't know how to tell). At any rate, the only way that I can get a graphical desktop environment is to start up the system in Recovery Mode and then type 'sudo /etc/init.d/kdm start'. 

Everything then appears to work, except for the natural consequences of having started at the wrong run level (e.g. dbus not started).

I've been putting up with this for a few months now and it's getting really tiresome. I can post any logs or config that anyone suggests. Any help is appreciated.

Thanks,

Harmony.

**EDIT:** Just to be precise - when I say the system crashes I mean the screen goes black and the keyboard is unresponsive (including toggling Num Lock). The computer is still running, drives open and close and I could probably remote login if I dug the laptop out and tried, but it's basically dead as far as monitor and peripherals are concerned).

---

### Post by ibutho on 2008-04-13
Disable KDM and see if you can start X manually. Run
```
sudo update-rc.d -f kdm remove
```
After that reboot in the normal mode. If you get to a login prompt, run "startx" and see if KDE runs.

---

