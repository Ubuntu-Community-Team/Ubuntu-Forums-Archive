---
title: "Unrecognized Network card"
date: 2006-07-30
forum: Desktop Environments
---

### Post by trawler on 2006-07-30
Two days ago I've upgraded my motherboard to ASUS P5800 SE.
Ever since then, my network card is undetected by ubuntu, and I'm forced to use my windows xp, which is really annoying.... :sad: 

I've tried installing the linux driver that came with the Asus CD, but it doesn't seem to be doing much. (attached)
The onboard lan card is an Intel Pro MT 1000. I followed the instructions, and used "make install" from the src library.
That created an e1000.ko file under /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000/.

According to the instructions, a simple "sudo modprobe e1000" should do the trick, but it doesn't.

I've read 2 posts regarding the same problem, with the same kind of intel lan card, but didn't find any solution.
I even tried using ndiswrapper, like somebody suggested, but only got a bunch of "invalid driver" messages.

Checking under dmesg shows that the eth0 is detected, but when i check under ifconfig, I only see the "lo" (loopback) interface.

Please, if anyone managed to find out how to install this same card, let me know. This is driving me crazy...

---

### Post by llamakc on 2006-07-30
Is the module loaded?

lsmod | grep e1000

If it is loaded, add a line for eth0 in /etc/network/interfaces.

---

### Post by trawler on 2006-07-30
Yes, the module is loaded, and eth0 is already defined in /etc/network/intefraces (I had it set up with my old mobo).

dmesg:
```

[17179587.360000] Intel(R) PRO/1000 Network Driver - version 7.1.9
[17179587.360000] Copyright (c) 1999-2006 Intel Corporation.
[17179587.628000] e1000: 0000:02:05.0: e1000_probe: (PCI:33MHz:32-bit) 00:17:31:12:47:47
[17179587.664000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection

```

lsmod:
```
Module                  Size  Used by
e1000                 136992  0
```

/etc/network/interfaces:
```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.10.53
netmask 255.255.255.0
gateway 192.168.10.1
```

But when I try "ifconfig eth0" I get "device not found"...

---

### Post by trawler on 2006-07-31
Ok, I just got to work, and asked some friends of mine. Luckily, they're pretty bright people :) - they suggested the problem was due to a mac address binding belonging to the old Lan card under /etc/sysconfig/network-scripts/ifcfg-eth0, and that I should remove it from the above mentioned file.

I'm gonna have to wait patiently till I get home to check it out... :-?

---

### Post by trawler on 2006-07-31
Internet is up and running, even though I kinda used a shortcut.
I wasn't able to find where that file (ifcfg-eth0). Apparentally that file only exists in CentOS or Fedora, so instead, I just changed the "eth0" entries in /etc/networking/interfaces to "eth1", which did the trick.

If anyone knows how i can still find where the old eth0 is defined, please let me know :)

---

