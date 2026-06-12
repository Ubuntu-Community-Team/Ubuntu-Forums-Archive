---
title: "No Remote Desktop in 11.10?"
date: 2011-10-17
forum: Desktop Environments
---

### Post by yellabelly on 2011-10-17
I can't find how to enable remote desktop sharing in a new installation of 11.10.

This was enabled in the menu "System->Preferences->Remote Desktop" back in 10.10. I can get new desktops with vncserver, freenx or neatx but I want to share the actual one running on the machine. Thanks,

---

### Post by DrJohn999 on 2011-10-17
In the dash, type "Desktop" or  "Remote", click on "Desktop Sharing" and set your preferences.

---

### Post by ^_Pepe_^ on 2011-10-17
+1. 

I've been ensuring that all is activated, but no VNC client is able to get the server.

The error is "authentication method not suported" in Windows (UltraVNC) and "Connection is closed" in Linux and Mac.

Any clue?

Thx
^_Pepe_^

---

### Post by yellabelly on 2011-10-17
Thanks I got it working. I switched to the Gnome desktop because I'm not a fan of Unity. Remote Desktop has been renamed Desktop Sharing and it's now in in the Internet group.
A tightVNC client was able to connect to the 11.10 desktop just like before.

---

### Post by rwb1920 on 2012-01-19
VNC Viewer - Free edition - works fine for me.  Thanks to all for the help in getting this feature running on my Ocelot!

---

### Post by bcarlowise on 2012-01-19
Remote Desktop Viewer from the software center can be used to Remote Desktop to an RDP system. I use it frequently for work to access Windows Servers.

---

### Post by luke@muti on 2012-04-03
A quick question while we are on this subject, i am pretty new to Ubuntu.. can someone tell me how i can make it so that when i use TightVNC to remote from my windows laptop, to my Ubuntu desktop, how i can use in Fullscreen with the same resolution that my laptop has?  it is 1366x768 

I can't seem to find a way of having my Ubuntu desktop in that same resolution. (The Ubuntu desktop is running on a ESXi Virtual server, so it is not a problem if it is only running in the resolution above, its just for me to access anyways)

Thanks in advance

---

### Post by jasinthaanganapati on 2012-05-05
vncserver :1 -geometry 1366x768

or similiar to other vncserver

---

