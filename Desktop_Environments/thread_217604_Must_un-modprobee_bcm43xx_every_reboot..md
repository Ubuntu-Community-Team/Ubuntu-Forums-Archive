---
title: "Must un-modprobee bcm43xx every reboot."
date: 2006-07-17
forum: Desktop Environments
---

### Post by WhiteStool on 2006-07-17
I have a Belkin F5D7010 with a broadcom chipset, and although Ubuntu says it supports it, it does not. I don't know why, but every time I rebooot my computer I must run the following.

```
sudo su
modprobe -r bcm43xx
modprobe ndiswrapper
ifconfig eth0 up
```

This really is annoying, and I know there must be an easy way to fix this with modifying the rc.d files, I just do not know what to do specifically.

---

### Post by asplode on 2006-07-17
I'm a bit of a novice myself sometimes when it comes to these things, but   couldn't you just blacklist the bcm43xx modules?

```
echo blacklist bcm43xx | sudo tee -a /etc/modprobe.d/blacklist
```

and then add ndiswrapper to the modules?

```
echo ndiswrapper | sudo tee -a /etc/modules
```

> **WhiteStool said:**
> I have a Belkin F5D7010 with a broadcom chipset, and although Ubuntu says it supports it, it does not. I don't know why, but every time I rebooot my computer I must run the following.

```
sudo su
modprobe -r bcm43xx
modprobe ndiswrapper
ifconfig eth0 up
```

This really is annoying, and I know there must be an easy way to fix this with modifying the rc.d files, I just do not know what to do specifically.

---

