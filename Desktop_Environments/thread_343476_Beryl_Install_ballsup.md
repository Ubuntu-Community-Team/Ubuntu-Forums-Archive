---
title: "Beryl Install ballsup"
date: 2007-01-21
forum: Desktop Environments
---

### Post by whistlerspa on 2007-01-21
I successfully installed Beryl on my desktop and then tried to do the same on my laptop - big mistake as it turns out. 

The laptop didn't like the changes to xorg-conf so I reconfigured the file using

sudo dpkg-reconfigure xserver-xorg

This seemed  OK and I checked the file using 

nano edit /etc/X11/xorg-conf 

and it seemed OK.

When I boot up though all I see now is a plain Blue screen and nothing else.
If I boot up in recovery mode and startx the root account works and all my programs and my home account directories are there. The users and groups option in System - Administration is not there though. Also no sound on login.

I'm really puzzled by all this. Is there a way to recover my account and settings short of a reinstall please?

---

### Post by whistlerspa on 2007-01-21
Every so often one misses the obvious. I needed to change session to xgl option was all. Beryl doen't work of course because the xorg.conf file has been rest to default. The sound had somehow muted itself.

---

### Post by whistlerspa on 2007-01-21
However on a second reconfiguration of xorg.conf Gnome works again. So how does one get Beryl working with a video setup where video ram is shared?

---

### Post by Shatrat on 2007-01-21
What video chipset do you have?  
Do you have the drivers installed and configured, glxinfo | grep rendering returns a yes?

---

