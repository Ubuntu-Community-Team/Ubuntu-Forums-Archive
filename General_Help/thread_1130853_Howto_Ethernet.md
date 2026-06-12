---
title: "Howto Ethernet"
date: 2009-04-20
forum: General Help
---

### Post by jrev on 2009-04-20
Hi all,

I just installed the eeebuntu  2.0 base and there I got no driver for my Eth0 module. I had it working on the NBR version of eeebuntu

So no connection to the Net.

Seems strange that those 2 different versions have not the same kernel  :D 

If I cannot solve this problem I have to install the third most complete version of eeebuntu, the "Standard" one.

If you can help me or give me an address ...

---

### Post by ugm6hr on 2009-04-20
Try giving more detail about the situation.

See the Wifi help? link below (most applies to wired connections too).  Post back necessary details.

---

### Post by jrev on 2009-04-21
What is the name of the Ethernet Atheros kernel module for the eeepc 701 4 G ?

Probably not in the l'eeebuntu base Kernel. The Etho driver isn't available...
It was OK in the NBR version

jean@jean:~$ ifconfig
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wlan0 Link encap:Ethernet HWaddr 00:15:af:a2:59:50
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wmaster0 Link encap:UNSPEC HWaddr 00-15-AF-A2-59-50-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

sudo modeprobe : command not found

sudo depmod -a : no answer

jean@jean:~$ lspci | grep Ethernet
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

locate .ko | grep Atheros no answer
locate .ko | grep Attansic no answer

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
pciehp pciehp_debug=1 pciehp_force=1
p4_clockmod
lp

Thanks for your attention :D
and remedy

---

### Post by jrev on 2009-04-25
Up please

---

