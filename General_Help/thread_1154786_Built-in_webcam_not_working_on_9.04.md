---
title: "Built-in webcam not working on 9.04"
date: 2009-05-10
forum: General Help
---

### Post by kentcb on 2009-05-10
Hi,

I'm trying to get my mum onto Ubuntu but only one thing is stopping me. Her built-in webcam isn't working. Output from lsusb is:
```

Bus 001 Device 002: ID 0db0:6877 Micro Star International RT2573
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0c45:624f Microdia PC Camera (SN9C201)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0db0:a97a Micro Star International Bluetooth EDR Device
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Having identified the webcam I found instructions on how to compile and install the drivers. I suppose I'm willing to do that but am wondering whether there's an easier and faster option. I would have thought it possible for someone (that someone may well be me) to precompile and share it with other 9.04 users. So:

[LIST=1]
[*]Is there an easier way to do this?
[*]Is there a repository containing pre-compiled drivers for 9.04?
[/LIST]

Thanks,
Kent

PS. For those searching, the laptop make is NEC Versa P7300

---

### Post by nzadLithium on 2009-05-10
1) Is there an easier way to do this?
It doesn't look like any of the drivers for this webcam are provided in the kernel or synaptic so unless there's some deb files hanging round somewhere your going to have to compile :S

2) Is there a repository containing pre-compiled drivers for 9.04?
I've never heard of one. The kernel includes alot of drivers though, and the linux-restricted-modules package provides a whole lot more.

It seems like someone created a bug report asking for the driver you want to be included in ubuntu, you might like to add your opinion. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/87054](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/87054)

These seem like good instructions for compiling the driver you want if your looking for some:
[http://blog.zerodogg.org/2008/04/27/microdia-0c45624f-webcam-on-linux/](http://blog.zerodogg.org/2008/04/27/microdia-0c45624f-webcam-on-linux/)

---

### Post by kentcb on 2009-05-12
Thanks for that - managed to get it working via the instructions on their site.

---

