---
title: "Got interface in block state"
date: 2011-11-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by luckysanj on 2011-11-03
Dear All, 
I  have small one problem  with my Ubuntu 11.10 os system on my laptop. With each reboot I got all my laptop interface  are in block state.

root@jupiter:~# rfkill ist
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

So i have to do manually unblock all interface every time with ```
ifup eth0
``` & it is irritating me &  I want to know what happen with my system why the interface are automatically block in each reboot.

I need your suggestion.


Luckysanj

---

