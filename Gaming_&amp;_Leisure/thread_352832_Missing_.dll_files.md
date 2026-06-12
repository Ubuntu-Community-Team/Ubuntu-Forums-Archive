---
title: "Missing .dll files?"
date: 2007-02-03
forum: Gaming &amp; Leisure
---

### Post by Bofur on 2007-02-03
Hey guys, I just installed wow with wine, and when I click the icon the little box pops up with all the blizzard news and updates along with the play button. But, when I click the play button, I get an error:```
 justin@justin-xt41fi7:~$ wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d050000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d050000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f328,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x18f9a0) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x18f9a0) Unhandled query type 8
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
wine: Unhandled page fault on read access to 0x00000000 at address 0x40e000 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0040e000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0040e000 ESP:0033fd20 EBP:0033fd48 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:00000000
 ESI:010cc508 EDI:00000001
Stack dump:
0x0033fd20:  0078c159 00000000 00000000 010c7688
0x0033fd30:  00000000 00000049 00854010 7698de7a
0x0033fd40:  0033fd74 0067f47c 0033fd74 0046de54
0x0033fd50:  00000000 00854008 0033fd68 0033fd73
0x0033fd60:  0033fd6c 00000400 00000004 00000003
0x0033fd70:  00000000 0033fd80 0046deda 0033fd94
Backtrace:
=>1 0x0040e000 in wow (+0xe000) (0x0033fd48)
  2 0x0046de54 in wow (+0x6de54) (0x0033fd74)
  3 0x0046deda in wow (+0x6deda) (0x0033fd80)
  4 0x0046d783 in wow (+0x6d783) (0x0033fdbc)
  5 0x00402c2b in wow (+0x2c2b) (0x0033fdf8)
  6 0x0042182a in wow (+0x2182a) (0x0033fe60)
  7 0x004215d1 in wow (+0x215d1) (0x0033fe78)
  8 0x0040447e in wow (+0x447e) (0x0033ff08)
  9 0x7b8702be in kernel32 (+0x502be) (0x0033ffe8)
  10 0xb7e9f587 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0040e000: movl        0x0(%ecx),%eax
Modules:
Module  Address                 Debug info      Name (102 modules)
PE      340000-3d0000   Deferred        fmod
PE      400000-d89000   Export          wow
PE      10000000-10069000       Deferred        divxdecoder
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc94000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc94000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c6eb000-7c700000       Deferred        psapi<elf>
  \-PE  7c6f0000-7c700000       \               psapi
ELF     7cc55000-7cc9e000       Deferred        dsound<elf>
  \-PE  7cc60000-7cc9e000       \               dsound
ELF     7cc9e000-7cce6000       Deferred        dbghelp<elf>
  \-PE  7ccb0000-7cce6000       \               dbghelp
ELF     7cce6000-7ccfa000       Deferred        mswsock<elf>
  \-PE  7ccf0000-7ccfa000       \               mswsock
ELF     7cf7e000-7d036000       Deferred        wined3d<elf>
  \-PE  7cf90000-7d036000       \               wined3d
ELF     7d036000-7d060000       Deferred        d3d9<elf>
  \-PE  7d040000-7d060000       \               d3d9
ELF     7d282000-7d297000       Deferred        midimap<elf>
  \-PE  7d290000-7d297000       \               midimap
PE      7d2a0000-7d2af000       --none--        msacm32
ELF     7d2af000-7d2eb000       Deferred        wineoss<elf>
  \-PE  7d2c0000-7d2eb000       \               wineoss
ELF     7d2eb000-7d31d000       Deferred        uxtheme<elf>
  \-PE  7d2f0000-7d31d000       \               uxtheme
ELF     7d54f000-7d554000       Deferred        libxfixes.so.3
ELF     7d554000-7d55d000       Deferred        libxcursor.so.1
ELF     7d55d000-7d57b000       Deferred        ximcp.so.2
ELF     7d57b000-7d57d000       Deferred        xlcutf8load.so.2
ELF     7d57d000-7d580000       Deferred        libxrandr.so.2
ELF     7d580000-7d588000       Deferred        libxrender.so.1
ELF     7d588000-7d58b000       Deferred        libxinerama.so.1
ELF     7da52000-7dadf000       Deferred        winex11<elf>
  \-PE  7da60000-7dadf000       \               winex11
ELF     7dadf000-7dafd000       Deferred        libexpat.so.1
ELF     7dafd000-7db2c000       Deferred        libfontconfig.so.1
ELF     7db2c000-7db40000       Deferred        libz.so.1
ELF     7db40000-7dbaa000       Deferred        libfreetype.so.6
ELF     7dbaa000-7dbc9000       Deferred        mpr<elf>
  \-PE  7dbb0000-7dbc9000       \               mpr
ELF     7dbc9000-7dc10000       Deferred        wininet<elf>
  \-PE  7dbd0000-7dc10000       \               wininet
ELF     7dc10000-7dc74000       Deferred        msvcrt<elf>
  \-PE  7dc20000-7dc74000       \               msvcrt
ELF     7dc74000-7dc9a000       Deferred        msacm32<elf>
ELF     7dc9a000-7dcae000       Deferred        lz32<elf>
  \-PE  7dca0000-7dcae000       \               lz32
ELF     7dcae000-7dcc7000       Deferred        version<elf>
  \-PE  7dcb0000-7dcc7000       \               version
ELF     7dcc7000-7dd55000       Deferred        winmm<elf>
  \-PE  7dcd0000-7dd55000       \               winmm
ELF     7dd55000-7dd71000       Deferred        imm32<elf>
  \-PE  7dd60000-7dd71000       \               imm32
ELF     7ddd2000-7e595000       Deferred        libglcore.so.1
ELF     7e595000-7e59a000       Deferred        libxdmcp.so.6
ELF     7e59a000-7e614000       Deferred        libglu.so.1
ELF     7e614000-7e699000       Deferred        libgl.so.1
ELF     7e699000-7e762000       Deferred        libx11.so.6
ELF     7e762000-7e76f000       Deferred        libxext.so.6
ELF     7e76f000-7e774000       Deferred        libxxf86vm.so.1
ELF     7e774000-7e78c000       Deferred        libice.so.6
ELF     7e78c000-7e806000       Deferred        opengl32<elf>
  \-PE  7e7a0000-7e806000       \               opengl32
ELF     7e806000-7e832000       Deferred        ws2_32<elf>
  \-PE  7e810000-7e832000       \               ws2_32
ELF     7e832000-7e84c000       Deferred        wsock32<elf>
  \-PE  7e840000-7e84c000       \               wsock32
ELF     7e84c000-7e85f000       Deferred        libresolv.so.2
ELF     7e85f000-7e87d000       Deferred        iphlpapi<elf>
  \-PE  7e870000-7e87d000       \               iphlpapi
ELF     7e87d000-7e8d2000       Deferred        rpcrt4<elf>
  \-PE  7e890000-7e8d2000       \               rpcrt4
ELF     7e8d2000-7e96b000       Deferred        ole32<elf>
  \-PE  7e8e0000-7e96b000       \               ole32
ELF     7e96b000-7e9c3000       Deferred        shlwapi<elf>
  \-PE  7e980000-7e9c3000       \               shlwapi
ELF     7e9c3000-7eab5000       Deferred        shell32<elf>
  \-PE  7e9d0000-7eab5000       \               shell32
ELF     7eab5000-7eac0000       Deferred        libgcc_s.so.1
ELF     7eac2000-7eac4000       Deferred        libnvidia-tls.so.1
ELF     7eac4000-7eacd000       Deferred        libsm.so.6
ELF     7ebac000-7ec63000       Deferred        gdi32<elf>
  \-PE  7ebc0000-7ec63000       \               gdi32
ELF     7ec63000-7ed9c000       Deferred        user32<elf>
  \-PE  7ec80000-7ed9c000       \               user32
ELF     7ed9c000-7ee5c000       Deferred        comctl32<elf>
  \-PE  7edb0000-7ee5c000       \               comctl32
ELF     7ee5c000-7eea2000       Deferred        advapi32<elf>
  \-PE  7ee70000-7eea2000       \               advapi32
ELF     7efac000-7efb7000       Deferred        libnss_files.so.2
ELF     7efb7000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff3000       Deferred        libm.so.6
ELF     7eff3000-7eff6000       Deferred        libxau.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d35000-b7d3e000       Deferred        libnss_compat.so.2
ELF     b7d3f000-b7d43000       Deferred        libdl.so.2
ELF     b7d43000-b7e77000       Deferred        libc.so.6
ELF     b7e78000-b7e8b000       Deferred        libpthread.so.0
ELF     b7e98000-b7fa9000       Export          libwine.so.1
ELF     b7fab000-b7fc6000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\World of Warcraft\WoW.exe
        00000019    0
        00000018    0
        00000017    0
        00000016    0
        00000015    0
        00000012    0
        00000011    0
        00000010    0
        0000000d    1
        00000009    0 <==
justin@justin-xt41fi7:~$ 


```

I tried downloading those dll's from that Ubuntu Wow/Wine installation guide and I put them in my .wine/system32 folder but alas it still didnt work. Does anyone have any ideas? Thanks!

---

### Post by Bofur on 2007-02-04
Anyone? Please?

---

### Post by Saubazi on 2007-02-05
I know nothing about WoW or so but 
normally, I'd expect that you need to define an override for the .dlls
as well after placing them to system32 folder. This you can do on
winecfg. Might be worth a trial...

---

### Post by conjur3r on 2007-02-05
Follow this thread.  It contains some extra things that you may have not done.  [http://ubuntuforums.org/showthread.php?t=312482](http://ubuntuforums.org/showthread.php?t=312482)

---

### Post by pay on 2007-02-05
> Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".That would probably be helpful aswell.

---

