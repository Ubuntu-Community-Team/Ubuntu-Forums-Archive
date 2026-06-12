---
title: "Mupen64Plus closes"
date: 2008-10-01
forum: Gaming &amp; Leisure
---

### Post by badfish69 on 2008-10-01
I finally got it to open, to recognize my Xbox306 controller. Now, however, when I try to run a rom, it opens up a screen that says "Mupen64Plus Started.." Then Mupen close entirely.

---

### Post by badfish69 on 2008-10-01
I opened Mupen using the terminal and I got this:
```

Compression: Uncompressed
Imagetype: .z64 (native)
Rom size: 67108864 bytes (or 64 Mb or 512 Megabits)
MD5: 00E2920665F2329B95797A7EAABC2390
80 37 12 40
ClockRate = f
Version: 1447
CRC: 30c7ac50 7704072d
Name: CONKER BFD
Manufacturer: Nintendo
Cartridge_ID: 5546
Country: USA
PC = 80001000
EEPROM type: 1
init timer!
memory initialized
[RiceVideo] Disabled SSE processing.
[blight's SDL input plugin]: No rumble supported on N64 joystick #1
[blight's SDL input plugin]: version 0.0.10 initialized.
[RiceVideo] Disabled SSE processing.
[RiceVideo] Found ROM 'CONKER BFD', CRC 50acc7302d070477-45
[RiceVideo] Enabled hacks for game: 'CONKER BFD'
InitExternalTextures
Initializing OpenGL Device Context
(II) Initializing SDL video subsystem...
(II) Getting video info...
(II) Setting video mode 1024x768...
Tungsten Graphics, Inc - Mesa DRI Intel(R) 945G 20061017 : 1.3 Mesa 7.0.3-rc2
[RiceVideo] OpenGL Combiner: Fragment Program
[JttL's SDL Audio plugin] version 1.4 initalizing.
[JttL's SDL Audio plugin] Initializing SDL audio subsystem...
[JttL's SDL Audio plugin] Allocating memory for audio buffer: 65536 bytes.
Starting r4300 emulator
R4300 Core mode: Dynamic Recompiler
R4300 core: starting 64-bit dynamic recompiler at: 0x7fa308481ac0.
Signal number 4 caught:
	errno = 0 (Success)
Illegal instruction

```

---

### Post by badfish69 on 2008-10-01
but when i try to run a different game i get
```

Compression: Uncompressed
Imagetype: .z64 (native)
Rom size: 8388608 bytes (or 8 Mb or 64 Megabits)
MD5: 20B854B239203BAF6C961B850A4A51A2
80 37 12 40
ClockRate = f
Version: 1444
CRC: 635a2bff 8b022326
Name: SUPER MARIO 64
Manufacturer: Nintendo
Cartridge_ID: 4d53
Country: USA
PC = 80246000
EEPROM type: 0
init timer!
memory initialized
[RiceVideo] SSE processing enabled.
[blight's SDL input plugin]: No rumble supported on N64 joystick #1
[blight's SDL input plugin]: version 0.0.10 initialized.
[RiceVideo] SSE processing enabled.
[RiceVideo] Found ROM 'SUPER MARIO 64', CRC ff2b5a632623028b-45
InitExternalTextures
Initializing OpenGL Device Context
(II) Initializing SDL video subsystem...
(II) Getting video info...
(II) Setting video mode 1024x768...
Tungsten Graphics, Inc - Mesa DRI Intel(R) 945G 20061017 : 1.3 Mesa 7.0.3-rc2
[RiceVideo] OpenGL Combiner: Fragment Program
[JttL's SDL Audio plugin] version 1.4 initalizing.
[JttL's SDL Audio plugin] Initializing SDL audio subsystem...
[JttL's SDL Audio plugin] Allocating memory for audio buffer: 65536 bytes.
Starting r4300 emulator
R4300 Core mode: Dynamic Recompiler
R4300 core: starting 64-bit dynamic recompiler at: 0x30fb800.
Signal number 4 caught:
	errno = 0 (Success)

```

with this rom, there's no "illegal instruction"

---

### Post by hessiess on 2008-10-02
what hardwere(cpu/gfx card etc) have you got?

---

### Post by badfish69 on 2008-10-02
It's a stock Gateway GT5408. The processor is an intel E4300. No gfx card that I'm aware of, though I've never needed one for N64 emulation in Vista. I may just do a fresh install of 32-bit ubuntu.

---

### Post by badfish69 on 2008-10-02
I just installed ubuntu 32 bit, and it's all running good, except now I can't get it to recognize blight's input plugin.

---

