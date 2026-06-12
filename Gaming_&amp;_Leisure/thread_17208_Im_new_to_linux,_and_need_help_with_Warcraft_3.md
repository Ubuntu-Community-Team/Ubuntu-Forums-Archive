---
title: "Im new to linux, and need help with Warcraft 3"
date: 2005-02-26
forum: Gaming &amp; Leisure
---

### Post by siDDis on 2005-02-26
I installed linux for the first time today on my own machine. I needed to get away from all those spyware programs that infected my windows system like once a week.

I like playing video games, though I play mostly on console. However I really like playing Warcraft 3 over battle.net and it would be great if I could get it to work.

To tell you the truth I have almost a clean install of Ubunto, WINE is working but when I run install.exe from the Warcraft 3 CD it says that Im running Win95.

Is there some way I can get around this?

---

### Post by bored2k on 2005-02-26
You should get cedega, its the standard for nix gaming for windows games.

once u get it, u just type cedega install.exe and it will do it lik a normal windows... i did 3days ago so i know its true .


u can go to linux-gamers.net to get some help on wine

---

### Post by Quest-Master on 2005-02-26
Warcraft III works *perfectly* in Wine, which is free.

[http://frankscorner.org/index.php?p=warcraft3](http://frankscorner.org/index.php?p=warcraft3) 

:)

---

### Post by siDDis on 2005-02-27
Okey I finally managed to get it to run. Im using cedega and grapevine. Works like a charm, even BNet :)

However, how do I enable fullscreen?

---

### Post by Snipersnest on 2005-02-28
Well if your a TransGaming subscriber I recommend Point2Play. Its a GUI for your Windows game installs.  Much easier to use!

But for Cedega to get your games to run full screen you need to edit the Cedega config file for that game. It should be there in "Desktop mode" or something similar. You just need to disable that part for full screen..

lol its just 2 clicks in Point2Play to do that!

---

### Post by RDo on 2005-04-19
Can somebody tell me how to get warcraft3 to correctly installed? I've got cedega installed and after cedega install.exe I get this message;

Warning: Language 'en_NL' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
Fontconfig error: "local.conf", line 29: mismatched tag
wine: Unhandled exception, starting debugger...
Warning: Language 'en_NL' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0xb7ff7195
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0xb7ee8000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0xb7ed3000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0xb7e0b000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0xb7e09000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0xb7dda000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0xb7cad000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0xb7c9d000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0xb7c9a000)
No debug information in ELF '/lib/ld-linux.so.2' (0xb7feb000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libgdi32.so' (0xb7799000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libkernel32.so' (0xb7718000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libadvapi32.so' (0xb76f1000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libuser32.so' (0xb75c9000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwinmm.so' (0xb7573000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libversion.so' (0xb7569000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/liblz32.so' (0xb7562000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libshell32.so' (0xb74e7000)
No debug information in ELF '/usr/lib/libpng.so.3' (0xb74b5000)
No debug information in ELF '/usr/lib/libz.so.1' (0xb74a4000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libshlwapi.so' (0xb7464000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libcomctl32.so' (0xb73de000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwineserver.so' (0xb739d000)
No debug information in ELF '/usr/lib/libfreetype.so.6' (0xb7322000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libx11drv.so' (0xb7296000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_tsx11.so' (0xb7284000)
No debug information in ELF '/usr/X11R6/lib/libSM.so.6' (0xb726d000)
No debug information in ELF '/usr/X11R6/lib/libICE.so.6' (0xb7255000)
No debug information in ELF '/usr/lib/libGL.so.1' (0xb71dd000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libGLU.so.1' (0xb7122000)
No debug information in ELF '/usr/X11R6/lib/libXext.so.6' (0xb7115000)
No debug information in ELF '/usr/X11R6/lib/libX11.so.6' (0xb7050000)
No debug information in ELF '/usr/lib/libGLcore.so.1' (0xb68ff000)
No debug information in ELF '/usr/lib/tls/libnvidia-tls.so.1' (0xb68fd000)
No debug information in ELF '/usr/X11R6/lib/X11/locale/lib/common/xlcUTF8Load.so.2' (0xb6863000)
No debug information in ELF '/usr/X11R6/lib/X11/locale/lib/common/ximcp.so.2' (0xb6847000)
No debug information in ELF '/usr/lib/libXcursor.so.1' (0xb6830000)
No debug information in ELF '/usr/lib/libXrender.so.1' (0xb6828000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwineoss.drv.so' (0xb6167000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmsacm32.so' (0xb6155000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmsacm.drv.so' (0xb6038000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmidimap.drv.so' (0xb6032000)
No debug information in 32bit DLL 'F:\install.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0xb7f25000)
No debug information in 32bit DLL 'KERNEL32.DLL' (0xb774b000)
No debug information in 32bit DLL 'ADVAPI32.DLL' (0xb7703000)
No debug information in 32bit DLL 'GDI32.DLL' (0xb77b8000)
No debug information in 32bit DLL 'USER32.DLL' (0xb7600000)
No debug information in 32bit DLL 'C:\WINDOWS\SYSTEM32\OLE32.DLL' (0x65f00000)
No debug information in 32bit DLL 'C:\WINDOWS\SYSTEM32\MSVCRT.DLL' (0x78000000)
No debug information in 32bit DLL 'WINMM.DLL' (0xb7581000)
No debug information in 32bit DLL 'LZ32.DLL' (0xb7565000)
No debug information in 32bit DLL 'VERSION.DLL' (0xb756c000)
No debug information in 32bit DLL 'SHLWAPI.DLL' (0xb7481000)
No debug information in 32bit DLL 'COMCTL32.DLL' (0xb73ec000)
No debug information in 32bit DLL 'SHELL32.DLL' (0xb750d000)
No debug information in 32bit DLL 'X11DRV.DLL' (0xb72b4000)
No debug information in 32bit DLL 'MSACM32.DLL' (0xb615a000)
No debug information in 32bit DLL 'WINEOSS.DRV' (0xb616a000)
No debug information in 32bit DLL 'MSACM.DRV' (0xb603b000)
No debug information in 32bit DLL 'MIDIMAP.DRV' (0xb6034000)
Unhandled exception: page fault on read access to 0x27eddd38 in 32-bit code (0x00427259).
In 32-bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:00427259 ESP:b7a2281c EBP:b7a228f0 EFLAGS:00010202(  R- 00  I   - - 1 )
 EAX:dddddddd EBX:b5f000a4 ECX:b5f000a0 EDX:4a0fff5b
 ESI:00000000 EDI:00000000
Stack dump:
0xb7a2281c (GDI32.DLL.pfnRealizePalette+0x223b74):  00000000 00000000 00000000 00425e9f
0xb7a2282c (GDI32.DLL.pfnRealizePalette+0x223b84):  00000004 00000000 00436160 00425e35
0xb7a2283c (GDI32.DLL.pfnRealizePalette+0x223b94):  78001e02 00000000 0041d6c9 00436000
0xb7a2284c (GDI32.DLL.pfnRealizePalette+0x223ba4):  00436184 b7a22890 b7a22880 b7a2288c
0xb7a2285c (GDI32.DLL.pfnRealizePalette+0x223bb4):  00000000 b7a22884 00436188 0043618c
0xb7a2286c (GDI32.DLL.pfnRealizePalette+0x223bc4):  00000000 00000000 b7fd08a8 c0000005
0xb7a2287c (GDI32.DLL.pfnRealizePalette+0x223bd4):

Backtrace:
=>0 0x00427259 (install.exe.EntryPoint+0x9c5a in F:\install.exe) (ebp=b7a228f0)
  1 0xb7f97cfc (NTDLL.DLL.wine_server_call+0x1a7c in libntdll.so) (ebp=b7a22994)  2 0xb7f97e0f (NTDLL.DLL.wine_server_call+0x1b8f in libntdll.so) (ebp=b7a22ac8)  3 0xb7ca1ae0 (GDI32.DLL.pfnRealizePalette+0x4a2e38 in libpthread.so.0) (ebp=b7a22b3c)
  4 0xb7d7fc9a (NTDLL.DLL.memcpy+0x5b36a in libc.so.6) (ebp=00000000)

0x00427259 (install.exe.EntryPoint+0x9c5a in F:\install.exe): movl      0x0(%eax,%edx,1),%edi
Modules:
Address                 Module  Name
0x65f00000-65fc1800     (PE)    C:\WINDOWS\SYSTEM32\OLE32.DLL
0x78000000-78046000     (PE)    C:\WINDOWS\SYSTEM32\MSVCRT.DLL
0xb6034000-b6036000     (PE)    MIDIMAP.DRV
0xb603b000-b603d000     (PE)    MSACM.DRV
0xb615a000-b615c000     (PE)    MSACM32.DLL
0xb616a000-b616c000     (PE)    WINEOSS.DRV
0xb72b4000-b72b6000     (PE)    X11DRV.DLL
0xb73ec000-b73ee000     (PE)    COMCTL32.DLL
0xb7481000-b7483000     (PE)    SHLWAPI.DLL
0xb750d000-b750f000     (PE)    SHELL32.DLL
0xb7565000-b7567000     (PE)    LZ32.DLL
0xb756c000-b756e000     (PE)    VERSION.DLL
0xb7581000-b7583000     (PE)    WINMM.DLL
0xb7600000-b7602000     (PE)    USER32.DLL
0xb7703000-b7705000     (PE)    ADVAPI32.DLL
0xb774b000-b774d000     (PE)    KERNEL32.DLL
0xb77b8000-b77ba000     (PE)    GDI32.DLL
0xb7f25000-b7f27000     (PE)    NTDLL.DLL
0x00400000-00457000     (PE)    F:\install.exe
Threads:
process  tid      prio
00000001 (D) F:\install.exe
        00000002    0 <==
WineDbg terminated on pid 1

---

### Post by snagaslas on 2005-04-24
Isnt this what happens if your in the wrong directory and try to start it? Think i read it in another post

---

### Post by jdodson on 2005-04-26
get the latest version 4.3.1 it should fix that problem.

---

