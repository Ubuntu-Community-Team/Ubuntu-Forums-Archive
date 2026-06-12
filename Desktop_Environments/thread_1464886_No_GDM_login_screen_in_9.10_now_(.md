---
title: "No GDM login screen in 9.10 now :("
date: 2010-04-28
forum: Desktop Environments
---

### Post by hypetech on 2010-04-28
I've been using Ubuntu 9.10 on my laptop for about a month now.  Everything has gone great up until today.  Today when I booted my laptop up, the splash screen came up fine, then when it transitioned to what would normally be my login screen, it was just the background wallpaper of the login screen.  No login prompt, and no session bar at the bottom.  I've been poking around some old bug reports and found similar issues with graphics cards and new installs, but this setup has been running fine for a month.  I tried installing KDM and WDM, but when I get loaded into GNOME on those, it throws up errors saying it can't load any of my applets on my panels, so I have no clock, taskbar, etc.  

I've tried to find information in the /var/log/gdm directory by dropping into my tty1 session, but the gdm directory is highlighted in blue when I run an ls and I'm not able to cd into the directory, getting a permission denied error.

Something that stands out in my mind is that last night when I went to power down, I ran 'shutdown -h now' from a terminal instead of using the GUI to shutdown.  I've used the command for years on *nix systems, but until last night I hadn't used it on this particular installation.  I don't know whether that has anything to do with it or not, but it is the last thing I did differently to the system.

Please help! :confused:

---

