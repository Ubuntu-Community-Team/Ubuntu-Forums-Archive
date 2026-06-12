---
title: "GX260 graphics problem (GL?)"
date: 2010-07-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mewski on 2010-07-11
Hello everyone, new guy here :)

I have a few old Optiplex GX260 machines to be given to charity with Ubuntu Lucid installed. The problem is graphics: whenever I choose some of the default screen savers (Ant Spotlight and GLSlideshow) the preview runs for about a second, then the screen becomes blank. Sometimes slowly blinking vertical bars on the top half can be seen.
Switching to a tty doesn't help, neither does ctrl+alt+del, apparently the system doesn't respond to any keyboard commands. It is still active though and when I press the power button, plymouth's Ubuntu logo and the system shuts down (by itself, so the Gnome shutdown menu isn't displayed).

Tried Mint 9 and had the same problem :(

I would love to find a solid solution instead of a workaround, since I doubt I will be able to offer any technical support after giving the machines away.

---

### Post by mörgæs on 2010-07-12
Hi, please post the output of 

```
hwinfo --gfx
```

---

### Post by mewski on 2010-07-13
Hi morgæs, here it is:
```
10: PCI 02.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_2562
  Unique ID: _Znp.4MB3MfGfow3
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel i845"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2562 "i845"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0126 
  Revision: 0x01
  Memory Range: 0xe8000000-0xefffffff (rw,prefetchable)
  Memory Range: 0xff680000-0xff6fffff (rw,non-prefetchable)
  IRQ: 16 (1937 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d00002562sv00001028sd00000126bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: intel
  Driver Info #1:
    XFree86 v4 Server Module: intel
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #10
```

---

### Post by mörgæs on 2010-07-13
[http://ubuntuforums.org/showthread.php?t=1525765](http://ubuntuforums.org/showthread.php?t=1525765)

---

### Post by mewski on 2010-07-13
Installing from the PPA seemed to do the trick, cheers mate :)

---

