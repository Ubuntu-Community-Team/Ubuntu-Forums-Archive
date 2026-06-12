---
title: "Wireless will not connect"
date: 2017-07-28
forum: Debian
---

### Post by yuriislove on 2017-07-28
My issue is that my wireless will not connect. I can see the network I want, and have triple checked the password. It'll start connecting but never make it. After a short time I get the 'network disconnected' message.

```


uname -a
Linux mixin 4.11.0-1-amd64 #1 SMP Debian 4.11.6-1 (2017-06-19) x86_64 GNU/Linux

Relevant lsusb
Bus 004 Device 002: ID 0846:9012 NetGear, Inc. WNDA4100 802.11abgn 3x3:3 [Ralink RT3573]
```

As listed, its a Ralink RT3573. I assume I already have the firmware as I can see the networks around me, however doing a modprobe rt3573sta spits out
```
modprobe: FATAL: Module rt3573sta not found in directory /lib/modules/4.11.0-1-amd64
```

I'm not really sure where to go from here. Any help would be appreciated, thanks.


Edit: I probably should mention that I tried following chili's post here [https://ubuntuforums.org/showthread.php?t=1942689&page=4](https://ubuntuforums.org/showthread.php?t=1942689&page=4) , but MAKE and MAKE INSTALL gives me a multitude of errors, so I had no luck there.

---

### Post by yuriislove on 2017-07-28
Got It
Network manager was trying to scramble my mac address and that was causing a problem connecting
I followed this [https://askubuntu.com/questions/902992/ubuntu-gnome-17-04-wi-fi-not-working-mac-address-keeps-changing/905019#905019](https://askubuntu.com/questions/902992/ubuntu-gnome-17-04-wi-fi-not-working-mac-address-keeps-changing/905019#905019) and restarted the manager. This fixed it

---

