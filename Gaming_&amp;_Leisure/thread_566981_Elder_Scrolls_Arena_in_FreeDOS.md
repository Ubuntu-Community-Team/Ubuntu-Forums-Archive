---
title: "Elder Scrolls: Arena in FreeDOS"
date: 2007-10-04
forum: Gaming &amp; Leisure
---

### Post by Githlar on 2007-10-04
This is mainly a copy of another thread I saw in this forum haha.

OK, I'm trying to run Elder Scrolls: Arena - an old DOS game in FreeDOS. I have my disk and GRUB all configured and FreeDOS boots and I can run the game. Well, kind of.

When I start the game, I get the error:
Not enough EMS...

I did a little research, and, from what I understand, EMS is extended memory beyond the 400k that DOS can access? I also understand that EMM386 is the program that manages this extra memory. I looked up the requirements of the game, and it tells me I need 4M of memory.

So, I need to edit C:\fdconfig.sys, right? I'd change:
2?DEVICE=C:\FDOS\BIN\EMM386.EXE X=TEST
to
2?DEVICE=C:\FDOS\BIN\EMM386.EXE EMM=4500 X=TEST
(4500 just to be safe)

But, I tried that and it still tells me "Not enough EMS..."

Could somebody tell me where I'm going wrong here?

I really want to get it working in FreeDOS, as all the emulators I've tried either don't work (Qemu booted straight from the hard drive) or are slow (DOSBox).

---

### Post by dmn_clown on 2007-10-04
> **Githlar said:**
> or are slow (DOSBox).

Increase your CPU cycles and it will run fine.

---

### Post by Githlar on 2007-10-04
I assume you mean the CPU cycles in Dosbox. I tried that and I would still rather play it full-speed in DOS. From what I've read, games perform much better in the actual environment than an emulated one.

Due to the fact that the emulator is emulating a CPU it can never run at full speed. And, unfortunately for me, I can never get this particular game to run full-speed in Dosbox, no matter the CPU cycles. It doesn't help that I've got no video card and only up to 8MB to share for video.

---

### Post by Zylar on 2007-10-04
Ha, I remember getting TES:Arena to run originally, way back when.  Still got the original cd too.  It's a royal PITA!  Needs every bit of free ram available.  I remember having to do a bunch of LOADHIGH and and other stuff in my config.sys, to get the 639k of conventional ram it needs.  

All I can say is good luck, I haven't actually tried to get it to work in years.

---

### Post by Githlar on 2007-10-04
I just need to find a way to get more EMS in FreeDOS. I'd think it'd be fairly simple, but I don't really have any experience with DOS. We used DOS when I was very young, but before I was even interested in computers, so I never really messed with it.

---

