---
title: "switching wireless network connections?"
date: 2005-09-29
forum: Desktop Environments
---

### Post by uperjer on 2005-09-29
i open up the kwifi manager, go into administrator mode, and try to specify the network that i want to connect my wireless adaptor to, and reboot.  everytime i boot, however, i end up on my neighbor's wifi.  any suggestions?

---

### Post by mlomker on 2005-09-29
Do you roam around with this machine or is it a PC that stays at home?

You could edit your /etc/network/interfaces file something like this:

```

iface wlan0 inet dhcp
wireless-essid yourAP

```

---

