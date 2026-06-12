---
title: "Every games I have crash once in a while..."
date: 2006-09-19
forum: Gaming &amp; Leisure
---

### Post by DarkAngel88 on 2006-09-19
Hi there,

I have a problem with a couple of games that I managed to install on my laptop.  I'm running Doomsday, UT99 GOTY and Quake III.  Everything is fine (sound, decent graphics) but once in a while, the game just plain crash !  

This is the message I get when it crashes : 

```
Login: DarkAngel88
Possessed PlayerPawn: TMale2 Entry.TMale1
Creating root window: UMenu.UMenuRootWindow
ut-bin: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down
Allocation checking disabled

```

I'm running Ubuntu 6.06-1 using aiglx.  (Tried running my games from metacity without success).  I'm also running kernel 2.6.15-26-686.
The videocard is an intel card and I know that it's running good since I don't have any problems with aiglx and I get decent framerate in the games.

So... if anyone have a clue about this problem.. I would be very gratefull !

Thank you in advance !

---

### Post by fatsheep on 2006-09-20
Make sure you have the latest drivers for your graphics card, that would be my only advice.

---

