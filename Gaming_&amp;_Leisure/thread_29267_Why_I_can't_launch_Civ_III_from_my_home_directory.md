---
title: "Why I can't launch Civ III from my home directory?"
date: 2005-04-23
forum: Gaming &amp; Leisure
---

### Post by Neo40 on 2005-04-23
Hi,

I have installed Civilization III with Cedega 4.3.1. If I go to the directory:
/home/eric/TransGaming_Drive/Program Files/Infogrames Interactive/Civilization III/
and I type "cedega Civilization3.exe" then it works just fine.
But if I'm in my home directory and I type:

cedega ~/TransGaming_Drive/"Program Files"/"Infogrames Interactive"/"Civilization III"/Civilization3.exe

then I see all this things:

WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x4000c410
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0x40017000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0x4011b000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0x40130000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0x401f7000)
No debug information in ELF '/lib/tls/libm.so.6' (0x4020a000)
No debug information in ELF '/lib/tls/libc.so.6' (0x4022d000)
No debug information in ELF '/lib/tls/libpthread.so.0' (0x40346000)
No debug information in ELF '/lib/tls/libdl.so.2' (0x40357000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libopengl32.so' (0x40893000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_tsx11.so' (0x40912000)
No debug information in ELF '/usr/X11R6/lib/libSM.so.6' (0x40933000)
No debug information in ELF '/usr/X11R6/lib/libICE.so.6' (0x4093c000)
No debug information in ELF '/usr/lib/libGL.so.1' (0x40954000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libGLU.so.1' (0x409cc000)
No debug information in ELF '/usr/X11R6/lib/libXext.so.6' (0x40a87000)
No debug information in ELF '/usr/X11R6/lib/libX11.so.6' (0x40a95000)
No debug information in ELF '/usr/lib/libGLcore.so.1' (0x40b61000)
No debug information in ELF '/usr/lib/tls/libnvidia-tls.so.1' (0x412b2000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libuser32.so' (0x4134c000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libgdi32.so' (0x41474000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libkernel32.so' (0x414eb000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libadvapi32.so' (0x4156c000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libddraw.so' (0x41593000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwinmm.so' (0x415d8000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libcomdlg32.so' (0x4162e000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libshell32.so' (0x41693000)
No debug information in ELF '/usr/lib/libpng.so.3' (0x4171e000)
No debug information in ELF '/usr/lib/libz.so.1' (0x41751000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libole32.so' (0x41762000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/librpcrt4.so' (0x417c7000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libshlwapi.so' (0x4180d000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libcomctl32.so' (0x4184d000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwinspool.drv.so' (0x418d2000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwineserver.so' (0x418e7000)
No debug information in ELF '/usr/lib/libfreetype.so.6' (0x41938000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libx11drv.so' (0x419aa000)
No debug information in ELF '/usr/X11R6/lib/X11/locale/lib/common/xlcDef.so.2' (0x41a2a000)
No debug information in ELF '/usr/X11R6/lib/X11/locale/lib/common/ximcp.so.2' (0x41a2d000)
No debug information in ELF '/usr/lib/gconv/ISO8859-1.so' (0x41a4c000)
No debug information in ELF '/usr/X11R6/lib/libXcursor.so.1' (0x41a5e000)
No debug information in ELF '/usr/X11R6/lib/libXrender.so.1' (0x41a67000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libd3dgl.so' (0x41ca0000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwineoss.drv.so' (0x43d17000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmsacm32.so' (0x43d30000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmsacm.drv.so' (0x43d42000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmidimap.drv.so' (0x43d4a000)
No debug information in 32bit DLL 'C:\Program Files\Infogrames Interactive\Civilization III\Civilization3.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40055000)
No debug information in 32bit DLL 'KERNEL32.DLL' (0x4151e000)
No debug information in 32bit DLL 'ADVAPI32.DLL' (0x4157e000)
No debug information in 32bit DLL 'GDI32.DLL' (0x41493000)
No debug information in 32bit DLL 'USER32.DLL' (0x41383000)
No debug information in 32bit DLL 'DDRAW.DLL' (0x415a9000)
No debug information in 32bit DLL 'OPENGL32.DLL' (0x408cf000)
No debug information in 32bit DLL 'WINMM.DLL' (0x415e6000)
No debug information in 32bit DLL 'C:\PROGRAM FILES\INFOGRAMES INTERACTIVE\CIVILIZATION III\BINKW32.DLL' (0x30000000)
No debug information in 32bit DLL 'RPCRT4.DLL' (0x417ea000)
No debug information in 32bit DLL 'OLE32.DLL' (0x41781000)
No debug information in 32bit DLL 'SHLWAPI.DLL' (0x4182a000)
No debug information in 32bit DLL 'COMCTL32.DLL' (0x4185b000)
No debug information in 32bit DLL 'SHELL32.DLL' (0x416b9000)
No debug information in 32bit DLL 'WINSPOOL.DRV' (0x418da000)
No debug information in 32bit DLL 'COMDLG32.DLL' (0x41640000)
No debug information in 32bit DLL 'X11DRV.DLL' (0x419c9000)
No debug information in 32bit DLL 'D3DGL.DLL' (0x41cb1000)
No debug information in 32bit DLL 'MSACM32.DLL' (0x43d35000)
No debug information in 32bit DLL 'WINEOSS.DRV' (0x43d1a000)
No debug information in 32bit DLL 'MSACM.DRV' (0x43d45000)
No debug information in 32bit DLL 'MIDIMAP.DRV' (0x43d4c000)
Unhandled exception: page fault on read access to 0x0000000c in 32-bit code (0x00571589).
In 32-bit mode.
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
EIP:00571589 ESP:40881f8c EBP:005f0180 EFLAGS:00010202( R- 00 I - - 1 )
EAX:00000000 EBX:40102368 ECX:40881fa8 EDX:441900a4
ESI:40881fa8 EDI:00000006
Stack dump:
0x40881f8c (NTDLL.DLL.memcpy+0x5ebc1c): 005f0287 00460740 00000103 00000000
0x40881f9c (NTDLL.DLL.memcpy+0x5ebc2c): 005f0180 408822cc 40102368 005acf58
0x40881fac (NTDLL.DLL.memcpy+0x5ebc3c): 74786574 62616c5c 2e736c65 00747874
0x40881fbc (NTDLL.DLL.memcpy+0x5ebc4c): d3d2d1d0 d7d6d5d4 dbdad9d8 dfdedddc
0x40881fcc (NTDLL.DLL.memcpy+0x5ebc5c): c3c2c1c0 c7c6c5c4 cbcac9c8 cfcecdcc
0x40881fdc (NTDLL.DLL.memcpy+0x5ebc6c): d3d2d1d0 f7d6d5d4 dbdad9d8 ffdedddc
0x40881fec (NTDLL.DLL.memcpy+0x5ebc7c):

Backtrace:
=>0 0x00571589 (Civilization3.exe..text+0x170589 in C:\Program Files\Infogrames Interactive\Civilization III\Civilization3.exe) (ebp=005f0180)

0x00571589 (Civilization3.exe..text+0x170589 in C:\Program Files\Infogrames Interactive\Civilization III\Civilization3.exe): testb $0x10,0xc(%eax)
Modules:
Address Module Name
0x00400000-0089e000 (PE) C:\Program Files\Infogrames Interactive\Civilization III\Civilization3.exe
0x30000000-30058400 (PE) C:\PROGRAM FILES\INFOGRAMES INTERACTIVE\CIVILIZATION III\BINKW32.DLL
0x40055000-40057000 (PE) NTDLL.DLL
0x408cf000-408d1000 (PE) OPENGL32.DLL
0x41383000-41385000 (PE) USER32.DLL
0x41493000-41495000 (PE) GDI32.DLL
0x4151e000-41520000 (PE) KERNEL32.DLL
0x4157e000-41580000 (PE) ADVAPI32.DLL
0x415a9000-415ab000 (PE) DDRAW.DLL
0x415e6000-415e8000 (PE) WINMM.DLL
0x41640000-41642000 (PE) COMDLG32.DLL
0x416b9000-416bb000 (PE) SHELL32.DLL
0x41781000-41783000 (PE) OLE32.DLL
0x417ea000-417ec000 (PE) RPCRT4.DLL
0x4182a000-4182c000 (PE) SHLWAPI.DLL
0x4185b000-4185d000 (PE) COMCTL32.DLL
0x418da000-418dc000 (PE) WINSPOOL.DRV
0x419c9000-419cb000 (PE) X11DRV.DLL
0x41cb1000-41cb3000 (PE) D3DGL.DLL
0x43d1a000-43d1c000 (PE) WINEOSS.DRV
0x43d35000-43d37000 (PE) MSACM32.DLL
0x43d45000-43d47000 (PE) MSACM.DRV
0x43d4c000-43d4e000 (PE) MIDIMAP.DRV
Threads:
process tid prio
00000001 (D) C:\Program Files\Infogrames Interactive\Civilization III\Civilization3.exe
00000002 0 <==
WineDbg terminated on pid 1


Any idea??

Thanks

---

### Post by Burgundavia on 2005-04-23
This is probably due to one of the apps, probably cedega looking in the current working directory for something that is in that subdir. 

Corey

---

### Post by Neo40 on 2005-04-23
[QUOTE=Burgundavia]This is probably due to one of the apps, probably cedega looking in the current working directory for something that is in that subdir. 

Corey[/QUOTE]

Hi,

Ok, then how can I add this to my menu in xfce4? Usualy, the command should be this: 
cedega ~/TransGaming_Drive/"Program Files"/"Infogrames Interactive"/"Civilization III"/Civilization3.exe

But like I said it won't work. :(

---

### Post by Alfonso VI on 2005-04-23
[QUOTE=Neo40]Hi,

Ok, then how can I add this to my menu in xfce4? Usualy, the command should be this: 
cedega ~/TransGaming_Drive/"Program Files"/"Infogrames Interactive"/"Civilization III"/Civilization3.exe

But like I said it won't work. :([/QUOTE]
 Maybe you could try using Point2Play in combination with Cedega - but I'm still having troubles getting Civ to start myself...

---

### Post by Dr Gonzo on 2005-04-25
I think you can use a flag like```
cedega -workdir "/home/YOU/.transgaming/c_drive/Program Files/Valve/Steam" "C:/Program Files/Valve/Steam/Steam.exe"
```This is how cedega creates shortcuts.

This is a wine thing.  Happens the same with cedega, crossover, and wine.

NOTE: change this to whatever program you're trying to start.

---

### Post by Neo40 on 2005-04-25
[QUOTE=Dr Gonzo]I think you can use a flag like```
cedega -workdir "/home/YOU/.transgaming/c_drive/Program Files/Valve/Steam" "C:/Program Files/Valve/Steam/Steam.exe"
```This is how cedega creates shortcuts.

This is a wine thing.  Happens the same with cedega, crossover, and wine.

NOTE: change this to whatever program you're trying to start.[/QUOTE]

Hi,
Thanks for your reply! Are you this is the right command? I tried it but nothing happens except I see a '>'

---

### Post by dafrabbit on 2005-04-26
Hrmm...well I'm not familiar with wine or cedega, but I have run into this problem with LimeWire. It needs to be started from within the LimeWire folder for the program to find all its files. In my case, the startup script was named "LimeWire.sh" so I just added at the top:

cd /absolute/path/to/LimeWire
#Program execution code here

In your case I think if you created a script and did that (cd into the Civilization III directory, then execute the executable using the cedega Civilization3.exe) then just call the script whenever you want to launch. Just remember to give the script executable permission with the command:

chmod +x scriptname

---

### Post by i-tech on 2005-04-28
I dont know about Cedega problem but if this Civ III that you mention is Call to Power there's a linux version of this game whih you can download from [http://www.torrentreactor.net](http://www.torrentreactor.net).
Enjoy!:grin:

---

