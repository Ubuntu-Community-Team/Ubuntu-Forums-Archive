---
title: "WoW wont load under wine"
date: 2007-02-24
forum: Gaming &amp; Leisure
---

### Post by dcampfield2007 on 2007-02-24
Hello,

WoW starts on my computer with Wine and logs on, but when I click on Enter World, it loads up to 3/4 of the way then crashes!

Here is the output from terminal:
```
derek@derek-desktop:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe -opengl
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:win:EnumDisplayDevicesW ((null),0,0x33d058,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d0b0,0x00000000), stub!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

```

and here is my config.wtf:
```
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "85"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.070000"
SET DistCull "450.000000"
SET trilinear "1"
SET farclip "350.000000"
SET specular "1"
SET particleDensity "0.600000"
SET unitDrawDist "300.000000"
SET movie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET locale "enUS"
SET accountName "FLASHBLUENET1"
SET realmName "Cho'gall"
SET gameTip "9"
SET timingTestError "0"

```

I have nvidia geforce 4000 mx gpu and 1.0.8776 driver installed correctly

I have OpenGL registry tweak installed also

WoW crashes and has this crash report:
```
==============================================================================
World of WarCraft (build 6403)

Exe:      C:\Program Files\World of Warcraft\WoW.exe
Time:     Feb 24, 2007 12:01:26.344 PM
User:     derek
Computer: derek-desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00000000

The instruction at "0x00000000" referenced memory at "0x00000000".
The memory could not be "read".


WoWBuild: 6403
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=0033F8BC  EBX=00000000  ECX=01108008  EDX=0110A874  ESI=0D479368
EDI=00D7FE54  EBP=0033F8B4  ESP=0033F8A4  EIP=00000000  FLG=00210202
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

00000000 0033F8B4 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
005D2DEE 0033F8C8 0001:001D1DEE C:\Program Files\World of Warcraft\WoW.exe
005CEB6F 0033F8FC 0001:001CDB6F C:\Program Files\World of Warcraft\WoW.exe
0072C34F 0033F920 0001:0032B34F C:\Program Files\World of Warcraft\WoW.exe
006EAAEA 0033F93C 0001:002E9AEA C:\Program Files\World of Warcraft\WoW.exe
0040198C 0033F958 0001:0000098C C:\Program Files\World of Warcraft\WoW.exe
00471FA4 0033FDAC 0001:00070FA4 C:\Program Files\World of Warcraft\WoW.exe
00426BB0 0033FDE0 0001:00025BB0 C:\Program Files\World of Warcraft\WoW.exe
004234DA 0033FE04 0001:000224DA C:\Program Files\World of Warcraft\WoW.exe
00423268 0033FE60 0001:00022268 C:\Program Files\World of Warcraft\WoW.exe
004230F1 0033FE78 0001:000220F1 C:\Program Files\World of Warcraft\WoW.exe
00404B0E 0033FF08 0001:00003B0E C:\Program Files\World of Warcraft\WoW.exe
7B87011E 0033FFE8 0001:0004F11E c:\windows\system32\kernel32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

005D2DEE WoW.exe      <unknown symbol>+0 (0x00D7FE54,0x00000000,0x00D7FE50,0x0084C276)
005CEB6F WoW.exe      <unknown symbol>+0 (0x008AB32C,0x0072C20D,0x00000000,0x00000001)
0072C34F WoW.exe      <unknown symbol>+0 (0x00000001,0x03CAE022,0x00000000,0x006C5793)
006EAAEA WoW.exe      <unknown symbol>+0 (0x00000001,0x00000001,0x0033FDC0,0x00000001)
0040198C WoW.exe      <unknown symbol>+0 (0xC3AF8091,0xC537E7CD,0x42B8CD05,0x0033FDC0)
00471FA4 WoW.exe      <unknown symbol>+0 (0x000075C6,0x0110CC08,0x00000000,0x06DDF568)
00426BB0 WoW.exe      <unknown symbol>+0 (0x0033FDF8,0x00000102,0x0110CC08,0x00000000)
004234DA WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x7B8AB500,0x69676E45)
00423268 WoW.exe      <unknown symbol>+0 (0x00000000,0x00402584,0x00000001,0x00000001)
004230F1 WoW.exe      <unknown symbol>+0 (0x0040A850,0x00400000,0x00000000,0x001166EB)
00404B0E WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B87011E kernel32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7EBA5A7              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00340000 - 0x003D0000  C:\Program Files\World of Warcraft\fmod.dll
0x00400000 - 0x00D9D000  C:\Program Files\World of Warcraft\WoW.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B926000  c:\windows\system32\kernel32.dll
0x7BC10000 - 0x7BC94000  c:\windows\system32\ntdll.dll
0x7BFC0000 - 0x7C000000  c:\windows\system32\dbghelp.dll
0x7CA80000 - 0x7CA89000  c:\windows\system32\psapi.dll
0x7CAA0000 - 0x7CAB2000  c:\windows\system32\mswsock.dll
0x7CB40000 - 0x7CB6A000  c:\windows\system32\wineoss.drv
0x7CB90000 - 0x7CBBC000  c:\windows\system32\uxtheme.dll
0x7D6E0000 - 0x7D6E7000  c:\windows\system32\midimap.dll
0x7DA60000 - 0x7DAD6000  c:\windows\system32\winex11.drv
0x7DBB0000 - 0x7DBC0000  c:\windows\system32\mpr.dll
0x7DBD0000 - 0x7DC07000  c:\windows\system32\wininet.dll
0x7DC20000 - 0x7DC6C000  c:\windows\system32\msvcrt.dll
0x7DC70000 - 0x7DC92000  c:\windows\system32\msacm32.drv
0x7DCA0000 - 0x7DCA6000  c:\windows\system32\lz32.dll
0x7DCB0000 - 0x7DCBF000  c:\windows\system32\version.dll
0x7DCD0000 - 0x7DD4D000  c:\windows\system32\winmm.dll
0x7DD50000 - 0x7DD69000  c:\windows\system32\imm32.dll
0x7E790000 - 0x7E7F6000  c:\windows\system32\opengl32.dll
0x7E800000 - 0x7E822000  c:\windows\system32\ws2_32.dll
0x7E830000 - 0x7E83C000  c:\windows\system32\wsock32.dll
0x7E860000 - 0x7E86D000  c:\windows\system32\iphlpapi.dll
0x7E880000 - 0x7E8C2000  c:\windows\system32\rpcrt4.dll
0x7E8D0000 - 0x7E95B000  c:\windows\system32\ole32.dll
0x7E970000 - 0x7E9B3000  c:\windows\system32\shlwapi.dll
0x7E9C0000 - 0x7EAA7000  c:\windows\system32\shell32.dll
0x7EBC0000 - 0x7EC57000  c:\windows\system32\gdi32.dll
0x7EC70000 - 0x7ED91000  c:\windows\system32\user32.dll
0x7EDA0000 - 0x7EE50000  c:\windows\system32\comctl32.dll
0x7EE60000 - 0x7EE96000  c:\windows\system32\advapi32.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 00000000)

00000000: <can't read from this address>


Stack: 1024 bytes starting at (ESP = 0033F8A4)

* = addr               **                                         *           
0033F8A0: 89 8D 5D 00  51 2D 5D 00  01 00 00 00  BC F8 33 00  ..].Q-].......3.
0033F8B0: 08 80 10 01  C8 F8 33 00  EE 2D 5D 00  68 93 47 0D  ......3..-].h.G.
0033F8C0: 01 00 00 00  08 4C 89 00  FC F8 33 00  6F EB 5C 00  .....L....3.o.\.
0033F8D0: 54 FE D7 00  00 00 00 00  50 FE D7 00  76 C2 84 00  T.......P...v...
0033F8E0: 01 00 00 00  4C 52 86 00  08 00 00 00  EC F8 33 00  ....LR........3.
0033F8F0: ED F8 33 00  00 00 00 00  01 02 00 00  20 F9 33 00  ..3......... .3.
0033F900: 4F C3 72 00  2C B3 8A 00  0D C2 72 00  00 00 00 00  O.r.,.....r.....
0033F910: 01 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033F920: 3C F9 33 00  EA AA 6E 00  01 00 00 00  22 E0 CA 03  <.3...n....."...
0033F930: 00 00 00 00  93 57 6C 00  34 01 D0 03  58 F9 33 00  .....Wl.4...X.3.
0033F940: 8C 19 40 00  01 00 00 00  01 00 00 00  C0 FD 33 00  ..@...........3.
0033F950: 01 00 00 00  01 00 00 00  AC FD 33 00  A4 1F 47 00  ..........3...G.
0033F960: 91 80 AF C3  CD E7 37 C5  05 CD B8 42  C0 FD 33 00  ......7....B..3.
0033F970: 68 F5 DD 06  68 F5 DD 06  00 00 11 00  00 00 00 00  h...h...........
0033F980: 00 00 00 00  01 00 00 00  B4 B7 D3 7E  9C F9 33 00  ...........~..3.
0033F990: 30 BC D0 7E  60 67 D5 7E  B4 B7 D3 7E  EC FC 33 00  0..~`g.~...~..3.
0033F9A0: E6 6D CC 7E  03 00 00 00  00 00 00 00  04 FA 33 00  .m.~..........3.
0033F9B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033F9C0: 74 FC 33 00  00 00 00 00  44 C0 FD 7F  F7 83 E9 B7  t.3.....D.......
0033F9D0: 93 00 00 00  00 A7 6C 7E  30 30 54 69  F7 83 E9 B7  ......l~00Ti....
0033F9E0: F1 66 C3 7B  00 A7 6C 7E  00 00 00 00  00 00 00 00  .f.{..l~........
0033F9F0: 00 00 00 00  00 00 00 00  93 00 00 00  00 00 00 00  ................
0033FA00: D9 8C E9 B7  00 00 00 00  00 00 00 00  DB 61 C5 7B  .............a.{
0033FA10: B4 B7 D3 7E  03 01 00 00  FF FF FF FF  EC FC 33 00  ...~..........3.
0033FA20: 43 54 CE 7E  00 00 11 00  00 00 00 00  00 00 00 00  CT.~............
0033FA30: 93 00 00 00  00 00 00 80  00 00 00 00  00 00 00 00  ................
0033FA40: 00 00 00 00  00 00 00 00  B8 10 02 7C  90 FA 33 00  ...........|..3.
0033FA50: 41 B9 CF 7E  00 00 00 00  B0 FA 33 00  68 93 C7 7B  A..~......3.h..{
0033FA60: 0B 00 00 00  00 00 00 00  00 00 00 00  20 FD 33 00  ............ .3.
0033FA70: 00 00 00 00  44 C0 FD 7F  F7 83 E9 B7  00 00 00 00  ....D...........
0033FA80: 00 A7 6C 7E  F8 12 47 00  F7 83 E9 B7  31 31 00 02  ..l~..G.....11..
0033FA90: 00 A7 6C 7E  00 00 00 00  00 00 00 00  00 00 00 00  ..l~............
0033FAA0: 00 00 00 00  00 00 00 00  00 00 00 00  D9 8C E9 B7  ................
0033FAB0: 03 01 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033FAC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033FAD0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033FAE0: 00 00 00 80  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033FAF0: 00 00 00 00  B8 10 02 7C  3C FB 33 00  A0 56 A8 7D  .......|<.3..V.}
0033FB00: 08 B0 1D 07  A8 E7 11 05  69 5A 5C 08  D4 FB 33 00  ........iZ\...3.
0033FB10: 08 B0 1D 07  00 00 00 00  3C FB 33 00  A0 56 A8 7D  ........<.3..V.}
0033FB20: FF 04 00 00  28 CF 07 7C  00 00 00 00  20 00 01 00  ....(..|.... ...
0033FB30: 1F 85 C2 7B  90 BC D0 7E  00 B5 8A 7B  7C FB 33 00  ...{...~...{|.3.
0033FB40: A0 75 88 7B  60 67 D5 7E  EB FF FF FF  EB 77 88 7B  .u.{`g.~.....w.{
0033FB50: B4 B7 D3 7E  02 00 00 00  00 00 00 00  6C FB 33 00  ...~........l.3.
0033FB60: 90 BC D0 7E  0C FC 33 00  00 00 00 00  30 FC 33 00  ...~..3.....0.3.
0033FB70: 89 A5 E9 B7  24 00 01 00  00 00 00 00  8C FB 33 00  ....$.........3.
0033FB80: 60 BC D0 7E  60 67 D5 7E  B4 B7 D3 7E  AC FB 33 00  `..~`g.~...~..3.
0033FB90: 55 CC D0 7E  24 00 01 00  00 B5 8A 7B  7B 66 A8 7D  U..~$......{{f.}
0033FBA0: 3C D5 AC 7D  00 00 00 00  78 1F 16 00  EC FC 33 00  <..}....x.....3.
0033FBB0: F6 69 A8 7D  00 00 00 00  24 00 01 00  00 02 00 00  .i.}....$.......
0033FBC0: 00 00 00 00  00 00 00 00  0C FC 33 00  40 00 00 00  ..........3.@...
0033FBD0: 40 00 00 00  0C FC 33 00  04 C4 E9 B7  40 00 00 00  @.....3.....@...
0033FBE0: 1A 60 C5 7B  05 00 00 00  04 FD 33 00  40 00 00 00  .`.{......3.@...
0033FBF0: 00 02 00 00  24 00 01 00  EC FC 33 00  00 C0 FD 7F  ....$.....3.....
0033FC00: 68 93 C7 7B  00 00 00 00  04 FD 33 00  EC FC 33 00  h..{......3...3.
0033FC10: FF 62 C5 7B  02 00 00 00  30 FC 33 00  00 00 00 00  .b.{....0.3.....
0033FC20: 7B 01 00 00  2B 02 00 00  00 00 00 00  30 FC 33 00  {...+.......0.3.
0033FC30: 00 00 00 00  00 00 00 00  00 00 00 00  7B 01 2B 02  ............{.+.
0033FC40: 24 00 01 00  00 00 00 00  B4 B7 D3 7E  00 00 00 00  $..........~....
0033FC50: 01 00 00 00  74 FC 33 00  01 00 00 00  58 02 00 00  ....t.3.....X...
0033FC60: 00 00 00 00  74 FC 33 00  01 00 00 00  00 C0 FD 7F  ....t.3.........
0033FC70: 01 00 00 00  24 00 01 00  00 02 00 00  00 00 00 00  ....$...........
0033FC80: 7B 01 2B 02  EB 75 00 00  7B 01 00 00  2B 02 00 00  {.+..u..{...+...
0033FC90: FF 73 88 7B  B4 B7 D3 7E  DC FC 33 00  CC FC 33 00  .s.{...~..3...3.
0033FCA0: AA 6F D1 7E  24 00 01 00  00 02 00 00  00 00 00 00  .o.~$...........


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
Processor Revision:     1033

Percent memory used:    21
Total physical memory:  527212544
Free Memory:            157278208
Page file:              1538084864
Total virtual memory:   2147352575

``` 
and says:confused:

---

### Post by Stemp on 2007-02-25
Are you using the latest wine package from wine.budgetdedicated.com repositories ? 
Are you using Edgy, Dapper, Feisty ?

---

### Post by Sammi on 2007-02-25
Have you tried a newer version of your graphics card driver?

See here for installation help: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by dcampfield2007 on 2007-02-26
I am using Edgy and wine from budgetdedicated... and nvidia-glx 1.0.8776 but WoW works fine with d3d enabled

---

