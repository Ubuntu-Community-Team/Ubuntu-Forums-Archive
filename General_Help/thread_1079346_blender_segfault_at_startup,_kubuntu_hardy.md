---
title: "blender segfault at startup, kubuntu hardy"
date: 2009-02-24
forum: General Help
---

### Post by ghoulsblade on 2009-02-24
hi all, i get a segfault when starting blender =(
it worked two months ago when i last tried.
one of the last updates or the new kernel subversion ? 
(using 2.6.24-23-generic now, used 2.6.24-21 before i think)

blender version
Blender 2.45 (sub 0) Build

output when running blender in commandline : 
```
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Segmentation fault
Exit 139

```
i see a window blinking up, but it immediately closes.

glxgears and other 3d apps (nexuiz, ogre samples..) work fine.



hwinfo : 
```
hwinfo --gfxcard
15: PCI 100.0: 0300 VGA compatible controller (VGA)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_10de_405
  Unique ID: VCu0.1pXSbtEeyqC
  Parent ID: vSkL.GplIvOMTy34
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "ASUSTeK VGA compatible controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0405
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x15d2
  Revision: 0xa1
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xfc000000-0xfcffffff (rw,non-prefetchable)
  Memory Range: 0xe0000000-0xefffffff (rw,prefetchable)
  Memory Range: 0xfa000000-0xfbffffff (rw,non-prefetchable)
  I/O Ports: 0xac00-0xac7f (rw)
  Memory Range: 0xfdee0000-0xfdefffff (ro,prefetchable,disabled)
  IRQ: 16 (103160 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd00000405sv00001043sd000015D2bc03sc00i00"
  Driver Info #0:
    Driver Status: nvidia is active
    Driver Activation Cmd: "modprobe nvidia"
  Driver Info #1:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #34 (PCI bridge)

Primary display adapter: #15

```

nvidia drivers installed via envyng
autodetect failed, but selecting  173.14.12 manually worked 

i'm on a laptop with GeForce 9500M

the hardware drivers manager list is empty, and it outputs the following warnings : 
```

sudo kdesu jockey-kde
QImage::smoothScale: Image is a null image
WARNING: modinfo for module nvidia_new failed: modinfo: could not find module nvidia_new


WARNING: modinfo for module nvidia_legacy failed: modinfo: could not find module nvidia_legacy


WARNING: modinfo for module fglrx failed: modinfo: could not find module fglrx


WARNING: modinfo for module wl failed: modinfo: could not find module wl

```

please help =)

is there a way to get a stacktrace or more detailed info on why/how it crashes ?

i'm going to try booting with the old kernel versions and if that doesn't work
 installing the 2.48a version from [http://www.blender.org/download/get-blender/](http://www.blender.org/download/get-blender/)  later this evening.

UPDATE : older kernel didn't help, but the new blender 2.48a doesn't crash, so the problem is solved for me =)

---

### Post by Jaapie on 2009-07-18
I get this error when running compiz. After changing to metacity (metacity --replace) blender runs.

---

