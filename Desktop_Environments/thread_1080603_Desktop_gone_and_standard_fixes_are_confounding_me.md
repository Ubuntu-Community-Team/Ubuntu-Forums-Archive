---
title: "Desktop gone and standard fixes are confounding me!"
date: 2009-02-25
forum: Desktop Environments
---

### Post by jaqrah on 2009-02-25
Hello.  I am using 8.10 on a Dell Mini 9.  Despite dire warning about mixing Netbook Remix and enabling compiz, I threw caution to the wind ;).  I was trying to use desktop-switcher to switch from Netbook Remix desktop theme and a traditional desktop theme with compiz enabled on highest setting.

There were dire consequences...I no longer have a desktop.  I removed the Netbook Remix app and all of its dependencies.  I removed the desktop-switcher app.  I disabled the compiz settings.  

I tried a number of solutions.  The first being reconfigureing xserver.xorg.  After I begin the reconfigure, I only get as far as resetting the keyboard defaults before I get kicked back to failsafe terminal with:

```
xserver.xorg postinst warning:overwriting possibly-customised configuration file;backup in /etc/X11/xorg.conf.20090255111540
```

I have tried 

```
sudo xstart
```

only to get this fatal error

```
X:warning;process set to priority -1 instead of requested priority 0 
fatal server error:
Server is already active for display 0
     If this server is no longer running,remove /tmp/.XO-lock and start again
```

If anyone has a clue to what is going on, I would greatly appreciate it.  Thanks in advance

---

