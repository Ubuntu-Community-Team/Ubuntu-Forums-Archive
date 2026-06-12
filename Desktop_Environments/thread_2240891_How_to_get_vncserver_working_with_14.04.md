---
title: "How to get vncserver working with 14.04"
date: 2014-08-22
forum: Desktop Environments
---

### Post by kstenerud on 2014-08-22
I've been trying for days to get vncserver working on 14.04 server.

So far I've followed the instructions on the following pages:
[LIST]
[*][https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)
[*][http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html](http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html)
[*][https://wiki.amahi.org/index.php/Install_VNC_server_on_Ubuntu_Server_12.04](https://wiki.amahi.org/index.php/Install_VNC_server_on_Ubuntu_Server_12.04)
[*][http://www.namhuy.net/3106/install-vnc-server-ubuntu-14-04.html](http://www.namhuy.net/3106/install-vnc-server-ubuntu-14-04.html)
[*][https://www.centos.org/docs/5/html/5.2/Virtualization/sect-Virtualization-Tips_and_tricks-Configuring_a_VNC_Server.html](https://www.centos.org/docs/5/html/5.2/Virtualization/sect-Virtualization-Tips_and_tricks-Configuring_a_VNC_Server.html)
[*][http://almost-a-technocrat.blogspot.com/2010/06/how-to-start-up-vnc-session-with-gnome.html](http://almost-a-technocrat.blogspot.com/2010/06/how-to-start-up-vnc-session-with-gnome.html)
[/LIST]


None of them work. I just get the standard X crosshatch background (or solid grey) and X cursor. I managed to get xcfe4 to run by manually starting it in the xstartup script. It sort of worked, except it acts like the command key is being held down ("s" key does nothing, "h" key hides the active window, down-arrow key maximizes the window, etc). I can also kind of get gnome working by manually starting all the services, but it has the same command key problem.

The logs don't seem to help much:

> Xvnc Free Edition 4.1.1 - built Jan 14 2013 22:28:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc


Fri Aug 22 16:22:11 2014
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/, removing from list!

Fri Aug 22 16:22:23 2014
 Connections: accepted: 0.0.0.0::59307
 SConnection: Client needs protocol version 3.8
 SConnection: Client requests security type VncAuth(2)
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 16 (16bpp) little-endian rgb565


Is there something I'm missing? All of the various instructions pages have pretty much the same information, yet none of them work for me.

---

### Post by steeldriver on 2014-08-22
What session did you specify in your ~/.vnc/xstartup file? what sessions are available in the /usr/share/xsessions directory?

---

