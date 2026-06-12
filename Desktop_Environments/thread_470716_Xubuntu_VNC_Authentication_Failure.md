---
title: "Xubuntu VNC Authentication Failure"
date: 2007-06-11
forum: Desktop Environments
---

### Post by Meyerjg on 2007-06-11
Hello all,

I've set up a desktop with Xubuntu 7.04, and I'm having a ton of problems getting VNC working. I have tried installing both x11vnc and vnc4server on the Xubuntu machine, and I've tried connecting to it with both UltraVNC and VNC Viewer 4 from my Windows XP machine. I've tried to connect through both a SSH tunnel and just directly to the IP address.

Every time I try and connect I get prompted for the password. I enter what I'm 100 percent positive is the correct password, and it always fails. 

I've tried resetting the VNC password many times, and I've tried restarting all the VNC processes. I just don't get it. The password file is not empty (although it is encrypted, so I can't tell what it says). The port file reads 5900. 

Also, when I started the x11vnc server I tried both using -rfbauth ... and -passwordfile ... but neither of them worked. 

Can anybody give me some advice? I'm a total Linux newb, so I'm not sure what else I can do. Is there anything I could use in place of VNC that might be easier to set up? 

Thanks!

---

### Post by Meyerjg on 2007-06-11
Also, I don't know if it makes any difference or not, but I did not have x11vnc and vnc4server running at the same time. I first tried x11vnc and had no success, and then I removed the package and deleted all of the files I created. After that I tried vnc4server

---

