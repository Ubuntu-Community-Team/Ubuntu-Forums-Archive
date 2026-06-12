---
title: "Space Cowboy Online"
date: 2007-10-21
forum: Gaming &amp; Leisure
---

### Post by survient on 2007-10-21
Ok, been trying to get this running for awhile now, making some good progress though. I've gotten things to the point where the installer will run, and then the launcher will pop up, let me type in my username and login, I'll hit start, the screen will go white, and then crash. This game does use direct X, however it's not that graphic intensive, so for WoW to be able to run and SCO not to, I find hard to believe. I'm running ubuntu 7.10 x64 with wine ver 0.9.47. This is what I get from the debugger:
> 
$winedbg SCO 
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x136f9c)->((null) 1 0x34e5e0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->((null) 25 2 0x34e5f4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->((null) 26 2 0x34e5f4 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x136f9c)->(0x34e630)
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34e6ec (nil))
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x137c10)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x137cd0)
fixme:urlmon:ObtainUserAgentString (0, 0x34d02b, 0x34d024): stub
fixme:urlmon:ObtainUserAgentString (0, 0x13a080, 0x34d024): stub
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x137c10)->(0x34d02c 0x34d024 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->((null) 29 2 0x34ee70 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x136f9c)
fixme:shdocvw:ClientSite_GetContainer (0x136f9c)->(0x34ee90)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x136f9c)->(0xf7df9189)
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->((null) 25 2 0x34edc4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->((null) 26 2 0x34edc4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->((null) 28 2 0x34ee1c (nil))
fixme:mshtml:HttpNegotiate_OnResponse (0x137c10)->(200 L"HTTP/1.0 200 OK\r\nConnection: keep-alive\r\nContent-Type: text/html\r\nAccept-Ranges: bytes\r\nETag: \"-4834906560023890857\"\r\nLast-Modified: Thu, 16 Aug 2007 19:58:13 GMT\r\nContent-Length: 1525\r\nDate: Sun, 21 Oct 2007 09:03:52 GMT\r\nServer: lighttpd/1.4.16\r\n\r\n" (null) 0x34edd8)
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 360, std (d/m/y): 4/11/2007, dlt (d/m/y): 11/03/2007
fixme:win:EnumDisplayDevicesW ((null),0,0x3235fc,0x00000000), stub!
fixme:imm:ImmGetOpenStatus (0x122fa0): semi-stub
fixme:imm:ImmReleaseContext (0x30026, 0x122fa0): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x322b74, 260): stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x561b90 (thread 0012), starting debugger...
fixme:winmm:MMDRV_Exit Closing while ll-driver open


can anybody make sense of this? I'm just trying to get this game running, I know it's something stupid keeping it from running, I'm just having trouble pinpointing what it is. It's a good game, and it would be nice to get it running on linux. Any help would be appreciated.

---

### Post by survient on 2007-10-21
I was able to get more debug output from it:
> 
$ env WINEPREFIX="/home/sam/.wine" wine "C:\Program Files\GPotato\SpaceCowboy\SpaceCowboy.exe"
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x136f9c)->((null) 1 0x34e5e0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->((null) 25 2 0x34e5f4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->((null) 26 2 0x34e5f4 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x136f9c)->(0x34e630)
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34e6ec (nil))
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x137c10)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x137cd0)
fixme:urlmon:ObtainUserAgentString (0, 0x34d02b, 0x34d024): stub
fixme:urlmon:ObtainUserAgentString (0, 0x13a080, 0x34d024): stub
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x137c10)->(0x34d02c 0x34d024 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->((null) 29 2 0x34ee70 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x136f9c)
fixme:shdocvw:ClientSite_GetContainer (0x136f9c)->(0x34ee90)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x136f9c)->(0xf7e2b189)
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->((null) 25 2 0x34edc4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->((null) 26 2 0x34edc4 (nil))
$ fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x136f9c)->((null) 28 2 0x34ee1c (nil))
fixme:mshtml:HttpNegotiate_OnResponse (0x137c10)->(200 L"HTTP/1.0 200 OK\r\nConnection: keep-alive\r\nContent-Type: text/html\r\nAccept-Ranges: bytes\r\nETag: \"-4834906560023890857\"\r\nLast-Modified: Thu, 16 Aug 2007 19:58:13 GMT\r\nContent-Length: 1525\r\nDate: Sun, 21 Oct 2007 09:18:36 GMT\r\nServer: lighttpd/1.4.16\r\n\r\n" (null) 0x34edd8)
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 360, std (d/m/y): 4/11/2007, dlt (d/m/y): 11/03/2007
fixme:win:EnumDisplayDevicesW ((null),0,0x3235fc,0x00000000), stub!
fixme:imm:ImmGetOpenStatus (0x122fa0): semi-stub
fixme:imm:ImmReleaseContext (0x30026, 0x122fa0): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x322b74, 260): stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x561b90 (thread 0010), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00561b90).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00561b90 ESP:003239b8 EBP:0034f42c EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00323f08 ECX:00000000 EDX:006efee4
 ESI:0012d778 EDI:7b888df0
Stack dump:
0x003239b8:  00323a8c 006745a9 ffffffff 004027c1
0x003239c8:  00323a8c 0012d778 003239f4 006717cb
0x003239d8:  ffffffff 00402812 00000002 40000000
0x003239e8:  00000000 00323a8c 00323a8c 0034fe70
0x003239f8:  006717f6 ffffffff 00513851 00000000
0x00323a08:  00323a8c 00000000 00000000 00323aa8
Backtrace:
=>1 0x00561b90 in spacecowboy.atm (+0x161b90) (0x0034f42c)
  2 0x20777328 (0x204c4148)
  3 0x00000000 (0x00000000)
0x00561b90: movl        0x0(%ecx),%eax
Modules:
Module  Address                 Debug info      Name (78 modules)
PE        400000-  6f9000       Export          spacecowboy.atm
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cc8b000-7cca0000       Deferred        midimap<elf>
  \-PE  7cc90000-7cca0000       \               midimap
ELF     7cca0000-7ccc6000       Deferred        msacm32<elf>
  \-PE  7ccb0000-7ccc6000       \               msacm32
ELF     7cf76000-7cf81000       Deferred        libgcc_s.so.1
ELF     7cf81000-7cf99000       Deferred        msacm32<elf>
  \-PE  7cf90000-7cf99000       \               msacm32
ELF     7cf99000-7cfd5000       Deferred        wineoss<elf>
  \-PE  7cfa0000-7cfd5000       \               wineoss
ELF     7cfe5000-7cfea000       Deferred        libxfixes.so.3
ELF     7cfea000-7cff3000       Deferred        libxcursor.so.1
ELF     7cff3000-7cff6000       Deferred        libxinerama.so.1
ELF     7daa7000-7e43f000       Deferred        libglcore.so.1
ELF     7e43f000-7e4d5000       Deferred        libgl.so.1
ELF     7e4d5000-7e4da000       Deferred        libxdmcp.so.6
ELF     7e4da000-7e4dd000       Deferred        libxau.so.6
ELF     7e4dd000-7e5ce000       Deferred        libx11.so.6
ELF     7e5ce000-7e5dc000       Deferred        libxext.so.6
ELF     7e5df000-7e5e7000       Deferred        libxrender.so.1
ELF     7e5f2000-7e681000       Deferred        winex11<elf>
  \-PE  7e600000-7e681000       \               winex11
ELF     7e6e9000-7e709000       Deferred        libexpat.so.1
ELF     7e709000-7e734000       Deferred        libfontconfig.so.1
ELF     7e734000-7e749000       Deferred        libz.so.1
ELF     7e749000-7e7b9000       Deferred        libfreetype.so.6
ELF     7e7cf000-7e7fc000       Deferred        ws2_32<elf>
  \-PE  7e7e0000-7e7fc000       \               ws2_32
ELF     7e7fc000-7e816000       Deferred        version<elf>
  \-PE  7e800000-7e816000       \               version
ELF     7e816000-7e8b3000       Deferred        oleaut32<elf>
  \-PE  7e830000-7e8b3000       \               oleaut32
ELF     7e8b3000-7e8d0000       Deferred        imm32<elf>
  \-PE  7e8c0000-7e8d0000       \               imm32
ELF     7e8d0000-7e95e000       Deferred        winmm<elf>
  \-PE  7e8e0000-7e95e000       \               winmm
ELF     7e95e000-7e9a7000       Deferred        dsound<elf>
  \-PE  7e970000-7e9a7000       \               dsound
ELF     7e9a7000-7e9dd000       Deferred        dinput<elf>
  \-PE  7e9b0000-7e9dd000       \               dinput
ELF     7e9dd000-7e9f6000       Deferred        dinput8<elf>
  \-PE  7e9e0000-7e9f6000       \               dinput8
ELF     7e9f6000-7ea09000       Deferred        libresolv.so.2
ELF     7ea09000-7ea27000       Deferred        iphlpapi<elf>
  \-PE  7ea10000-7ea27000       \               iphlpapi
ELF     7ea27000-7ea80000       Deferred        rpcrt4<elf>
  \-PE  7ea30000-7ea80000       \               rpcrt4
ELF     7ea80000-7eb21000       Deferred        ole32<elf>
  \-PE  7ea90000-7eb21000       \               ole32
ELF     7eb21000-7eb3d000       Deferred        d3dxof<elf>
  \-PE  7eb30000-7eb3d000       \               d3dxof
ELF     7eb3d000-7ebd8000       Deferred        gdi32<elf>
  \-PE  7eb50000-7ebd8000       \               gdi32
ELF     7ebd8000-7ed16000       Deferred        user32<elf>
  \-PE  7ebf0000-7ed16000       \               user32
ELF     7ed16000-7edf7000       Deferred        wined3d<elf>
  \-PE  7ed30000-7edf7000       \               wined3d
PE      7edf7000-7ee26000       Deferred        d3d9
ELF     7ee26000-7ee6f000       Deferred        advapi32<elf>
  \-PE  7ee30000-7ee6f000       \               advapi32
ELF     7ee6f000-7ee87000       Deferred        libnsl.so.1
ELF     7ee87000-7ee90000       Deferred        libnss_compat.so.2
ELF     7ee90000-7ee92000       Deferred        libnvidia-tls.so.1
ELF     7ee92000-7eea6000       Deferred        lz32<elf>
  \-PE  7eea0000-7eea6000       \               lz32
ELF     7efc5000-7efea000       Deferred        libm.so.6
ELF     7eff5000-7f000000       Deferred        libnss_files.so.2
ELF     f7d02000-f7d06000       Deferred        libdl.so.2
ELF     f7d06000-f7e50000       Deferred        libc.so.6
ELF     f7e51000-f7e69000       Deferred        libpthread.so.0
ELF     f7e6b000-f7e75000       Deferred        libnss_nis.so.2
ELF     f7e7f000-f7f93000       Deferred        libwine.so.1
ELF     f7f95000-f7fb3000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f (D) C:\Program Files\GPotato\SpaceCowboy\SpaceCowboy.atm
        0000001c   15
        00000014   15
        00000011    0
        00000010    0 <==
0000000c 
        0000000e    0
        0000000d    0
0000000a 
        0000000b    0
fixme:winmm:MMDRV_Exit Closing while ll-driver open

wtf?

---

### Post by hikaricore on 2007-10-21
This application may use things such as .NET framework or other obscure protocols that aren't yet implemented in WINE, but I'm not really sure.

Consider adding further information to the WINE Application Database page for SCO here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7206](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7206)

It's unlikely the game will run anytime the way that it's looking, however your info is always useful to the cause.

^_^

---

