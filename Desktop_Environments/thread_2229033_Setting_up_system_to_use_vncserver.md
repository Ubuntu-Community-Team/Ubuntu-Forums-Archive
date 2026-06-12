---
title: "Setting up system to use vncserver"
date: 2014-06-10
forum: Desktop Environments
---

### Post by Wolfpup on 2014-06-10
i have a system that i just upgraded from Ubuntu 10.04 to Xubuntu 12.04 and now I need to re-set up the VNC connection.
i can get it to run if i use :
```
sudo /usr/lib/vino/vino-server 
```
but I have to go to the system and do it any time the system is restarted. I want it to auto start so that I do not have to do that, plus I do not want to use any of the other VNC servers since I have this one installed and running even if it dose not auto start.

---

### Post by kira_belka2 on 2014-06-11
you can add it to /etc/init.d/ as job or to add this to cron (for each startup)

---

### Post by steeldriver on 2014-06-11
What are you trying to do exactly? vino-server would usually be run as a *desktop sharing* VNC server, started from the user's desktop session (rather than as root). Unless you are trying to connect remotely to the login display manager that's probably what you should stick with.

Traditionally XFCE4/Xubuntu would use x11vnc, instead of vino-server (which probably brings in a bunch of gnome dependencies).

---

### Post by Wolfpup on 2014-06-11
Actually when I installed vino it did not install with any dependencies. I am using it to be able to access the desktop on my server so that i do not have to got where the server actually is. that cmd line starts it as the root and I would prefer that it did not.

---

