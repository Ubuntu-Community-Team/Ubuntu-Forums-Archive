---
title: "Wireless works in Gnome but not KDE?"
date: 2008-10-18
forum: Desktop Environments
---

### Post by blazemore on 2008-10-18
This is so weird. I have a Linsys WUSB545s v2 wireless network adaptor (Which now works natively in 8.10, yay).

But, and this is the weird thing: Only the Gnome Network Manager packaged with Ubuntu will see the wireless networks.

On the KDE one (fresh Kubuntu, or KDE installed on base Ubuntu) it doesn't detect any of the wireless networks.

An obvious workaround is to use the Gnome network manager, but I can't install it without Internet connections (far to many dependancies)

Why is this? Is it a known issue? How can I fix it?

---

### Post by blazemore on 2008-10-19
*bump*

---

### Post by Dave_Connor on 2008-10-19
Have you tried booting into KDE and doing in terminal "sudo /etc/init.d/networking restart" and see if that helps with anything.

---

### Post by blazemore on 2008-10-19
What would that do? Would that restart the network device, or just the manager program?

---

### Post by Dave_Connor on 2008-10-19
It would restart your nic card and sometimes it could be the card with wireless issues. Happens with my laptop when it is having connection issues.

---

