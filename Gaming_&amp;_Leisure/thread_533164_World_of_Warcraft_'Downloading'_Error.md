---
title: "World of Warcraft 'Downloading' Error"
date: 2007-08-23
forum: Gaming &amp; Leisure
---

### Post by Unicow on 2007-08-23
I've very recently -- it just started today -- getting an error while trying to run World of Warcraft under wine. I'll start the program up and get to the log in screen fine, with no problems, but once I enter my information and hit 'enter', it will go for a few seconds before invariably stopping during the log-in process where the box reads 'downloading' and freeze. Here's my konsole output; 

```
cow@crystal:~/.wine/drive_c/Program Files/World of Warcraft$ aoss wine WoW.exe
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f2d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f520,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x34f008,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wave:wodOpen fragment size set failed, size is now 4096
Your Open Sound System driver did not let us configure small enough sound fragments.
This may cause delays and other problems in audio playback with certain applications.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:reg:GetNativeSystemInfo (0x374026c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7c76e554) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:powrprof:DllMain (0x7d120000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d120000, 0, (nil)) not fully implemented
fixme:reg:GetNativeSystemInfo (0x34b020) using GetSystemInfo()
fixme:reg:GetNativeSystemInfo (0x34ab34) using GetSystemInfo()
err:d3d:InitAdapters Failed to initialize gl caps for default adapter
err:wine_d3d:WineDirect3DCreate Failed to initialize direct3d adapters
Killed

```
Does anyone have any experience with this error?

---

### Post by lou1998 on 2007-08-23
I have the same problem.  Just started today.
When I tried WoW on my windows machine, it had the downloading box followed by a submitting non-personal information box.  That might be where the hang is.

---

### Post by ErusGuleilmus on 2007-08-23
i dont really know what the problem is, but all I did was uninstall then reinstall wine and it worked for me.

---

### Post by cotter on 2007-08-23
just learned i have the same problem..
i'm VERY new to linux/ubuntu/wine, so any help would be greatly appreciated.  last nite, i did install a few updates, but none for wine that i recall.  also unfortunately, i have no idea what version of unbuntu or wine i currently have (any help w/ where to look, as well?)

anyway, in short i'm struggling here... thanks in advance for your assistance.  and i'm not savvy enough to know how to post this error code in a separate box, but here it is:

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	H:\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7BFEDBE5

The instruction at "0x7BFEDBE5" referenced memory at "0x00000000".
The memory could not be "read".


WoWBuild: 6898
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000000  EBX=7BFFF718  ECX=7BFFFE94  EDX=FFFFFFFF  ESI=0021B0C8
EDI=7BFFFE90  EBP=0033ACF8  ESP=0033ACD4  EIP=7BFEDBE5  FLG=00010246
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

7BFEDBE5 0033ACF8 0001:0000CBE5 c:\windows\system32\d3d9.dll
093D25D5 08048008 0001:000015D5 H:\World of Warcraft\Cache\Survey.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

7BFEDBE5 d3d9.dll     <unknown symbol>+0 (0x0021B0C8,0x7EAE7670,0x656E5553,0x093F1E50)
093D25D5 Survey.dll   <unknown symbol>+0 (0x44206D65,0x72637365,0x69747069,0x32206E6F)
74737953 <unknown module> <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00340000 - 0x003A9000  H:\World of Warcraft\DivxDecoder.dll
0x00400000 - 0x00CEE000  H:\World of Warcraft\WoW.exe
0x093D0000 - 0x093EF000  H:\World of Warcraft\Cache\Survey.dll
0x10000000 - 0x10090000  H:\World of Warcraft\fmod.dll
0x7B820000 - 0x7B929000  c:\windows\system32\KERNEL32.dll
0x7B9B0000 - 0x7B9EF000  c:\windows\system32\dbghelp.dll
0x7BC10000 - 0x7BC97000  c:\windows\system32\ntdll.dll
0x7BF20000 - 0x7BFD2000  c:\windows\system32\wined3d.dll
0x7BFE0000 - 0x7C000000  c:\windows\system32\d3d9.dll
0x7CA80000 - 0x7CA87000  c:\windows\system32\psapi.dll
0x7CA90000 - 0x7CACF000  c:\windows\system32\dsound.dll
0x7CE60000 - 0x7CE84000  c:\windows\system32\uxtheme.dll
0x7CE90000 - 0x7CE9C000  c:\windows\system32\msacm32.drv
0x7CEA0000 - 0x7CED8000  c:\windows\system32\wineoss.drv
0x7D1F0000 - 0x7D1FE000  c:\windows\system32\midimap.dll
0x7D210000 - 0x7D230000  c:\windows\system32\winealsa.drv
0x7D7F0000 - 0x7D86E000  c:\windows\system32\winex11.drv
0x7DA70000 - 0x7DB1F000  c:\windows\system32\comctl32.dll
0x7DB30000 - 0x7DC1D000  c:\windows\system32\shell32.dll
0x7DC30000 - 0x7DC76000  c:\windows\system32\shlwapi.dll
0x7DC80000 - 0x7DC96000  c:\windows\system32\mpr.dll
0x7DCA0000 - 0x7DCDF000  c:\windows\system32\wininet.dll
0x7DCF0000 - 0x7DD38000  c:\windows\system32\rpcrt4.dll
0x7DD50000 - 0x7DDD7000  c:\windows\system32\ole32.dll
0x7DDF0000 - 0x7DE3E000  c:\windows\system32\msvcrt.dll
0x7DE50000 - 0x7DE64000  c:\windows\system32\msacm32.dll
0x7DE70000 - 0x7DE81000  c:\windows\system32\imm32.dll
0x7DE90000 - 0x7DE95000  c:\windows\system32\lz32.dll
0x7DEA0000 - 0x7DEAF000  c:\windows\system32\version.dll
0x7E9E0000 - 0x7EA48000  c:\windows\system32\opengl32.dll
0x7EA60000 - 0x7EA79000  c:\windows\system32\iphlpapi.dll
0x7EA80000 - 0x7EAA6000  c:\windows\system32\ws2_32.dll
0x7EAB0000 - 0x7EAC0000  c:\windows\system32\wsock32.dll
0x7EAD0000 - 0x7EB08000  c:\windows\system32\advapi32.dll
0x7EC20000 - 0x7ECCC000  c:\windows\system32\gdi32.dll
0x7ECF0000 - 0x7EE09000  c:\windows\system32\user32.dll
0x7EE20000 - 0x7EE97000  c:\windows\system32\winmm.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 7BFEDBE5)

7BFEDBE5: 8B 10 83 EC  04 89 04 24  FF 52 10 83  EC 04 89 C6  .......$.R......


Stack: 1024 bytes starting at (ESP = 0033ACD4)

* = addr               **                                         *           
0033ACD0: 90 FE FF 7B  F0 FE FF 7B  24 BC FF 7B  B9 D3 FF 7B  ...{...{$..{...{
0033ACE0: C8 B0 21 00  30 3A 3F 09  98 B4 C7 7B  C8 B0 21 00  ..!.0:?....{..!.
0033ACF0: 40 44 3E 09  14 B3 33 00  08 80 04 08  D5 25 3D 09  @D>...3......%=.
0033AD00: C8 B0 21 00  70 76 AE 7E  53 55 6E 65  50 1E 3F 09  ..!.pv.~SUneP.?.
0033AD10: 14 B3 33 00  EA 01 00 00  50 8A 3E 09  E8 4B 3D 09  ..3.....P.>..K=.
0033AD20: 00 00 00 00  00 00 3F 09  38 3A 3F 09  02 00 00 00  ......?.8:?.....
0033AD30: 02 00 00 00  02 00 00 00  44 AD 33 00  00 00 3F 09  ........D.3...?.
0033AD40: 00 83 C3 7B  00 00 00 00  02 00 00 00  02 00 00 00  ...{............
0033AD50: 44 9E 3D 09  00 00 3F 09  00 00 00 00  02 00 00 00  D.=...?.........
0033AD60: 00 3A 3F 09  02 00 00 00  01 00 00 00  38 3A 3F 09  .:?.........8:?.
0033AD70: A3 AE 33 00  D8 23 3D 09  38 3A 3F 09  BB AE 33 00  ..3..#=.8:?...3.
0033AD80: 01 00 00 00  00 3A 3F 09  02 00 00 00  3D 01 00 00  .....:?.....=...
0033AD90: 7C 25 3D 09  01 00 00 00  D4 00 00 00  D4 00 00 00  |%=.............
0033ADA0: 00 00 00 00  EA AD 33 00  D8 D0 15 30  F8 FE 33 00  ......3....0..3.
0033ADB0: EB 3E 3E 09  FF FF FF FF  EC 2C 3D 09  22 2E 3D 09  .>>......,=.".=.
0033ADC0: FF FF 00 00  02 00 00 00  05 00 00 00  00 00 00 00  ................
0033ADD0: 93 08 00 00  0F 00 00 00  00 00 00 00  00 00 00 1E  ................
0033ADE0: 53 65 72 76  69 63 65 20  50 61 63 6B  20 34 00 00  Service Pack 4..
0033ADF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033AE00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033AE10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033AE20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033AE30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033AE40: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033AE50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033AE60: 4E 54 46 53  00 00 00 00  00 00 00 00  00 00 00 00  NTFS............
0033AE70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033AE80: 00 00 00 00  00 D0 83 17  06 00 00 00  00 A0 A7 27  ...............'
0033AE90: 11 00 00 00  73 69 73 74  41 74 74 61  63 6B 20 22  ....sistAttack "
0033AEA0: 31 22 0A 53  45 54 20 6C  61 73 74 43  68 61 72 61  1".SET lastChara
0033AEB0: 63 74 65 72  49 6E 64 65  78 20 22 32  22 0A 6C 65  cterIndex "2".le
0033AEC0: 20 22 31 22  08 AF 33 00  1A 00 00 00  1A 00 00 00   "1"..3.........
0033AED0: 08 AF 33 00  94 C1 E6 B7  1A 00 00 00  DA 7C C5 7B  ..3..........|.{
0033AEE0: 05 00 00 00  24 B1 33 00  1A 00 00 00  F5 5E DE B7  ....$.3......^..
0033AEF0: AC AF 33 00  03 00 00 00  00 C0 FD 7F  98 B4 C7 7B  ..3............{
0033AF00: AC AF 33 00  1C B0 33 00  E8 AF 33 00  BF 7F C5 7B  ..3...3...3....{
0033AF10: 02 00 00 00  2C AF 33 00  00 00 00 00  BE 6A C3 7B  ....,.3......j.{
0033AF20: 00 00 3F 09  C1 9E C2 7B  2C AF 33 00  00 00 00 00  ..?....{,.3.....
0033AF30: 00 00 00 00  3F 98 C2 7B  00 00 3F 09  98 B4 C7 7B  ....?..{..?....{
0033AF40: 80 AF 33 00  07 7B C3 7B  20 00 3F 09  20 00 3F 09  ..3..{.{ .?. .?.
0033AF50: 20 00 3F 09  53 65 6C 66  43 61 73 74  44 ED E8 B7   .?.SelfCastD...
0033AF60: 0A 53 45 54  20 53 6F 75  00 00 00 00  B4 AF 33 00  .SET Sou......3.
0033AF70: F0 70 3D 09  09 00 00 00  B4 AF 33 00  9C 72 3D 09  .p=.......3..r=.
0033AF80: 00 00 00 00  89 45 3E 09  A4 AF 33 00  A7 72 3D 09  .....E>...3..r=.
0033AF90: A4 AF 33 00  AD 3A 3D 09  D0 B2 33 00  14 DA 3D 09  ..3..:=...3...=.
0033AFA0: 00 00 00 00  28 87 3E 09  08 0E 3F 09  F8 00 3F 09  ....(.>...?...?.
0033AFB0: 00 00 00 00  48 B0 33 00  88 03 00 00  D4 B2 33 00  ....H.3.......3.
0033AFC0: 53 84 3D 09  13 8F 3D 09  FF 00 00 00  00 00 00 00  S.=...=.........
0033AFD0: 60 B2 33 00  BF 90 3D 09  44 B2 33 00  28 87 3E 09  `.3...=.D.3.(.>.
0033AFE0: 08 0E 3F 09  F8 00 3F 09  01 B0 33 00  00 00 00 00  ..?...?...3.....
0033AFF0: 48 B2 33 00  00 00 00 00  1A 00 00 00  5E 01 00 00  H.3.........^...
0033B000: 00 00 00 00  00 00 00 00  38 B0 33 00  04 00 00 00  ........8.3.....
0033B010: D4 B2 33 00  BC B0 33 00  00 00 00 00  E0 B0 33 00  ..3...3.......3.
0033B020: 49 A3 E6 B7  50 B0 33 00  64 00 00 00  04 00 00 00  I...P.3.d.......
0033B030: 00 00 00 04  F0 B1 33 00  00 00 01 00  00 00 00 00  ......3.........
0033B040: 00 00 00 FF  FF FF FF FF  00 00 00 00  0C 00 00 00  ................
0033B050: 0D 00 00 00  00 00 00 00  98 B0 33 00  B0 06 C3 7B  ..........3....{
0033B060: 60 52 F8 B7  00 00 00 00  24 B1 33 00  0D 00 00 00  `R......$.3.....
0033B070: 60 B2 33 00  0D 00 00 00  BC B0 33 00  40 00 00 00  `.3.......3.@...
0033B080: 40 00 00 00  BC B0 33 00  94 C1 E6 B7  40 00 00 00  @.....3.....@...
0033B090: DA 7C C5 7B  05 00 00 00  B0 B1 33 00  40 00 00 00  .|.{......3.@...
0033B0A0: 00 00 00 00  0D 00 00 00  9C B1 33 00  00 C0 FD 7F  ..........3.....
0033B0B0: 98 B4 C7 7B  00 00 00 00  B0 B1 33 00  9C B1 33 00  ...{......3...3.
0033B0C0: BF 7F C5 7B  02 00 00 00  E0 B0 33 00  00 00 00 00  ...{......3.....
0033B0D0: 18 B1 33 00  00 00 00 00  5C B2 33 00  E0 B0 33 00  ..3.....\.3...3.


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x3
Number of Processors:   2
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     3842

Percent memory used:    15
Total physical memory:  2124345344
Free Memory:            1787904000
Page file:              -1
Total virtual memory:   2147352575

---

### Post by Xcarma on 2007-08-23
Got this from the WOW forums...

> - Disable OpenGL ( remove the SET gxapi "opengl" line in your config.wtf)
- Login, wait until the "Non-personal system information" has been submitted
- Exit
- Reenable OpenGL (by restoring the set gxapi line) 
Worked for me

---

### Post by Unicow on 2007-08-23
I love the linux community. :)

---

### Post by lou1998 on 2007-08-23
Worked for me too.  Thanks!

---

### Post by hikaricore on 2007-08-23
I love how Blizzard puts out patches that are needlessly buggy just to fit their patch release schedule.
I remember after one the 2.0 patches where everyone would randomly be running in place while standing still.  Wasn't a super important bug, but could have been easily avoided.

Makes me wonder if they ever fixed the EPL buff bug I reported to them like 8 months ago where a series of PVP related buffs caused enemies to aggro you from any distance for simply targeting them.  ^_^

---

### Post by BitTorrentBuddha on 2007-08-23
If only every community were so friendly, responsive, and intelligent.

---

### Post by moahrs on 2007-08-23
I have the same problem, but i not have this line i my config.wtf....

bu i have -opengl in this line command... and remove , and worked for my now



thanks a lot.

moacir jr.

---

### Post by Seraed on 2007-08-23
I think I remember reading in some how to for wow with wine that you need to use direct x to patch, or was it starcraft... *shrug* either way it makes sense then that to download/apply a patch of this nature that OGL be disabled. (be it the Config.wtf or as a CL parameter)

Indeed it worked on my machine.

---

### Post by Pikestaff on 2007-08-23
Xcarma's suggestion worked for me as well... thanks so much!

---

### Post by Kingsfan on 2007-08-23
> **Xcarma said:**
> Got this from the WOW forums...


Worked for me

thanks!

---

### Post by ronz0o on 2007-08-23
> **Xcarma said:**
> Got this from the WOW forums...

Quote:
- Disable OpenGL ( remove the SET gxapi "opengl" line in your config.wtf)
- Login, wait until the "Non-personal system information" has been submitted
- Exit
- Reenable OpenGL (by restoring the set gxapi line)
Worked for me
__________________


I run wow with the sudo wine WoW.exe -opengl command. i got mine to work by running sudo wine WoW.exe, logging in, and letting it freeze, then rebooted. after reboot, ran it with -opengl, and it worked like a charm!  :guitar:

---

### Post by sparau on 2007-08-24
worked for me :)

again thx ubuntu community :)

---

### Post by T'sora on 2007-08-24
Temporarily removing the opengl line from config.wtf worked for me, just like a charm.

Thanks guys!

---

### Post by hikaricore on 2007-08-24
This issue came back to bite me in the *** last night.

My girlfriend got off work around 1am. About 20 minutes or so after telling me to go back to sleep, I was awakened suddenly
to a "*** ****it what the ****" and promptly stumbled out of bed to fix the silly issue.  >.<

---

### Post by Kelderkeuken on 2007-08-24
I love you guys, worked like a charm.

I tried to fix it myself for a few hours, somehow it didn't dawn on me that this was something all of us were facing. It wasn't even a patch eh, just that stupid background downloader. Anyway, thanks a ton. All good, for now :)

---

### Post by Skylander on 2007-08-24
Unfortunately none of the fixes you guys have suggest is working for me.  I've run it under D3D mode,  removed the Opengl line from the WTF file ,   reinstalled ,  repeated the OGL line removal,  copied from the one in windows.   Still just locks up at the Download banner.   All this happened when Blizzard released that patch the other night.   :(   


Fiesty Fawn 7.04
Windows XP Home
200 gig harddrive
60 gig harddrive
2.0 ghz Celeron
768 Ram
256 Nvidia GeForce 6200
Syntax SVX-400 Motherboard

---

### Post by hikaricore on 2007-08-24
> **Skylander said:**
> Unfortunately none of the fixes you guys have suggest is working for me.  I've run it under D3D mode,  removed the Opengl line from the WTF file ,   reinstalled ,  repeated the OGL line removal,  copied from the one in windows.   Still just locks up at the Download banner.   All this happened when Blizzard released that patch the other night.   :(   


Fiesty Fawn 7.04
Windows XP Home
200 gig harddrive
60 gig harddrive
2.0 ghz Celeron
768 Ram
256 Nvidia GeForce 6200
Syntax SVX-400 Motherboard

I know D3D mode is supposed to be default, but just incase WoW is being finicky, have you tried forcing D3D mode?

```
wine WoW.exe -d3d
```

To be 100% sure it's not running in opengl mode?  Just a thought.  Sorry if it's also no good. >.<

---

### Post by Skylander on 2007-08-24
> **hikaricore said:**
> I know D3D mode is supposed to be default, but just incase WoW is being finicky, have you tried forcing D3D mode?

```
wine WoW.exe -d3d
```

To be 100% sure it's not running in opengl mode?  Just a thought.  Sorry if it's also no good. >.<

Yep did this too and it still clams up.  :(    Perhaps I should wait till Blizzard releases then next update that I can manually download since this one was a pre-release update?

---

### Post by Rode on 2007-08-25
> **Skylander said:**
> Yep did this too and it still clams up.  :(    Perhaps I should wait till Blizzard releases then next update that I can manually download since this one was a pre-release update?

I had this problem to on one of my computers. Wondered why because the 2 computers are more or less identical, but I solved it. 

The simple solution for me was to look at sound in winecfg, since this has caused problems before. I use ALSA sound and none other on my computer, but on the other both ALSA and OSS was checked, and after removing OSS, and only using ALSA everything worked like a charm.  :KS

---

### Post by georgie_o on 2007-08-25
Ok- after trying this out I can get back into the log-in screen. But am now back to problem one when I have OGL- 3D acceleration error occurs and I can't log in. 
But when I just open without OGL- the performance is so poor its unplayable.
Have a new gfx card on order, really hope this will solve the situation. 
But in anycase does anyone have any ideas? (have already added SET ffxDeath "0" SET,  ffxGlow "0",  SET SoundOutputSystem "1",  SET SoundBufferSize "150" in wtf and set sound to OSS).

---

### Post by brokendown on 2007-08-25
I also had this problem yesterday and what I did to fix it was run the Repair.exe with all the options checked.  I played most of last night with a few freezes, but overall running well.  However, now I freeze once the loading bar is full every time.

---

### Post by UbuntuniX on 2007-08-26
> **Xcarma said:**
> Got this from the WOW forums...


Worked for me

Cheers! If only there was rep to spread. :)

---

### Post by andreasbond on 2007-09-01
where can i find this opengl thing
i have the same problem and i'm working for it now al long time so plz help me

---

### Post by andreasbond on 2007-09-01
where can i find this opengl thing or something i can't find it

---

