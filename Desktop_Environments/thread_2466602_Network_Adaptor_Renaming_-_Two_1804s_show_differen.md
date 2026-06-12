---
title: "Network Adaptor Renaming - Two 18:04s show different IDs"
date: 2021-08-31
forum: Desktop Environments
---

### Post by Geoff_Lane on 2021-08-31
Folks, not sure the theory behind Ubuntu renaming the NICs from the well known eth0 and wlan0 to the other less memorable IDs but I am puzzled as to why one version of 18:04 LTS has the old names and another shows the new names.

18:04 in US shows eth0 and wlan0
18:04 in UK shows enp1s0 and wlp2s0

The 18:04 in US was installed by me on a visit, cannot recall exactly what method I used but it is on a Gateway laptop, no other OS.  Machine used as a dlna media server and ssh server.

At the time my laptop in UK also had 18:04

Why might these two machines differ?

Geoff

---

### Post by jeremy31 on 2021-08-31
Any chance someone used one of the methods at [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/) under I don't like this, how do I disable this?

---

### Post by Geoff_Lane on 2021-09-02
> **jeremy31 said:**
> Any chance someone used one of the methods at [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/) under I don't like this, how do I disable this?

Thanks for link, fascinating.

No chance anyone would have changed settings, machine not used and owner has no idea of Linux.  I installed the Ubuntu system when visiting, it merely runs a DLNA server (miniDLNA for media streaming) and ssh, the latter so I can manage it.  Machine used merely to stream any videos to her TV

I can understand the reasoning now behind changing from eth(n) and wlan(n) and realise the average home user the old system is fine.

Geoff

---

