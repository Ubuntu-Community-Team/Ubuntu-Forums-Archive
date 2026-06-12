---
title: "Scheduled Tasks:  Error Parsing Option -c"
date: 2015-02-20
forum: Desktop Environments
---

### Post by mrcpuhead on 2015-02-20
I'm running LXLE (with Ubuntu 12.04.5 LTS & kernel version 3.2.0-77).  I've added a scheduled task to launch xcompmgr at reboot using a simple script.  Here's the script content:

compositor.sh:
------
xcompmgr &
exit
------

The script is in my home directory.  The task definition is:

Command:  ./compositor.sh
Default Behavior
Time & Date:  At Reboot

Execution gives a ROXTerm error dialog:  Error parsing command line options: Error parsing option -c

I can successfully run the same command from the Run utility.

Any ideas?

---

### Post by TheFu on 2015-02-20
Linux is multi-user. At reboot, your userid isn't logged in.  That takes a little longer, assuming you have auto-login enabled.
X/Windows programs cannot be run until after a user X-session is set up.  Plus a HOME directory environment is needed, which doesn't happen until after login to a graphical environment.  You don't want to run that program if a remote login happens - that won't do what you want.

So - what you need is to run the program 
* after a GUI login
* after X-session is up

How to do this depends on the GUI you run and the Window manager being used.  For openbox, the file is ~/.config/openbox/autostart LXDE uses openbox by default.  [http://wiki.lxde.org/en/Autostart](http://wiki.lxde.org/en/Autostart) should help.

---

