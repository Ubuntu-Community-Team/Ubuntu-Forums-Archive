---
title: "Boinc/Setiathome crashing/ kernel panic"
date: 2009-05-07
forum: General Help
---

### Post by adeodatus on 2009-05-07
I have a box that I really want to run the boinc/seti@home applications on but it keeps crashing. I've had the box for over a year and I built it myself (no trashing me for that one, I'm not horrible at that part). The board is an MSI K9N Neo-F V3. It has 1 GB of RAM and an AMD Athlon 64 X2 (dual core) 4200+. Its been running stable versions of Ubuntu since I built it, starting at 8.04 and currently 9.04. It is stable using it as a typical desktop. However, within a few minutes after starting up my boinc client it kernel panics (X is frozen and keyboard lights are blinking.) I've kill off the desktop startup so now I just boot to the console, which I actually prefer. I have turned on crashdumps and some other debugging stuff but I've yet to get a core or crash dump. Since you all are *nix geeks as well, perhaps some of your knowledge and experience can point me in the right direction. I've ran various kernels/versions of ubuntu and different binaries for boinc and seti on this machine ... all with the same result so far. Once boinc starts up and starts the seit@home applications, its just a matter of time (minutes) before it ends up locked up. Let me show you what I have on it and perhaps some of you can direct or assist me. In this dump, only one of the seti processes has crashed and the system is still running so I have this:

[  507.876007] BUG: unable to handle kernel NULL pointer dereference at 0000000000000000
[  507.876007] IP: [<ffffffff80210d62>] exit_idle+0x2/0x50
<8>[  507.876007] PGD 39930067 PUD 39931067 PMD 0
[  507.876007] Oops: 0000 [#1] SMP
[  507.876007] last sysfs file: /sys/devices/platform/serial8250/tty/ttyS0/uevent
[  507.876007] Dumping ftrace buffer:
[  507.876007]    (ftrace buffer empty)
<8>[  507.876007] CPU 1
<8>[ 507.876007] Modules linked in: binfmt_misc netconsole configfs lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device i2c_nforce2 k8temp snd soundcore snd_page_alloc nvidia(P) pcspkr psmouse serio_raw r8169 mii fbcon tileblit font bitblit softcursor
[  507.876007] Pid: 2737, comm: astropulse-5.03 Tainted: P           2.6.28-11-generic #42-Ubuntu
[  507.876007] RIP: 0010:[<ffffffff80210d62>]  [<ffffffff80210d62>] exit_idle+0x2/0x50
[  507.876007] RSP: 0000:ffff88003f73ff80  EFLAGS: 00010083
[  507.876007] RAX: ffffffff8089a460 RBX: ffffffff80a65180 RCX: 00000000015cd210
[  507.876007] RDX: ffffffff80a6aa90 RSI: 0000000000000000 RDI: ffffffffff5fc0b0
[  507.876007] RBP: ffff88003f73ffa8 R08: 0000000000000006 R09: 0000000000000010
[  507.876007] R10: 00000000015e7ba0 R11: 0000000000000360 R12: ffffffff80a6aa90
[  507.876007] R13: 0000000000000000 R14: 00007f35272c2010 R15: 00000000015cd870
[  507.876007] FS:  00007f3527376700(0000) GS:ffff88003f406900(0000) knlGS:0000000000000000
[  507.876007] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  507.876007] CR2: 0000000000000000 CR3: 000000003e9a5000 CR4: 00000000000006a0
[  507.876007] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  507.876007] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
<8>[  507.876007] Process astropulse-5.03 (pid: 2737, threadinfo ffff880039900000, task ffff88003e9f2cc0)
[  507.876007] Stack:
<8>[  507.876007]  ffffffff8022760d 0000000000000001 0000000000000000 00000000015cd160
[  507.876007]  00007f35272c2014 ffff880039901f80 ffffffff80213668 ffff880039901f80 <EOI>
[  507.876007]  00007f35272c2014 0000000000000360 00000000015e7ba0 0000000000000010
[  507.876007] Call Trace:
[  507.876007]  <IRQ> <0> [<ffffffff8022760d>] ? smp_apic_timer_interrupt+0x4d/0xc0
[  507.876007]  [<ffffffff80213668>] apic_timer_interrupt+0x88/0x90
[ 507.876007] <EOI> <0>Code: 00 00 00 e8 11 fd ff ff 48 8b 4b 20 48 8d 93 a8 00 00 00 48 89 de 31 ff e8 bc 4f 00 00 48 83 c4 08 5b c9 c3 0f 1f 44 00 00 55 65 <48> 8b 04 25 00 00 00 00 8b b0 68 02 00 00 48 89 e5 85 f6 75 10
[  507.876007] RIP  [<ffffffff80210d62>] exit_idle+0x2/0x50
<8>[  507.876007]  RSP <ffff88003f73ff80>
[  507.876007] CR2: 0000000000000000
[  507.876007] ---[ end trace 9a065575ff770bbd ]---

Thanks much for anything you can help me out on. 

--Mark

---

### Post by DeMus on 2009-05-11
Are you running an optimized version, or the normal of the stock software?
My pc does not panic, but I only get computation errors when using the optimized versions.
I'm also trying on the Seti forums to get an answer, but so far nothing worked.
Maybe you have some info for me, please have a look at the thread Set@home on Jaunty in the General forum.
Thanks.

---

