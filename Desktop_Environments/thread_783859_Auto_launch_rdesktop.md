---
title: "Auto launch rdesktop"
date: 2008-05-06
forum: Desktop Environments
---

### Post by AndyD on 2008-05-06
Hi,

I would like to create a user in Ubuntu that when they login, rdesktop is the only application to launch with specific parameters. When they quit the RDP session they are logged out of Ubuntu again.

Is this possible?  Using .xinitrc maybe?

Thanks,
Andy.

---

### Post by DFLiddle on 2008-06-30
I'm trying to do something similar for the computers in our training room. So far, I have Automatic Login enabled for a user in System > Administration > Login Window > Security. In that user's profile, I added the *rdesktop* command, with parameters, to System > Preferences > Sessions > Startup Programs.

Everything runs as configured, except that the Remote Desktop command seems to execute before the Ubuntu desktop has finished loading. I see the terminal server screen for a few seconds, and then the Ubuntu desktop takes over again. The *rdesktop* process is still running, but I can't get back to the terminal session. It's really rather amusing to watch.

What I/we are missing at this point is help with ensuring that the *rdesktop* command does not execute so soon, and with configuring an automatic logout, if possible.

---

### Post by reviver on 2008-07-08
The following link is a How-To that tells how to set up what you're looking for, just using VNC instead of rdesktop.

[http://ubuntuforums.org/showthread.php?p=4963842](http://ubuntuforums.org/showthread.php?p=4963842)

---

### Post by firmit on 2008-07-09
> **AndyD said:**
> Hi,

I would like to create a user in Ubuntu that when they login, rdesktop is the only application to launch with specific parameters. When they quit the RDP session they are logged out of Ubuntu again.

Is this possible?  Using .xinitrc maybe?

Thanks,
Andy.

/home/specificuser/.config/autostart/

place the appropriate .desktop files with your Exec=/usr/bin/run -option

---

