---
title: "wow,wine,feisty,freeze"
date: 2007-08-06
forum: Gaming &amp; Leisure
---

### Post by little cazy on 2007-08-06
i got wow on my computer but i have it open by going in 'wine file' and opening  the install progarm then it freeze (after i connet to a server) form any where beteewn 1sec and 5 min. nomaly i'll go over to my second desktop, make my resolution bigger, go back close out then try again.
                                     l
but if i let it be i get this\l/
----------------------------------------------------------------------------------------
This appliction has encountered a critical error:

ERROR # 132 (0X85100084) Fatal Exception
Program:          C:\World of Warcraft\WoW.exe
Exception:        0xC0000005 (ACCESS_VIOLATION) at 0073:7CB31775

The instruction at "0x7CB31775" referenced memory at "0x25C62C2A".
The memory could not be "read".
------------------------------------------------------------------------------------------
World of WarCraft (build 6898)

Exe:      C:\World of Warcraft\WoW.exe
Time:     Aug  6, 2007  7:50:56.558 PM
User:     eyez
Computer: Zola
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7CB31775

The instruction at "0x7CB31775" referenced memory at "0x25C62C2A".
The memory could not be "read".


WoWBuild: 6898
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=082A27C0  EBX=7CBC1F1C  ECX=00110020  EDX=082A27C0  ESI=25C62C2A
EDI=7D7F7F15  EBP=0034FC10  ESP=0034FBC8  EIP=7CB31775  FLG=00210202
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B
----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

7CB31775 0034FC10 0001:00010775 c:\windows\system32\wined3d.dll
7CB59A80 0034FC40 0001:00038A80 c:\windows\system32\wined3d.dll
7CB7A6D7 0034FC80 0001:000596D7 c:\windows\system32\wined3d.dll
7CBE1138 0034FCB0 0001:00010138 c:\windows\system32\d3d9.dll
7CBD8EA4 0034FCF0 0001:00007EA4 c:\windows\system32\d3d9.dll
7CB82BB3 0034FD20 0001:00061BB3 c:\windows\system32\wined3d.dll
7CBE2C6E 0034FD50 0001:00011C6E c:\windows\system32\d3d9.dll
005778CF 0034FD64 0001:001768CF C:\World of Warcraft\WoW.exe
00563D74 0034FD70 0001:00162D74 C:\World of Warcraft\WoW.exe
00446A44 0034FD90 0001:00045A44 C:\World of Warcraft\WoW.exe
00405104 0034FDB0 0001:00004104 C:\World of Warcraft\WoW.exe
0041F474 0034FDEC 0001:0001E474 C:\World of Warcraft\WoW.exe
0041D529 0034FE54 0001:0001C529 C:\World of Warcraft\WoW.exe
0041D661 0034FE6C 0001:0001C661 C:\World of Warcraft\WoW.exe
00405868 0034FF08 0001:00004868 C:\World of Warcraft\WoW.exe
7B87221E 0034FFE8 0001:0005121E c:\windows\system32\kernel32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

7CB31775 wined3d.dll  <unknown symbol>+0 (0x00173000,0x082A27C0,0x082A28B0,0x0034FCB4)
7CB59A80 wined3d.dll  IWineD3DResourceImpl_CleanUp+128 (0x082A27C0,0x00000000,0x00000000,0x00000000)
7CB7A6D7 wined3d.dll  IWineD3DSurfaceImpl_Release+167 (0x082A27C0,0x0034FCE4,0x458CF185,0xC30A2354)
7CBE1138 d3d9.dll     <unknown symbol>+0 (0x082A2798,0x0034FCE4,0x005A4AE4,0x7CB7348E)
7CBD8EA4 d3d9.dll     D3D9CB_DestroySurface+116 (0x082A27C0,0x00000000,0x00000000,0xEC28E3D7)
7CB82BB3 wined3d.dll  <unknown symbol>+0 (0x082A22F8,0x7CBD8E30,0x3F800000,0x00000000)
7CBE2C6E d3d9.dll     <unknown symbol>+0 (0x001F50A0,0x00AC5B50,0x01CDDCC8,0x0034FD70)
005778CF WoW.exe      <unknown symbol>+0 (0x07050008,0x0034FD90,0x00446A44,0x07050008)
00563D74 WoW.exe      <unknown symbol>+0 (0x07050008,0x011055FC,0x01CDDCC8,0x01105418)
00446A44 WoW.exe      <unknown symbol>+0 (0x00BF8763,0x0079F740,0x00000008,0x0034FDA4)
00405104 WoW.exe      <unknown symbol>+0 (0x0034FDCC,0x00000000,0x00000102,0x00000000)
0041F474 WoW.exe      <unknown symbol>+0 (0x011055DC,0x00000A28,0x00000002,0x00000001)
0041D529 WoW.exe      <unknown symbol>+0 (0x00000001,0x00405828,0x00000001,0x00000001)
0041D661 WoW.exe      <unknown symbol>+0 (0x00409449,0x00400000,0x00000000,0x001165B6)
00405868 WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B87221E kernel32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7EB3897              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00350000 - 0x003B9000  C:\World of Warcraft\DivxDecoder.dll
0x00400000 - 0x00CEE000  C:\World of Warcraft\WoW.exe
0x10000000 - 0x10090000  C:\World of Warcraft\fmod.dll
0x7B820000 - 0x7B926000  c:\windows\system32\kernel32.dll
0x7BC10000 - 0x7BC97000  c:\windows\system32\ntdll.dll
0x7BF40000 - 0x7BF80000  c:\windows\system32\dbghelp.dll
0x7C2C0000 - 0x7C2FD000  c:\windows\system32\dsound.dll
0x7C330000 - 0x7C342000  c:\windows\system32\psapi.dll
0x7CB20000 - 0x7CBC3000  c:\windows\system32\wined3d.dll
0x7CBD0000 - 0x7CBEE000  c:\windows\system32\d3d9.dll
0x7CC60000 - 0x7CC85000  c:\windows\system32\uxtheme.dll
0x7CC90000 - 0x7CC9A000  c:\windows\system32\midimap.dll
0x7CCA0000 - 0x7CCB2000  c:\windows\system32\msacm32.drv
0x7D600000 - 0x7D639000  c:\windows\system32\wineoss.drv
0x7D8A0000 - 0x7D922000  c:\windows\system32\winex11.drv
0x7DA90000 - 0x7DB3F000  c:\windows\system32\comctl32.dll
0x7DB50000 - 0x7DC34000  c:\windows\system32\shell32.dll
0x7DC40000 - 0x7DC8D000  c:\windows\system32\shlwapi.dll
0x7DC90000 - 0x7DCAC000  c:\windows\system32\mpr.dll
0x7DCC0000 - 0x7DCF4000  c:\windows\system32\wininet.dll
0x7DD00000 - 0x7DD49000  c:\windows\system32\rpcrt4.dll
0x7DD60000 - 0x7DDE3000  c:\windows\system32\ole32.dll
0x7DDF0000 - 0x7DE4A000  c:\windows\system32\msvcrt.dll
0x7DE50000 - 0x7DE70000  c:\windows\system32\msacm32.dll
0x7DE80000 - 0x7DE8D000  c:\windows\system32\imm32.dll
0x7DE90000 - 0x7DEA1000  c:\windows\system32\lz32.dll
0x7DEB0000 - 0x7DEBA000  c:\windows\system32\version.dll
0x7E9E0000 - 0x7EA49000  c:\windows\system32\opengl32.dll
0x7EA60000 - 0x7EA7A000  c:\windows\system32\iphlpapi.dll
0x7EA80000 - 0x7EAA7000  c:\windows\system32\ws2_32.dll
0x7EAB0000 - 0x7EAC1000  c:\windows\system32\wsock32.dll
0x7EAD0000 - 0x7EB07000  c:\windows\system32\advapi32.dll
0x7EC10000 - 0x7ECBA000  c:\windows\system32\gdi32.dll
0x7ECE0000 - 0x7EDF6000  c:\windows\system32\user32.dll
0x7EE00000 - 0x7EE85000  c:\windows\system32\winmm.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 7CB31775)
7CB31775: 3B 06 74 55  89 F7 8B 76  04 85 F6 75  F0 F6 83 80  ;.tU...v...u....


Stack: 1024 bytes starting at (ESP = 0034FBC8)

* = addr                            **                                *       
0034FBC0: 10 FC 34 00  EC 16 B3 7C  C0 27 2A 08  50 B5 C7 7B  ..4....|.'*.P..{
0034FBD0: 10 FC 34 00  87 78 C3 7B  20 00 11 00  E0 2B 17 00  ..4..x.{ ....+..
0034FBE0: 03 00 00 00  14 FC 34 00  45 AA BD 7C  00 30 17 00  ......4.E..|.0..
0034FBF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 11 00  ................
0034FC00: CB 16 B3 7C  1C 1F BC 7C  C0 27 2A 08  00 30 17 00  ...|...|.'*..0..
0034FC10: 40 FC 34 00  80 9A B5 7C  00 30 17 00  C0 27 2A 08  @.4....|.0...'*.
0034FC20: B0 28 2A 08  B4 FC 34 00  ED 1D 45 00  34 FC 34 00  .(*...4...E.4.4.
0034FC30: 48 95 D3 01  0A 9A B5 7C  1C 1F BC 7C  C0 27 2A 08  H......|...|.'*.
0034FC40: 80 FC 34 00  D7 A6 B7 7C  C0 27 2A 08  00 00 00 00  ..4....|.'*.....
0034FC50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 80 3F  ...............?
0034FC60: 00 00 00 00  1C 1F BC 7C  C0 27 2A 08  00 00 00 00  .......|.'*.....
0034FC70: 80 FC 34 00  14 D7 BE 7C  00 00 00 00  98 27 2A 08  ..4....|.....'*.
0034FC80: B0 FC 34 00  38 11 BE 7C  C0 27 2A 08  E4 FC 34 00  ..4.8..|.'*...4.
0034FC90: 85 F1 8C 45  54 23 0A C3  85 F1 8C 45  54 23 0A C3  ...ET#.....ET#..
0034FCA0: 00 00 00 00  14 D7 BE 7C  C0 27 2A 08  F8 22 2A 08  .......|.'*.."*.
0034FCB0: F0 FC 34 00  A4 8E BD 7C  98 27 2A 08  E4 FC 34 00  ..4....|.'*...4.
0034FCC0: E4 4A 5A 00  8E 34 B7 7C  18 32 0F 3F  80 34 54 3F  .JZ..4.|.2.?.4T?
0034FCD0: 00 00 00 00  00 00 00 00  80 34 54 BF  18 32 0F 3F  .........4T..2.?
0034FCE0: 00 00 00 00  98 27 2A 08  1C 1F BC 7C  00 00 00 00  .....'*....|....
0034FCF0: 20 FD 34 00  B3 2B B8 7C  C0 27 2A 08  00 00 00 00   .4..+.|.'*.....
0034FD00: 00 00 00 00  D7 E3 28 EC  32 01 00 00  4C FD 34 00  ......(.2...L.4.
0034FD10: 3B 2B B8 7C  14 D7 BE 7C  00 00 00 00  A0 50 1F 00  ;+.|...|.....P..
0034FD20: 50 FD 34 00  6E 2C BE 7C  F8 22 2A 08  30 8E BD 7C  P.4.n,.|."*.0..|
0034FD30: 00 00 80 3F  00 00 00 00  E0 B3 B7 46  D8 C8 07 00  ...?.......F....
0034FD40: 08 D9 8A 7B  28 9B BC 06  08 00 05 07  08 00 10 01  ...{(...........
0034FD50: 64 FD 34 00  CF 78 57 00  A0 50 1F 00  50 5B AC 00  d.4..xW..P..P[..
0034FD60: C8 DC CD 01  70 FD 34 00  74 3D 56 00  08 00 05 07  ....p.4.t=V.....
0034FD70: 90 FD 34 00  44 6A 44 00  08 00 05 07  FC 55 10 01  ..4.DjD......U..
0034FD80: C8 DC CD 01  18 54 10 01  05 00 00 00  03 00 00 00  .....T..........
0034FD90: B0 FD 34 00  04 51 40 00  63 87 BF 00  40 F7 79 00  ..4..Q@.c...@.y.
0034FDA0: 08 00 00 00  A4 FD 34 00  A5 FD 34 00  00 00 00 00  ......4...4.....
0034FDB0: EC FD 34 00  74 F4 41 00  CC FD 34 00  00 00 00 00  ..4.t.A...4.....
0034FDC0: 02 01 00 00  00 00 00 00  08 54 10 01  00 00 80 3E  .........T.....>
0034FDD0: 63 87 BF 00  C1 C9 B0 7C  03 00 00 00  D0 50 40 00  c......|.....P@.
0034FDE0: 00 00 00 00  FC 55 10 01  63 87 BF 00  54 FE 34 00  .....U..c...T.4.
0034FDF0: 29 D5 41 00  DC 55 10 01  28 0A 00 00  02 00 00 00  ).A..U..(.......
0034FE00: 01 00 00 00  63 87 BF 00  00 00 00 00  00 00 00 00  ....c...........
0034FE10: 45 6E 67 69  6E 65 20 39  33 00 11 00  B0 F7 16 00  Engine 93.......
0034FE20: 06 00 00 00  08 D9 8A 7B  08 D9 8A 7B  28 0A 00 00  .......{...{(...
0034FE30: 50 FE 34 00  1A 6D 88 7B  84 20 00 00  00 00 00 00  P.4..m.{. ......
0034FE40: 00 00 00 00  00 00 00 00  01 00 00 00  02 00 00 00  ................
0034FE50: 11 9F 35 00  6C FE 34 00  61 D6 41 00  01 00 00 00  ..5.l.4.a.A.....
0034FE60: 28 58 40 00  01 00 00 00  01 00 00 00  08 FF 34 00  (X@...........4.
0034FE70: 68 58 40 00  49 94 40 00  00 00 40 00  00 00 00 00  hX@.I.@...@.....
0034FE80: B6 65 11 00  0A 00 00 00  4D 9E 35 00  00 F0 FD 7F  .e......M.5.....
0034FE90: 00 10 40 00  08 D9 8A 7B  44 00 00 00  00 00 00 00  ..@....{D.......
0034FEA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FEB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FEC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FED0: 0C 00 00 00  10 00 00 00  14 00 00 00  05 00 00 C0  ................
0034FEE0: 01 00 00 00  05 00 00 00  00 00 00 00  00 F0 FD 7F  ................
0034FEF0: 88 FE 34 00  40 F7 34 00  2C FF 34 00  E0 BA 40 00  ..4.@.4.,.4...@.
0034FF00: 9D D9 81 00  01 00 00 00  E8 FF 34 00  1E 22 87 7B  ..........4..".{
0034FF10: 00 F0 FD 7F  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FF20: 00 00 00 00  00 00 00 00  00 00 00 00  FF FF FF FF  ................
0034FF30: 10 DF 82 7B  20 27 84 7B  08 D9 8A 7B  00 C0 FD 7F  ...{ '.{...{....
0034FF40: 00 10 00 00  E8 FF 34 00  10 FF 3E FF  90 21 8D 84  ......4...>..!..
0034FF50: 01 00 00 00  03 2A 01 10  00 00 00 00  00 00 00 00  .....*..........
0034FF60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FF70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FF80: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FF90: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FFA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FFB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FFC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................


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
Processor Revision:     11266

Percent memory used:    75
Total physical memory:  527421440
Free Memory:            128532480
Page file:              2147483647
Total virtual memory:   2147352575
-------------------------------------------------------------------
i've already reinstalled it and it keep happening.

---

