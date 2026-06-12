---
title: "Dell Inspiron 510M: Ubuntu Crashes"
date: 2010-07-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gopa on 2010-07-07
Hi,

   First of all I am new to Ubuntu. Recently switched to lucidlynx from winXP and
am pretty happy with it. I am running Lucid lynx on a Dell Inspiron 510M laptop. 
Occasionally Ubuntu crashes flashing a blank screen and after some time
displays a message that the graphics was not configured properly and I need
to reconfigure by myself. Following it I get an option "Run Ubuntu on low graphics
mode" and I could load my desktop again. I checked /etc/X11/xorg.conf and there
is no such file in my case. I have no idea how to fix this. Could somebody tell me
how to fix this problem.

Thanks in advance for the help

-Gopa

---

### Post by mörgæs on 2010-07-07
Welcome to the forum.

A good first test in this case is to run memtest to see how the RAM is behaving. It might take some time, so best is to do it overnight.

---

### Post by gopa on 2010-07-07
> **mörgæs said:**
> 
A good first test in this case is to run memtest to see how the RAM is behaving. It might take some time, so best is to do it overnight.

Hi, I already did the memtest few days back and it gave me no error.
Does this problem has to do something with the RAM? Since I am missing
the xorg.conf file in my /etc/X11/ I thought something went wrong in this
direction. Any help? :rolleyes:

---

### Post by mörgæs on 2010-07-08
The new Ubuntus do not have an xorg.conf by default. However, if the file is there, it is used.

Which screen card do you have? Please post the output of 

```
hwinfo --gfx
```

---

### Post by gopa on 2010-07-08
> **mörgæs said:**
> 
Which screen card do you have? Please post the output of 

```
hwinfo --gfx
```


Hi, here is the output of "hwinfo --gfx"

> 11: PCI 02.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_3582
  Unique ID: _Znp.JtozZ9Kbt53
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel 855 GM"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x3582 "855 GM"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0164 
  Revision: 0x02
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0xf0000000-0xf7ffffff (rw,prefetchable)
  Memory Range: 0xfaf80000-0xfaffffff (rw,non-prefetchable)
  I/O Ports: 0xc000-0xc007 (rw)
  IRQ: 11 (95850 events)
  Module Alias: "pci:v00008086d00003582sv00001028sd00000164bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: intel
  Driver Info #1:
    XFree86 v4 Server Module: intel
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown

12: PCI 02.1: 0380 Display controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_3582_0
  Unique ID: ruGf.JvDs_QVYdK8
  SysFS ID: /devices/pci0000:00/0000:00:02.1
  SysFS BusID: 0000:00:02.1
  Hardware Class: graphics card
  Model: "Intel 855 GM"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x3582 "855 GM"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0164 
  Revision: 0x02
  Memory Range: 0xe8000000-0xefffffff (rw,prefetchable)
  Memory Range: 0xfaf00000-0xfaf7ffff (rw,non-prefetchable)
  Module Alias: "pci:v00008086d00003582sv00001028sd00000164bc03sc80i00"
  Driver Info #0:
    XFree86 v4 Server Module: intel
  Driver Info #1:
    XFree86 v4 Server Module: intel
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #11

---

### Post by mörgæs on 2010-07-08
Intel 855 and Ubuntu 10.04 are not really good friends. 

You can try these instructions
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

but I guess the easiest approach is to switch to 9.10, which does not have this kind of trouble. It is supported almost a year from now.

[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

### Post by gopa on 2010-07-08
> **mörgæs said:**
> Intel 855 and Ubuntu 10.04 are not really good friends. 

You can try these instructions
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

but I guess the easiest approach is to switch to 9.10, which does not have this kind of trouble. It is supported almost a year from now.

[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)
Hi,
many thanks for the suggestions.. Few months back I have upgraded to 
lucid lynx from 9.10. I was wondering whether it is possible to revert back 
without losing my data?

---

### Post by mörgæs on 2010-07-08
No, you can not roll back a release. You need a backup and a clean install.

---

### Post by anilw3 on 2011-05-12
hello Gopa, 
what did you finally end up doing?
Im using Ubunto 10.10, should I go back to 9.10 or upgrade to 11.04 to get my graphics working well (Scilab crashes when I try doing any type of graph, and sometimes my screen goes black for a second and comes back) on my Dell 510m. I have the same configuration as you do.
thanks

---

### Post by mörgæs on 2011-05-13
9.10 is unsupported now, so this is not an option any more.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

How does a live boot of 11.04 work?

---

