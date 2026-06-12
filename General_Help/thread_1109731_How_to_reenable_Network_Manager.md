---
title: "How to reenable Network Manager ?"
date: 2009-03-29
forum: General Help
---

### Post by k0k0 on 2009-03-29
I used "sudo update-rc.d -f NetworkManager remove" but i don't have internet now ... i tried sudo update-rc.d -f NetworkManager start 2 0 but it says it is already there.. i ahve cross on the icon of the network manager..

---

### Post by ViMMeD on 2009-03-29
I had this problem a while ago, try booting into an earlier kernel (if you have one, it's always good to) go into synaptic and find the kernel version you deleted nwm on (will probably look like "linux-headers-2.6.27-11-generic") and set it to mark for reinstallation.  boot back into that kernel, i'm not sure if doing this will "format" the kernel, but it's what i did to solve the problem.  If you don't have any kernel settings saved for any great importance you can try this.  You could always create a new default kernel which will have it installed.

---

### Post by k0k0 on 2009-03-29
Thanks I'll try this solution :)

---

