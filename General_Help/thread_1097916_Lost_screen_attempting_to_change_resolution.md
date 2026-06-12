---
title: "Lost screen attempting to change resolution"
date: 2009-03-16
forum: General Help
---

### Post by vcollazo on 2009-03-16
Hi I'm a newbie to both Ubuntu and Linux,
Last week I installed Ubuntu 10.0 and fortunately set up two user accounts.  On one of the accounts I attempted to change my screen resolution and my screen went almost totally blank with thin horizontal and vertical lines.  There was a mouse pointer, but it was static.  I've spent the better part of three days trying remedies posted here but nothing worked.  When I tried to use nano or vi to modify the .config/monitors xml file I was denied permission no matter which of my 2 user accounts I  attempted (my other account was not affected by the resolution problem).  Finally I noticed that my good account did not have the above mentioned file.  In one of the forum threads I learned about the gksudo nautilus command and used that to finally remove the offending file.  My problem is solved for now but how can I change resolution settings without encountering this problem?  My computer is a Dell Inspiron 1501 and the graphic card is an ATI RS482[Radeon Express 200M]  By the way, I used System>preferences>screen resolution to attempt to change from 1280x800 to 1024x768 and that's when everything went haywire.  Thanks in advance.:(

---

### Post by S.A.A on 2009-03-16
First of all there's no ubuntu 10.0 the last one is 9.04 and it's still alpha, anyway did you install the driver for you card, if you did that try this at the terminal:
```
sudo dpkg-reconfigure xserver-xorg 
```
and follow the wizard.

---

### Post by vcollazo on 2009-03-16
Sorry about that.  It was Ubuntu 8.10.

---

