---
title: "XGL Problem: failed to start the x server"
date: 2007-05-29
forum: Desktop Environments
---

### Post by Usvainen on 2007-05-29
Hello,

I tried to install xgl by doing it like it's done here [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl).
After I rebooted my computer, it became really slow after logging in and soon always automatically rebooted itself. 

So I tried uninstalling xgl and compiz with sudo apt-get remove xserver-xgl compiz compiz gnome, but now  I can't even log in! It says: "Failed to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?" if I enter yes it says "GDM: xserver not found: usr/bin/xgl :1 -fullscreen -br-accel glx: pbuffer -dpi 100 -nolisten tcp-auth /var/lib/gdm/:1.xauth -nolisten tcp vt7
Error: Command could not be executed! Please install the x server or correct GDM configuration and restart GDM. The x server is now disabled. Restart GDM when it is configured correctly." 

Okay, well I thought that maybe I should delete
```
 [servers]
1=Xgl #Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR FGLRX, 0 works on Edgy+FGLRX).  

[server-Xgl] 
name=Xgl server
command=/usr/bin/Xgl -fullscreen -br -accel xv:pbuffer -accel glx:pbuffer -dpi 100 -nolisten tcp
flexible=true 

```
from gdm.conf-custom so it will work again, but how can I do it? 

When I tried```
 gksudo gedit /etc/gdm/gdm.conf-custom
``` it said (gksudo:4938)6tk-warning **: cannot open display. Does anyone now how I can correct it? Thanks in advance.

---

### Post by NullHead on 2007-05-29
install xgl again```
sudo apt-get install xserver-xgl
```

---

### Post by Usvainen on 2007-05-30
Thanks, it's working now again :)

---

