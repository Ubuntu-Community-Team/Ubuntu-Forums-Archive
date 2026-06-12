---
title: "unable to start window manager"
date: 2009-11-02
forum: Desktop Environments
---

### Post by jchuma on 2009-11-02
Hi,

I have a dual boot system with ubuntu and xp, on separate hard drives.  Since installing ubuntu, I have always had a problem with ubuntu freezing up, seemingly at random times, with the only solution being a reboot.   I haven't been able to find a solution for this, but have just lived with it, even though it is very annoying.  Recently after a freeze up and a reboot, the window manager didn't start, and I'm left in "console mode".  I have tried ```
startx
```, and ```
sudo /etc/init.d/gdm start
```, and ```
sudo aptiitude install ubuntu-desktop
``` followed by ```
startx
```.  It doesn't work, and the following error message is displayed:
> Failed to initialize GLX extension (Compatible NVIDIA X driver not found) /etc/X11/Xsession: 81: stat: not found [:81: Illegal number:Any help would be greatly appreciated.

Joe Chuma

---

