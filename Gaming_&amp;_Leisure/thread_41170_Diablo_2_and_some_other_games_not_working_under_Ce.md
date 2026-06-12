---
title: "Diablo 2 and some other games not working under Cedega"
date: 2005-06-12
forum: Gaming &amp; Leisure
---

### Post by Turambar on 2005-06-12
I have Cedega version 4.2.1-1 and I have Radeon 9600 Pro with OpenGL working. When trying to execute command "cedega Game_crk.exe", Cedega returns this:

```

wine: Unhandled exception, starting debugger...
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0xb7ff7195
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0xb7ee8000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0xb7ed3000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0xb7e0b000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0xb7e09000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0xb7ddc000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0xb7caf000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0xb7c9f000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0xb7c9c000)
No debug information in ELF '/lib/ld-linux.so.2' (0xb7feb000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libcrtdll.so' (0xb77cb000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libkernel32.so' (0xb774a000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libuser32.so' (0xb7622000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libgdi32.so' (0xb75ab000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libadvapi32.so' (0xb7584000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libcomdlg32.so' (0xb751f000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libshell32.so' (0xb74a4000)
No debug information in ELF '/usr/lib/libpng.so.3' (0xb7474000)
No debug information in ELF '/usr/lib/libz.so.1' (0xb7463000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libole32.so' (0xb73fe000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/librpcrt4.so' (0xb73b8000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libshlwapi.so' (0xb7378000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libcomctl32.so' (0xb72f2000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwinspool.drv.so' (0xb72dd000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libversion.so' (0xb72d3000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/liblz32.so' (0xb72cc000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwsock32.so' (0xb72bf000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libws2_32.so' (0xb72a7000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libiphlpapi.so' (0xb7298000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libdsound.so' (0xb7276000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwinmm.so' (0xb7220000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwineserver.so' (0xb71df000)
No debug information in ELF '/usr/lib/libfreetype.so.6' (0xb6c43000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libx11drv.so' (0xb6bc5000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_tsx11.so' (0xb6bb3000)
No debug information in ELF '/usr/X11R6/lib/libSM.so.6' (0xb6b9e000)
No debug information in ELF '/usr/X11R6/lib/libICE.so.6' (0xb6b86000)
No debug information in ELF '/usr/X11R6/lib/libGL.so.1' (0xb6ae1000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libGLU.so.1' (0xb6a26000)
No debug information in ELF '/usr/X11R6/lib/libXext.so.6' (0xb6a19000)
No debug information in ELF '/usr/X11R6/lib/libX11.so.6' (0xb6954000)
No debug information in ELF '/usr/X11R6/lib/modules/dri/fglrx_dri.so' (0xb60c4000)
No debug information in ELF '/lib/tls/i686/cmov/librt.so.1' (0xb5ff7000)
No debug information in ELF '/lib/libgcc_s.so.1' (0xb5fec000)
No debug information in ELF '/usr/X11R6/lib/X11/locale/lib/common/xlcDef.so.2' (0xadafa000)
No debug information in ELF '/usr/X11R6/lib/X11/locale/lib/common/ximcp.so.2' (0xadade000)
No debug information in ELF '/usr/lib/gconv/ISO8859-15.so' (0xadada000)
No debug information in ELF '/usr/lib/libXcursor.so.1' (0xadac5000)
No debug information in ELF '/usr/lib/libXrender.so.1' (0xadabd000)
No debug information in 32bit DLL 'G:\media\hdb1\Games\Diablo II\Game_crk.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0xb7f25000)
No debug information in 32bit DLL 'KERNEL32.DLL' (0xb777d000)
No debug information in 32bit DLL 'C:\WINDOWS\SYSTEM32\MSVCRT.DLL' (0x78000000)
No debug information in 32bit DLL 'CRTDLL.DLL' (0xb77d7000)
No debug information in 32bit DLL 'ADVAPI32.DLL' (0xb7596000)
No debug information in 32bit DLL 'GDI32.DLL' (0xb75ca000)
No debug information in 32bit DLL 'USER32.DLL' (0xb7659000)
No debug information in 32bit DLL 'RPCRT4.DLL' (0xb73db000)
No debug information in 32bit DLL 'OLE32.DLL' (0xb741d000)
No debug information in 32bit DLL 'SHLWAPI.DLL' (0xb7395000)
No debug information in 32bit DLL 'COMCTL32.DLL' (0xb7300000)
No debug information in 32bit DLL 'SHELL32.DLL' (0xb74ca000)
No debug information in 32bit DLL 'WINSPOOL.DRV' (0xb72e5000)
No debug information in 32bit DLL 'COMDLG32.DLL' (0xb7531000)
No debug information in 32bit DLL 'LZ32.DLL' (0xb72cf000)
No debug information in 32bit DLL 'VERSION.DLL' (0xb72d6000)
No debug information in 32bit DLL 'G:\MEDIA\HDB1\GAMES\DIABLO II\STORM.DLL' (0x6ffb0000)
No debug information in 32bit DLL 'IPHLPAPI.DLL' (0xb729f000)
No debug information in 32bit DLL 'WS2_32.DLL' (0xb72af000)
No debug information in 32bit DLL 'WSOCK32.DLL' (0xb72c3000)
No debug information in 32bit DLL 'G:\MEDIA\HDB1\GAMES\DIABLO II\FOG.DLL' (0x6ff50000)
No debug information in 32bit DLL 'G:\MEDIA\HDB1\GAMES\DIABLO II\D2GFX.DLL' (0x6fa70000)
No debug information in 32bit DLL 'G:\MEDIA\HDB1\GAMES\DIABLO II\D2MCPCLIENT.DLL' (0x6f9f0000)
No debug information in 32bit DLL 'WINMM.DLL' (0xb722e000)
No debug information in 32bit DLL 'DSOUND.DLL' (0xb7283000)
No debug information in 32bit DLL 'G:\MEDIA\HDB1\GAMES\DIABLO II\D2SOUND.DLL' (0x6f980000)
No debug information in 32bit DLL 'G:\MEDIA\HDB1\GAMES\DIABLO II\D2CMP.DLL' (0x6fdf0000)
No debug information in 32bit DLL 'G:\MEDIA\HDB1\GAMES\DIABLO II\D2LANG.DLL' (0x6fc10000)
No debug information in 32bit DLL 'G:\MEDIA\HDB1\GAMES\DIABLO II\IJL11.DLL' (0x60000000)
No debug information in 32bit DLL 'G:\MEDIA\HDB1\GAMES\DIABLO II\D2WIN.DLL' (0x6f8a0000)
No debug information in 32bit DLL 'X11DRV.DLL' (0xb6be3000)
Unhandled exception: page fault on read access to 0x305bdd40 in 32-bit code (0x6ffd968b).
In 32-bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:6ffd968b ESP:b79f2820 EBP:b79f2878 EFLAGS:00010213(  R- 00  I   -A- 1C)
 EAX:305bdd40 EBX:ad82009c ECX:ad820098 EDX:527dff63
 ESI:00000000 EDI:00000000
Stack dump:
0xb79f2820 (CRTDLL.DLL._osmode_dll+0x212c2c):  00000000 00000000 b7fd08a8 6ffd5e3f
0xb79f2830 (CRTDLL.DLL._osmode_dll+0x212c3c):  00000004 6ffee074 6ffee068 6ffd5dd5
0xb79f2840 (CRTDLL.DLL._osmode_dll+0x212c4c):  6ffd9ed2 00000001 00000001 6ffd9de0
0xb79f2850 (CRTDLL.DLL._osmode_dll+0x212c5c):  00000001 6ffb0000 b7f5ad93 6ffb0000
0xb79f2860 (CRTDLL.DLL._osmode_dll+0x212c6c):  00000001 00000001 6ffd9dd0 b7fd08a8
0xb79f2870 (CRTDLL.DLL._osmode_dll+0x212c7c):  b7b804e0 00000001 b79f28a0 b7f56501
0xb79f2880 (CRTDLL.DLL._osmode_dll+0x212c8c):

Backtrace:
=>0 0x6ffd968b (STORM.DLL.533+0x183b in G:\MEDIA\HDB1\GAMES\DIABLO II\STORM.DLL) (ebp=b79f2878)
  1 0xb7f56501 (KERNEL32.DLL.__wine_call_from_16_regs+0x1ff5 in libntdll.so) (ebp=b79f28a0)
  2 0xb7f5667f (KERNEL32.DLL.__wine_call_from_16_regs+0x2173 in libntdll.so) (ebp=b79f28c8)
  3 0xb7f566c7 (KERNEL32.DLL.__wine_call_from_16_regs+0x21bb in libntdll.so) (ebp=b79f28ec)
  4 0xb7f97c6c (NTDLL.DLL.wine_server_call+0x19ec in libntdll.so) (ebp=b79f2994)  5 0xb7f97e0f (NTDLL.DLL.wine_server_call+0x1b8f in libntdll.so) (ebp=b79f2ac8)  6 0xb7ca3ae0 (CRTDLL.DLL._osmode_dll+0x4c3eec in libpthread.so.0) (ebp=b79f2b3c)
  7 0xb7d81c9a (NTDLL.DLL.memcpy+0x5b36a in libc.so.6) (ebp=00000000)

0x6ffd968b (STORM.DLL.533+0x183b in G:\MEDIA\HDB1\GAMES\DIABLO II\STORM.DLL): movl      0x0(%eax),%edi
Modules:
Address                 Module  Name
0x60000000-6002e000     (PE)    G:\MEDIA\HDB1\GAMES\DIABLO II\IJL11.DLL
0x6f8a0000-6f970000     (PE)    G:\MEDIA\HDB1\GAMES\DIABLO II\D2WIN.DLL
0x6f980000-6f996000     (PE)    G:\MEDIA\HDB1\GAMES\DIABLO II\D2SOUND.DLL
0x6f9f0000-6fa05000     (PE)    G:\MEDIA\HDB1\GAMES\DIABLO II\D2MCPCLIENT.DLL
0x6fa70000-6fa91000     (PE)    G:\MEDIA\HDB1\GAMES\DIABLO II\D2GFX.DLL
0x6fc10000-6fc25000     (PE)    G:\MEDIA\HDB1\GAMES\DIABLO II\D2LANG.DLL
0x6fdf0000-6fef7000     (PE)    G:\MEDIA\HDB1\GAMES\DIABLO II\D2CMP.DLL
0x6ff50000-6ffa6000     (PE)    G:\MEDIA\HDB1\GAMES\DIABLO II\FOG.DLL
0x6ffb0000-6fff5000     (PE)    G:\MEDIA\HDB1\GAMES\DIABLO II\STORM.DLL
0x78000000-78046000     (PE)    C:\WINDOWS\SYSTEM32\MSVCRT.DLL
0xb6be3000-b6be5000     (PE)    X11DRV.DLL
0xb722e000-b7230000     (PE)    WINMM.DLL
0xb7283000-b7285000     (PE)    DSOUND.DLL
0xb729f000-b72a1000     (PE)    IPHLPAPI.DLL
0xb72af000-b72b1000     (PE)    WS2_32.DLL
0xb72c3000-b72c5000     (PE)    WSOCK32.DLL
0xb72cf000-b72d1000     (PE)    LZ32.DLL
0xb72d6000-b72d8000     (PE)    VERSION.DLL
0xb72e5000-b72e7000     (PE)    WINSPOOL.DRV
0xb7300000-b7302000     (PE)    COMCTL32.DLL
0xb7395000-b7397000     (PE)    SHLWAPI.DLL
0xb73db000-b73dd000     (PE)    RPCRT4.DLL
0xb741d000-b741f000     (PE)    OLE32.DLL
0xb74ca000-b74cc000     (PE)    SHELL32.DLL
0xb7531000-b7533000     (PE)    COMDLG32.DLL
0xb7596000-b7598000     (PE)    ADVAPI32.DLL
0xb75ca000-b75cc000     (PE)    GDI32.DLL
0xb7659000-b765b000     (PE)    USER32.DLL
0xb777d000-b777f000     (PE)    KERNEL32.DLL
0xb77d7000-b77d9000     (PE)    CRTDLL.DLL
0xb7f25000-b7f27000     (PE)    NTDLL.DLL
0x00400000-00416000     (PE)    G:\media\hdb1\Games\Diablo II\Game_crk.exe
Threads:
process  tid      prio
00000001 (D) G:\media\hdb1\Games\Diablo II\Game_crk.exe
        00000002    0 <==
WineDbg terminated on pid 1

```

Diablo is installed on my Windows partition, but it works fine with the latest Wine. I want to get rid of Wine, because it doesn't support so many games. I have searched these forums, Google and Transgaming, but I haven't solved the problem. Also some other games like Red Alert return this error. I tried to install Diablo again from the cd, but I got the error again. Curiously I don't get any errors while loading Counter-Strike 1.5. I have read the Cedega FAQ and tried to configure many times, but nothing helps.

Any suggestions?

---

### Post by tread on 2005-06-12
I have absolutely nothing useful to say ... but ...

>  Game_crk.exe 

 :smile:  :razz:  :razz:

---

### Post by kostkon on 2005-06-12
[QUOTE=tread]I have absolutely nothing useful to say ... but ...

Game_crk.exe

 :smile:  :razz:  :razz:[/QUOTE]

Hahahahaha!

Yes, tread maybe you found the reason why our friend Turambar here, is getting these errors!

---

### Post by Turambar on 2005-06-12
Heh

As far as I known that "crack" is only a no-cd loader which somehow makes the game think the cd is in the drive. With the original Game.exe I get exactly the same errors. And by the way I really own this game, it has not been downloaded via Bittorrent or any else p2p software.

---

### Post by tread on 2005-06-12
Sok, relax .. I just found it amusing :) Didn't mean to criticise or anything .. even if it were a bittorrent download, well, it would be your call to make.

---

### Post by Trickyphillips on 2005-06-13
Cedega is terrible. I purchased it, and have tried installing more than 10 games on multiple versions of Cedega and Point2Play, and have only got one working. Even then, the netplay didn't work. 

I have even seen several threads on TransGaming's own boards about how terrible their software is.

My advice: Stay away from Cedega; although it's obviously too late for that. :[

---

### Post by kostkon on 2005-06-13
[QUOTE=Turambar]Heh

As far as I known that "crack" is only a no-cd loader which somehow makes the game think the cd is in the drive. With the original Game.exe I get exactly the same errors. And by the way I really own this game, it has not been downloaded via Bittorrent or any else p2p software.[/QUOTE]

My comment, also, was a light-hearted one, Turambar. You have the right to do anything you want, noone is going to judged you here for something!

---

### Post by Turambar on 2005-06-13
Yes, I understand that you found it funny. But also notice that my post makes clear that my Diablo isn't cracked ten times and the errors don't occur because of the crack. So people who can help me can find the right solution.

:)

---

### Post by tread on 2005-06-13
Hmm .. I wonder .. do you get the no_cd thingy working with wine? Because a no_cd type of utility is essentially a hack and may not be implemented in wine. As a workaround, you could maintain wine in a different location just for  the purpose of running diablo2 (addictive game, isn't it?)

---

### Post by mike998 on 2005-06-14
I'd love to play Diablo 2 (one of my favourite games, ever) with Wine, but I can't get the thing to either install or play - it's annoying.
I'm also not 100% comfortable with using a no CD hack for a game I own.

---

