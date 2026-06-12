---
title: "browsing internet"
date: 2005-08-02
forum: Desktop Environments
---

### Post by rick3352 on 2005-08-02
Although I am a fairly advanced computer user (going back to CP/M), I am new to Linux.  I recently installed Ubuntu and have been feeling my around and was able to get my external US Robotics modem set up to dial my ISP.  However, once connected, when I try to open FireFox and go to a web site, it tries but eventually times out.  Any suggestion on what I might need to do.  Thanks

---

### Post by cwaldbieser on 2005-08-02
Try pinging 64.233.161.104 ([www.google.com)](www.google.com)), but use the IP address.  It may be that your name resolver is just not configured properly.  If that doesn't work, try posting the output of the "ifconfig" and "route" commands.  They will show if your network card(s) are configured correctly and if you have a route to the Internet.

---

