---
title: "No Plug-and-Play for wireless mouse"
date: 2009-01-20
forum: General Help
---

### Post by nathanscottdaniels on 2009-01-20
I've got Ubuntu 8.04 and a nifty little wireless laptop mouse (on a laptop).  The problem is, the mouse's receiver NEEDS to be plugged into the computer before I turn it on.  If I forget to plug it in or I unplug it while it is on, I have to restart the system to use the mouse. (I's like a PS/2 Mouse) Is there some magical terminal command I can use to tell Ubuntu to look for a new mouse plugged in?  Does Linux even support Plug-n-Play peripherals?

---

### Post by adult swim on 2009-01-20
if it isnt found, try running ```
lsusb
``` and see if it will work after that

---

### Post by nathanscottdaniels on 2009-01-20
OMG it worked!  Thank you!

---

