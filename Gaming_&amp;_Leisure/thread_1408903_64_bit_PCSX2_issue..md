---
title: "64 bit PCSX2 issue."
date: 2010-02-17
forum: Gaming &amp; Leisure
---

### Post by murderslastcrow on 2010-02-17
"GS plugin failed to open. Error code: 1"

This is the error message I receive when running both PCSX2 0.9.6 and the PCSX2 0.9.7 beta.

I have installed all of the required dependencies, and even installed the 32 bit packages recommended in another thread (ia32-libs-pcsx2.deb). In fact, when I choose the null graphics driver I can hear the PS2 bios perfectly fine, so everything else seems to be working great.

I've also tested the ZZOGL plugin for graphics. Anyone know what might be up? Anyone gotten this emulator to run successfully in Linux?

By the way, lspci states this is my video card.

> 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400

I have a dual core computer, Dell Inspiron E1505 to be precise. It should be able to run at least poorly. XD

The only proprietary drivers I've installed are for my Broadcom wireless card, nothing else appears under Hardware Drivers.

---

### Post by murderslastcrow on 2010-02-17
*Lil' bump*

I've put a lot of work into this. I'm even willing to learn how to create deb and rpm packages to assist in making whatever specific changes needed available easily to the community so we can do this automatically.

I just need some assistance from people who might know a lot about this already.

---

### Post by murderslastcrow on 2010-02-19
I don't wanna' install Windows just to get this stuff working. It's ridiculous. :\ I guess I'll just have to figure it all out myself. Crikey.

---

### Post by COden6484 on 2010-02-20
PCSX2 doesn't work on 64-bit installs anymore.  I tried for a week with different versions, but came to the conclusion you need a 32-bit install to use it.  The PCSX2 forums say you should be able to run it in a 32-bit chroot, but I just gave up.

---

### Post by caibbor on 2010-03-23
I'm on a [SIZE=5]32 bit [/SIZE]system and I'm getting the exact same error.

```

Savestate version: 8b410001
x86Init:
        CPU vendor name =  GenuineIntel
        FamilyID  =  6
        x86Family =  Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
        CPU speed =  2.260 ghz
        Cores     =  2 physical [2 logical]
        x86PType  =  Standard OEM
        x86Flags  =  bfebfbff 0008e3fd
        x86EFlags =  20100000

Features:
        Detected MMX
        Detected SSE
        Detected SSE2
        Detected SSE3
        Detected SSSE3
        Detected SSE4.1
        Not Detected SSE4.2

Loading plugins...
Plugins loaded successfully.
Resetting...
Ready
Initializing plugins...
Plugins initialized successfully.
detected blocksize = 2352
isoOpen: /mnt/dat/iso/silenthill.iso ok
offset = 0
blockofs = 0
blocksize = 2352
blocks = 262110
type = 1
 * CDVD Disk Open: CD, 1 tracks (1 to 1):
 * * Track 1: Data (Mode 1) (262110 sectors)
Bios Version 2.0
Bios Warning > rom2 not found.
Bios Warning > erom not found.
Framelimiter rate updated (UpdateVSyncRate): 59.94 fps
Opening Plugins...
ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.4
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
GS plugin failed to open. Error code: 1

```

---

### Post by caibbor on 2010-03-23
solved my issue. I switched from ZeroGS to the zzogl plugin. google it.

(ps, I'm on gentoo, not ubuntu.)

---

