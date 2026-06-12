---
title: "cant connect to lamp server trough ssh outside my lan"
date: 2009-05-18
forum: General Help
---

### Post by malanco on 2009-05-18
hi guys, ive installed a LAMP server with dynds and ddclient, everything is working great except that i cant connect to my web server through ssh typing my dyndns domain name example (lamp.server.net), i get a timeout error, but i try to connect to it inside my home network (192.168.1.70) everything is ok?, any help will be greatly appreciated!!:p

---

### Post by mb_webguy on 2009-05-18
Have you configured your router for port forwarding of ssh to your server?  I'm assuming you did for the http ports, otherwise you wouldn't be able to connect to your web server from outside your home network.

---

### Post by colsandurz on 2009-05-18
also, are you sure the ssh daemon is running?

I think the command is

```
/etc/init.d/sshd start
```

then, as the previous poster said, forward port N on your router and do

ssh -p N user@address

---

### Post by cariboo on 2009-05-18
Go to [canyouseeme]("http://www.canyouseeme.org/") to check what ports are open to the outside world.

---

### Post by malanco on 2009-05-18
i have open ports 22 and 80 guys

---

### Post by malanco on 2009-05-19
lol i just found out that firestarter was blocking my ports, now everything is working, thanks!:D

---

