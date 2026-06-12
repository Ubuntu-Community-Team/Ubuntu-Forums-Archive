---
title: "I have hosed my Xorg/GDM config and need help!"
date: 2009-05-13
forum: Desktop Environments
---

### Post by cmfarley19 on 2009-05-13
I have been having some issues trying to run a headless server that I can VNC into.  I want to use a GUI sometimes so I have GDM running.

The initial issue was that I can boot with a monitor attached just fine.  I can remove the monitor while still booted and that's OK.
It's when I reboot without a monitor attached.  the boot process halts along the way and black screen with the following message dialog is displayed:
```
Ubuntu is running in low graphics mode.
The following errors were encountered:
(EE) intel(0): No valid Modes
(EE) Screens found but none have a usable configuration.
```
Here is the link to my original post:
[http://ubuntuforums.org/showthread.php?t=1143015](http://ubuntuforums.org/showthread.php?t=1143015)

I found this post that seemed to offer some hope:
[http://ubuntuforums.org/showthread.php?t=988789&page=3](http://ubuntuforums.org/showthread.php?t=988789&page=3)
I followed the advice offered by the user hutchia:
> I had a similar problem with Debian and it took a long while to figure out the simple fix.

Boot would stall when no monitor was found.

Here is why and how to fix:

The Video drivers now auto-detect monitor, and in particular its available modes. It will only do this with monitor connected. I spend long time looking for work around here - but this was wasted time.

Xorg software stalls during boot when it gets video error because it prompts user to look at log file and/or continue. There are some scripts that get invoked when error occurs. I was very tempted to rewrite these so they did not require for keyboard input on error.

Then it came to me!

The Xorg software was set up to create XSERVER on console (ie normal monitor/keyboard) - expecting this to be used as Xterminal to access applications locally or elsewhere.

Though I am using an XServer, it's not local. In my case I was running GNOME desktop so a check on the login setup (login window prefs, security,configure x-server) shows VT0 listed as Xserver. Removing this entry FIXED THE PROBLEM!

An Xserver can still be run on machine after connecting monitor - just log in and type startx.

I removed the VT0 entry and rebooted.
Now I always get a message that "No servers were defined in the configuration file and XDMCP can not start".
I want to restore that setting but I can not find which configuration file was changed when removing the VT0 from the servers list.

Can anybody tell me where to find the file file to edit to fix this problem?

Thanks,

Chris

---

### Post by cmfarley19 on 2009-05-21
I figured this out...
I had to edit the /etc/gdm/gdm.conf and add
```
0=Standard device=/dev/console
```

---

