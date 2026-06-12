---
title: "WIFI scan networks with Ubuntu"
date: 2006-02-27
forum: Desktop Environments
---

### Post by petr2 on 2006-02-27
HEllo

can anybody help me how to scan wifi networks with Ubuntu Live CD I would like to try it before installation.

Thank you

Vaclav

:KS

---

### Post by hw-tph on 2006-02-27
Enable your interface (make sure the driver is loaded) and type **sudo iwlist wlan0 scan** where wlan0 should be replaced by the actual name of your wireless network device name (depends on the driver).


Håkan

---

### Post by svref on 2006-02-27
```
root@umlaut:~# iwlist eth1 scan
eth1      Interface doesn't support scanning : Operation not supported

```
Nuts-o!  This is an apple Airport card, and I know Apple has figured out how to scan with it, because I booted to os 10, copied down the essid, and rebuntued.

Here's hoping kismet is craftier...  : (

---

