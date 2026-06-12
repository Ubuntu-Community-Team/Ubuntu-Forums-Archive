---
title: "mtrr: no MTRR for c0000000,8000000 found (slow 3d, radeon 9600)"
date: 2007-07-23
forum: Desktop Effects &amp; Customization
---

### Post by gmaniac on 2007-07-23
I see this message in the dmesg output
glxgears reports 492.925 FPS ( with compiz-fusion installed)
I think i have slow reponse in 3d
cpu AMD Athlon(tm) XP 2200+ and memory is 512 MB

....

dmesg:

[17871.160380] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17871.160400] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17871.160442] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[17871.436846] [drm] Setting GART location based on new memory map
[17871.436860] [drm] Loading R300 Microcode
[17871.436911] [drm] writeback test succeeded in 1 usecs

[17879.604574] mtrr: no MTRR for c0000000,8000000 found

[17882.040496] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17882.040516] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17882.040558] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[17882.309895] [drm] Setting GART location based on new memory map
[17882.309909] [drm] Loading R300 Microcode
[17882.309959] [drm] writeback test succeeded in 1 usecs

cat /proc/mtrr

reg00: base=0x00000000 ( 0MB), size= 512MB: write-back, count=1
reg01: base=0xe0000000 (3584MB), size= 64MB: write-combining, count=2
reg02: base=0xc0000000 (3072MB), size= 256MB: write-combining, count=2

(is this the correct size= 256MB of my graphics card ?)

lspci

02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (prog-if 00 [VGA])
Subsystem: C.P. Technology Co. Ltd Unknown device 2075
Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
Memory at c0000000 (32-bit, prefetchable) [size=256M]
I/O ports at d000 [size=256]
Memory at e5000000 (32-bit, non-prefetchable) [size=64K]
[virtual] Expansion ROM at e4000000 [disabled] [size=128K]
Capabilities: <access denied>

I have enabled support in the kernel for mtrr

---

### Post by gmaniac on 2007-07-24
Uhmmmm, is it a difficult question or it isn't important for the 3d acceleration
I've read that mtrr could give you 2x performance gains. Is it true ? :confused:
Could anyone direct me to where I could post this question to get an answer?
That would be great. 
Thnx

---

