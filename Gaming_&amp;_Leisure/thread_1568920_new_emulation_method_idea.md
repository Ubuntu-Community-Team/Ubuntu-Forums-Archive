---
title: "new emulation method idea"
date: 2010-09-06
forum: Gaming &amp; Leisure
---

### Post by dan-420 on 2010-09-06
would it be possible to make an emulator that you would need to install like an OS ( making a bootable partition on your hard drive ) since emulators for newer systems like the ps2 or Xbox are slow because they use alot of system resources. if the emulator was a bootable OS ( so to speak ) that would cut resource usage in half because there is no other OS, programs, and system processes in the background that the system would have to worry about. so for example just turn on your pc boot the emulator ( lets say its a ps2 emulator ) pop Metal Gear Solid: 3 in, plug in and configure your game-pad and play as if your pc WAS a ps2.

damn that was alot of typing lol

let me know what you guys think :)

---

### Post by Dukenukemx on 2010-09-06
That's not how emulators work, or how computers work in general.  

You won't boost the speed of any application by cutting out the OS.  What your suggesting isn't possible, except for maybe Xbox 1, as Xbox 1 uses an X86 CPU, like most PCs use.  What few emulators that exist for Xbox 1, try to recreate the environment that the Xbox 1 has, much like Wine does for Linux.  I believe Dxbx or Cxbx does this. 

For most consoles you'll need to emulate the hardware.  PCs use an X86 cpu, but most consoles use MIPS or PowerPC.  Even then, a lot of the hardware is custom made, like the PS2's emotion engine.  

In this day in age, nobody makes an application that doesn't need an OS.  Even back in the DOS days of PC gaming, you still needed to boot up into a OS.  Modern development tools would also rely on the OS.  

In the end, if you want a faster emulator then just wait, or help out the developers.  Any little help you give can go towards optimizing their emulator.  From testing, donations, or even helping out in code if possible.  You also gotta remember that emulator developers would rather work on compatibility first, over speed.  Even PCSX2 is putting compatibility over speed right now.

---

### Post by dan-420 on 2010-09-06
thanks for the info man ;)

---

### Post by weblordpepe on 2010-09-08
Well.

There are emulator OSes out there. Like MAME systems and the like. Linux can be configured to be so small, it might as well be just the emulator.

Also, this is how hypervisors work ...ish. A hypervisor is a tiny operating system which serves only to load up other operating systems. The operating systems are all emulated. The 'emulation' is handled by special hardware in the CPU designed for emulation. The 'emulated' operating system is still touching bare metal, but its under control of the master operating system, the hypervisor. But these are all the same type of CPU. i dont know enough about emulating other types of cpus. basically the dude above is correct, but just do a search for emulator based linux distros.

oh and hail to the king baby

---

### Post by TheBuzzSaw on 2010-09-08
There is still some credibility to this idea, but I would run the other direction with it: create a kind of ROM compiler. Rather than try to shrink the operating system to a mechanism designed to run these ROMs, find a way to translate the ROM data into a semi-executable file.

---

### Post by del_diablo on 2010-09-08
Ain't the current emulation buzz that the application is run native after translating?

---

### Post by TheBuzzSaw on 2010-09-09
> **del_diablo said:**
> Ain't the current emulation buzz that the application is run native after translating?

I believe that buzz was around WINE running Windows code natively. I'm not familiar with actual emulators translating to native code. An emulator JIT compiler would be friggin epic.

---

