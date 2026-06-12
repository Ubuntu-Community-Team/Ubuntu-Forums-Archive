---
title: "SSD: booting slowly anyway?"
date: 2011-03-02
forum: Desktop Environments
---

### Post by Markus72 on 2011-03-02
Hi folx,

I just installed a OCZ Vertex2 and was a bit disappointed by the boot time (Kubuntu 10.10 64bit).

Honestly speaking, booting itself is fast at least until disk access is concerned but it seems that the system faces some delays which I cannot explain.

Here is a excerpt from my dmesg:

```
[    2.903360] md: raid6 personality registered for level 6
[    2.903362] md: raid5 personality registered for level 5
[    2.903364] md: raid4 personality registered for level 4
[    2.908459] md: raid10 personality registered for level 10
[    7.920675] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    9.363057] udev[479]: starting version 163
[    9.366032] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.470644] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[    9.472175] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[    9.618629] r852 0000:15:00.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
```

As you can see, from line 4 to 5 about 5 seconds are lost and another 1,5 from line 5 to line 6.

Any idea what could be the reason and how to change this?
I'd really like to see booting with full 275MB/s read speed :-))

Thanks in advance
Markus

---

### Post by Markus72 on 2011-03-09
Solution: [http://ubuntuforums.org/showthread.php?t=1703593]("http://ubuntuforums.org/showthread.php?t=1703593")

---

