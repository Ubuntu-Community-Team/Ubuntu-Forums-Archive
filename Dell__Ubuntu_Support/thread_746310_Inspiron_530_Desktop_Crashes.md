---
title: "Inspiron 530 Desktop Crashes"
date: 2008-04-05
forum: Dell  Ubuntu Support
---

### Post by WCD on 2008-04-05
Please help.  I have a new Inspiron 530 that came with Vista.  I installed the bios upgrade, 64-Bit Ubuntu 7.10 and 8GB ram.

I cannot log into my desktop which to me looks like the video card...an Intel Corporation 82G33/G31.  I am able to log into failsafe-gnome but that is it.  There logs are showing a message of no more mtrr's available.  Will a new graphics card solve this?  Additional hardware info below:

uname -a
Linux linux-fs 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

mtrr
reg00: base=0x100000000 (4096MB), size=4096MB: write-back, count=1
reg01: base=0x200000000 (8192MB), size= 512MB: write-back, count=1
reg02: base=0x220000000 (8704MB), size= 256MB: write-back, count=1
reg03: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg04: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg05: base=0xc0000000 (3072MB), size= 256MB: write-back, count=1
reg06: base=0xcf700000 (3319MB), size=   1MB: uncachable, count=1
reg07: base=0xcf800000 (3320MB), size=   8MB: uncachable, count=1

/proc/pci 
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 020d
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ff00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

---

