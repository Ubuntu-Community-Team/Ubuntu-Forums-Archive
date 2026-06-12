---
title: "WoW error, can't get it to work"
date: 2008-09-27
forum: Gaming &amp; Leisure
---

### Post by eldutcho on 2008-09-27
I've been trying for about 2 months to get WoW to work on my acer laptop. I can get it to boot up but right before it goes to the login scree I get this error:

This application has encountered a critical error:



ERROR #132 (0x85100084) Fatal Exception

Program:	C:\World of Warcraft\WoW.exe

Exception:	0xC0000005 (ACCESS_VIOLATION) at 0023:7C06A7A8



The instruction at "0x7C06A7A8" referenced memory at "0x7C06A7A8".

The memory could not be "written".





WoWBuild: 6080

------------------------------------------------------------------------------



----------------------------------------

    x86 Registers

----------------------------------------



EAX=0033F6F8  EBX=737FC124  ECX=00134328  EDX=737FCDC0  ESI=00000000

EDI=737E9267  EBP=0033F714  ESP=0033F6C8  EIP=7C06A7A8  FLG=00010202

CS =0023      DS =002B      ES =002B      SS =002B      FS =0063      GS =006B





----------------------------------------

    Stack Trace (Manual)

----------------------------------------



Address  Frame    Logical addr  Module



7C06A7A8 0033F714 0000:00000000 C:\World of Warcraft\WoW.exe

7372F91C 0033F794 0001:0001E91C C:\windows\system32\wined3d.dll

7376450B 0033FAA4 0001:0005350B C:\windows\system32\wined3d.dll

7373C19B 0033FB14 0001:0002B19B C:\windows\system32\wined3d.dll

7BBE6C5E 0033FB44 0001:00005C5E C:\windows\system32\d3d9.dll

005D75E0 0033FB78 0001:001D65E0 C:\World of Warcraft\WoW.exe

005C0B68 0033FB94 0001:001BFB68 C:\World of Warcraft\WoW.exe

005C0B7B 0033FBBC 0001:001BFB7B C:\World of Warcraft\WoW.exe

007D93C5 0033FCA0 0001:003D83C5 C:\World of Warcraft\WoW.exe

007D956D 0033FCC4 0001:003D856D C:\World of Warcraft\WoW.exe

007B2B17 0033FCE8 0001:003B1B17 C:\World of Warcraft\WoW.exe

007B13CC 0033FCF4 0001:003B03CC C:\World of Warcraft\WoW.exe

0044305E 0033FDBC 0001:0004205E C:\World of Warcraft\WoW.exe

00425090 0033FDF0 0001:00024090 C:\World of Warcraft\WoW.exe

00421A4F 0033FE60 0001:00020A4F C:\World of Warcraft\WoW.exe

004215D1 0033FE78 0001:000205D1 C:\World of Warcraft\WoW.exe

0040447E 0033FF08 0001:0000347E C:\World of Warcraft\WoW.exe

7B877B27 0033FFE8 0001:00056B27 C:\windows\system32\KERNEL32.dll



----------------------------------------

    Stack Trace (Using DBGHELP.DLL)

----------------------------------------



7C06A7A8 <unknown module> <unknown symbol>+0 (0x000000D8,0x0013A9A8,0x026400A0,0x00000003)

7372F91C wined3d.dll  ActivateContext+1276 (0x00134328,0x001484C0,0x00000002,0x7BC88444)

7376450B wined3d.dll  drawPrimitive+379 (0x00134328,0x00000005,0x00000002,0x00000000)

7373C19B wined3d.dll  <unknown symbol>+0 (0x00134328,0x00000005,0x00000000,0x00000004)

7BBE6C5E d3d9.dll     <unknown symbol>+0 (0x00136640,0x00000005,0x00000000,0x00000000)

005D75E0 WoW.exe      <unknown symbol>+0 (0x00000001,0x00000000,0x00000001,0x00000004)

005C0B68 WoW.exe      <unknown symbol>+0 (0x00000001,0x005C066A,0x06F08B94,0x00000000)

005C0B7B WoW.exe      <unknown symbol>+0 (0x008A3778,0x06B1D484,0x06F08808,0x066996A8)

007D93C5 WoW.exe      <unknown symbol>+0 (0x00000000,0x007BC481,0x00000001,0x06B1D408)

007D956D WoW.exe      <unknown symbol>+0 (0x013E2308,0x06ABC008,0x0696B108,0x00000000)

007B2B17 WoW.exe      <unknown symbol>+0 (0x0696B120,0x0033FDBC,0x0044305E,0x0696B120)

007B13CC WoW.exe      <unknown symbol>+0 (0x0696B120,0x41061CAC,0x0033FDD0,0x0122DE28)

0044305E WoW.exe      <unknown symbol>+0 (0x0122E018,0x0122E008,0x00000000,0x0122DE28)

00425090 WoW.exe      <unknown symbol>+0 (0x00000000,0x00000102,0x0122E008,0x00000000)

00421A4F WoW.exe      <unknown symbol>+0 (0x00000000,0x00402489,0x00000001,0x00000001)

004215D1 WoW.exe      <unknown symbol>+0 (0x0040A380,0x00400000,0x00000000,0x0011184E)

0040447E WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)

7B877B27 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)





----------------------------------------

    Loaded Modules

----------------------------------------



0x00340000 - 0x003D0000  C:\World of Warcraft\fmod.dll

0x00400000 - 0x00D89000  C:\World of Warcraft\WoW.exe

0x10000000 - 0x10069000  C:\World of Warcraft\DivxDecoder.dll

0x736C0000 - 0x736FD000  C:\windows\system32\dbghelp.dll

0x73710000 - 0x73800000  C:\windows\system32\wined3d.dll

0x7B820000 - 0x7B92D000  C:\windows\system32\KERNEL32.dll

0x7B960000 - 0x7B99F000  C:\windows\system32\dsound.dll

0x7BBB0000 - 0x7BBB8000  C:\windows\system32\psapi.dll

0x7BBE0000 - 0x7BC00000  C:\windows\system32\d3d9.dll

0x7BC10000 - 0x7BCA4000  C:\windows\system32\ntdll.dll

0x7BCB0000 - 0x7BCBB000  C:\windows\system32\mswsock.dll

0x7BEF0000 - 0x7BF00000  C:\windows\system32\midimap.dll

0x7BFD0000 - 0x7C000000  C:\windows\system32\winealsa.drv

0x7C3C0000 - 0x7C3CC000  C:\windows\system32\msacm32.drv

0x7E2B0000 - 0x7E2E0000  C:\windows\system32\uxtheme.dll

0x7E320000 - 0x7E3AB000  C:\windows\system32\winex11.drv

0x7E4B0000 - 0x7E4C1000  C:\windows\system32\mpr.dll

0x7E4D0000 - 0x7E50F000  C:\windows\system32\wininet.dll

0x7E520000 - 0x7E570000  C:\windows\system32\rpcrt4.dll

0x7E580000 - 0x7E614000  C:\windows\system32\ole32.dll

0x7E620000 - 0x7E67E000  C:\windows\system32\msvcrt.dll

0x7E680000 - 0x7E6A4000  C:\windows\system32\msacm32.dll

0x7E6B0000 - 0x7E6B8000  C:\windows\system32\lz32.dll

0x7E6C0000 - 0x7E6D1000  C:\windows\system32\version.dll

0x7E6E0000 - 0x7E763000  C:\windows\system32\winmm.dll

0x7E770000 - 0x7E783000  C:\windows\system32\imm32.dll

0x7E930000 - 0x7E996000  C:\windows\system32\opengl32.dll

0x7E9B0000 - 0x7E9C7000  C:\windows\system32\iphlpapi.dll

0x7E9D0000 - 0x7E9F3000  C:\windows\system32\ws2_32.dll

0x7EA00000 - 0x7EA0D000  C:\windows\system32\wsock32.dll

0x7EA20000 - 0x7EA66000  C:\windows\system32\shlwapi.dll

0x7EA80000 - 0x7EB78000  C:\windows\system32\shell32.dll

0x7EB90000 - 0x7EC13000  C:\windows\system32\gdi32.dll

0x7EC30000 - 0x7ED5A000  C:\windows\system32\user32.dll

0x7ED60000 - 0x7EE19000  C:\windows\system32\comctl32.dll

0x7EE30000 - 0x7EE6B000  C:\windows\system32\advapi32.dll





----------------------------------------

    Memory Dump

----------------------------------------



Code: 16 bytes starting at (EIP = 7C06A7A8)



7C06A7A8: A1 60 A9 81  7E 85 C0 74  06 FF A0 E0  0C 00 00 E8  .`..~..t........





Stack: 1024 bytes starting at (ESP = 0033F6C8)



* = addr                            **                                *       

0033F6C0: C0 84 00 00  14 F7 33 00  B9 B2 78 73  75 87 00 00  ......3...xsu...

0033F6D0: F8 F6 33 00  00 00 00 00  04 00 00 00  02 00 00 00  ..3.............

0033F6E0: 01 00 00 00  01 00 00 00  31 B7 78 73  67 92 7E 73  ........1.xsg.~s

0033F6F0: 00 00 80 3F  67 92 7E 73  00 00 00 00  00 00 00 00  ...?g.~s........

0033F700: 00 00 00 00  00 00 00 00  24 C1 7F 73  06 00 00 00  ........$..s....

0033F710: 43 00 00 00  94 F7 33 00  1C F9 72 73  D8 00 00 00  C.....3...rs....

0033F720: A8 A9 13 00  A0 00 64 02  03 00 00 00  00 00 00 03  ......d.........

0033F730: 00 00 2D 00  CB A5 7A 73  24 C1 7F 73  08 51 13 00  ..-...zs$..s.Q..

0033F740: 9C 63 7F 73  94 F7 33 00  8E 78 79 73  08 51 13 00  .c.s..3..xys.Q..

0033F750: 9C 63 7F 73  94 FA 33 00  AE 79 79 73  00 00 00 00  .c.s..3..yys....

0033F760: A0 00 64 02  00 80 7F 73  8C A1 7A 73  D0 02 00 00  ..d....s..zs....

0033F770: 37 36 C7 7B  26 C8 F5 72  43 00 00 00  D0 02 00 00  76.{&..rC.......

0033F780: 44 84 C8 7B  00 00 00 00  24 C1 7F 73  1C D7 7F 73  D..{....$..s...s

0033F790: 28 43 13 00  A4 FA 33 00  0B 45 76 73  28 43 13 00  (C....3..Evs(C..

0033F7A0: C0 84 14 00  02 00 00 00  44 84 C8 7B  CC F8 33 00  ........D..{..3.

0033F7B0: 50 F8 33 00  C9 5E DE F7  F4 F7 33 00  03 00 00 00  P.3..^....3.....

0033F7C0: 00 00 11 00  FF FF 00 00  80 FE D1 7E  00 00 00 00  ...........~....

0033F7D0: 00 00 00 00  90 71 DD F7  4C 00 05 00  79 83 DB F7  .....q..L...y...

0033F7E0: 9C 63 7F 73  00 00 AA 09  00 00 2D 00  FF FF 00 00  .c.s......-.....

0033F7F0: 0C F8 33 00  00 00 02 00  00 00 00 00  9C F8 33 00  ..3...........3.

0033F800: C9 5E DE F7  00 00 00 00  10 01 00 00  5C F8 33 00  .^..........\.3.

0033F810: 23 4A C7 7B  96 C4 F5 72  03 00 00 00  10 01 00 00  #J.{...r........

0033F820: 00 00 77 09  00 00 00 00  70 F8 33 00  29 0D D6 F7  ..w.....p.3.)...

0033F830: 40 00 00 00  20 07 98 09  88 F8 33 00  CF 33 C4 7B  @... .....3..3.{

0033F840: 40 00 00 00  44 84 C8 7B  B0 F8 00 00  00 00 88 09  @...D..{........

0033F850: 60 07 98 09  00 00 99 09  00 00 11 00  44 84 C8 7B  `...........D..{

0033F860: 18 07 98 09  30 00 00 00  88 F8 33 00  2E 2A C4 7B  ....0.....3..*.{

0033F870: 90 F9 33 00  00 00 11 00  60 07 98 09  7F 37 C3 7B  ..3.....`....7.{

0033F880: 18 07 98 09  44 84 C8 7B  E8 F8 33 00  FE 3C C4 7B  ....D..{..3..<.{

0033F890: 48 00 11 00  00 00 11 00  44 84 C8 7B  F0 F8 33 00  H.......D..{..3.

0033F8A0: AC 74 F2 F7  FC CC 7F 73  E8 F8 33 00  52 A0 E0 F7  .t.....s..3.R...

0033F8B0: FC CC 7F 73  30 00 AA 09  00 00 00 00  00 00 00 00  ...s0...........

0033F8C0: 20 07 98 09  00 00 11 00  02 00 00 00  CF 33 C4 7B   ............3.{

0033F8D0: 17 2F C4 7B  FF FF FF FF  00 00 88 09  24 C1 7F 73  ./.{........$..s

0033F8E0: 30 00 00 00  70 17 1B 09  78 F9 33 00  DD C9 7C 73  0...p...x.3...|s

0033F8F0: 20 07 98 09  E8 06 98 09  30 00 00 00  E4 47 7F 73   .......0....G.s

0033F900: 70 17 1B 09  09 00 00 00  38 00 00 00  00 00 88 09  p.......8.......

0033F910: F0 06 98 09  18 07 98 09  00 00 11 00  44 84 C8 7B  ............D..{

0033F920: E0 06 98 09  38 00 00 00  78 F9 33 00  A6 2A C4 7B  ....8...x.3..*.{

0033F930: E8 06 98 09  20 00 00 00  04 00 00 00  85 12 C4 7B  .... ..........{

0033F940: 00 00 AA 09  00 00 11 00  98 00 A9 09  4E 1B C4 7B  ............N..{

0033F950: 70 17 1B 09  00 00 11 00  00 00 88 09  D9 60 BE 7B  p............`.{

0033F960: 00 00 00 00  00 00 00 00  00 00 88 09  7F 37 C3 7B  .............7.{

0033F970: 00 00 88 09  44 84 C8 7B  B8 F9 33 00  37 2D C4 7B  ....D..{..3.7-.{

0033F980: 78 F6 BF 7B  01 00 00 00  B8 F9 33 00  B2 39 BF 7B  x..{......3..9.{

0033F990: 40 66 13 00  00 00 11 00  02 00 00 00  D1 3D C3 7B  @f...........=.{

0033F9A0: 49 9B 7C 73  00 00 11 00  02 00 00 00  78 F6 BF 7B  I.|s........x..{

0033F9B0: 7C FE BF 7B  00 00 00 00  08 FA 33 00  00 01 00 00  |..{......3.....

0033F9C0: E8 03 00 00  00 00 00 00  00 00 00 00  0C FA 33 00  ..............3.

0033F9D0: 25 2B 74 73  28 43 13 00  E6 03 00 00  E8 03 00 00  %+ts(C..........

0033F9E0: 28 43 13 00  70 17 1B 09  18 FA 33 00  08 55 73 73  (C..p.....3..Uss

0033F9F0: D1 3D C3 7B  E8 03 00 00  E8 06 98 09  80 FE BF 7B  .=.{...........{

0033FA00: 7F 37 C3 7B  40 2A 74 73  78 F6 BF 7B  3C FA 33 00  .7.{@*tsx..{<.3.

0033FA10: 5C 68 BE 7B  7C FE BF 7B  00 00 00 00  68 06 98 09  \h.{|..{....h...

0033FA20: 00 00 00 00  20 00 00 00  01 00 00 00  00 00 00 00  .... ...........

0033FA30: 58 FA 33 00  08 80 22 01  00 00 00 00  58 FB 33 00  X.3...".....X.3.

0033FA40: CB 88 5D 00  40 66 13 00  00 00 00 00  D8 16 17 09  ..].@f..........

0033FA50: 00 00 00 00  20 00 00 00  20 00 00 00  00 00 00 00  .... ... .......

0033FA60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

0033FA70: 00 00 00 00  00 00 00 00  DE 0C 77 73  00 00 00 00  ..........ws....

0033FA80: 00 00 00 00  00 00 00 00  00 00 00 00  88 FA 21 01  ..............!.

0033FA90: 00 00 00 00  08 51 13 00  24 C1 7F 73  02 00 00 00  .....Q..$..s....

0033FAA0: F0 16 17 09  14 FB 33 00  9B C1 73 73  28 43 13 00  ......3...ss(C..

0033FAB0: 05 00 00 00  02 00 00 00  00 00 00 00  04 00 00 00  ................

0033FAC0: 00 00 00 00  02 00 00 00  60 17 17 09  00 00 00 00  ........`.......





------------------------------------------------------------------------------


any help is appreciated, I want to keep using using Linux but WoW withdrawal is kicking in. Oh, when this error happens i can hear the music on the login screen, but its just black. Thanks in advance

---

### Post by eldutcho on 2008-09-27
oops i just read the sticky, I'll post it in the wine section

---

