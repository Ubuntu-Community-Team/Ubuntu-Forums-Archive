---
title: "Emulator for ZX 81 with Joystick support?"
date: 2012-08-04
forum: Emulators
---

### Post by honeybear on 2012-08-04
Hi,

Just curious, any hint regarding which emulator under ubuntu could support well the joysticks/gamepads?

thanks

---

### Post by Grumbel on 2012-08-06
No idea, but you can use tools such as qjoypad, joy2key, etc. to emulate keyboard presses with a joystick, that should work for most emulators.

---

### Post by honeybear on 2012-08-06
> **Grumbel said:**
> No idea, but you can use tools such as qjoypad, joy2key, etc. to emulate keyboard presses with a joystick, that should work for most emulators.

I have a regular gamepad. Well, qjoypad, joy2key,... might work indeed. 

It must be certainly a program that handles the /dev/input/js1 and  /dev/input/js2. Zx81 is a old thing, might be... :confused:  I havent found yet. 


```
$ apt-cache search zx81
z80dasm - disassembler for the Zilog Z80 microprocessor
z88dk - a Z80 processor assembler and SmallC+ cross compiler
```

---

