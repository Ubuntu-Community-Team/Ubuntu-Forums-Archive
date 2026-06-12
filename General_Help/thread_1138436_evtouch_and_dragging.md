---
title: "evtouch and dragging"
date: 2009-04-26
forum: General Help
---

### Post by CaptainIntercom on 2009-04-26
I'm using a USB touchscreen with the evtouch driver in Jaunty, and for some reason I can't drag-and-drop anything with the stylus anymore. Tap-to-click works, and the cursor follows the stylus around fine, but it doesn't 'hold' the clicked status, if that makes sense. It worked fine in Intrepid before I upgraded. It seems like such a trivial thing to overlook, but I guess the functionality was left out for some reason.

I've tried installing the xserver-xorg-input-evtouch package from Intrepid, but it depends on xserver-xorg-input-2.1, and I guess it doesn't like that. 

Anyone know a way of getting drag-and-drop back? This touchscreen is pretty much going to waste without it :(

---

### Post by hackeron on 2009-05-09
I'm experiencing the same problem. It seems this is the patch that is supposed to fix this. I will try to apply it and report back: [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127)

---

### Post by hackeron on 2009-05-09
I found a solution, see: [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127)

---

