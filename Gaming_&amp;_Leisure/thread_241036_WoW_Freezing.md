---
title: "WoW Freezing"
date: 2006-08-21
forum: Gaming &amp; Leisure
---

### Post by notoriouslou1022 on 2006-08-21
I have to newest version of WINE installed and when i installed WoW following this guide.[]("https://help.ubuntu.com/community/WorldofWarcraft"). I have no problem loggin in or anything and i have played for awhile and everything work fine. But sometimes i loggin and start playing for 3 seconds and EVERYTHING freezes, even my system and I am forced to turn of my computer. Also my video card is configured correctly. If you want anyother information just ask. Thank you guys. ;)

---

### Post by hikaricore on 2006-08-21
Just curious does this happen more often zoning into cities or buildings?  There is a known issue involving the minimap causing crashes on zonein or entering certain areas since the last patch.  There's also a mod to resolve this issue, but I don't have the link handy.

---

### Post by notoriouslou1022 on 2006-08-22
I'm afriad no... but can you post that link if you have time?  Thanks ;)

---

### Post by hikaricore on 2006-08-22
[http://www.curse-gaming.com/en/wow/addons-4147-1-minimap-autohide.html](http://www.curse-gaming.com/en/wow/addons-4147-1-minimap-autohide.html)

here it is :)

---

### Post by Toxicity999 on 2006-08-22
Any specifics on where it happens, what happens, and the hardware your running? Certain cards might have issues with specifics things... also are you using A Cedega front or wine standalone?

---

### Post by notoriouslou1022 on 2006-08-22
I'm just using wine and my video cards is a readon x600.

---

### Post by notoriouslou1022 on 2006-08-23
Does this help anything. Please keep helpin. :wink: Thanks



```
==============================================================================

World of WarCraft (build 5464)



Exe:      C:\Program_Files\World_of_Warcraft\WoW.exe

Time:     Aug 20, 2006  5:07:23.175 AM

User:     luigi

Computer: luigi-desktop

------------------------------------------------------------------------------



This application has encountered a critical error:



ERROR #132 (0x85100084) Fatal Exception

Program:	C:\Program_Files\World_of_Warcraft\WoW.exe

Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:0048BA7D



The instruction at "0x0048BA7D" referenced memory at "0x00000000".

The memory could not be "read".





WoWBuild: 5464

------------------------------------------------------------------------------



----------------------------------------

    x86 Registers

----------------------------------------



EAX=00000000  EBX=0106BD08  ECX=00000018  EDX=00000018  ESI=00000000

EDI=0106BC08  EBP=0033FAC4  ESP=0033FA88  EIP=0048BA7D  FLG=00210246

CS =0073      DS =007B      ES =007B      SS =007B      FS =003B      GS =0033





----------------------------------------

    Stack Trace (Manual)

----------------------------------------



Address  Frame    Logical addr  Module



0048BA7D 0033FAC4 0001:0008AA7D C:\Program_Files\World_of_Warcraft\WoW.exe

006ED3DA 0033FADC 0001:002EC3DA C:\Program_Files\World_of_Warcraft\WoW.exe

006F0461 0033FB24 0001:002EF461 C:\Program_Files\World_of_Warcraft\WoW.exe

006ED81F 0033FB34 0001:002EC81F C:\Program_Files\World_of_Warcraft\WoW.exe

006EB48B 0033FB9C 0001:002EA48B C:\Program_Files\World_of_Warcraft\WoW.exe

006EDBCB 0033FBC4 0001:002ECBCB C:\Program_Files\World_of_Warcraft\WoW.exe

006EB46C 0033FBE8 0001:002EA46C C:\Program_Files\World_of_Warcraft\WoW.exe

006FC3DE 0033FC74 0001:002FB3DE C:\Program_Files\World_of_Warcraft\WoW.exe

006F9977 0033FC90 0001:002F8977 C:\Program_Files\World_of_Warcraft\WoW.exe

006F9938 0033FCA8 0001:002F8938 C:\Program_Files\World_of_Warcraft\WoW.exe

00770246 0033FCDC 0001:0036F246 C:\Program_Files\World_of_Warcraft\WoW.exe

0077000F 0033FD00 0001:0036F00F C:\Program_Files\World_of_Warcraft\WoW.exe

0075D127 0033FD54 0001:0035C127 C:\Program_Files\World_of_Warcraft\WoW.exe

00424490 0033FD88 0001:00023490 C:\Program_Files\World_of_Warcraft\WoW.exe

00423EF5 0033FDBC 0001:00022EF5 C:\Program_Files\World_of_Warcraft\WoW.exe

004238BA 0033FDD4 0001:000228BA C:\Program_Files\World_of_Warcraft\WoW.exe

00423751 0033FE04 0001:00022751 C:\Program_Files\World_of_Warcraft\WoW.exe

00420B08 0033FE60 0001:0001FB08 C:\Program_Files\World_of_Warcraft\WoW.exe

004209D1 0033FE78 0001:0001F9D1 C:\Program_Files\World_of_Warcraft\WoW.exe

00403F1E 0033FF08 0001:00002F1E C:\Program_Files\World_of_Warcraft\WoW.exe

7EEA3A6F 0033FFE8 0001:00052A6F c:\windows\system32\kernel32.dll



----------------------------------------

    Stack Trace (Using DBGHELP.DLL)

----------------------------------------



0048BA7D WoW.exe      <unknown symbol>+0 (0x0557A988,0x00000059,0x00000000,0x00000080)

006ED3DA WoW.exe      <unknown symbol>+0 (0x0D522068,0x0557A988,0x07A18808,0x00000000)

006F0461 WoW.exe      <unknown symbol>+0 (0x0557A988,0x006EB480,0x0033FB9C,0x006EB48B)

006ED81F WoW.exe      <unknown symbol>+0 (0x00000000,0x006ED027,0x00000000,0x0557A988)

006EB48B WoW.exe      <unknown symbol>+0 (0x0033FBE0,0x0D522008,0x00000050,0x07A18808)

006EDBCB WoW.exe      <unknown symbol>+0 (0x0033FBE0,0x00000060,0x00000050,0xFFFFFFFF)

006EB46C WoW.exe      <unknown symbol>+0 (0x00000000,0xFFFFFFFE,0x3A474244,0x6974704F)

006FC3DE WoW.exe      <unknown symbol>+0 (0x00000C2C,0x07A18808,0x07A0BCA8,0x0033FC1C)

006F9977 WoW.exe      <unknown symbol>+0 (0x07A18808,0x07A18CD4,0x00824200,0x0033FCBC)

006F9938 WoW.exe      <unknown symbol>+0 (0x07A18808,0x07A18CD4,0x00824200,0x0086D8E0)

00770246 WoW.exe      <unknown symbol>+0 (0x00000001,0x00000000,0x0033FD98,0x071C8008)

0077000F WoW.exe      <unknown symbol>+0 (0x00000001,0x0033FD68,0x07AB41C8,0x07AB41C8)

0075D127 WoW.exe      <unknown symbol>+0 (0x0033FE5C,0x011C2408,0x00000001,0x07AB41C8)

00424490 WoW.exe      <unknown symbol>+0 (0x0033FD98,0x011C2408,0x00000000,0x00000001)

00423EF5 WoW.exe      <unknown symbol>+0 (0x0000030E,0x0000036A,0x00000000,0x000169B1)

004238BA WoW.exe      <unknown symbol>+0 (0x0033FDF0,0x0033FE5C,0x00000000,0x00000102)

00423751 WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x7EEDC8A8,0x69676E45)

00420B08 WoW.exe      <unknown symbol>+0 (0x00000000,0x004021D9,0x00000001,0x00000001)

004209D1 WoW.exe      <unknown symbol>+0 (0x00409780,0x00400000,0x00000000,0x00116579)

00403F1E WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)

7EEA3A6F kernel32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)

B7E85287              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)





----------------------------------------

    Loaded Modules

----------------------------------------



0x00340000 - 0x003D6000  C:\Program_Files\World_of_Warcraft\fmod.dll

0x00400000 - 0x00CFA000  C:\Program_Files\World_of_Warcraft\WoW.exe

0x10000000 - 0x10069000  C:\Program_Files\World_of_Warcraft\DivxDecoder.dll

0x6E670000 - 0x6E6A7000  c:\windows\system32\dbghelp.dll

0x71710000 - 0x7171B000  c:\windows\system32\psapi.dll

0x7BFD0000 - 0x7BFDE000  c:\windows\system32\mswsock.dll

0x7BFF0000 - 0x7C000000  c:\windows\system32\midimap.dll

0x7C390000 - 0x7C3C0000  c:\windows\system32\wineoss.drv

0x7CFA0000 - 0x7CFC6000  c:\windows\system32\uxtheme.dll

0x7E240000 - 0x7E2AF000  c:\windows\system32\winex11.drv

0x7E380000 - 0x7E398000  c:\windows\system32\mpr.dll

0x7E3A0000 - 0x7E3DF000  c:\windows\system32\wininet.dll

0x7E3F0000 - 0x7E441000  c:\windows\system32\msvcrt.dll

0x7E450000 - 0x7E467000  c:\windows\system32\msacm32.drv

0x7E470000 - 0x7E4EF000  c:\windows\system32\winmm.dll

0x7E500000 - 0x7E50B000  c:\windows\system32\imm32.dll

0x7E750000 - 0x7E7A9000  c:\windows\system32\opengl32.dll

0x7E7B0000 - 0x7E7D3000  c:\windows\system32\ws2_32.dll

0x7E7E0000 - 0x7E7ED000  c:\windows\system32\wsock32.dll

0x7E810000 - 0x7E81F000  c:\windows\system32\iphlpapi.dll

0x7E830000 - 0x7E86E000  c:\windows\system32\rpcrt4.dll

0x7E880000 - 0x7E8FE000  c:\windows\system32\ole32.dll

0x7E910000 - 0x7E954000  c:\windows\system32\shlwapi.dll

0x7E960000 - 0x7EA3A000  c:\windows\system32\shell32.dll

0x7EB30000 - 0x7EBCB000  c:\windows\system32\gdi32.dll

0x7EBF0000 - 0x7ECFE000  c:\windows\system32\user32.dll

0x7ED10000 - 0x7EDC0000  c:\windows\system32\comctl32.dll

0x7EDD0000 - 0x7EE04000  c:\windows\system32\advapi32.dll

0x7EE50000 - 0x7EF38000  c:\windows\system32\kernel32.dll

0x7EF90000 - 0x7F000000  c:\windows\system32\ntdll.dll





----------------------------------------

    Memory Dump

----------------------------------------



Code: 16 bytes starting at (EIP = 0048BA7D)



0048BA7D: 3B 0C 06 75  13 3B 54 06  04 75 0D 8B  4D F8 3B 4C  ;..u.;T..u..M.;L





Stack: 1024 bytes starting at (ESP = 0033FA88)



* = addr                            **                                *       

0033FA80: 08 BD 06 01  4B BA 48 00  D0 B9 48 00  88 A9 57 05  ....K.H...H...W.

0033FA90: 88 20 52 0D  88 A9 57 05  A8 8A 51 07  A8 8A 51 07  . R...W...Q...Q.

0033FAA0: B4 FA 33 00  86 1A 6F 00  88 20 52 0D  A8 8A 51 07  ..3...o.. R...Q.

0033FAB0: 88 A9 57 05  D4 FA 33 00  00 05 00 00  01 00 00 00  ..W...3.........

0033FAC0: 08 65 1B 01  DC FA 33 00  DA D3 6E 00  88 A9 57 05  .e....3...n...W.

0033FAD0: 59 00 00 00  00 00 00 00  80 00 00 00  24 FB 33 00  Y...........$.3.

0033FAE0: 61 04 6F 00  68 20 52 0D  88 A9 57 05  08 88 A1 07  a.o.h R...W.....

0033FAF0: 00 00 00 00  02 00 00 00  80 B4 6E 00  88 B0 C7 7E  ..........n....~

0033FB00: 60 43 CC 7E  00 00 00 00  28 FB 33 00  00 00 00 00  `C.~....(.3.....

0033FB10: 88 04 61 07  08 20 22 07  88 20 52 0D  60 AA 20 07  ..a.. ".. R.`. .

0033FB20: 88 A9 57 05  34 FB 33 00  1F D8 6E 00  88 A9 57 05  ..W.4.3...n...W.

0033FB30: 80 B4 6E 00  9C FB 33 00  8B B4 6E 00  00 00 00 00  ..n...3...n.....

0033FB40: 27 D0 6E 00  00 00 00 00  88 A9 57 05  00 00 00 00  '.n.......W.....

0033FB50: 9C FB 33 00  08 88 A1 07  00 00 00 00  88 A9 57 05  ..3...........W.

0033FB60: 38 FB 33 00  0C D0 6E 00  F8 FE 33 00  00 00 00 00  8.3...n...3.....

0033FB70: 30 32 43 56  00 00 00 00  00 00 00 00  00 00 00 00  02CV............

0033FB80: 7C FC 33 00  64 FC 33 00  CA 3D FD 7E  02 00 00 00  |.3.d.3..=.~....

0033FB90: 00 00 00 00  80 B4 6E 00  88 A9 57 05  C4 FB 33 00  ......n...W...3.

0033FBA0: CB DB 6E 00  E0 FB 33 00  08 20 52 0D  50 00 00 00  ..n...3.. R.P...

0033FBB0: 08 88 A1 07  00 00 00 00  00 00 00 00  88 A9 00 00  ................

0033FBC0: E0 FB 33 01  E8 FB 33 00  6C B4 6E 00  E0 FB 33 00  ..3...3.l.n...3.

0033FBD0: 60 00 00 00  50 00 00 00  FF FF FF FF  88 A9 57 05  `...P.........W.

0033FBE0: 68 20 52 0D  00 00 00 00  74 FC 33 00  DE C3 6F 00  h R.....t.3...o.

0033FBF0: 00 00 00 00  FE FF FF FF  44 42 47 3A  4F 70 74 69  ........DBG:Opti

0033FC00: 6F 6E 73 46  72 61 6D 65  4F 6B 61 79  00 C3 6F 00  onsFrameOkay..o.

0033FC10: 01 00 00 00  00 00 00 00  B1 69 01 00  FF FF FF FF  .........i......

0033FC20: 31 BB C6 7E  00 00 00 00  88 52 FF 7E  01 00 00 00  1..~.....R.~....

0033FC30: 8C FC 33 00  C4 FC 33 00  2A 73 FD 7E  4C FC 33 00  ..3...3.*s.~L.3.

0033FC40: AC FC 33 00  12 60 58 00  4C FC 33 00  00 00 00 00  ..3..`X.L.3.....

0033FC50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

0033FC60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

0033FC70: 01 00 00 00  90 FC 33 00  77 99 6F 00  2C 0C 00 00  ......3.w.o.,...

0033FC80: 08 88 A1 07  A8 BC A0 07  1C FC 33 00  08 88 A1 07  ..........3.....

0033FC90: A8 FC 33 00  38 99 6F 00  08 88 A1 07  D4 8C A1 07  ..3.8.o.........

0033FCA0: 00 42 82 00  BC FC 33 00  DC FC 33 00  46 02 77 00  .B....3...3.F.w.

0033FCB0: 08 88 A1 07  D4 8C A1 07  00 42 82 00  E0 D8 86 00  .........B......

0033FCC0: 18 FD 33 00  08 88 A1 07  B1 69 01 00  00 00 00 00  ..3......i......

0033FCD0: 7F 0E 7F 02  E4 FC 33 00  95 B5 42 00  00 FD 33 00  ......3...B...3.

0033FCE0: 0F 00 77 00  01 00 00 00  00 00 00 00  98 FD 33 00  ..w...........3.

0033FCF0: 08 80 1C 07  08 88 A1 07  79 41 F4 3E  95 68 BB 3D  ........yA.>.h.=

0033FD00: 54 FD 33 00  27 D1 75 00  01 00 00 00  68 FD 33 00  T.3.'.u.....h.3.

0033FD10: C8 41 AB 07  C8 41 AB 07  DC 83 7F 00  00 00 00 00  .A...A..........

0033FD20: C9 00 05 40  00 00 00 00  00 00 00 00  01 00 00 00  ...@............

0033FD30: 00 00 00 00  00 00 00 00  00 00 00 00  79 41 F4 3E  ............yA.>

0033FD40: 95 68 BB 3D  8A 69 01 00  B1 69 01 00  00 00 00 00  .h.=.i...i......

0033FD50: C0 1E 49 00  88 FD 33 00  90 44 42 00  5C FE 33 00  ..I...3..DB.\.3.

0033FD60: 08 24 1C 01  01 00 00 00  C8 41 AB 07  11 25 1C 01  .$.......A...%..

0033FD70: 00 04 00 00  6A 03 00 00  00 05 00 00  01 00 00 00  ....j...........

0033FD80: 0E 00 00 00  0C 25 1C 01  BC FD 33 00  F5 3E 42 00  .....%....3..>B.

0033FD90: 98 FD 33 00  08 24 1C 01  00 00 00 00  01 00 00 00  ..3..$..........

0033FDA0: 00 00 00 00  00 00 00 00  00 00 00 00  66 66 1C 3F  ............ff.?

0033FDB0: 00 00 16 3E  8A 69 01 00  B1 69 01 00  D4 FD 33 00  ...>.i...i....3.

0033FDC0: BA 38 42 00  0E 03 00 00  6A 03 00 00  00 00 00 00  .8B.....j.......

0033FDD0: B1 69 01 00  04 FE 33 00  51 37 42 00  F0 FD 33 00  .i....3.Q7B...3.

0033FDE0: 5C FE 33 00  00 00 00 00  02 01 00 00  08 24 1C 01  \.3..........$..

0033FDF0: 01 00 00 00  0E 03 00 00  6A 03 00 00  B1 69 01 00  ........j....i..

0033FE00: 0D 00 00 00  60 FE 33 00  08 0B 42 00  00 F0 FD 7F  ....`.3...B.....

0033FE10: 00 00 00 00  A8 C8 ED 7E  45 6E 67 69  6E 65 20 39  .......~Engine 9

0033FE20: 00 00 11 00  A0 BD 16 00  06 00 00 00  27 9C FA 7E  ............'..~

0033FE30: 65 6E 00 7E  A8 C8 ED 7E  00 F0 FD 7F  5C FE 33 00  en.~...~....\.3.

0033FE40: 14 79 EB 7E  98 20 00 00  00 00 00 00  64 FE 33 00  .y.~. ......d.3.

0033FE50: 57 44 42 43  A8 C8 ED 7E  B1 69 01 00  00 00 00 00  WDBC...~.i......

0033FE60: 78 FE 33 00  D1 09 42 00  00 00 00 00  D9 21 40 00  x.3...B......!@.

0033FE70: 01 00 00 00  01 00 00 00  08 FF 33 00  1E 3F 40 00  ..........3..?@.

0033FE80: 80 97 40 00  00 00 40 00  00 00 00 00  79 65 11 00  ..@...@.....ye..





------------------------------------------------------------------------------


```

---

