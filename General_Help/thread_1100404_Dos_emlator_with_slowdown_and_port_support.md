---
title: "Dos emlator with slowdown and port support??"
date: 2009-03-19
forum: General Help
---

### Post by antmenj on 2009-03-19
I'm looking for a dos emulator to run an old program for installing firmware into the E2prom of a device.

So far I'v found dosbox dosn't support the parallel port required to do the programing.  The program fired up fine in dosbox but acted as if the programing cable was unpluged.

The other thing is it needs to slow the output from the port right down so it dosn't over do the write speed of the E2prom.

I'v tryed the software on a P1 75 with win95b and a 486DX66 with dos 6.22 and both where too fast.  I have been able to get it to work well on a 286 with dos 4.01.

Only trouble is 286s are pretty rare these days and I'v been hoping to be able to use an emulator in case the 286 packs it in.

Any ideas?

---

### Post by albandy on 2009-03-19
Create a machine with virtualbox and install DOS in it, with virtualbox you can map usb and serial devices

---

### Post by antmenj on 2009-03-22
Thanks for the reply.

> **albandy said:**
> Create a machine with virtualbox and install DOS in it, with virtualbox you can map usb and serial devices

How about the parallel port?

Also what do you mean by "maping"

The big issue is makeing sure the output from the parallel port is slowwwwww enough.

---

### Post by albandy on 2009-03-22
sorry I was thinking in serial ports, and I have not parallel port so I cannot verify if virtualbox supports it.

Ok, have you tried to modify the parallel port options in the Pentium BIOS? I remember some options like ecp + epp modes, try all.

When I say map a port in virtualbox is like disconnecting the port of the host pc and putting it in the virtualized one.

---

### Post by CatKiller on 2009-03-22
dosemu is quite good. Might be worth a play. DOSBox has a stated objective of making DOS games run, and the devs won't expend any effort in features that aren't specific to that task. I've never done anything like programming a device over a parallel port, but dosemu did let me run an old line-of-business application on Ubuntu with support for the parallel printer. Potentially it might let you control the parallel port hardware directly.

---

