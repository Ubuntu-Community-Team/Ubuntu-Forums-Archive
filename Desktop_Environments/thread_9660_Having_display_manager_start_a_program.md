---
title: "Having display manager start a program"
date: 2004-12-30
forum: Desktop Environments
---

### Post by Dustin Wyatt on 2004-12-30
I'm trying to install [Synergy](http://synergy2.sourceforge.net/).  I've got it working almost perfect, but I would like it to start with X so that I can use it even when the logon screen is displayed.  From the Synergy install manual:

[quote="The Synergy install manual"]To have the display manager start synergy, edit the Xsetup script.
The location of this file depends on your installation.  It might
be /etc/X11/xdm/Xsetup.[/quote]

Where is the Xsetup script located in Ubuntu?

Thanks for the help.

---

### Post by AndersAA on 2004-12-30
Computer -> Desktop preferances -> Sessions and click startup programs :)

---

### Post by Dustin Wyatt on 2004-12-30
[QUOTE=AndersAA]Computer -> Desktop preferances -> Sessions and click startup programs :)[/QUOTE]
 Unfortunately that only starts a program once you login.  I need this to start before that so I can use it at the login screen.

---

### Post by thomaswwagner on 2005-01-23
I edited /etc/X11/gdm/Init/Default to get synergy started at the login screen:

/usr/bin/killall synergyc 
sleep 1 
/usr/bin/synergyc --name gimp 192.168.0.3

It works cool there but when I log in it ends and I have to manually start it again.  Looking for the config file to start it when the login is processed (don't want to do it the easy way so it works for all users  :wink: )

---

### Post by thomaswwagner on 2005-01-23
Got it to work...put it in /etc/X11/gdm/Xsession     8-)

---

