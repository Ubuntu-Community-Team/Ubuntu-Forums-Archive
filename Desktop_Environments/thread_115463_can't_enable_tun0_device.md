---
title: "can't enable tun0 device"
date: 2006-01-10
forum: Desktop Environments
---

### Post by suoko on 2006-01-10
Hi,

I installed the tun module via 'modprobe tun' but ifconfig doesn't show it anyway. I have no firewall installed.
Ho do I enable it ???

---

### Post by cwaldbieser on 2006-01-10
[QUOTE=suoko]Hi,

I installed the tun module via 'modprobe tun' but ifconfig doesn't show it anyway. I have no firewall installed.
Ho do I enable it ???[/QUOTE]
I think you need something like this:
[http://vtun.sourceforge.net/]("http://vtun.sourceforge.net/")

---

### Post by suoko on 2006-01-10
Is that really needed?
Should'nt I find tun0 among ifconfig device list just installing the tun module?

---

### Post by cylon359 on 2006-01-10
No, you need something to create the tunnel interface.

---

### Post by cwaldbieser on 2006-01-11
[QUOTE=suoko]Is that really needed?
Should'nt I find tun0 among ifconfig device list just installing the tun module?[/QUOTE]
tun is just a kind of driver for a "virtual software device".  If you have an ethernet driver installed, but not ethernet card, the device won't show up.  Roughly speaking, the same idea applies here.

---

