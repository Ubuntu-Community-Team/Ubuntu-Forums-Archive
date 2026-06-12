---
title: "Can see remote desktop but can't control it."
date: 2010-12-01
forum: Desktop Environments
---

### Post by jacron on 2010-12-01
I recently installed 10.10 64-bit on my laptop.  I have an older laptop with 9.10 32-bit on it.  I installed vnc4viewer on the 9.10 laptop and started and set up remote desktop connections to let the remote user view and control the local desktop.  I then tried Remote Desktop Viewer for the Applications menu on the 10.10 laptop and I can log in and see the remote desktop.  When I try to do anything through the vnc viewer I can see my changes affect the serving machine but not the viewing machine.  For instance, if I grab a window on the viewing machine and try to move it around the desktop, I can see it move on the serving machine.  I guess the connection could just be very slow but it seems real time on the serving machine.  Any ideas?

---

### Post by mokhan on 2011-01-16
I am experiencing a similar scenario. I am trying to connect to a 64 bit instance of ubuntu 10.10 from a 32 bit instance of ubuntu 10.10 using Remote Desktop Viewer. When I connect I can see the login screen for my 64 bit machine but when I click on the window I can't take control of the screen.

Is there something that I am missing? Or doing wrong?

---

### Post by dmbware on 2011-02-18
I am having the same problem with Windows 7 and Ubuntu 64 bit. I am able to connect and control the mouse but the refresh of my remote computer does not update and I see the same screen over and over. The remote is working its just I cant see what I am doing. nor well my remote screen update a menu drop down or a launch of a program.

---

### Post by Krytarik on 2011-02-18
The performance and if it works at all or not very much depends on what programs you use, I run "x11vnc" as server at the remote machine and RealVNC as the viewer at my machine.

I also tried "Remote Desktop Viewer" most recently, and it didn't work "remotely" as good as my usual setup. I guess it froze, or at least was painfully slow.

Also check this guide: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

