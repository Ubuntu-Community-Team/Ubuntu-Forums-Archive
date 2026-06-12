---
title: "VNC security types"
date: 2009-03-23
forum: General Help
---

### Post by Comzee on 2009-03-23
I have an Ubuntu system running as a server. I like to have VNC on it, but not without security. I say this because when I try to connect to my Ubuntu server via windows VNC client it always says "security type not recognized" or "Invalid security type". I have used Ubuntu's default "remote desktop" program (vino) and I get the error. I have also tried Tightvncserver and the error persists. On my Windows box while trying to connect I have used a volley of different VNC clients and all of them have the invalid security type error. 

Turning the passwords (security) off on my VNCserver I can connect normally from a windows box. I have searched the forums and found quite a few people have had this problem, but I haven't been able to uncover a solution.

Anybody have a solution for this?

---

### Post by Bachstelze on 2009-03-23
Here's what I do on my server:

1) Startup the TightVNC server listening on localhost only
2) Create a SSH tunnel (in windows, putty can do this)
3) Connect to 127.0.0.1:1 using the tightvnc client on my windows box
4) ?????
5) PROFIT! :)

---

