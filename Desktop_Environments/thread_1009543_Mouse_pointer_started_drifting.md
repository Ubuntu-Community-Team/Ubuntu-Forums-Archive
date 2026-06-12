---
title: "Mouse pointer started drifting"
date: 2008-12-12
forum: Desktop Environments
---

### Post by carpii on 2008-12-12
Hi all, Im on kubuntu 8.04 

For the past couple of days, my mouse pointer has started drifting to the right. Its a Microsoft Gaming Laser mouse 6000 (not wireless).

I managed to narrow it down to the psmouse module, and if I do 
modprobe -r psmouse

the pointer stops moving and I can use the mouse normally again.

1) Is anyone else having this problem. I want to know why its suddenly started happening

2) The psmouse mod comes back after a reboot. How can I prevent the module being loaded at all, it seems to be causing nothing but problems now

Thanks

---

### Post by fcigoi on 2009-11-29
Same problem here.
I upgraded to Karmic and all the sudden both mouse and trackpad started drifting.
The even stranger thing is that the drifting speed changes at every reboot of the system.

---

