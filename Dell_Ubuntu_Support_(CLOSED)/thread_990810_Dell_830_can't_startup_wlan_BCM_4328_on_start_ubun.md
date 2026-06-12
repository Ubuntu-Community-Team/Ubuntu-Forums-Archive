---
title: "Dell 830 can't startup wlan BCM 4328 on start ubuntu"
date: 2008-11-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by leopard555 on 2008-11-23
Hi,
I have Dell 830 laptop with wireless LAN Broadcom BCM 4328. I upgraded ubuntu from 8.04 to 8.10. Before, i have no problem with my Wlan.
Now everytime i boot on ubuntu i have to write those commands to activate/startup the wlan card.

sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl

I want wlan to startup during the system startup (as before). I already tried to add the previous commands to the startup menu (system|preferences|sessions) but it doesn't work.

I also createed a file "modprobe" in the modprobe.d folder and added them and reboot the machaine, but still the problem not resolved.

Any solutions?!
Thanks

---

### Post by leopard555 on 2008-11-23
Hi,
I found out the solution :) . Just go to:
System|Administration|Hardware Drivers
Then you will see an item " Broadcom STA wireless Driver ", activate it and everything should be OK :)
Thanks!

---

