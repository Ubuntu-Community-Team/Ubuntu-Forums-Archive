---
title: "WIFI problem on dell xps 1530"
date: 2009-03-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by manasmohan on 2009-03-01
i am using ubuntu 8.10 on my dell laptop(xps 1530).... whenever turn on my laptop and boot ubuntu on my laptop, my wifi doesnt work, then i have to restart my computer and boot windows first, the wifi gets on there,then again i have to restart my computer and boot ubuntu, generally the wifi gets on(not always).... please suggest me some solution so that i may use the wifi without so much effort...

---

### Post by smani on 2009-03-01
Please post the output of
```
ifconfig
```
and
```
sudo lshw
```
when your wireless fails to work.

---

### Post by smashagnome on 2009-03-11
I had the same problem with my XPS 1530.  I needed to add a noapic boot parameter in the grub.

/boot/grub/menu.lst


Make it look something like this


kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=10cad5a0-5f15-4f99-b08f-455d46fbd882 ro quiet splash **noapic **nmi_watchdog=0


Hope that helps.

Regards

---

