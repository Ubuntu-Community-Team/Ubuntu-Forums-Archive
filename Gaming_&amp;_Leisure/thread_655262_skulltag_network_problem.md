---
title: "skulltag network problem"
date: 2008-01-01
forum: Gaming &amp; Leisure
---

### Post by syms on 2008-01-01
hello,
i finally get runed skulltag on my xubuntu gutsy. it works fine offline but when i try browse the servers it crashes, here:
Skulltag v0.97d-beta4.3 - SVN revision 836 - SDL version
Compiled on Oct  6 2007

M_LoadDefaults: Load system defaults.
Please select a game wad (or 0 to exit):
1. DOOM 2: Plutonia Experiment (plutonia.wad)
2. DOOM 2: TNT - Evilution (tnt.wad)
3. DOOM 2: Hell on Earth (doomu.wad)
Which one? 1
W_Init: Init WADfiles.
 adding /media/disk/Zaidimai/Skulltag/skulltag.pk3
 adding /media/disk/Zaidimai/Skulltag/plutonia.wad (2984 lumps)
 adding /media/disk/Zaidimai/Skulltag/skulltag.wad (4961 lumps)
I_Init: Setting up machine state.
CPU Speed: ~898.723249 MHz
CPU Vendor ID: AuthenticAMD
  Name: AMD Duron(tm) processor
  Family 6 (7), Model 3, Stepping 1
  Features: MMX MMX+ 3DNow! 3DNow!+
V_Init: allocate screen.
Switching to OpenGL renderer...
S_Init: Setting up sound.
ST_Init: Init startup screen.
P_Init: Checking cmd-line parameters...
G_ParseMapInfo: Load map definitions.
S_InitData: Load sound definitions.
LoadDecorations: Load external actors.
R_Init: Init Doom refresh subsystem
DecalLibrary: Load decals.
M_Init: Init miscellaneous info.
P_Init: Init Playloop state.
D_CheckNetGame: Checking network game status.
player 1 of 1 (1 nodes)
Initializing network subsystem.
IP address 127.0.1.1:10667
UDP Initialized.
Resolution: 400 x 300


*** Fatal Error ***
Address not mapped to object (signal 11)

Generating skulltag-crash.log and killing process 5064, please wait... sh: Syntax error: end of file unexpected (expecting "fi")
Killed
-------------------------------------------------------------------------------------
and here is the log file:
*** Fatal Error ***
Address not mapped to object (signal 11)
Address: 0x46b2a4d1

System: Linux simas-desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
GCC version: 4.1.3

Skulltag version 0.97d-beta4.3 (Oct  6 2007)

Command line: /media/disk/Zaidimai/Skulltag/skulltag -void.wad -nomusic -nosound

Wad 0: skulltag.pk3
Wad 1: plutonia.wad
Wad 2: skulltag.wad

Not in a level.

Executing: gdb --quiet --batch --command=gdb-respfile-dNYDRA --pid=5064
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1214138688 (LWP 5064)]
[New Thread -1215349872 (LWP 5065)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1214138688 (LWP 5064)]
0xb7c2855b in strlen () from /lib/tls/i686/cmov/libc.so.6

* Loaded Libraries
From        To          Syms Read   Shared Object Library
0xb7f91cd0  0xb7f97d04  Yes         /usr/lib/libFLAC++.so.5
0xb7f71910  0xb7f7f104  Yes         /usr/lib/libz.so.1
0xb7f526b0  0xb7f6c3b4  Yes         /usr/lib/libjpeg.so.62
0xb7ed0ae0  0xb7f10c49  Yes         /usr/lib/libfmod.so
0xb7e2c470  0xb7e84844  Yes         /usr/lib/libSDL-1.2.so.0
0xb7d75a40  0xb7df2d34  Yes         /usr/lib/libstdc++.so.6
0xb7d10460  0xb7d2a3f4  Yes         /lib/tls/i686/cmov/libm.so.6
0xb7d03970  0xb7d0ae64  Yes         /lib/libgcc_s.so.1
0xb7bcde30  0xb7ccab24  Yes         /lib/tls/i686/cmov/libc.so.6
0xb7b7c170  0xb7bb4cb4  Yes         /usr/lib/libFLAC.so.8
0xb7b6ea70  0xb7b6fa74  Yes         /lib/tls/i686/cmov/libdl.so.2
0xb7b59250  0xb7b64224  Yes         /lib/tls/i686/cmov/libpthread.so.0
0xb7ab1ca0  0xb7b3c744  Yes         /usr/lib/libasound.so.2
0xb7a43110  0xb7a85e14  Yes         /usr/lib/libdirectfb-0.9.so.25
0xb7a33d60  0xb7a363b4  Yes         /usr/lib/libfusion-0.9.so.25
0xb7a25f50  0xb7a2ed34  Yes         /usr/lib/libdirect-0.9.so.25
0xb7fac7f0  0xb7fc11af  Yes         /lib/ld-linux.so.2
0xb7a1e3c0  0xb7a20614  Yes         /usr/lib/libogg.so.0
0xb79353a0  0xb79c47f4  Yes         /usr/lib/libX11.so.6
0xb7fa78a0  0xb7fa8514  Yes         /usr/lib/libXau.so.6
0xb7fa2e20  0xb7fa4a94  Yes         /usr/lib/libXdmcp.so.6
0xb7912a90  0xb791c724  Yes         /usr/lib/libXext.so.6
0xb7909250  0xb790e8f4  Yes         /usr/lib/libXrender.so.1
0xb79032b0  0xb7906e44  Yes         /usr/lib/libXrandr.so.2
0xb78fb070  0xb79001e4  Yes         /usr/lib/libXcursor.so.1
0xb78f4e00  0xb78f7134  Yes         /usr/lib/libXfixes.so.3
0xb7a11370  0xb7a11d84  Yes         /usr/lib/gconv/ISO8859-1.so
0xb7094920  0xb709b364  Yes         /lib/tls/i686/cmov/libnss_files.so.2
0xb7055770  0xb70563a4  Yes         /lib/libnss_mdns4_minimal.so.2
0xb704fb90  0xb7052714  Yes         /lib/tls/i686/cmov/libnss_dns.so.2
0xb703e110  0xb7049314  Yes         /lib/tls/i686/cmov/libresolv.so.2

* Threads
  2 Thread -1215349872 (LWP 5065)  0xffffe410 in __kernel_vsyscall ()
* 1 Thread -1214138688 (LWP 5064)  0xb7c2855b in strlen ()
   from /lib/tls/i686/cmov/libc.so.6

* FPU Status
  R7: Empty   0x00000000000000000000
  R6: Empty   0x00000000000000000000
  R5: Empty   0x400f8000000000000000
  R4: Empty   0x400f8000000000000000
  R3: Empty   0x3fffa000000000000000
  R2: Empty   0x4011a000000000000000
  R1: Empty   0x40169600000000000000
=>R0: Empty   0xffff0000000000000000

Status Word:         0x4022      DE          PE                      C3
                       TOP: 0
Control Word:        0x037f   IM DM ZM OM UM PM
                       PC: Extended Precision (64-bits)
                       RC: Round to nearest
Tag Word:            0xffff
Instruction Pointer: 0x00:0x00000000
Operand Pointer:     0x00:0x00000000
Opcode:              0x0000

* Registers
eax            0x46b2a4d1	1186112721
ecx            0x1	1
edx            0x46b2a4d1	1186112721
ebx            0xb7cfdff4	-1211113484
esp            0xbfc9e2ac	0xbfc9e2ac
ebp            0xbfc9e8d4	0xbfc9e8d4
esi            0x46b2a4d1	1186112721
edi            0x86a0dea	141168106
eip            0xb7c2855b	0xb7c2855b <strlen+11>
eflags         0x10202	[ IF RF ]
cs             0x73	115
ss             0x7b	123
ds             0x7b	123
es             0x7b	123
fs             0x0	0
gs             0x33	51

* Bytes near %eip:
0xb7c28558 <strlen+8>:	0x38287403
0xb7c2855b <strlen+11>:	0x840f2838

* Backtrace
#0  0xb7c2855b in strlen () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#1  0xb7bf8de0 in vfprintf () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb7c1333c in vsprintf () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#3  0xb7bfe9be in sprintf () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#4  0x080676f2 in ?? ()
No symbol table info available.
#5  0x080b3b55 in ?? ()
No symbol table info available.
#6  0x0809b7f5 in ?? ()
No symbol table info available.
#7  0x08096c6d in ?? ()
No symbol table info available.
#8  0x08098081 in ?? ()
No symbol table info available.
#9  0x0828a972 in ?? ()
No symbol table info available.
#10 0xb7bce050 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#11 0x0804ca61 in ?? ()
No symbol table info available.
Kill the program being debugged? (y or n) [answered Y; input not from terminal]

what i need to do? i rly love doom and skulltag and if play it on linux that will be awesome.

---

### Post by disturbedite on 2008-01-01
i'm quite familiar with st as i am a beta tester, but i can't help you.

my advice tho, would be to post this at the st forum.

---

