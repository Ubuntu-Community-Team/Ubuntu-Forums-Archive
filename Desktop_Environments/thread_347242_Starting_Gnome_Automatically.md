---
title: "Starting Gnome Automatically"
date: 2007-01-26
forum: Desktop Environments
---

### Post by m4c4 on 2007-01-26
hi, im a new user of the ubuntu system, i use the ubuntu 6.10, recently id install the full gnome packet, and everything was okay, but my father used my machine and before that the gnome dont start automatically, him don't know what he did, ether i, hehehe. so im trying to make it starts automatically again, can anyone help me with that, i was searching in the /etc/event.d, but im not dont have certainly in what to do. actualy i need to login, type startx to make gnome up.

Tnks for any help. Carlos     

PS: sorry for my horrible english. :(

---

### Post by Ptero-4 on 2007-01-27
First make sure that gdm is installed.
Second make sure that /etc/init.d/gdm exists and have the proper permissions. and
type:
```
sudo /etc/init.d/gdm start
``` at the terminal.

---

