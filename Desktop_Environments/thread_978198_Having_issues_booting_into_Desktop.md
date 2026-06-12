---
title: "Having issues booting into Desktop"
date: 2008-11-10
forum: Desktop Environments
---

### Post by ImOverIt on 2008-11-10
Hey guys im a new user to the forum :)

Having some issues with my other pc running Ubuntu 8.10 Intrepid.
I have a LCD monitor connected to my pc through DVI using a GeForce 6800, recently I also connected a VGA wire to the card and my 42 inch Sony TV so I can clone the desktop on both my TV and LCD monitor, I had some issues adjusting the image so I gave up and just disconnected the VGA connection to the TV. I think I may have overwritten some xorg configuration cause today when I turned on my pc its saying it did not detect a x server and to reconfigure it then run gdm again, only thing I can do is log in as either myself or root and type in some configurations into a black screen but Im farely new to Linux myself so not sure what sort of commands would resolve this issue, any suggestions would be very appreciated, Thanks!

---

### Post by kernelhaxor on 2008-11-10
As root user, type in

> dpkg-reconfigure xserver-xorg

it should open a graphical interface to reconfigure your xorg

---

### Post by ImOverIt on 2008-11-11
Ah nice thats what I was looking for, got that sucker reconfigured, backup and running thanks! :-P

---

