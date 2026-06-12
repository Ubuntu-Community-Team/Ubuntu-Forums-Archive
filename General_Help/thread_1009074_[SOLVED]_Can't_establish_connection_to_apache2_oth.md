---
title: "[SOLVED] Can't establish connection to apache2 other than through 127.0.0.1"
date: 2008-12-12
forum: General Help
---

### Post by LoneWolfJack on 2008-12-12
Ok, I've just been trying to solve this for over an hour. 

I have apache2 installed and it works perfect when I access it through 127.0.0.1.

When I try to access it through my servers IP address from any other PC on my network, I'm getting "Firefox can't establish a connection to the server at...".

I suppose something is blocking the request, but disabling ufw didn't get me anywhere. 

Any help would be appreciated.

---

### Post by LoneWolfJack on 2008-12-12
Ok, got it... installed firestarter and managed to turn off the firewall. disabling ufw apparently isn't enough.

---

