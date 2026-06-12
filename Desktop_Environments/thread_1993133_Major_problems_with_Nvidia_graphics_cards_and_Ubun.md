---
title: "Major problems with Nvidia graphics cards and Ubuntu 12.04"
date: 2012-06-01
forum: Desktop Environments
---

### Post by birdzhavefangs on 2012-06-01
I'm trying to install Ubuntu 12.04 on 4 machines, none of which are recognizing the Nvidia graphics cards.  I've tried installing the proprietary versions of the drivers from the "additional drivers" in system settings and also this [http://askubuntu.com/questions/136045/ubuntu-12-04-wont-recognize-my-graphics-driver](http://askubuntu.com/questions/136045/ubuntu-12-04-wont-recognize-my-graphics-driver) 

Neither of which got any of the systems to recognize the graphics cards.  Here is the output suggested in this post [http://ubuntuforums.org/showpost.php?p=11949675&postcount=26](http://ubuntuforums.org/showpost.php?p=11949675&postcount=26)

```
lspci -nnk | grep -i VGA
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF100 [Tesla C2050 / C2070] [10de:06d1] (rev a3)
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF100 [Tesla C2050 / C2070] [10de:06d1] (rev a3)
07:01.0 VGA compatible controller [0300]: Matrox Graphics, Inc. MGA G200eW WPCM450 [102b:0532] (rev 0a)
83:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF100 [Tesla C2050 / C2070] [10de:06d1] (rev a3)
84:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF100 [Tesla C2050 / C2070] [10de:06d1] (rev a3)

apt-cache policy nvidia-current
nvidia-current:
  Installed: (none)
  Candidate: 295.53-0ubuntu1~precise~xup1
  Version table:
     295.53-0ubuntu1~precise~xup1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main amd64 Packages
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages

sudo lsmod | grep -i nv 
nvidia              12344812  0 

sudo modinfo nvidia
ERROR: modinfo: could not find module nvidia

sudo hwinfo --gfxcard
> hal.1: read hal dataprocess 5083: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
42: PCI 200.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  Unique ID: B35A.zwJu6lqnnE5
  Parent ID: 3hqH.cVcQD+7+A_4
  SysFS ID: /devices/pci0000:00/0000:00:03.0/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: graphics card
  Model: "nVidia VGA compatible controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x06d1 
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0x0771 
  Revision: 0xa3
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xf6000000-0xf7ffffff (rw,non-prefetchable)
  Memory Range: 0xd4000000-0xd7ffffff (ro,non-prefetchable)
  Memory Range: 0xd0000000-0xd3ffffff (ro,non-prefetchable)
  I/O Ports: 0x9c00-0x9c7f (rw)
  Memory Range: 0xf5f80000-0xf5ffffff (ro,non-prefetchable,disabled)
  IRQ: 16 (no events)
  Module Alias: "pci:v000010DEd000006D1sv000010DEsd00000771bc03sc00i00"
  Driver Info #0:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Driver Info #1:
    Driver Status: nouveau is not active
    Driver Activation Cmd: "modprobe nouveau"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #10 (PCI bridge)

44: PCI 300.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  Unique ID: svHJ.zwJu6lqnnE5
  Parent ID: M71A.g9OQ8HcpHW6
  SysFS ID: /devices/pci0000:00/0000:00:07.0/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: graphics card
  Model: "nVidia VGA compatible controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x06d1 
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0x0771 
  Revision: 0xa3
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xf8000000-0xf9ffffff (rw,non-prefetchable)
  Memory Range: 0xdc000000-0xdfffffff (ro,non-prefetchable)
  Memory Range: 0xd8000000-0xdbffffff (ro,non-prefetchable)
  I/O Ports: 0xac00-0xac7f (rw)
  Memory Range: 0xfad80000-0xfadfffff (ro,non-prefetchable,disabled)
  IRQ: 16 (no events)
  Module Alias: "pci:v000010DEd000006D1sv000010DEsd00000771bc03sc00i00"
  Driver Info #0:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Driver Info #1:
    Driver Status: nouveau is not active
    Driver Activation Cmd: "modprobe nouveau"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #11 (PCI bridge)

48: PCI 701.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  Unique ID: fR8M.TQIpfKa0X8E
  Parent ID: 6NW+.9zV1OSrHdy7
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:07:01.0
  SysFS BusID: 0000:07:01.0
  Hardware Class: graphics card
  Model: "Matrox MGA G200eW WPCM450"
  Vendor: pci 0x102b "Matrox Graphics, Inc."
  Device: pci 0x0532 "MGA G200eW WPCM450"
  SubVendor: pci 0x15d9 "Super Micro Computer Inc"
  SubDevice: pci 0x0606 
  Revision: 0x0a
  Memory Range: 0xf4000000-0xf4ffffff (ro,non-prefetchable)
  Memory Range: 0xfbefc000-0xfbefffff (rw,non-prefetchable)
  Memory Range: 0xfb000000-0xfb7fffff (rw,non-prefetchable)
  IRQ: 15 (no events)
  Module Alias: "pci:v0000102Bd00000532sv000015D9sd00000606bc03sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #37 (PCI bridge)

66: PCI 8300.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  Unique ID: Cyr+.zwJu6lqnnE5
  Parent ID: OjO_.tB1A+Ktctx1
  SysFS ID: /devices/pci0000:80/0000:80:03.0/0000:83:00.0
  SysFS BusID: 0000:83:00.0
  Hardware Class: graphics card
  Model: "nVidia VGA compatible controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x06d1 
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0x0771 
  Revision: 0xa3
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xca000000-0xcbffffff (rw,non-prefetchable)
  Memory Range: 0xbc000000-0xbfffffff (ro,non-prefetchable)
  Memory Range: 0xb8000000-0xbbffffff (ro,non-prefetchable)
  I/O Ports: 0xdc00-0xdc7f (rw)
  Memory Range: 0xcde80000-0xcdefffff (ro,non-prefetchable,disabled)
  IRQ: 16 (no events)
  Module Alias: "pci:v000010DEd000006D1sv000010DEsd00000771bc03sc00i00"
  Driver Info #0:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Driver Info #1:
    Driver Status: nouveau is not active
    Driver Activation Cmd: "modprobe nouveau"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #51 (PCI bridge)

68: PCI 8400.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  Unique ID: to29.zwJu6lqnnE5
  Parent ID: i9bs.xro9wcLR_T3
  SysFS ID: /devices/pci0000:80/0000:80:07.0/0000:84:00.0
  SysFS BusID: 0000:84:00.0
  Hardware Class: graphics card
  Model: "nVidia VGA compatible controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x06d1 
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0x0771 
  Revision: 0xa3
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xce000000-0xcfffffff (rw,non-prefetchable)
  Memory Range: 0xc4000000-0xc7ffffff (ro,non-prefetchable)
  Memory Range: 0xc0000000-0xc3ffffff (ro,non-prefetchable)
  I/O Ports: 0xec00-0xec7f (rw)
  Memory Range: 0xcdf80000-0xcdffffff (ro,non-prefetchable,disabled)
  IRQ: 16 (no events)
  Module Alias: "pci:v000010DEd000006D1sv000010DEsd00000771bc03sc00i00"
  Driver Info #0:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Driver Info #1:
    Driver Status: nouveau is not active
    Driver Activation Cmd: "modprobe nouveau"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #52 (PCI bridge)

Primary display adapter: #42


```

---

