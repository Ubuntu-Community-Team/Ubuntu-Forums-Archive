---
title: "X crash - Intel 945 chipset"
date: 2008-12-10
forum: General Help
---

### Post by markwren on 2008-12-10
Have been using Ubuntu since Hoary. Recently did a fresh install of 8.04 on my Thinkpad R60e with an Intel 945 graphics chipset, 1.6G Celeron chip and 1.5G RAM. Then I upgraded to 8.10 with no problems. Have done no config changes at all (to compiz, X or anything else) just a standard install. 

But 3 times now X has crashed and will not recover, or allow access to an ASCII session off Alt-F2, etc, requiring reboot off the power button. Never had this sort of problem with previous releases.

Both times it was while I was running "Freecell Solitaire" with a hefty set of Firefox 3 tabs also running. A common setup when I am bored!

/var/log/messages has:
Dec 10 21:18:45 mark-laptop kernel: [273311.882731] __ratelimit: 485 callbacks suppressed
Dec 10 21:18:45 mark-laptop kernel: [273311.882740] Xorg[5738]: segfault at 7665755f ip b7acd208 sp bf860a60 error 6 in intel_drv.so[b7ab5000+58000]
Dec 10 21:18:52 mark-laptop kernel: [273318.215831] Xorg[31105]: segfault at 7665755f ip b7a77208 sp bf80bfe0 error 6 in intel_drv.so[b7a5f000+58000]
Dec 10 21:18:59 mark-laptop kernel: [273325.202514] Xorg[31126]: segfault at 7665755f ip b7b2f208 sp bfec2a90 error 6 in intel_drv.so[b7b17000+58000]
Dec 10 21:19:06 mark-laptop kernel: [273332.219886] Xorg[31148]: segfault at 7665755f ip b7a05208 sp bfe9aa60 error 6 in intel_drv.so[b79ed000+58000]
Dec 10 21:19:07 mark-laptop kernel: [273333.915339] mtrr: base(0xd0000000) is not aligned on a size(0x7b0000) boundary

Sounds like an Intel driver bug ...

Anyone else had similar issues?

---

### Post by newacct on 2009-01-03
Dear Sir,
Yeah, I am having a similar problem. I also have Intel 945 chipset in my Gateway MX6927 laptop. About every 2 days (it's pretty regular), X crashes. It looks like X tries to recover a few times, but fails. Sometimes I see the initial "X" cursor when it tries to recover, but then after a second it gets frozen in a pattern of weird colored lines. Ctrl-Alt-F1, etc. and Ctrl-Alt-Backspace don't work. The only thing that seems to do anything is I am able to press the power button and most of the time it will indeed shut down (the shut down screen though is messed up and looks like it was displayed with the wrong horizontal resolution). This regular crashing pattern happened after I installed 8.10 Intrepid. I did not have this problem on 8.04 Hardy. I have re-installed 8.10 but the problem persists without change.

Have you gotten any progress fixing this problem since you posted? If you have any solutions I would really appreciate it.

If it would help, the following is my /var/log/messages (the second to last line kinda scares me: "BIOS not found"):
```
Dec 31 02:34:31 stupid kernel: [87077.336197] Xorg[5291]: segfault at 14 ip b7b3cce0 sp bff59410 error 4 in libdri.so[b7b38000+8000]
Dec 31 02:34:42 stupid kernel: [87088.111888] Xorg[17466]: segfault at 1 ip b7b12d64 sp bf934d70 error 4 in libdri.so[b7b0f000+8000]
Dec 31 02:34:54 stupid kernel: [87100.503192] Xorg[17495]: segfault at 1 ip b7a09d64 sp bf829f70 error 4 in libdri.so[b7a06000+8000]
Dec 31 02:34:56 stupid kernel: [87102.115421] apm: BIOS not found.
Dec 31 02:34:58 stupid kernel: [87104.276127] ip6_tables: (C) 2000-2006 Netfilter Core Team
```

Here is the end of my Xorg.log:
```
Error in I830WaitLpRing(), timeout for 2 seconds
pgetbl_ctl: 0x3ffc0001 getbl_err: 0x00000000
ipeir: 0x00000000 iphdr: 0x54f00006
LP ring tail: 0x00000100 head: 0x0001cad4 len: 0x0001f001 start 0x00000000
eir: 0x0000 esr: 0x0001 emr: 0xffff
instdone: 0xfa41 instpm: 0x0000
memmode: 0x00000306 instps: 0x800f04d1
hwstam: 0xfffe ier: 0x0002 imr: 0x0000 iir: 0x0070
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring at virtual 0xa774c000 head 0x1cad4 tail 0x100 count 3467
Ring end
space: 117196 wanted 131064
(II) intel(0): [drm] removed 1 reserved context for kernel
(II) intel(0): [drm] unmapping 8192 bytes of SAREA 0xf8cdf000 at 0xb7f03000
(II) intel(0): [drm] Closed DRM master.

Fatal server error:
lockup

(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) HID 413c:3010: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) AIGLX: Suspending AIGLX clients for VT switch

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb7f2b400]
2: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb799cb50]
3: /usr/X11R6/bin/X [0x80d6b0a]
4: /usr/lib/xorg/modules/extensions//libglx.so [0xb7a59be9]
5: /usr/X11R6/bin/X(AbortDDX+0x79) [0x80a8b09]
6: /usr/X11R6/bin/X(AbortServer+0x28) [0x813c498]
7: /usr/X11R6/bin/X(FatalError+0x63) [0x813caa3]
8: /usr/lib/xorg/modules/drivers//intel_drv.so(I830WaitLpRing+0x201) [0xb79911d1]
9: /usr/lib/xorg/modules/drivers//intel_drv.so(I830Sync+0x1c3) [0xb79915e3]
10: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb79b97ea]
11: /usr/lib/xorg/modules//libexa.so(exaWaitSync+0x65) [0xb786b045]
12: /usr/lib/xorg/modules/drivers//intel_drv.so(i830WaitSync+0xaf) [0xb799ce9f]
13: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb7996cf4]
14: /usr/X11R6/bin/X(xf86CrtcSetMode+0x13b) [0x80eaf8b]
15: /usr/lib/xorg/modules/drivers//intel_drv.so(i830GetLoadDetectPipe+0x15d) [0xb7997a1d]
16: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb79b320d]
17: /usr/X11R6/bin/X(xf86ProbeOutputModes+0x1a0) [0x80eb9f0]
18: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb799a598]
19: /usr/X11R6/bin/X [0x812df67]
20: /usr/X11R6/bin/X(WaitForSomething+0x5cf) [0x812e63f]
21: /usr/X11R6/bin/X(Dispatch+0x7e) [0x808c5ce]
22: /usr/X11R6/bin/X(main+0x47d) [0x8071d1d]
23: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b31685]
24: /usr/X11R6/bin/X [0x8071101]
Saw signal 11.  Server aborting.
(II) AIGLX: Suspending AIGLX clients for VT switch
```

---

### Post by noworry on 2009-03-04
I am also having the same problem. X crashed unexpectedly and I had to reboot my laptop. The same errors as in the previous message.

The frequency of crash was thrice in the last month.
I am unable to reproduce the issue.

Can somebody help ?

---

### Post by zaicic on 2009-04-11
Hi,

I think that's related with this bug

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/351187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/351187)

---

