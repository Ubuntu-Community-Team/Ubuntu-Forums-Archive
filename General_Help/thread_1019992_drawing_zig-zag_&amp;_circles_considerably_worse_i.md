---
title: "drawing zig-zag &amp; circles considerably worse in ubuntu 8.10"
date: 2008-12-23
forum: General Help
---

### Post by klerfayt on 2008-12-23
I don't have ubuntu 8.04 installed, so I can't tell how drawing diagonals with pencil tool in gimp works there, but if I would compare 7.10 to 8.10, then I would say 8.10 is worse.
In both ubuntu versions (that is 8.10 and 7.10) mouse cursor acceleration is disabled.
```
xset m 1 1
```The drawing is done with pencil tool - brush Circle (01) and Circle (03). [SIZE=1]Stuff in red is written with paintbrush tool Circle (01) in ubuntu 8.10, but that doesn't matter, compare only things appearing in black[/SIZE]
[IMG]http://i39.tinypic.com/23peok.png[/IMG]
usb mouse:
cat /proc/bus/input/devices
```
I: Bus=0003 Vendor=046d Product=c03f Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=17
B: KEY=f0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10
```

---

### Post by klerfayt on 2008-12-23
Exhibit B: drawing horizontal and vertical lines with free hand, attempt at smilies. 8.10 versions are quiet disturbing, as if drawn by robot hand.

[IMG]http://i42.tinypic.com/j7b96f.png[/IMG]

---

