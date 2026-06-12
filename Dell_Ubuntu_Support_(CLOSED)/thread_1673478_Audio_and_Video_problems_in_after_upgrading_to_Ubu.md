---
title: "Audio and Video problems in after upgrading to Ubuntu 10.10"
date: 2011-01-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tmm786 on 2011-01-22
Hello,

I have been using Ubuntu for the past few distributions, but after upgrading to Ubuntu 10.10 I have had an issue with sound and video.  I first noticed it when trying to watch a video, the picture was jumpy, and the audio was split up and jumpy as well, almost as if it couldn't be processed correctly.  I don't really even know where to begin to troubleshoot this one.  Anybody have any ideas or suggestions?  It would be greatly appreciated.

Thanks,
Tim

---

### Post by mikewhatever on 2011-01-22
You should probably start by posting the hardware specs, also, the output of the **lspci** command would be useful.

---

### Post by tmm786 on 2011-01-22
Output of lspci:

```
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
04:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
04:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller

```Its a Dell Dimension 8400, P4 HT 3.0 GHz processor with 3 GB of ram.  Looks like the sound and video card info is in the output data.  If I can provide anything else, let me know.

Tim

PS: I learned something already, I didn't know about that command...

---

### Post by mikewhatever on 2011-01-22
Thanks for posting the info, it shows exactly what's needed.
There are major problems with Intel's 8xx GPU drivers in both 10.04 and 10.10.
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Some workarounds are suggested in the links above, but those GPUs are probably not going to work well until Intel fixes the drivers.

---

### Post by tmm786 on 2011-01-28
Thanks for the links, I'll be checking those out soon...

---

### Post by jsbiff on 2011-01-29
> **mikewhatever said:**
> Thanks for posting the info, it shows exactly what's needed.
There are major problems with Intel's 8xx GPU drivers in both 10.04 and 10.10.

Now. . . I could be wrong, but from the LSPCI output, it looks like he's using an ATI/AMD Radeon GPU, not an Intel GPU? Probably, the mobo has the onboard video chipset, but wouldn't it be disabled since he has an ATI GPU in the expansion slot?

---

