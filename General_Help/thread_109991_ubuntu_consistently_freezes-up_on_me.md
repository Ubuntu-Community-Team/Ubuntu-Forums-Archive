---
title: "ubuntu consistently freezes-up on me"
date: 2005-12-29
forum: General Help
---

### Post by PsycoEwok on 2005-12-29
I've had a hell of a time getting Ubuntu up and running on my computer. =/  I can manage to log in and see the desktop and everything, but Ubuntu has persistently just frozen within 10 minutes of use. And this is on a brand-new installation. (There was one time when I didn't even make it past the log-in screen before it froze)

I've even had problems with the installation itself (I've installed Ubuntu at least 5 times within the past two days now). So far, there's only been 1 time that I've managed to completely install it without it freezing up during the installation. All the other times, it's died while trying to install the packages. I managed to catch an error message during one of the installations just before it froze:

[I]Unable to handle kernel paging request at virtual address 000e00d
printing eip:
c0103bdb
*pde = 00000000
Recursive die() failure, output suppressed
<0>Kernel panic - not syncing: Fatal exception in interrupt[/I]

Not sure if that tells you anything or not, but I thought that maybe it was a memory problem. So I performed the memory test included on the Ubuntu install cd, and it did 3 full passes with no errors. So now I'm just out of ideas, and would really appreciate if you guys could provide any help at all. :|

I've tried installing both the 64-bit and 32-bit versions of Ubuntu. Both produce the same results of Ubuntu hanging randomly. =/

If you need them, I'll post my system specs below:
AMD Athlon 64 2800+
(can't remember the motherboard off the top of my head, but it has the nForce 3 chipset)
1 GB of RAM
ATI Radeon 9500 Pro video card
Sound Blaster Live sound card
umm, can't imagine any of my other components being too important to this discussion.

---

### Post by sciurus on 2005-12-29
Let it run the entire suite of memtest checks overnight.

---

