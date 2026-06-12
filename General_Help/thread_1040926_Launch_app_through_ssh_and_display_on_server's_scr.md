---
title: "Launch app through ssh and display on server's screen"
date: 2009-01-16
forum: General Help
---

### Post by ccc0219 on 2009-01-16
I'm trying to find out how to launch an application from a remote machine through ssh but have it display on the server side's screen.  For example, I have my server attached through hdmi to my tv, but it does not have a mouse or keyboard.  I would like to be able to launch a video through ssh from my laptop and have it display on the tv connected to the server.  This seems contrary to everything I have found when searching, because everyone seems to want to forward X11 to the client side. Thanks for any advice.

---

### Post by Ahadiel on 2009-01-16
```
DISPLAY=:0.0 command
```
Do that while SSH'd into the server.

---

### Post by ccc0219 on 2009-01-16
That worked perfectly.  Thanks a lot.

---

