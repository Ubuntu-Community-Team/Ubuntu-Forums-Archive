---
title: "Garbled characters 'l'"
date: 2015-02-24
forum: Desktop Environments
---

### Post by bmvakili on 2015-02-24
Hi the 'l' character's messed up; that is, the lowercase 'L' character. Please see attached screenshot for what I mean.

It's not messed up everywhere; for example, on webpages it's fine; though sytem portion of window's garbled.

Here are some details about system:
```

$ uname -a
Linux mali2 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

```

$ sudo lspci -v  | grep -A 16  'VGA\|Display'
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: CLEVO/KAPOK Computer Device 5105
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

...

--
01:00.0 VGA compatible controller: NVIDIA Corporation GK104M [GeForce GTX 670MX] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: CLEVO/KAPOK Computer Device 5105
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    Kernel driver in use: nouveau
```


I don't know what you need to help with this; so let me know if you need more info.
I'm sure if I restart it'll work again; but this is not the first time it's happened; and it's becoming quite irritating.

Thank you for your help in advance gurus.

---

