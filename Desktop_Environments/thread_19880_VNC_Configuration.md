---
title: "VNC Configuration"
date: 2005-03-14
forum: Desktop Environments
---

### Post by maj on 2005-03-14
Hi,

I have the following installed:

warty
tightvncserver 1.2.7-3
x11vnc 0.6-2
vncserver 3.3.7-1ubuntu1

Let me know if you need further configuration details.

I'm trying to get a vncserver (vncserver, tightvncserver, x11vnc) to start up at boot time so that I can access the Linux box from my PC. Basically I want to stick my noisy Linux box in another room without a monitor etc but still be able to access the desktop remotely.

I have managed to get all of the variants listed above working but only AFTER I log in. It works fine. However, I cannot get it to work on boot.

I have my passwd file setup, the link to xinitrc sorted out (after I changed the file to execute permissions).

I have trawled through many web pages trying to figure out the problem but have now lost my patience with this. I have tried:

1. rc script startup - does not start the process

2. inetd startup - does not appear to start the process, I'm currently trying to troubleshoot this.

3. introducing vnc.so module support - could not get the vnc.so module. I believe it is part of a later release.

All in various permutations, for far too long. 

If anyone can offer assistance I would be most appreciative. Let me know if you need more info.

Thanks in advance.

Mark

---

