---
title: "Can't mount devices and disks for some reason."
date: 2009-01-15
forum: General Help
---

### Post by kokkus on 2009-01-15
Hey.
Today when I started the PC, I got this error when I tried to access afile on another disk.

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

It's a local hard driver.

---

### Post by kokkus on 2009-01-16
BüMp

Pleass help!

---

### Post by PmDematagoda on 2009-01-16
Can you post the output of:-
```
dmesg | tail -25
```

---

### Post by kokkus on 2009-01-16
[   31.696877] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   31.697132] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   31.986553] NET: Registered protocol family 17
[   41.932008] eth0: no IPv6 routers present
[  124.988305] ppdev0: registered pardevice
[  125.037235] ppdev0: unregistered pardevice
[  126.224085] ppdev0: registered pardevice
[  126.272025] ppdev0: unregistered pardevice
[  126.431347] ppdev0: registered pardevice
[  126.481985] ppdev0: unregistered pardevice
[  552.964197] heci: schedule work the heci_bh_handler failed error=0
[  944.968998] heci: schedule work the heci_bh_handler failed error=0
[ 1416.964547] heci: schedule work the heci_bh_handler failed error=0
[ 2403.048383] ppdev0: registered pardevice
[ 2403.096157] ppdev0: unregistered pardevice
[ 2404.208087] ppdev0: registered pardevice
[ 2404.256019] ppdev0: unregistered pardevice
[ 2404.282172] ppdev0: registered pardevice
[ 2404.328210] ppdev0: unregistered pardevice
[ 3168.964405] heci: schedule work the heci_bh_handler failed error=0
[ 3372.964329] heci: schedule work the heci_bh_handler failed error=0
[ 3780.964185] heci: schedule work the heci_bh_handler failed error=0
[ 3828.965148] heci: schedule work the heci_bh_handler failed error=0
[ 5000.965000] heci: schedule work the heci_bh_handler failed error=0
[ 5512.964125] heci: schedule work the heci_bh_handler failed error=0

---

