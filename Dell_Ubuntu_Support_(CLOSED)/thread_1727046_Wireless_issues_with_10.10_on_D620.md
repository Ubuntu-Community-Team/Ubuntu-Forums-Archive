---
title: "Wireless issues with 10.10 on D620"
date: 2011-04-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dale58 on 2011-04-12
I have a DELL Latitude D620 that works fine with Ubuntu Desktop v10.10, but if I install Ubuntu Studio v10.10 the wireless fails.  This last install I was able to get the wireless to connect and get an IP address, but can only open local web sites.  PING also works only on the local LAN.  If I try to open external web sites, they just time out but I do get DNS lookup.  Both installs are on the same laptop.

What differences are in the Studio version of Ubuntu 10.10 compared to Desktop 10.10? It looks like they both use the same drivers.

Dale

---

### Post by Grafens on 2011-04-12
There is an issue with ubuntustudio and wifi. When I first started using ubuntustudio10.04 the problem was that wifi would interfere with the “real time kernel” that 10.04 used. Now although 10.10 uses a “low latency kernel” there still seems to be issues. What they are I'm not sure.

As to the differences between ubuntustudo10.10 and regular ubuntu10.10 I don't think there's much, but you can always test it by monitoring how much latency regular ubuntu has. The lower the better.

Grafens

---

