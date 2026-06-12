---
title: "[ubuntu] Radeon HD 7550: unknown device"
date: 2017-02-07
forum: Desktop Environments
---

### Post by mmiat on 2017-02-07
hi
I've HP Elitebook 8470p with ATI Radeon HD7550

```
29: PCI 100.0: 0300 VGA compatible controller (VGA)
  [Created at pci.366]
  Unique ID: VCu0.QctWuGieLU1
  Parent ID: vSkL.DQccioWPun3
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Device Name: "0"
  Model: "ATI Thames [Radeon HD 7550M/7570M/7650M]"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x6841 "Thames [Radeon HD 7550M/7570M/7650M]"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x179d 
  Driver: "radeon"
  Driver Modules: "drm"
  Memory Range: 0xc0000000-0xcfffffff (ro,non-prefetchable)
  Memory Range: 0xd4300000-0xd431ffff (rw,non-prefetchable)
  I/O Ports: 0x4000-0x4fff (rw)
  Memory Range: 0xd4340000-0xd435ffff (ro,non-prefetchable,disabled)
  IRQ: 32 (97420 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d00006841sv0000103Csd0000179Dbc03sc00i00"
  Driver Info #0:
    Driver Status: radeon is active
    Driver Activation Cmd: "modprobe radeon"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)
```

as you can see in the attachment, my system can't see the card
ubuntu 16.04 LTS

thanks

---

### Post by howefield on 2017-02-07
Have a browse here : [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Graphics_and_Display](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Graphics_and_Display)

---

