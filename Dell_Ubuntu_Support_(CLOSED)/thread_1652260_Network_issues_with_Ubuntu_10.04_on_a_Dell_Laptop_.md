---
title: "Network issues with Ubuntu 10.04 on a Dell Laptop N5010"
date: 2010-12-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by leviathan8 on 2010-12-24
Hello, I just got my Dell laptop N5010 today, and I installed ubuntu 10.04 on it. The problem is, that when I try to connect to internet, using the Network Manager, there are no wireless access points. I tried to manually connect to my home router, but unfortunately, after writing down the SSID, MAC Address and WLAN security mode, nothing happened. Tried hundred of times, still won't work. Any ideas?

---

### Post by mikewhatever on 2010-12-24
Dell loves using Broadcom wireless cards which require a proprietary driver to work. Hook up an ethernet cable, then open System->Administration->Drivers to search for one.

---

### Post by leviathan8 on 2010-12-27
> **mikewhatever said:**
> Dell loves using Broadcom wireless cards which require a proprietary driver to work. Hook up an ethernet cable, then open System->Administration->Drivers to search for one.

That worked. Thanks a lot.

---

