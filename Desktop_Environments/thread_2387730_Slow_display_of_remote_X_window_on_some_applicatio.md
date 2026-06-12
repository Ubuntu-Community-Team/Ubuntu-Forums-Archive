---
title: "Slow display of remote X window on some applications"
date: 2018-03-22
forum: Desktop Environments
---

### Post by bkammp on 2018-03-22
On my Lubuntu 17.10 x64, some application's remote display window is very slow while others are OK. For instance, Altera Quartus 13.1 is very slow, you can see window refreshing from top to bottom. But Quartus 12.1 is normal, just as local executions.

My laptop is Intel i7-8550 with AMD Radeon 520. The applications are running on a Xeon server, which is CentOS 7.

Is there any idea about this?

---

### Post by TheFu on 2018-03-24
Default Ubuntu 17.10 uses Wayland for display, unless you force it to use xorg. The setting for that is in the "gear" BEFORE login.
Also, if wifi is used, the connection might not be solid enough.  Use wired ethernet whenever possible for a solid, stable, network connection.

I have no idea if Lubuntu uses Wayland or not.

Lastly, if the network isn't at least 100mbps the entire way between the client and server, using remote X11 probably isn't the best choice.

Have you ruled out Quartus 13.1 as the issue?  Can you boot from a Try Ubuntu 16.04 disk/flash and test?

---

### Post by bkammp on 2018-03-25
Thank you for your reply.

I tried lubuntu15.10 and 16.04, they have the same problem. The Quartus13's main window will do a slow scroll even it is resized to a very small dimension, but Quartus12 is OK.

I don't think the network will be the issue because the network I'm using is 100mps and the file transfer rate is steady 13MByte/s bidirectional.

There're some other applications, lower version is OK and higher is slow. Quartus is not alone.

---

### Post by TheFu on 2018-03-25
I'm completely unfamiliar with this software.

v13.1 seems to be really old - from 2013.  Looks like contacting Altera support for any issues is the best course of action.  Back when I wrote commercial software for Unix systems, OS upgrades would often break our code completely as the underlying system libraries changed.  Seems pretty amazing to me that a GUI program still works from 2013 without full recompiling.

[https://www.altera.com/support/support-resources/download/os-support.html](https://www.altera.com/support/support-resources/download/os-support.html) says Ubuntu 16.04 is the latest, supported, OS. Remote X11 ought to work, but we never know when mixing different versions of xlib, Xm and Xt. I'm assuming the remote system is still running 16.04?

BTW, I'd throw away 15.10. 

Also, if you are seeing 13 MB/s, then the network**is** saturated - that's 104 Mbps.  Not good.

---

### Post by TheFu on 2018-03-25
Just saw this bug for Gnome. [https://www.phoronix.com/scan.php?page=news_item&px=GNOME-Performance-Fix-Clutter](https://www.phoronix.com/scan.php?page=news_item&px=GNOME-Performance-Fix-Clutter) might have something to do with the slowness.

---

### Post by bkammp on 2018-03-25
Thank you again for your reply.

I've read this article. But my Lubuntu17.10 use LXDE as desktop and the remote server's CentOS7 has been changed to XFCE. Maybe GNOME's bug cannot help me.

Another application is Beyond Compare. The version 3.3.3_i386 is OK and 4.2.3_x64 is as slow as Quartus. I'll trying to find more software for this issue.

BTW, The server is using 1000m LAN and the only user is me. I'm planning to upgrade my NIC to 1000m and make the server my external storage, so it fine.

---

