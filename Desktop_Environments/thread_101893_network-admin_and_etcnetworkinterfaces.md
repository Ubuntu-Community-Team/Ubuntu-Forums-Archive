---
title: "network-admin and /etc/network/interfaces"
date: 2005-12-10
forum: Desktop Environments
---

### Post by rrenomeron on 2005-12-10
My wifi adapter is configured in /etc/network/interfaces like this:
```

iface wlan0 inet dhcp
     pre-up /etc/init.d/wpasupplicant restart
     pre-up sleep 1

```
However, I've noticed that the pre-up bits don't run when I use the GNOME Network Admin tool ("Networking" on the Administration menu) to bring wlan0 up and down.  The command-line stuff (ifup wlan0/ifdown wlan0) works fine.

Is there something I'm missing with respect to configuring the Network Admin tool?  Or is this a bug?

---

