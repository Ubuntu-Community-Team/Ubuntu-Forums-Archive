---
title: "remotely control a Xubuntu-XFCE laptop"
date: 2008-04-05
forum: Desktop Environments
---

### Post by boondocks on 2008-04-05
I am running Xubuntu with its XFCE environment on my laptop.

[INDENT]On my Ubuntu desktop, I can simply click on
System -> Preferences -> Remote Desktop
and setup my Remote Desktop Preferences
and remotely connect to my Ubuntu desktop.
[/INDENT]
But on my Xubuntu-XFCE-laptop, I am unable to do the same thing.
I have already installed the "vino" package on this Xubuntu-XFCE-laptop.

I am stuck at this point.
What should I do?

I just want to remotely control this Xubuntu-XFCE-laptop when I cannot take it with me.

---

### Post by trippinnik on 2008-04-06
Xubuntu used GDM as the login manager, right?  You can use XDCMP to login to the laptop remotely.  First on the computer you want to login to go to the settings for the Login window and enable remote connections via XDCMP.  Then on the client computer, at the login screen choose the xdcmp option from the bottom left menu. Type in the address, then login as normal.
You could also install vnc-server package on the laptop and then make sure the service is started by default, then use vnc-viewer from the client computer.
Also I recommend tunneling over SSH though.  I haven't used it from windows, but you can run individual applications from the server to client but without the whole desktop being shown.

---

### Post by boondocks on 2008-04-06
Thanks for the suggestions.
> **trippinnik said:**
>  ... You could also install vnc-server package on the laptop and then make sure the service is started by default, then use vnc-viewer from the client computer. ... 
I installed the vnc-server package.
How do I configure this now (with password protection, etc.) ?

---

