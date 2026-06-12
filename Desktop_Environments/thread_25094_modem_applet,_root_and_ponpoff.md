---
title: "modem applet, root and pon/poff"
date: 2005-04-09
forum: Desktop Environments
---

### Post by aledin on 2005-04-09
Gnome 2.10 has changed the way that modem applet works: now, you can't (well, maybe I haven't seen an option to do it...) use a script to connect and disconnect to internet with a modem (usually, pon and poff configured with pppconfig), but you have to configure directly the modem. Sadly, in this way to configure the applet you have to sudo to root, and it seems that even to *connect* you have to sudo to root.

So, i can't put the modem applet in the desktop of other users (users that haven't sudo privileges): they can't configure the applet nor connect to internet. With Gnome 2.8 all i had to do is to assign pon and poff to the modem light applet.

Is there a way to fix it or am i dreaming about the new applet? :)

(anyway, the new applet crashes very often...)

said that, congratulations to the team for Hoary!

---

### Post by puddleglum on 2005-06-07
Yes, this is definitely a problem with Gnome 2.10.  I've had to have users type
pon/poff on a terminal window after setting them up with modem priveledges.

It is quite an unelegant solution and I still get complaints about not getting any
feedback on transfer rates.  Anyone know if we can use the Gnome 2.8 Modem
Lights panel applet in 2.10?

---

### Post by az on 2005-06-07
You may use gnome-ppp from universe.

---

