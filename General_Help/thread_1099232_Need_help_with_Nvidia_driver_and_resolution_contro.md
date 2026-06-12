---
title: "Need help with Nvidia driver and resolution control"
date: 2009-03-18
forum: General Help
---

### Post by JerryI on 2009-03-18
Today started well.  I managed to uninstall VMware and install VirtualBox on my Hardy installation.  I also managed to get Nvidia Twinview running again, which really got me excited.  My kernel is x86-64, which I think means that I have Hardy 64-bit installed (AMD64 architecture). I kinda wish I had Hardy 32, but I hope I don't have to go through all the trouble again of putting in a new Ubuntu system.

Since then, everything has gone way downhill.  I tried to put XP into VirtualBox.  Installation hung at 33 minutes remaining.  I tried to figure out the logic with the right control button and two cursors showing and warnings about whether or not to send keystrokes to some kind of console.  Finally I got it so screwed up I couldn't see anything so I rebooted and Ubuntu came up in low-res with only one monitor.  Got message 'You do not appear to be using the Nvidia X driver.  Please edit x-configuration file (Just run Nvidia x-config as root and restart x-server)  Ran sudo nvidia-xconfig and then ran sudo /etc/init -d/gdm restart which caused the bootup to hang and so I rebooted a couple more times and still have lo res.

How do I get my monitor resolution control back, preferably with dual-monitors?  Then I guess I need to find out how to uninstall VirtualBox so it won't take my whole system down again.

---

