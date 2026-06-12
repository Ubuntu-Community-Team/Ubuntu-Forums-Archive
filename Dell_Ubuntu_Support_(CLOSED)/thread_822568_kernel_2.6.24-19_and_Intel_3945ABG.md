---
title: "kernel 2.6.24-19 and Intel 3945ABG"
date: 2008-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LK_gandalf_ on 2008-06-08
Hi, I have a dell XPS M1530, with Kubuntu 8.04 64 bit: I've never used the wifi card (Intel 3945ABG), but it was checked and installed out of the box.  

Now, After the kernel update yesterday (2.6.24-19) it seems disappeared.
The drivers are correctly detected,... 

```
~$lsmod | egrep 'Module|iwl|ipw'
Module                  Size  Used by
iwl3945               100468  0
iwlwifi_mac80211      251876  1 iwl3945
cfg80211               17680  1 iwlwifi_mac80211

```

But there is no wlan on ifconfig:

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:36:4d:62
          inet addr:xxxxxxxxxxx  Bcast:xxxxxxxxxxxxx  Mask:255.255.248.0
          inet6 addr: fe80::21d:9ff:fe36:4d62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20716654 (19.7 MB)  TX bytes:18504728 (17.6 MB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22773 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3061474 (2.9 MB)  TX bytes:3061474 (2.9 MB)

```

What about you?

---

