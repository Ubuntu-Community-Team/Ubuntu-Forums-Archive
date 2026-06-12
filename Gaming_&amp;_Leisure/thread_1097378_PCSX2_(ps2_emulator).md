---
title: "PCSX2 (ps2 emulator)"
date: 2009-03-15
forum: Gaming &amp; Leisure
---

### Post by mikedmor on 2009-03-15
So i have decided to move all my ps2 games onto my os. i have just recently converted over to ubuntu from windows (as in 3 months ago). i am running 9.04 currently and having problems with PCSX2. I have install using a pre-configured .deb and everything runs just fine, all the way till i try to run a ps2 game, then it crashes. does anyone know whats going on?

if there is anything else you need information wise just let me know what it is and how to get it

thanks 

-mike

---

### Post by orlox on 2009-03-16
Maybe you could try running the program from a terminal. The output given when the program crashes (if it gives any) could be of use

---

### Post by mikedmor on 2009-03-16
well here is the out put hope someone can help.

```
** (<unknown>:18698): WARNING **: Couldn't find pixmap file: pcsxAbout.bmp
EE Recompiler data reset
Bios Version 16777215.255



**************
rom1 NOT FOUND
**************





**************
rom2 NOT FOUND
**************





**************
erom NOT FOUND
**************


GIF reset
NTSC
Framelimiter rate updated (UpdateVSyncRate): 60 fps
ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.3
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: Disabling MRT depth writing
ZeroGS: Creating effects
ZeroGS: Creating extra effects
ZeroGS: using accurate shaders
ZeroGS: initialization successful
Using Frame Skipping: Normal
Framelimiter rate updated (cpuExecuteBios): 60 fps
* PCSX2 *: ExecuteBios
/usr/games/pcsx2: line 10: 18698 Segmentation fault      (core dumped) /usr/share/pcsx2/pcsx2
```

---

### Post by hikaricore on 2009-03-16
Might also help if you told us something about your hardware.
Often hardware such as Intel integrated "graphics" chipsets which work well under ***dows
work terribly under Linux due to crappy driver support and reliance on DirectX.
Just one example of a possible problem.

Also did you compile pcsx2 yourself or install it from a package or prebuilt binary?
Is this version compatible with your architecture (x86 or 64bit)?

---

### Post by mikedmor on 2009-03-16
i installed it from a .deb i found online (couldnt recall where it was. just found it after lots of searching). and my hardware shouldnt be a problem but here is a list of everything i have:

Processor: 	
AMD Phenom(tm) 9950 Quad-Core Processor (4 CPUs), ~2.6GHz
Memory: 	
6.00 GB RAM
Video Card: 	
NVIDIA GeForce 9600 GT
Motherboard: 	
MSI K9N SLI-F V.2 (MS-7390-010)

If there is anything else you need just let me know.

Also this showed up as soon as i ran pcsx2

```
$ pcsx2

	F1 - save state
	(Shift +) F2 - cycle states
	F3 - load state
	F10 - dump performance counters
	F11 - save GS state
	F12 - dump hardware registers
PCSX2 v0.9.4 save ver: 7a30000f
EE pc offset: 0x2a8, PSX pc offset: 0x208
x86Init: 
	CPU vender name =  AuthenticAMD
	FamilyID	=  3
	x86Family =  AMD Phenom(tm) 9950 Quad-Core Processor
	CPU speed =  2.615 Ghz
	x86PType  =  Standard OEM
	x86Flags  =  178bfbff
	x86EFlags =  efd3fbff
Features: 
	Detected MMX
	Detected SSE
	Detected SSE2
	Not Detected SSE3
 Extented AMD Features: 
	Detected MMX2
	Detected 3DNOW
	Detected 3DNOW2

** (<unknown>:20929): WARNING **: Couldn't find pixmap file: pcsxAbout.bmp


```

---

### Post by debili on 2010-11-01
when i run pcsx2 then file>run cd pcsx crashe; my output:
```

./pcsx2


(<unknown>:11617): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libequinox.so: wrong ELF class: ELFCLASS64

(<unknown>:11617): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libequinox.so: wrong ELF class: ELFCLASS64

(<unknown>:11617): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libequinox.so: wrong ELF class: ELFCLASS64

(<unknown>:11617): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libequinox.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "globalmenu-plugin": /usr/lib/gtk-2.0/modules/libglobalmenu-plugin.so: wrong ELF class: ELFCLASS64
    F1 - save state

    (Shift +) F2 - cycle states

    F3 - load state

PCSX2 0.9.6 - compiled on Feb 28 2009

Savestate version: 8b400004

x86Init:

    CPU vendor name =  AuthenticAMD
    FamilyID  =  2
    x86Family =  AMD Athlon(tm) II X2 240 Processor
    CPU speed =  2.797 Ghz
    Cores     =  2 physical [2 logical]
    x86PType  =  Standard OEM
    x86Flags  =  178bfbff 00802009
    x86EFlags =  efd3fbff


Features:

    Detected MMX
    Detected SSE
    Detected SSE2
    Detected SSE3
    Not Detected SSSE3
    Not Detected SSE4.1


 Extended AMD Features:

    Detected MMX2
    Detected 3DNOW
    Detected 3DNOW2



** (<unknown>:11617): WARNING **: Couldn't find pixmap file: pcsxAbout.bmp
Disabling game slots until a game is loaded.

Bios Version 16777215.255




**************
rom1 NOT FOUND
**************







**************
rom2 NOT FOUND
**************







**************
erom NOT FOUND
**************




Framelimiter rate updated (UpdateVSyncRate): 59.94 fps

ZeroGS: creating zerogs
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.4
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: Disabling MRT depth writing
ZeroGS: Creating effects
ZeroGS: Creating extra effects
ZeroGS: using accurate shaders
ZeroGS: initialization successful
Boot Error > SYSTEM.CNF not found

Running the PS2 BIOS...

ZeroGS: Disabling MRT depth writing
Segmentation fault


```
could you guys help me with what these warnings mean?
thanks

---

### Post by debili on 2010-11-03
ok so the issue was ps2 bios missing, now I can run it, even a ps2 dvd ( however only after opening the conf screen, otherwise I get a bios not found error) but slow Frame Rates are my problem now, menus @ logos report 50-60 fps, but when i enter the game and start to play the fps drops under 20.... anyone could help me how to fix that ?
i have a Athlon II X2 240, 4gb ram and the nvidia GT210.

thanks for all advices

---

### Post by thatguruguy on 2010-11-03
pcsx2 is slow unless you have extremely high-end hardware.

---

### Post by wingnux on 2010-11-04
As said before, your cpu is pretty weak: CPU speed =  2.797 Ghz

You need at least a dual core @ 3,5ghz to play ps2 games properly.

---

### Post by Jakey_TheSnake on 2011-01-27
> **wingnux said:**
> As said before, your cpu is pretty weak: CPU speed =  2.797 Ghz

You need at least a dual core @ 3,5ghz to play ps2 games properly.

Would a quad core @ 2.8gHz be okay? Less speed, 2 more cores...

---

### Post by Fxkrait on 2011-01-27
it should work great on that. i can run anything that ive done inside linux with a q6600 (2.4ghz quad core)

---

