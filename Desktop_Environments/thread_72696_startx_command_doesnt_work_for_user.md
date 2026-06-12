---
title: "startx command doesnt work for user"
date: 2005-10-07
forum: Desktop Environments
---

### Post by Pippen101 on 2005-10-07
Hey,

Wierd problem. Used synaptic to update a few pkgs ( quiet a few actually..) and now i can "startx" with my user.

I have to sudo startx

and it logs me in as root.

help plz how to change permissions on startx command!

---

### Post by Ampersand on 2005-10-07
You can get round the problem by running /sudo /etc/init.d/gdm restart' instead of 'startx'. This will bring you to the login screen.

---

