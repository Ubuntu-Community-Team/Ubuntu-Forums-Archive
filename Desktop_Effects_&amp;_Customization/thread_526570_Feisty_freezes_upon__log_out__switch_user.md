---
title: "Feisty freezes upon  log out / switch user"
date: 2007-08-15
forum: Desktop Effects &amp; Customization
---

### Post by remick182 on 2007-08-15
I am having an issue with my Feisty install.  I've had it on my laptop now for a couple of months.  I recently installed and configured Beryl as well.  I've noticed that when I try to log out, switch users or go into suspend mode, my computer locks up.  I've searched for similar problems in this forum, but they seem to be unresolved.

I have tried some things to narrow the problem down, but I am not too savy with the inner workings of Linux.  So far I have this information:

Log out, switch user issue is noticed under a gnome session and an XGL session.

Alt-Ctrl-Backspace works fine in either session.

Reboot and Shut down both work 100% of the time.

I don't think that the issue is and XGL or Beryl issue, but I didn't notice it until after the configuration.  It could just be something not properly disabling or closing out, but I have no idea what processes are invoked/killed when logging out as opposed to rebooting.

Thanks in advance!

---

### Post by Paul133 on 2007-08-15
I had the same problem. Check System-> Administration - > Login Window. Is the box next to 'Restart the Xserver with each Login' checked? If that's the case, it's always been like that (unfortunately, that''s the default). You just didn't notice it until you installed XGL/Beryl because you've never had to logout before; you could always just shut down. When you install XGL, however, you have to logout of Gnome and start an XGL session.

---

### Post by remick182 on 2007-08-22
Well, I looked into the System -> Administration -> Login Window and I did not have the tick mark for the "Restart the Xserver with each login."  I checked it, and I still have the blank screen after logging out.

Does anyone else have any ideas?  It's not a big deal to reboot or shutdown, but the only real reason that I even log out is to change my session to Gnome instead of XGL because if I want to watch a DVD under an XGL session, its video is choppy.  Without Beryl running, they play fine.

Also, games using 3D acceleration run at a lower framerate under Beryl.

---

