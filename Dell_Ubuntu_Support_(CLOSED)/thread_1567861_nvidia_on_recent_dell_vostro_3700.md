---
title: "nvidia on recent dell vostro 3700"
date: 2010-09-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rep on 2010-09-04
As reported here :
[http://www.nvnews.net/vbulletin/showthread.php?t=154723](http://www.nvnews.net/vbulletin/showthread.php?t=154723)
I have big problems installing nvidia driver on recent dell vostro 3700
(install is ok but driver won't load)

nvidia bug report :
[nvidia-bug-report.log.gz]("http://314r.free.fr/dellvostro3700/nvidia-bug-report.log.gz")

Other topic on the nvidia forum :
[http://forums.nvidia.com/index.php?showtopic=179637](http://forums.nvidia.com/index.php?showtopic=179637)

Is someone here have some advices on how it can be done ?

As you can see LSPCI see the two cards :
> 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18 )
Subsystem: Dell Device 044f
Flags: bus master, fast devsel, latency 0, IRQ 36
Memory at fa400000 (64-bit, non-prefetchable) [size=4M]
Memory at b0000000 (64-bit, prefetchable) [size=256M]
I/O ports at f080 [size=8]
Capabilities: <access denied>
Kernel driver in use: i915
Kernel modules: i915

01:00.0 VGA compatible controller: nVidia Corporation Device 0a29 (rev a2)
Subsystem: Dell Device 044f
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
Memory at c0000000 (64-bit, prefetchable) [size=256M]
Memory at d0000000 (64-bit, prefetchable) [size=32M]
**I/O ports at e000 [disabled] [size=128]**
Expansion ROM at fa000000 [disabled] [size=512K]
Capabilities: <access denied>
Kernel driver in use: nvidia
Kernel modules: nvidia-current, nvidiafb, nouveau


But only the intel will work.
Is this because I/O ports on the nvidia are [disabled] ??

---

