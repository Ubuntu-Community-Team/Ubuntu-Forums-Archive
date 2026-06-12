---
title: "Dell D620 and IrDA"
date: 2007-06-09
forum: Dell  Ubuntu Support
---

### Post by FerhatBingol on 2007-06-09
hi,

I am trying to make my IrDA device work which is on D620.

It is a SMC IrCC.

I had some search on the forums and found that it might work if I can switch from Fast IrDA (FIR) to Standard IrDA (SIR). Some Dell computer BIOS allows users to change this, but mine does not, which is A08.

I tried to see if the hardware is totally death or not as below; I think it is there but I cannot make it work so far.

[B][COLOR="DarkGreen"]root@lp:~# dmesg | grep -i tty
[    1.435144] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.435305] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.435845] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.470974]   hash matches device ttyed
[   36.180000] sirdev_get_instance - ttyS0
[   36.180000] irtty_open - ttyS0: irda line discipline opened[/COLOR][/B]


**[COLOR="DarkGreen"]irattach /dev/ttyS0 -s[/COLOR]**

Ihad started irdadump and point my smartPhone to the on board IrDA.
**[COLOR="DarkGreen"]irdadump[/COLOR]**

What I have got is...
[B][COLOR="DarkGreen"]21:14:43.232525 xid:cmd 6c3112a7 > ffffffff S=6 s=0 (14)
21:14:43.320521 xid:cmd 6c3112a7 > ffffffff S=6 s=1 (14)
21:14:43.408521 xid:cmd 6c3112a7 > ffffffff S=6 s=2 (14)
21:14:43.496494 xid:cmd 6c3112a7 > ffffffff S=6 s=3 (14)
21:14:43.584522 xid:cmd 6c3112a7 > ffffffff S=6 s=4 (14)
21:14:43.672521 xid:cmd 6c3112a7 > ffffffff S=6 s=5 (14)
21:14:43.756528 xid:rsp 6c3112a7 < 00011cce S=6 s=5 SmartPhone hint=9224 [ PDA/Palmtop Modem IrCOMM IrOBEX ] (27)
21:14:43.760536 xid:cmd 6c3112a7 > ffffffff S=6 s=* lp-10894 hint=0400 [ Computer ] (24)[/COLOR][/B]


Maybe you also would like to know what I wanna do. I am trying to run LIRC and remote control some applications.

Any idea what to do?

cheers...

---

