---
title: "Wine 0.9.9: World of Warcraft Crashes"
date: 2006-06-17
forum: Desktop Environments
---

### Post by srev2004 on 2006-06-17
==============================================================================
World of WarCraft (build 5302)

Exe:      C:\Program Files\World of Warcraft\WoW.exe
Time:     Jun 17, 2006  2:46:04.366 PM
User:     sravan
Computer: sravan-desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:        C:\Program Files\World of Warcraft\WoW.exe
Exception:      0xC0000005 (ACCESS_VIOLATION) at 0073:007833E9

The instruction at "0x007833E9" referenced memory at "0x00000000".
The memory could not be "written".


WoWBuild: 5302
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000008  EBX=64676248  ECX=00000000  EDX=C0077C19  ESI=7FB9C688
EDI=64D82408  EBP=7FB9C5D8  ESP=7FB9C544  EIP=007833E9  FLG=00010202
CS =0073      DS =007B      ES =007B      SS =007B      FS =1007      GS =0033


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

007833E9 7FB9C5D8 0001:003823E9 C:\Program Files\World of Warcraft\WoW.exe
007842D9 7FB9C614 0001:003832D9 C:\Program Files\World of Warcraft\WoW.exe
00784ABC 7FB9C780 0001:00383ABC C:\Program Files\World of Warcraft\WoW.exe
0078520E 7FB9C794 0001:0038420E C:\Program Files\World of Warcraft\WoW.exe
006FF92B 7FB9C7A8 0001:002FE92B C:\Program Files\World of Warcraft\WoW.exe
006FD53F 7FB9C83C 0001:002FC53F C:\Program Files\World of Warcraft\WoW.exe
006FA86E 7FB9FBB8 0001:002F986E C:\Program Files\World of Warcraft\WoW.exe
0073FC6E 7FB9FC90 0001:0033EC6E C:\Program Files\World of Warcraft\WoW.exe
0046547F 7FB9FCB4 0001:0006447F C:\Program Files\World of Warcraft\WoW.exe
0073A177 7FB9FCD8 0001:00339177 C:\Program Files\World of Warcraft\WoW.exe
00738DEC 7FB9FCE4 0001:00337DEC C:\Program Files\World of Warcraft\WoW.exe
0043872E 7FB9FDAC 0001:0003772E C:\Program Files\World of Warcraft\WoW.exe
00416470 7FB9FDE0 0001:00015470 C:\Program Files\World of Warcraft\WoW.exe
00412E3F 7FB9FE50 0001:00011E3F C:\Program Files\World of Warcraft\WoW.exe
004129C1 7FB9FE68 0001:000119C1 C:\Program Files\World of Warcraft\WoW.exe
00403F60 7FB9FF08 0001:00002F60 C:\Program Files\World of Warcraft\WoW.exe
7FC5B311 7FB9FFE8 0001:0004A311 c:\windows\system32\kernel32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

007833E9 WoW.exe      <unknown symbol>+0 (0x64676248,0x00000000,0x00000018,0x00000008)
007842D9 WoW.exe      <unknown symbol>+0 (0x7FB9C688,0x00000008,0x64D82408,0x00000000)
00784ABC WoW.exe      <unknown symbol>+0 (0x00000000,0x00000008,0x7FB9C85C,0x7FB9C7A8)
0078520E WoW.exe      <unknown symbol>+0 (0x00000000,0x7FB9C85C,0x00040015,0x7FB9C83C)
006FF92B WoW.exe      <unknown symbol>+0 (0x00000001,0x64E78008,0x645DE528,0xBE6F4097)
006FD53F WoW.exe      <unknown symbol>+0 (0x00000001,0x648FC008,0x648FB208,0x00000026)
006FA86E WoW.exe      <unknown symbol>+0 (0x00000001,0x64E7A408,0x3F800000,0x00000000)
0073FC6E WoW.exe      <unknown symbol>+0 (0x00000000,0x00743C91,0x00000001,0x64D83608)
0046547F WoW.exe      <unknown symbol>+0 (0x6AD0FC88,0x64D68008,0x64D23988,0x00000000)
0073A177 WoW.exe      <unknown symbol>+0 (0x64D239A0,0x7FB9FDAC,0x0043872E,0x64D239A0)
00738DEC WoW.exe      <unknown symbol>+0 (0x64D239A0,0x3C8B4396,0x7FB9FDC0,0x6AF73F48)
0043872E WoW.exe      <unknown symbol>+0 (0x6AF7C018,0x6AF7C008,0x00000000,0x6AF73F48)
00416470 WoW.exe      <unknown symbol>+0 (0x00000000,0x00000102,0x6AF7C008,0x00000000)
00412E3F WoW.exe      <unknown symbol>+0 (0x00000000,0x004021D9,0x00000001,0x00000001)

004129C1 WoW.exe      <unknown symbol>+0 (0x00409814,0x00400000,0x00000000,0x7FCF642F)
00403F60 WoW.exe      <unknown symbol>+0 (0x7FFDF760,0x00000000,0x00000000,0x00000000)
7FC5B311 kernel32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7F2FDDB              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x00CA7000  C:\Program Files\World of Warcraft\WoW.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x60CA0000 - 0x60CAA000  c:\windows\system32\psapi.dll
0x60CB0000 - 0x60CEB000  c:\windows\system32\dbghelp.dll
0x7C7A0000 - 0x7C7DE000  c:\windows\system32\dsound.dll
0x7C830000 - 0x7C840000  c:\windows\system32\mswsock.dll
0x7CCE0000 - 0x7CCF0000  c:\windows\system32\midimap.dll
0x7CE10000 - 0x7CE1C000  c:\windows\system32\msacm.drv
0x7CE30000 - 0x7CE60000  c:\windows\system32\wineoss.drv
0x7DBB0000 - 0x7DBD9000  c:\windows\system32\uxtheme.dll
0x7EE70000 - 0x7EEDA000  c:\windows\system32\winex11.drv
0x7EFB0000 - 0x7EFC3000  c:\windows\system32\mpr.dll
0x7EFD0000 - 0x7F00A000  c:\windows\system32\wininet.dll
0x7F010000 - 0x7F030000  c:\windows\system32\msacm32.dll
0x7F030000 - 0x7F0C0000  C:\Program Files\World of Warcraft\fmod.dll
0x7F0D0000 - 0x7F14F000  c:\windows\system32\winmm.dll
0x7F160000 - 0x7F16B000  c:\windows\system32\imm32.dll
0x7F3C0000 - 0x7F418000  c:\windows\system32\opengl32.dll
0x7F420000 - 0x7F443000  c:\windows\system32\ws2_32.dll
0x7F450000 - 0x7F45D000  c:\windows\system32\wsock32.dll
0x7F460000 - 0x7F47C000  c:\windows\system32\iphlpapi.dll
0x7F490000 - 0x7F4C5000  c:\windows\system32\rpcrt4.dll
0x7F4E0000 - 0x7F556000  c:\windows\system32\ole32.dll
0x7F570000 - 0x7F5B1000  c:\windows\system32\shlwapi.dll
0x7F5D0000 - 0x7F67D000  c:\windows\system32\shell32.dll
0x7F690000 - 0x7F6BD000  c:\windows\system32\advapi32.dll
0x7F7B0000 - 0x7F843000  c:\windows\system32\gdi32.dll
0x7F860000 - 0x7F96F000  c:\windows\system32\user32.dll
0x7F980000 - 0x7FA2F000  c:\windows\system32\comctl32.dll
0x7FA40000 - 0x7FA90000  c:\windows\system32\msvcrt.dll
0x7FC10000 - 0x7FCF0000  c:\windows\system32\kernel32.dll
0x7FF80000 - 0x7FFE0000  c:\windows\system32\ntdll.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 007833E9)

007833E9: 89 11 8B 55  E0 89 51 04  D9 5D E4 8B  55 E4 89 51  ...U..Q..]..U..Q


Stack: 1024 bytes starting at (ESP = 7FB9C544)

* = addr               **                                         *
7FB9C540: 38 96 C9 00  08 24 D8 64  00 00 00 00  08 24 D8 64  8....$.d.....$.d
7FB9C550: 60 C5 B9 7F  4E 8D 25 7F  80 DF F8 7F  D0 F2 40 7F  `...N.%.......@.
7FB9C560: A0 C5 B9 7F  E0 4F 3F 7F  75 58 F1 B7  D0 F2 40 7F  .....O?.uX....@.
7FB9C570: B9 88 00 00  84 C5 B9 7F  4E 8D 25 7F  01 00 00 00  ........N.%.....
7FB9C580: D0 F2 40 7F  C4 C5 B9 7F  E0 4F 3F 7F  0C 26 ED 7E  ..@......O?..&.~
7FB9C590: A0 C5 B9 7F  00 00 00 00  00 00 00 00  00 00 00 00  ................
7FB9C5A0: 00 00 00 00  40 42 3C 7F  D9 98 05 C0  F4 DD 88 3E  ....@B<........>
7FB9C5B0: ED E4 A9 40  19 7C 07 C0  F0 F7 97 3E  20 52 ED 7E  ...@.|.....> R.~
7FB9C5C0: FC 1A 0C 27  FC 1A 0C 27  C6 9F F1 3C  92 88 00 00  ...'...'...<....
7FB9C5D0: 00 00 00 00  00 00 00 00  14 C6 B9 7F  D9 42 78 00  .............Bx.
7FB9C5E0: 48 62 67 64  00 00 00 00  18 00 00 00  08 00 00 00  Hbgd............
7FB9C5F0: 08 24 D8 64  10 C6 B9 7F  E9 88 57 00  92 88 00 00  .$.d......W.....
7FB9C600: B9 88 00 00  18 00 00 00  08 00 00 00  08 24 D8 64  .............$.d
7FB9C610: 08 24 D8 64  80 C7 B9 7F  BC 4A 78 00  88 C6 B9 7F  .$.d.....Jx.....
7FB9C620: 08 00 00 00  08 24 D8 64  00 00 00 00  7E 36 5C BE  .....$.d....~6\.
7FB9C630: 12 B1 A3 3E  9C DE 60 BF  00 00 00 00  CB A5 6A 3F  ...>..`.......j?
7FB9C640: E8 1F 7F 3E  56 BA 08 BE  00 00 00 00  49 A2 3B BE  ...>V.......I.;.
7FB9C650: 47 9E 60 3F  CE 7F BB 3E  00 00 00 00  0C F6 6E 3F  G.`?...>......n?
7FB9C660: 92 FB E8 BF  B5 47 31 41  FF FF 7F 3F  6D 8A 75 3F  .....G1A...?m.u?
7FB9C670: 4C 73 18 3C  4F D8 68 34  00 00 00 00  5D 73 18 BC  Ls.<O.h4....]s..
7FB9C680: 33 C1 70 3F  A0 F9 40 3E  00 00 00 00  30 93 C9 00  3.p?..@>....0...
7FB9C690: 0C 00 00 00  10 00 00 00  18 00 00 00  00 00 00 00  ................
7FB9C6A0: 18 00 00 00  18 00 00 00  00 00 00 00  00 00 80 3F  ...............?
7FB9C6B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
7FB9C6C0: 00 00 80 3F  00 00 00 00  00 00 00 00  00 00 00 00  ...?............
7FB9C6D0: 00 00 00 00  00 00 80 3F  00 00 00 00  00 00 00 00  .......?........
7FB9C6E0: 00 00 00 00  00 00 00 00  00 00 80 3F  00 00 80 3F  ...........?...?
7FB9C6F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
7FB9C700: 00 00 80 3F  00 00 00 00  00 00 00 00  00 00 00 00  ...?............
7FB9C710: 00 00 00 00  00 00 80 3F  00 00 00 00  75 7B 75 C0  .......?....u{u.
7FB9C720: D7 BC 00 C0  57 6C 83 3F  00 00 80 3F  97 40 6F BE  ....Wl.?...?.@o.
7FB9C730: 75 44 AA 3E  30 E7 69 BF  00 00 00 00  18 EA 78 3F  uD.>0.i.......x?
7FB9C740: 7B A8 A3 3D  DA D2 60 BE  00 00 00 00  00 00 00 00  {..=..`.........
7FB9C750: B3 8F 70 3F  3E 1D AF 3E  00 00 00 00  59 CA 02 B4  ..p?>..>....Y...
7FB9C760: DD 6D 81 32  72 8D 11 35  00 00 80 3F  88 02 F7 6A  .m.2r..5...?...j
7FB9C770: 00 00 00 00  75 7B 75 C0  D7 BC 00 C0  57 6C 83 3F  ....u{u.....Wl.?
7FB9C780: 94 C7 B9 7F  0E 52 78 00  00 00 00 00  08 00 00 00  .....Rx.........
7FB9C790: 5C C8 B9 7F  A8 C7 B9 7F  2B F9 6F 00  00 00 00 00  \.......+.o.....
7FB9C7A0: 5C C8 B9 7F  15 00 04 00  3C C8 B9 7F  3F D5 6F 00  \.......<...?.o.
7FB9C7B0: 01 00 00 00  08 80 E7 64  28 E5 5D 64  97 40 6F BE  .......d(.]d.@o.
7FB9C7C0: 75 44 AA 3E  30 E7 69 BF  00 00 00 00  18 EA 78 3F  uD.>0.i.......x?
7FB9C7D0: 7B A8 A3 3D  DA D2 60 BE  00 00 00 00  00 00 00 00  {..=..`.........
7FB9C7E0: B3 8F 70 3F  3E 1D AF 3E  00 00 00 00  00 00 00 00  ..p?>..>........
7FB9C7F0: 00 00 00 00  00 00 00 00  00 00 80 3F  E6 95 C6 3F  ...........?...?
7FB9C800: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
7FB9C810: F0 63 04 40  00 00 00 00  00 00 00 00  00 00 00 00  .c.@............
7FB9C820: 00 00 00 00  31 08 80 3F  00 00 80 3F  00 00 00 00  ....1..?...?....
7FB9C830: 00 00 00 00  81 95 E3 BE  00 00 00 00  B8 FB B9 7F  ................
7FB9C840: 6E A8 6F 00  01 00 00 00  08 C0 8F 64  08 B2 8F 64  n.o........d...d
7FB9C850: 26 00 00 00  74 36 D8 64  08 A4 E7 64  C9 01 25 3F  &...t6.d...d..%?
7FB9C860: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
7FB9C870: AB 82 F7 3E  00 00 00 00  00 00 00 00  00 00 00 00  ...>............
7FB9C880: 00 00 00 00  00 00 00 00  00 00 80 3F  00 00 00 00  ...........?....
7FB9C890: 00 00 00 00  64 FB 0F C0  9B 04 10 40  08 80 E7 64  ....d......@...d
7FB9C8A0: 80 2E C9 00  10 00 EB 64  01 00 00 00  00 00 00 00  .......d........
7FB9C8B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
7FB9C8C0: 00 00 00 00  00 00 00 00  00 00 00 00  E6 95 C6 3F  ...............?
7FB9C8D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
7FB9C8E0: F0 63 04 40  00 00 00 00  00 00 00 00  00 00 00 00  .c.@............
7FB9C8F0: 00 00 00 00  31 08 80 3F  81 95 E3 BE  00 00 00 00  ....1..?........
7FB9C900: 00 00 00 00  00 00 80 3F  00 00 00 00  00 00 80 3F  .......?.......?
7FB9C910: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
7FB9C920: 00 00 80 3F  00 00 00 00  00 00 00 00  00 00 00 00  ...?............
7FB9C930: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
7FB9C940: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................


____________________________________________________________________

Any Ideas....? It loads WoW up just fine, no lag whatsoever but it crashes right after login confirms and it goes to downloading (patch).

My WoW version is 1.10.2 (5302)
April, 2006 release

Any help would help greatly.

Here is my Config.wtf file

SET gxColorBits "24"
SET gxResolution "800x600"
SET gxWindow "1"
SET gxApi "opengl"
SET gxDepthBits "24"
SET gxRefresh "60"
SET hwDetect "0"
SET fullAlpha "1"
SET doodadAnim "0"
SET lodDist "100.000000"
SET SmallCull "0.070000"
SET DistCull "450.000000"
SET trilinear "1"
SET frillDensity "12"
SET farclip "350.000000"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET gxMultisampleQuality "0.000000"
SET readScanning "-1"
SET readContest "-1"


It would be awesome if someone could help me fix this.

---

### Post by srev2004 on 2006-06-17
anyone have any ideas?!

---

