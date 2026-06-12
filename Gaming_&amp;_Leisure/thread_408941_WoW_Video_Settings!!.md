---
title: "WoW Video Settings?!?!"
date: 2007-04-14
forum: Gaming &amp; Leisure
---

### Post by Darkblizz on 2007-04-14
==============================================================================
World of WarCraft (build 6546)

Exe:      C:\Program Files\World of Warcraft\WoW.exe
Time:     Apr 13, 2007 10:58:12.842 PM
User:     harry
Computer: harry-laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:004968BD

The instruction at "0x004968BD" referenced memory at "0x00000000".
The memory could not be "read".


WoWBuild: 6546
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000000  EBX=01118108  ECX=00000010  EDX=00000018  ESI=00000000
EDI=010F5A08  EBP=0034FAE0  ESP=0034FAA4  EIP=004968BD  FLG=00210246
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

004968BD 0034FAE0 0001:000958BD C:\Program Files\World of Warcraft\WoW.exe
00798999 0034FAFC 0001:00397999 C:\Program Files\World of Warcraft\WoW.exe
0079B802 0034FB88 0001:0039A802 C:\Program Files\World of Warcraft\WoW.exe
00798D68 0034FB98 0001:00397D68 C:\Program Files\World of Warcraft\WoW.exe
00790D2B 0034FBFC 0001:0038FD2B C:\Program Files\World of Warcraft\WoW.exe
00798F4B 0034FC24 0001:00397F4B C:\Program Files\World of Warcraft\WoW.exe
00790CFC 0034FC48 0001:0038FCFC C:\Program Files\World of Warcraft\WoW.exe
00754A95 0034FC9C 0001:00353A95 C:\Program Files\World of Warcraft\WoW.exe
00752061 0034FCB4 0001:00351061 C:\Program Files\World of Warcraft\WoW.exe
007E2EF8 0034FCD8 0001:003E1EF8 C:\Program Files\World of Warcraft\WoW.exe
007E2CDE 0034FCFC 0001:003E1CDE C:\Program Files\World of Warcraft\WoW.exe
007C9AF9 0034FD54 0001:003C8AF9 C:\Program Files\World of Warcraft\WoW.exe
00426BB0 0034FD88 0001:00025BB0 C:\Program Files\World of Warcraft\WoW.exe
00426615 0034FDBC 0001:00025615 C:\Program Files\World of Warcraft\WoW.exe
00425FDA 0034FDD4 0001:00024FDA C:\Program Files\World of Warcraft\WoW.exe
00425E71 0034FE04 0001:00024E71 C:\Program Files\World of Warcraft\WoW.exe
00423228 0034FE60 0001:00022228 C:\Program Files\World of Warcraft\WoW.exe
004230F1 0034FE78 0001:000220F1 C:\Program Files\World of Warcraft\WoW.exe
00404B0E 0034FF08 0001:00003B0E C:\Program Files\World of Warcraft\WoW.exe
7B86D50F 0034FFE8 0001:0004C50F c:\windows\system32\kernel32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

004968BD WoW.exe      <unknown symbol>+0 (0x051870C8,0x00000000,0x04B96608,0x05187108)
00798999 WoW.exe      <unknown symbol>+0 (0x00000000,0x05187078,0x04B96608,0x00000002)
0079B802 WoW.exe      <unknown symbol>+0 (0x00000000,0x04B96608,0x0034FBFC,0x00790D2B)
00798D68 WoW.exe      <unknown symbol>+0 (0x00000000,0x00798544,0x04B96608,0x00000000)
00790D2B WoW.exe      <unknown symbol>+0 (0x0034FC40,0x00000000,0x04B96608,0x00000002)
00798F4B WoW.exe      <unknown symbol>+0 (0x0034FC40,0x00000070,0x00000060,0x00000002)
00790CFC WoW.exe      <unknown symbol>+0 (0x00000000,0xFFFFFFFB,0x3A474244,0x6974704F)
00754A95 WoW.exe      <unknown symbol>+0 (0x00000002,0x00000000,0x00000000,0x0517E008)
00752061 WoW.exe      <unknown symbol>+0 (0x0517E500,0x00000002,0x00000000,0x000C86F3)
007E2EF8 WoW.exe      <unknown symbol>+0 (0x00875B98,0x00000000,0x0034FD98,0x05180008)
007E2CDE WoW.exe      <unknown symbol>+0 (0x0034FD18,0x00000000,0x0034FD68,0x06EAFFA8)
007C9AF9 WoW.exe      <unknown symbol>+0 (0x0034FE5C,0x014D9808,0x00000001,0x06EAFFA8)
00426BB0 WoW.exe      <unknown symbol>+0 (0x0034FD98,0x014D9808,0x00000000,0x00000001)
00426615 WoW.exe      <unknown symbol>+0 (0x00000454,0x000003FD,0x00000000,0x000C86F3)
00425FDA WoW.exe      <unknown symbol>+0 (0x0034FDF0,0x0034FE5C,0x00000000,0x00000102)
00425E71 WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x7B8A78A0,0x69676E45)
00423228 WoW.exe      <unknown symbol>+0 (0x00000000,0x00402584,0x00000001,0x00000001)
004230F1 WoW.exe      <unknown symbol>+0 (0x0040A850,0x00400000,0x00000000,0x0011666C)
00404B0E WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B86D50F kernel32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7E03397              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00350000 - 0x003E0000  C:\Program Files\World of Warcraft\fmod.dll
0x00400000 - 0x00D9E000  C:\Program Files\World of Warcraft\WoW.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B920000  c:\windows\system32\kernel32.dll
0x7BC10000 - 0x7BC94000  c:\windows\system32\ntdll.dll
0x7BFC0000 - 0x7C000000  c:\windows\system32\dbghelp.dll
0x7CFE0000 - 0x7CFE4000  c:\windows\system32\psapi.dll
0x7D020000 - 0x7D029000  c:\windows\system32\mswsock.dll
0x7D2B0000 - 0x7D2C2000  c:\windows\system32\midimap.dll
0x7D2D0000 - 0x7D2DA000  c:\windows\system32\msacm32.drv
0x7D2E0000 - 0x7D316000  c:\windows\system32\wineoss.drv
0x7D550000 - 0x7D575000  c:\windows\system32\uxtheme.dll
0x7DA70000 - 0x7DAE8000  c:\windows\system32\winex11.drv
0x7DBC0000 - 0x7DBD2000  c:\windows\system32\mpr.dll
0x7DBE0000 - 0x7DC19000  c:\windows\system32\wininet.dll
0x7DC30000 - 0x7DC6D000  c:\windows\system32\rpcrt4.dll
0x7DC80000 - 0x7DD05000  c:\windows\system32\ole32.dll
0x7DD10000 - 0x7DD67000  c:\windows\system32\msvcrt.dll
0x7DD70000 - 0x7DD8D000  c:\windows\system32\msacm32.dll
0x7DD90000 - 0x7DDA1000  c:\windows\system32\lz32.dll
0x7DDB0000 - 0x7DDBA000  c:\windows\system32\version.dll
0x7DDD0000 - 0x7DE47000  c:\windows\system32\winmm.dll
0x7DE50000 - 0x7DE63000  c:\windows\system32\imm32.dll
0x7E8B0000 - 0x7E90E000  c:\windows\system32\opengl32.dll
0x7E930000 - 0x7E940000  c:\windows\system32\iphlpapi.dll
0x7E950000 - 0x7E96B000  c:\windows\system32\ws2_32.dll
0x7E970000 - 0x7E985000  c:\windows\system32\wsock32.dll
0x7E990000 - 0x7E9DC000  c:\windows\system32\shlwapi.dll
0x7E9F0000 - 0x7EAD2000  c:\windows\system32\shell32.dll
0x7EBD0000 - 0x7EC68000  c:\windows\system32\gdi32.dll
0x7EC80000 - 0x7ED9E000  c:\windows\system32\user32.dll
0x7EDB0000 - 0x7EE5C000  c:\windows\system32\comctl32.dll
0x7EE70000 - 0x7EEA0000  c:\windows\system32\advapi32.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 004968BD)

004968BD: 3B 0C 06 75  13 3B 54 06  04 75 0D 8B  4D F8 3B 4C  ;..u.;T..u..M.;L


Stack: 1024 bytes starting at (ESP = 0034FAA4)

* = addr               **                                         *           
0034FAA0: 8B 68 49 00  10 68 49 00  08 66 B9 04  08 70 18 05  .hI..hI..f...p..
0034FAB0: 08 66 B9 04  35 04 79 00  01 00 00 00  0A 36 6C 03  .f..5.y......6l.
0034FAC0: 68 16 FE 07  71 CA 79 00  E8 70 18 05  68 16 FE 07  h...q.y..p..h...
0034FAD0: 00 00 00 00  80 07 00 00  01 00 00 00  08 86 11 01  ................
0034FAE0: FC FA 34 00  99 89 79 00  C8 70 18 05  00 00 00 00  ..4...y..p......
0034FAF0: 08 66 B9 04  08 71 18 05  C0 00 00 00  88 FB 34 00  .f...q........4.
0034FB00: 02 B8 79 00  00 00 00 00  78 70 18 05  08 66 B9 04  ..y.....xp...f..
0034FB10: 02 00 00 00  40 00 00 00  4C FC 34 00  54 FB 34 00  ....@...L.4.T.4.
0034FB20: 74 85 DE B7  08 00 EE 06  16 49 C5 7B  05 00 00 00  t........I.{....
0034FB30: 88 94 24 07  40 00 00 00  58 00 00 00  00 00 00 00  ..$.@...X.......
0034FB40: 34 FC 34 00  00 C0 FD 7F  A8 85 C7 7B  01 00 00 00  4.4........{....
0034FB50: 4C FC 34 00  34 FC 34 00  EA 4A C5 7B  08 66 B9 04  L.4.4.4..J.{.f..
0034FB60: 18 71 18 05  00 00 00 00  00 00 00 00  A5 AA 83 7B  .q.............{
0034FB70: 02 00 00 00  00 00 00 00  C8 04 FE 07  08 C8 47 07  ..............G.
0034FB80: C8 70 18 05  68 FA 48 07  98 FB 34 00  68 8D 79 00  .p..h.H...4.h.y.
0034FB90: 00 00 00 00  08 66 B9 04  FC FB 34 00  2B 0D 79 00  .....f....4.+.y.
0034FBA0: 00 00 00 00  44 85 79 00  08 66 B9 04  00 00 00 00  ....D.y..f......
0034FBB0: FC FB 34 00  02 00 00 00  00 00 00 00  08 66 B9 04  ..4..........f..
0034FBC0: 9C FB 34 00  32 85 79 00  F8 FE 34 00  00 00 00 00  ..4.2.y...4.....
0034FBD0: 30 32 43 56  00 00 00 00  08 00 EE 06  01 00 00 00  02CV............
0034FBE0: 54 04 00 00  FD 03 00 00  FC FB 34 00  F6 CA 79 00  T.........4...y.
0034FBF0: 00 00 00 00  20 0D 79 00  08 66 B9 04  24 FC 34 00  .... .y..f..$.4.
0034FC00: 4B 8F 79 00  40 FC 34 00  00 00 00 00  08 66 B9 04  K.y.@.4......f..
0034FC10: 02 00 00 00  00 00 00 00  00 00 00 00  08 66 00 00  .............f..
0034FC20: 4C FC 34 01  48 FC 34 00  FC 0C 79 00  40 FC 34 00  L.4.H.4...y.@.4.
0034FC30: 70 00 00 00  60 00 00 00  02 00 00 00  08 66 B9 04  p...`........f..
0034FC40: 78 70 18 05  00 00 00 00  9C FC 34 00  95 4A 75 00  xp........4..Ju.
0034FC50: 00 00 00 00  FB FF FF FF  44 42 47 3A  4F 70 74 69  ........DBG:Opti
0034FC60: 6F 6E 73 46  72 61 6D 65  4F 6B 61 79  00 48 75 00  onsFrameOkay.Hu.
0034FC70: 98 5B 87 00  00 E5 17 05  08 66 B9 04  3C 03 00 00  .[.......f..<...
0034FC80: 00 00 00 00  58 FC 34 00  00 00 00 00  08 E0 17 05  ....X.4.........
0034FC90: 03 00 00 00  01 00 00 00  02 00 00 00  B4 FC 34 00  ..............4.
0034FCA0: 61 20 75 00  02 00 00 00  00 00 00 00  00 00 00 00  a u.............
0034FCB0: 08 E0 17 05  D8 FC 34 00  F8 2E 7E 00  00 E5 17 05  ......4...~.....
0034FCC0: 02 00 00 00  00 00 00 00  F3 86 0C 00  98 5B 87 00  .............[..
0034FCD0: 08 E0 17 05  00 00 00 00  FC FC 34 00  DE 2C 7E 00  ..........4..,~.
0034FCE0: 98 5B 87 00  00 00 00 00  98 FD 34 00  08 00 18 05  .[........4.....
0034FCF0: 08 E0 17 05  24 8E FA 3E  42 E9 A1 3D  54 FD 34 00  ....$..>B..=T.4.
0034FD00: F9 9A 7C 00  18 FD 34 00  00 00 00 00  68 FD 34 00  ..|...4.....h.4.
0034FD10: A8 FF EA 06  A8 FF EA 06  A8 7A 86 00  00 00 00 00  .........z......
0034FD20: C9 00 05 40  00 00 00 00  00 00 00 00  01 00 00 00  ...@............
0034FD30: 00 00 00 00  00 00 00 00  00 00 00 00  24 8E FA 3E  ............$..>
0034FD40: 42 E9 A1 3D  DA 86 0C 00  F3 86 0C 00  00 00 00 00  B..=............
0034FD50: 00 EF 49 00  88 FD 34 00  B0 6B 42 00  5C FE 34 00  ..I...4..kB.\.4.
0034FD60: 08 98 4D 01  01 00 00 00  A8 FF EA 06  11 99 4D 01  ..M...........M.
0034FD70: B0 04 00 00  FD 03 00 00  80 07 00 00  01 00 00 00  ................
0034FD80: 0E 00 00 00  0C 99 4D 01  BC FD 34 00  15 66 42 00  ......M...4..fB.
0034FD90: 98 FD 34 00  08 98 4D 01  00 00 00 00  01 00 00 00  ..4...M.........
0034FDA0: 00 00 00 00  00 00 00 00  00 00 00 00  BC BB 13 3F  ...............?
0034FDB0: 26 BF 18 3E  DA 86 0C 00  F3 86 0C 00  D4 FD 34 00  &..>..........4.
0034FDC0: DA 5F 42 00  54 04 00 00  FD 03 00 00  00 00 00 00  ._B.T...........
0034FDD0: F3 86 0C 00  04 FE 34 00  71 5E 42 00  F0 FD 34 00  ......4.q^B...4.
0034FDE0: 5C FE 34 00  00 00 00 00  02 01 00 00  08 98 4D 01  \.4...........M.
0034FDF0: 01 00 00 00  54 04 00 00  FD 03 00 00  F3 86 0C 00  ....T...........
0034FE00: 0D 00 00 00  60 FE 34 00  28 32 42 00  00 F0 FD 7F  ....`.4.(2B.....
0034FE10: 00 00 00 00  A0 78 8A 7B  45 6E 67 69  6E 65 20 31  .....x.{Engine 1
0034FE20: 62 00 11 00  98 AF 16 00  65 6E 00 00  40 8B C2 7B  b.......en..@..{
0034FE30: 40 8B C2 7B  A0 78 8A 7B  00 F0 FD 7F  5C FE 34 00  @..{.x.{....\.4.
0034FE40: 25 2A 88 7B  84 20 00 00  00 00 00 00  0B 00 00 00  %*.{. ..........
0034FE50: A4 02 00 00  A0 78 8A 7B  F3 86 0C 00  00 00 00 00  .....x.{........
0034FE60: 78 FE 34 00  F1 30 42 00  00 00 00 00  84 25 40 00  x.4..0B......%@.
0034FE70: 01 00 00 00  01 00 00 00  08 FF 34 00  0E 4B 40 00  ..........4..K@.
0034FE80: 50 A8 40 00  00 00 40 00  00 00 00 00  6C 66 11 00  P.@...@.....lf..
0034FE90: 01 00 00 00  00 F0 FD 7F  00 10 40 00  A0 78 8A 7B  ..........@..x.{
0034FEA0: 05 00 00 C0  6C 66 11 00  00 00 00 00  44 00 00 00  ....lf......D...


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x1
Number of Processors:   1
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     3336

Percent memory used:    14
Total physical memory:  2126213120
Free Memory:            1818828800
Page file:              -1
Total virtual memory:   2147352575


Well this is the error i get form wow when go to change some of my video settings before it does this it just freezes and after a while it goes to that does anybody else have this problem with wow? 

Using WIne BTW! to run it

---

### Post by hikaricore on 2007-04-14
This has been a known issue since the dawn of time sadly.  You'll need to either edit setting in D3D mode then switch back to opengl after applying changes, or edit your config.wtf manually.

---

### Post by Darkblizz on 2007-04-15
lol what the heck is d3d mode ! lol < linux noob > just switched over :)

---

### Post by hikaricore on 2007-04-15
[http://help.ubuntu.com/community/WorldofWarcraft#head-2ac1ae13cb6a81b0519108cc62933d3cbdcdb85a](http://help.ubuntu.com/community/WorldofWarcraft#head-2ac1ae13cb6a81b0519108cc62933d3cbdcdb85a)

Under troubleshooting which the above link should take you to directly, 6th bullet down talks about video configuration.

---

