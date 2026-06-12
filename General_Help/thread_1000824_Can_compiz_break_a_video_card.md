---
title: "Can compiz break a video card ??"
date: 2008-12-03
forum: General Help
---

### Post by jonj on 2008-12-03
Hi All,

Before I file a bug I though I'd get some opinions on whether compiz could actually inflict permanent damage to a video card, or whether the card was probably broken anyway.

The background is this: I have an ati radeon x600 card and was able to run compiz in Hardy Heron ok.  I installed Suse 11 to see what it was like and within about 10 minutes of enabling compiz the screen freezes horribly and the box crashes. Ok, so back to ubuntu, compiz is fine when I use it.  Eventually I upgrade to Intrepid Ibex.    Everything's fine until I try out compiz - about 10 minutes and it crashes horribly.  I reboot the machine and this time the graphics are all messed up, even for the bios screen. I've taken out the X600 card as it's definitely broken. 

The hardware failure was related to the compiz crash, the question is which was the cause and which was the effect?  Since those kind of crashes only ever happened when I used compiz (90% of time I don't use it) I wonder if compiz was actually the cause.

The log dump went like this:

```
Dec  3 13:27:07 sej21 kernel: [ 8772.612174] [fglrx] ASIC hang happens.
Dec  3 13:27:07 sej21 kernel: [ 8772.612188] Pid: 7441, comm: Xorg Tainted: P          2.6.27-7-generic #1
Dec  3 13:27:07 sej21 kernel: [ 8772.612192] 
Dec  3 13:27:07 sej21 kernel: [ 8772.612193] Call Trace:
Dec  3 13:27:07 sej21 kernel: [ 8772.612293]  [<ffffffffa03377e4>] ? _ZN4Asic18isTimeStampExpiredE14_LARGE_INTEGERj+0x64/0x100 [fglrx]
Dec  3 13:27:07 sej21 kernel: [ 8772.612346]  [<ffffffffa02b0cfe>] KCL_dump_stack+0xe/0x10 [fglrx]
Dec  3 13:27:07 sej21 kernel: [ 8772.612392]  [<ffffffffa02c378c>] firegl_hardwareHangRecovery+0x1c/0x50 [fglrx]
Dec  3 13:27:07 sej21 kernel: [ 8772.612470]  [<ffffffffa03379d9>] ? _ZN4Asic9WaitUntil15ResetASICIfHungEv+0x9/0x10 [fglrx]
Dec  3 13:27:07 sej21 kernel: [ 8772.612547]  [<ffffffffa033798c>] ? _ZN4Asic9WaitUntil15WaitForCompleteEv+0x6c/0xb0 [fglrx]
Dec  3 13:27:07 sej21 kernel: [ 8772.612624]  [<ffffffffa0336a24>] ? _ZN4Asic19PM4ElapsedTimeStampERK23PM4_TS_INTERRUPT_PARAMSj14_LARGE_INTEGER+0x134/0x1c0 [fglrx]
Dec  3 13:27:07 sej21 kernel: [ 8772.612704]  [<ffffffffa0329a52>] ? _Z19uQSTimeStampRetiredmjj14_LARGE_INTEGER+0xd2/0xe0 [fglrx]
Dec  3 13:27:07 sej21 kernel: [ 8772.612777]  [<ffffffffa0325a38>] ? _Z8uCWDDEQCmjjPvjS_+0x378/0x1040 [fglrx]
Dec  3 13:27:07 sej21 kernel: [ 8772.612833]  [<ffffffffa02dd6e8>] ? firegl_cmmqs_CWDDE_32+0x368/0x410 [fglrx]
Dec  3 13:27:07 sej21 kernel: [ 8772.612884]  [<ffffffffa02dc2e3>] ? firegl_cmmqs_CWDDE32+0x73/0x110 [fglrx]
Dec  3 13:27:07 sej21 kernel: [ 8772.612896]  [<ffffffff80386251>] ? apparmor_capable+0x21/0x70
Dec  3 13:27:07 sej21 kernel: [ 8772.612946]  [<ffffffffa02dc270>] ? firegl_cmmqs_CWDDE32+0x0/0x110 [fglrx]
Dec  3 13:27:07 sej21 kernel: [ 8772.612990]  [<ffffffffa02bf40d>] ? firegl_ioctl+0x1ed/0x260 [fglrx]
Dec  3 13:27:07 sej21 kernel: [ 8772.613036]  [<ffffffffa02b4d16>] ? ip_firegl_ioctl+0x16/0x20 [fglrx]
Dec  3 13:27:07 sej21 kernel: [ 8772.613041]  [<ffffffff802f85d5>] ? vfs_ioctl+0x85/0xb0
Dec  3 13:27:07 sej21 kernel: [ 8772.613046]  [<ffffffff805005b4>] ? thread_return+0x37/0x3c3
Dec  3 13:27:07 sej21 kernel: [ 8772.613050]  [<ffffffff802f8883>] ? do_vfs_ioctl+0x283/0x2f0
Dec  3 13:27:07 sej21 kernel: [ 8772.613054]  [<ffffffff802f8991>] ? sys_ioctl+0xa1/0xb0
Dec  3 13:27:07 sej21 kernel: [ 8772.613059]  [<ffffffff8021285a>] ? system_call_fastpath+0x16/0x1b
Dec  3 13:27:07 sej21 kernel: [ 8772.613062] 
Dec  3 13:27:07 sej21 kernel: [ 8772.613067] pubdev:0xffffffffa04a92e0, num of device:1 , name:fglrx, major 8, minor 54. 
Dec  3 13:27:07 sej21 kernel: [ 8772.613070] device 0 : 0xffff8800ba0e0000 .
Dec  3 13:27:07 sej21 kernel: [ 8772.613074] Asic ID:0x5b62, revision:0x4, MMIOReg:0xffffc200010a0000.
Dec  3 13:27:07 sej21 kernel: [ 8772.613077] FB phys addr: 0xe0000000, MC :0xc0000000, Total FB size :0x8000000.
Dec  3 13:27:07 sej21 kernel: [ 8772.613081] gart table MC:0xc7fbb000, Physical:0xe7fbb000, size:0x44000.
Dec  3 13:27:07 sej21 kernel: [ 8772.613085] mc_node :MC_NODE__FB, total 1 zones
Dec  3 13:27:07 sej21 kernel: [ 8772.613088]     MC start:0xc0000000, Physical:0xe0000000, size:0x8000000.
Dec  3 13:27:07 sej21 kernel: [ 8772.613092]     Mapped heap -- Offset:0x0, size:0x7fbb000, reference count:5, mapping count:0,
Dec  3 13:27:07 sej21 kernel: [ 8772.613096]     Mapped heap -- Offset:0x0, size:0x40000, reference count:1, mapping count:0,
Dec  3 13:27:07 sej21 kernel: [ 8772.613100]     Mapped heap -- Offset:0x7fbb000, size:0x44000, reference count:1, mapping count:0,
Dec  3 13:27:07 sej21 kernel: [ 8772.613104]     Mapped heap -- Offset:0x7fff000, size:0x1000, reference count:1, mapping count:0,
Dec  3 13:27:07 sej21 kernel: [ 8772.613107] mc_node :MC_NODE__GART_USWC, total 2 zones
Dec  3 13:27:07 sej21 kernel: [ 8772.613110]     MC start:0xcd0c0000, Physical:0x0, size:0xbf40000.
Dec  3 13:27:07 sej21 kernel: [ 8772.613114]     Mapped heap -- Offset:0x3800000, size:0x800000, reference count:1, mapping count:0,
Dec  3 13:27:07 sej21 kernel: [ 8772.613118]     Mapped heap -- Offset:0x3000000, size:0x800000, reference count:1, mapping count:0,
Dec  3 13:27:07 sej21 kernel: [ 8772.613122]     Mapped heap -- Offset:0x2800000, size:0x800000, reference count:1, mapping count:0,
Dec  3 13:27:07 sej21 kernel: [ 8772.613126]     Mapped heap -- Offset:0x2000000, size:0x800000, reference count:1, mapping count:0,
Dec  3 13:27:07 sej21 kernel: [ 8772.613130]     Mapped heap -- Offset:0x0, size:0x2000000, reference count:9, mapping count:0,
Dec  3 13:27:07 sej21 kernel: [ 8772.613133] mc_node :MC_NODE__GART_CACHEABLE, total 3 zones
Dec  3 13:27:07 sej21 kernel: [ 8772.613136]     MC start:0xc8400000, Physical:0x0, size:0x4cc0000.
Dec  3 13:27:07 sej21 kernel: [ 8772.613140]     Mapped heap -- Offset:0x0, size:0x200000, reference count:3, mapping count:0,
Dec  3 13:27:07 sej21 kernel: [ 8772.613143] Dump the trace queue.
Dec  3 13:27:07 sej21 kernel: [ 8772.613146] End of dump
```

thanks for any input!

---

### Post by iponeverything on 2008-12-03
It might have been like a big-mac for someone that was already close to heart attack. Your card may have been on its way out anyway and all it needed was little push.

---

