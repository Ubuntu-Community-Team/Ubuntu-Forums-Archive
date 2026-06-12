---
title: "remote desktop display issues"
date: 2016-05-14
forum: Desktop Environments
---

### Post by Skizzorp on 2016-05-14
I'm very new with ubuntu and am trying to set up remote desktop.  I got it connecting fine with one glitch   what i open up on the remote conn  only opens on the screen of the  win 10 screen im connecting with   and not on the linux nuc im connecting to's screen..  another issue i have is that i can't reboot machine from rem desktop..   besides teamviewer are there any other ways to do this ?

---

### Post by CharlesT423 on 2016-05-14
Are you trying to access the Ubuntu desktop remotely from a Windows box, or a Windows desktop remotely from your Ubuntu box?  I'd recommend VNC.  Works well for both ways (although if you are trying to access a Windows Desktop remotely Terminal Services gives better performance and you can use the rdesktop package in Ubuntu to access it.)  On the Windows side [http://TightVNC.org/](http://TightVNC.org/) is a good package that includes both the server (if you want to access a Windows desktop from Ubuntu) and the client (VNCViewer)  On Ubuntu I'd use x11vnc for the server and vncviewer for the client.

---

### Post by Skizzorp on 2016-05-14
accessing  ubuntu box from win 10 box  thank you for the help  ill work on this tonight a lil more

---

