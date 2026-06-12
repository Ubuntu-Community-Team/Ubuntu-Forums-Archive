---
title: "[xfce4] ubuntu 14.04 - Unable to start Xfce Display Settings/system is using RandR1.1"
date: 2015-10-02
forum: Desktop Environments
---

### Post by Eamonn_Collins on 2015-10-02
Hi everyone

I'm setting up a ec2 server with amazon that's running ubuntu 14.04. I want to use it for web hosting.

I followed this guide to install the desktop and get rdp running:
[https://aws.amazon.com/premiumsupport/knowledge-center/connect-to-linux-desktop-from-windows/](https://aws.amazon.com/premiumsupport/knowledge-center/connect-to-linux-desktop-from-windows/)

I installed the xfce4 desktop and it runs OK, but i want to reduce the resolution, after opening display i get this error message:


[IMG]http://i.imgur.com/6j1aNaH.png[/IMG]

It seems i have 1.4.1 installed but the server is only using 1.1 :/

[IMG]http://i.imgur.com/0mCC2iC.png[/IMG]

Can anyone help me to get this server running version 1.2? Either that or help me change the display via command line. (In which case i'd appreciate exact commands to try)

I want to reduce the resolution to 800x600.

Thanks everybody,

---

### Post by Eamonn_Collins on 2015-10-02
Ahh it turns out the xrandr inherits the display size from the first rdp connection i make after boot.

So  i changed the "Display" settings in my windows "Remote Desktop  Connection" program to be 800x600. Then i rebooted the server and it  "inherited" the smaller resolution from my first rdp connection to it.

Solved.  [IMG]http://forums.linuxmint.com/images/smilies/icon_mrgreen.gif[/IMG]

---

