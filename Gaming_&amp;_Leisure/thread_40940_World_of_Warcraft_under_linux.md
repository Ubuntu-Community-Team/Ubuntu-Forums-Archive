---
title: "World of Warcraft under linux"
date: 2005-06-11
forum: Gaming &amp; Leisure
---

### Post by Comrad on 2005-06-11
I am trying to run World of Warcraft on linux with wine.  But all that happens is that i get a ton of error messages in the consol window i am launching the game from. And then the WoW client crashes and shows some error messages. 
If anyone could help me i would greatly appreciate it
Below is the output from both World of warcraft and the consoll

Thanks in advance




The output from World of warcraft:
```

==============================================================================
World of WarCraft (build 4442)

Exe:      C:\Program Files\World of Warcraft\WoW.exe
Time:     Jun  9, 2005 10:32:28.965 PM
User:     chhenni
Computer: UberBoxLin
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084)
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7698FE23

The instruction at "0x7698FE23" referenced memory at "0x00000084".
The memory could not be "read".


WoWBuild: 4442
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=7797F204  EBX=769A6384  ECX=7797F210  EDX=00000000  ESI=00000001
EDI=77C644C0  EBP=7797F61C  ESP=7797F1D0  EIP=7698FE23  FLG=00010202
CS =0073      DS =007B      ES =007B      SS =007B      FS =003B      GS =0033


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

7698FE23 7797F61C 0001:0003EE23 c:\windows\system\opengl32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

7698FE23 opengl32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000400,0x00000300)
005616D7 WoW.exe      <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x00AD5000  WoW.exe
0x02800000 - 0x028D1000  dbghelp.dll
0x10000000 - 0x10069000  DivxDecoder.dll
0x76540000 - 0x76557000  mpr.dll
0x76560000 - 0x7659C000  wininet.dll
0x765A0000 - 0x765C0000  msacm32.dll
0x765C0000 - 0x76650000  fmod.dll
0x76670000 - 0x766D8000  winmm.dll
0x766E0000 - 0x766F7000  imm32.dll
0x76950000 - 0x769A8000  opengl32.dll
0x769B0000 - 0x769D3000  ws2_32.dll
0x769E0000 - 0x769F0000  wsock32.dll
0x76A00000 - 0x76A10000  iphlpapi.dll
0x76A30000 - 0x76A5A000  rpcrt4.dll
0x76A70000 - 0x76AE8000  ole32.dll
0x76B00000 - 0x76B46000  shlwapi.dll
0x76B60000 - 0x76C0D000  shell32.dll
0x76C20000 - 0x76C4D000  advapi32.dll
0x76D70000 - 0x77629000  gdi32.dll
0x77650000 - 0x7775B000  user32.dll
0x77770000 - 0x7781D000  comctl32.dll
0x77830000 - 0x77880000  msvcrt.dll
0x77B20000 - 0x77C10000  kernel32.dll
0x77EA0000 - 0x77F00000  ntdll.dll
0x7F2D0000 - 0x7F30D000  unicows.dll
0x7F760000 - 0x7F782000  msvfw32.dll
0x7F790000 - 0x7F796000  avicap32.dll
0x7F7A0000 - 0x7F7B0000  oledlg.dll
0x7F7C0000 - 0x7F7C6000  lz32.dll
0x7F7D0000 - 0x7F7E1000  version.dll
0x7F7F0000 - 0x7F809000  winspool.drv
0x7F820000 - 0x7F89B000  comdlg32.dll
0x7F8A0000 - 0x7F8B0000  midimap.drv
0x7F9D0000 - 0x7F9DB000  msacm.drv
0x7F9F0000 - 0x7FA20000  wineoss.drv
0x7FEC0000 - 0x7FF2F000  x11drv.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 7698FE23)

7698FE23: 8B 82 84 00  00 00 89 14  24 89 44 24  04 E8 E3 1F  ........$.D$....


Stack: 1024 bytes starting at (ESP = 7797F1D0)

* = addr  **                                                  *               
7797F1D0: 44 F6 97 77  10 F2 97 77  10 F2 97 77  04 F2 97 77  D..w...w...w...w
7797F1E0: 04 00 00 00  0C F2 97 77  01 00 00 00  01 00 00 00  .......w........
7797F1F0: 01 00 00 00  00 00 00 00  10 F2 97 77  50 62 9A 76  ...........wPb.v
7797F200: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
7797F210: 00 00 00 00  E4 B6 F9 B7  07 00 00 00  07 00 00 00  ................
7797F220: E4 B6 F9 B7  40 F2 97 77  C0 F3 97 77  05 00 00 00  ....@..w...w....
7797F230: 5B 53 EE B7  00 00 00 00  90 9E 70 77  00 00 00 00  [S........pw....
7797F240: 2C F8 97 77  3B C7 EC B7  50 F8 97 77  90 9E 70 77  ,..w;...P..w..pw
7797F250: 09 00 00 00  AC AB EC B7  04 F8 97 77  2E 3E C6 77  ...........w.>.w
7797F260: 01 00 00 00  6A F4 97 77  AC AB EC B7  18 F8 97 77  ....j..w.......w
7797F270: 00 00 00 00  00 00 00 00  CB E1 C0 77  00 00 00 00  ...........w....
7797F280: 80 AC 86 77  00 00 00 00  01 00 00 00  C8 F2 97 77  ...w...........w
7797F290: 07 F4 85 77  00 00 00 00  00 00 00 00  2E 3E C6 77  ...w.........>.w
7797F2A0: 01 00 00 00  6A F4 97 77  01 00 00 00  11 CC 69 77  ....j..w......iw
7797F2B0: 00 00 00 00  ED 2D ED B7  01 00 00 00  80 AC 86 77  .....-.........w
7797F2C0: 00 00 00 00  F8 F2 97 77  0C 00 00 00  C0 F3 97 77  .......w.......w
7797F2D0: F8 F2 97 77  04 C5 FB B7  7A 69 EB 77  C8 1F 86 76  ...w....zi.w...v
7797F2E0: A4 E4 C0 77  03 00 00 00  00 50 E8 77  20 F3 97 77  ...w.....P.w ..w
7797F2F0: 8C C2 B8 77  80 D1 60 77  18 F3 97 77  81 6A EB 77  ...w..`w...w.j.w
7797F300: 10 49 06 78  A4 E4 C0 77  44 F3 97 77  1B C4 B8 77  .I.x...wD..w...w
7797F310: 80 D1 60 77  A0 82 61 77  FF FF 00 00  00 00 00 00  ..`w..aw........
7797F320: 54 F3 97 77  1B 56 DA 76  80 D1 60 77  CC F3 97 77  T..w.V.v..`w...w
7797F330: 00 00 00 00  D4 F3 97 77  00 00 00 00  E8 F3 97 77  .......w.......w
7797F340: 02 E4 EA B7  3F 18 EC 77  00 00 C1 77  90 43 C6 77  ....?..w...w.C.w
7797F350: 02 00 00 00  6C F3 97 77  AB 37 D8 76  00 00 00 00  ....l..w.7.v....
7797F360: 00 00 00 00  94 F3 97 77  E5 16 F1 7F  CC F3 97 77  .......w.......w
7797F370: 40 00 00 00  D4 F3 97 77  40 00 00 00  2C F5 97 77  @......w@...,..w
7797F380: D4 F3 97 77  84 C4 FB B7  40 00 00 00  26 B6 ED 77  ...w....@...&..w
7797F390: 04 00 00 00  2C F5 97 77  40 00 00 00  D4 F3 97 77  ....,..w@......w
7797F3A0: 40 00 00 00  2C F5 97 77  D4 F3 97 77  04 C5 FB B7  @...,..w...w....
7797F3B0: 40 00 00 00  92 B6 ED 77  05 00 00 00  2C F5 97 77  @......w....,..w
7797F3C0: 40 00 00 00  00 50 E8 77  A0 D9 EF 77  2C F5 97 77  @....P.w...w,..w
7797F3D0: E8 F3 97 77  74 F4 97 77  56 B7 ED 77  02 00 00 00  ...wt..wV..w....
7797F3E0: E8 F3 97 77  00 00 00 00  00 00 00 00  00 00 00 00  ...w............
7797F3F0: 7A 69 EB 77  E0 09 FB B7  A4 E4 C0 77  02 00 00 00  zi.w.......w....
7797F400: 00 50 E8 77  81 6A EB 77  8C C2 B8 77  A4 E4 C0 77  .P.w.j.w...w...w
7797F410: 4C F4 97 77  1B C4 B8 77  60 83 72 77  81 6A EB 77  L..w...w`.rw.j.w
7797F420: 8C C2 B8 77  A4 E4 C0 77  64 F4 97 77  8C 8A 72 77  ...w...wd..w..rw
7797F430: 01 00 00 00  F4 FF FF FF  2F E2 C0 77  B1 C5 B8 77  ......../..w...w
7797F440: 8C 8A 72 77  B1 C5 B8 77  F4 FF FF FF  5C F4 97 77  ..rw...w....\..w
7797F450: 2E 37 B5 77  6C F4 97 77  2E 37 B5 77  74 F4 97 77  .7.wl..w.7.wt..w
7797F460: 8C 8A 72 77  74 F4 97 77  8C 8A 72 77  2C F5 97 77  ..rwt..w..rw,..w
7797F470: B8 E7 C4 77  B8 F7 97 77  DE EC 6B 77  2C F5 97 77  ...w...w..kw,..w
7797F480: 00 00 00 00  40 00 00 00  2C F5 97 77  65 0F 69 77  ....@...,..we.iw
7797F490: 22 00 02 00  60 83 72 77  00 00 00 87  94 F5 97 77  "...`.rw.......w
7797F4A0: 00 00 00 00  9C F5 97 77  00 00 00 00  00 00 00 00  .......w........
7797F4B0: 00 00 00 00  00 00 00 00  00 00 00 00  C8 F5 97 77  ...............w
7797F4C0: 14 F5 97 77  84 C4 FB B7  40 00 00 00  26 B6 ED 77  ...w....@...&..w
7797F4D0: 04 00 00 00  C8 F5 97 77  40 00 00 00  14 F5 97 77  .......w@......w
7797F4E0: 40 00 00 00  C8 F5 97 77  14 F5 97 77  04 C5 FB B7  @......w...w....
7797F4F0: 40 00 00 00  92 B6 ED 77  05 00 00 00  C8 F5 97 77  @......w.......w
7797F500: 40 00 00 00  00 50 E8 77  A0 D9 EF 77  C8 F5 97 77  @....P.w...w...w
7797F510: 28 F5 97 77  B4 F5 97 77  56 B7 ED 77  02 00 00 00  (..w...wV..w....
7797F520: 28 F5 97 77  00 00 00 00  00 00 00 00  00 00 00 00  (..w............
7797F530: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
7797F540: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
7797F550: 00 00 00 00  00 00 00 00  7A 69 EB 77  00 00 00 00  ........zi.w....
7797F560: A4 E4 C0 77  02 00 00 00  00 50 E8 77  81 6A EB 77  ...w.....P.w.j.w
7797F570: 8C C2 B8 77  A4 E4 C0 77  B4 F5 97 77  1B C4 B8 77  ...w...w...w...w
7797F580: 80 D1 60 77  8C C2 B8 77  80 D1 60 77  A4 E4 C0 77  ..`w...w..`w...w
7797F590: CC F5 97 77  8C 8A 72 77  01 00 00 00  EB FF FF FF  ...w..rw........
7797F5A0: 2F E2 C0 77  2F E2 C0 77  A0 82 61 77  FF FF 00 00  /..w/..w..aw....
7797F5B0: 00 00 00 00  E8 F5 97 77  BC 56 DA 76  80 D1 60 77  .......w.V.v..`w
7797F5C0: 8C 8A 72 77  68 F6 97 77  65 0F 69 77  22 00 02 00  ..rwh..we.iw"...


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7fffffff
Processor Mask:         0x1
Number of Processors:   1
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     1

Percent memory used:    0
Total physical memory:  928419840
Free Memory:            622284800
Page file:              -1580666880
Total virtual memory:   2147418111


```

And the output from the consoll:
```

$ wine WoW.exe /opengl
Warning: Language 'no_NO' was not recognized, defaulting to English.
Warning: Language 'no_NO' was not recognized, defaulting to English.
Warning: Language 'no_NO' was not recognized, defaulting to English.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
fixme:opengl:query_function_pbuffer gl_version is: "1.2 (1.5 Mesa 6.2.1)"
fixme:opengl:query_function_pbuffer glx_exts is: "GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_ARB_m
fixme:opengl:query_function_pbuffer gl_version is: "1.2 (1.5 Mesa 6.2.1)"
fixme:opengl:query_function_pbuffer glx_exts is: "GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_ARB_m
fixme:advapi:SetSecurityInfo stub
fixme:user:EnumDisplayDevicesA ((nil),0,0x7797f2a8,0x00000000), stub!
fixme:user:EnumDisplayDevicesA ((nil),0,0x7797f58c,0x00000000), stub!
fixme:user:EnumDisplayDevicesA ((nil),0,0x7797fb28,0x00000000), stub!
fixme:user:EnumDisplayDevicesA ((nil),0,0x7797fb28,0x00000000), stub!
fixme:user:EnumDisplayDevicesA ((nil),0,0x7797faa0,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:user:EnumDisplayDevicesA ((nil),0,0x7797fa9c,0x00000000), stub!
fixme:user:EnumDisplayDevicesA ((nil),0,0x7797faa0,0x00000000), stub!
fixme:msvcrt:_XcptFilter (-1073741819,0x7797ed84)semi-stub
fixme:thread:GetThreadTimes Cannot get kerneltime or usertime of other threads
fixme:thread:GetThreadTimes Cannot get kerneltime or usertime of other threads
fixme:thread:GetThreadTimes Cannot get kerneltime or usertime of other threads
fixme:thread:GetThreadTimes Cannot get kerneltime or usertime of other threads
Warning: Language 'no_NO' was not recognized, defaulting to English.
Warning: Language 'no_NO' was not recognized, defaulting to English.
Warning: Language 'no_NO' was not recognized, defaulting to English.
 
```

---

### Post by Marmal on 2005-06-11
Hi,

i play WoW on Ubuntu for more than 2 month and it runs great. But i really recommend not to use wine. If you want to play WoW there are two ways:

- the first method is to use a commercial version wich is called Point2Play. But its very easy to install and you have a comfortable menu programm to install and configure. It can be purchase on [www.transgaming.com](www.transgaming.com)

- if you dont want to pay for this software there is another way to get WoW to run. This transgaing software could be downloaded for free as a CVS version. Someone wrote a Shelscript which allows you easily to install and compile that cvs verion. You can gat this script here: [http://winecvs.linux-gamers.net/index.php/Main_Page](http://winecvs.linux-gamers.net/index.php/Main_Page)

i bought Point2play and got WoW to work in less than a half hour. Another reason why i bought it is, that they have done good work and you have great support at the offical transgaming forum at [www.transgaming.org](www.transgaming.org). Every update of WoW they do quick fixes in less than 12 hours. If you do not have access you will have much trouble after every WoW Update.

There is no other way that i know to get WoW to work without loosing your fun on WoW.

Best regards,

Marc F.

P.s.: I put some screenshots on my Homepage to let you see how good WoW works. My Homepage: [www.marcanoid.com](www.marcanoid.com)

---

### Post by jhardtone on 2005-06-14
Do you have OpenGL 3D acceleration working in other games/programs? If you do have you got OpenGL support compiled in WINE?

Also have you read [this howto](http://forums.gentoo.org/viewtopic-t-246098.html) ?

---

