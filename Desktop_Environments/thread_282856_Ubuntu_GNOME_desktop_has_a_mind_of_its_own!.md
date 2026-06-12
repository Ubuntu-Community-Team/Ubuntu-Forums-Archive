---
title: "Ubuntu GNOME desktop has a mind of its own!"
date: 2006-10-23
forum: Desktop Environments
---

### Post by rcwatson on 2006-10-23
I'm getting phantom mouse movements in the default desktop environment (GNOME) of an Ubuntu installation.  Every so often (randomly) the mouse simply wigs out and starts opening stuff from the task bar and at very high speeds.  Many times it opens the shutdown dialog.  It's almost as if it is being taken over by someone else.  All I can do is wait for it to finish whatever it thinks it's doing and then undo all of the damage.  

For a while I was thinking it was someone hacking in and taking over the VNC capabilities.  But turning off my network connection didn't seem to help.  It still wigs out and goes into "HAL-9000" mode.  What gives?

---

### Post by rcwatson on 2006-10-23
I found another posting about KVM switches that describes this same issue.  There is a HOWTO posting that says to put the following line in the /etc/modules file.  So far it seems to be working out.

psmouse proto=exps

---

