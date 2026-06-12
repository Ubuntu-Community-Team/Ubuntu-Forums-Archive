---
title: "Vostro 1700 Wireless (Can't get it working)"
date: 2008-10-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TheFlyingScotsman on 2008-10-17
Hi there, 

I've read a number of guides before posting this thread as I'm sure you have all heard this kind of problem before. But nothing in any of the guides I have read has worked for me yet.

Here are commands I have run with the output they return:

lspci -n | grep '14e4:43'

14e4:4311(rev01)

lsb_release -d

Ubuntu 8.04.1

uname -mr 

2.6.24-19-generic i686

lshw -C network

Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
module=ssb

So far I've been mainly trying NDISWrapper and I seem to have the driver installed but can't seem to make the wireless want to use it, removing SSB makes the network unclassified rather than changing to module=NDISWrapper. Don't know if I should continue trying this or if the guides I have read are out of date for the latest version of Ubuntu I am using and there is some other method I should be attempting.

---

