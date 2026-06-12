---
title: "Wine help, getting a Windows installation of WoW to work?"
date: 2006-12-24
forum: Gaming &amp; Leisure
---

### Post by dyzzy on 2006-12-24
Hey guys, I have WoW installed on my computer from Windows so I was trying to get it to work under Wine (why waste space by reinstalling it?) All of the guides and HowTo's I've seen were installing WoW from Linux with Wine and getting that to work. 

I followed the (un?)official HowTo on the Ubuntu wiki step by step (after the installation section), with editing the wine config to use OSS and config.wtf to use opengl, but all I get when I try to run WoW is a blank black screen. I hear what I think is the background sound for the opening screen, but I can't see anything.

So basically, what am I doing wrong? Do I need to actually install WoW using Wine? The HowTo says that I could just use an existing Windows installation so I thought it would be fine. Did I just do something wrong when trying to run WoW?

Thanks for any help!

---

### Post by dio525i on 2006-12-24
run it from the terminal and post any errors

---

### Post by yange on 2006-12-24
I also have the exact same problem, I've stated in recent thread. This is what happens after wow crashes... 

```
yange@yange-desktop:~/Programs/World_of_Warcraft$ wine wow.exe -opengl
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d640000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d640000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f34c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
*********************************WARN_ONCE*********************************
File r300_vertexprog.c function t_dst_index line 184
Unknown output 3
***************************************************************************
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 406
Software fallback:ctx->Multisample.Enabled
***************************************************************************
Try R300_SPAN_DISABLE_LOCKING env var if this hangs.
wine: Unhandled page fault on read access to 0x00007548 at address 0x7e09aa03 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00007548 in 32-bit code (0x7e09aa03).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e09aa03 ESP:0033c62c EBP:0033c6a4 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:000010c5 EBX:7e26b4a0 ECX:00007548 EDX:00000000
 ESI:7c10b6e0 EDI:7d9881c8
Stack dump:
0x0033c62c:  7c054e38 7d9881c8 00000018 00000002
0x0033c63c:  0000000c 00001403 00007548 7e26b4a0
0x0033c64c:  7c10b6e0 00000004 10c5c694 0033c668
0x0033c65c:  7c054e38 7e129b5e 00007548 7c12a730
0x0033c66c:  7d97c000 0000c1c8 0000c1e0 0000c1c8
0x0033c67c:  e030f1c8 00000000 00000000 00000000
Backtrace:
=>1 0x7e09aa03 in r300_dri.so (+0x2ca03) (0x0033c6a4)
  2 0x7e12c83d in r300_dri.so (+0xbe83d) (0x0033c6d4)
  3 0x7e673cbd glDrawRangeElementsEXT+0x4d() in libgl.so.1 (0x0033c704)
  4 0x7e7d8e60 in opengl32 (+0x28e60) (0x0033c744)
  5 0x005d8a73 in wow (+0x1d8a73) (0x0033c770)
  6 0x005c3308 in wow (+0x1c3308) (0x0033c78c)
  7 0x005c331b in wow (+0x1c331b) (0x0033c7b8)
  8 0x007473ec in wow (+0x3473ec) (0x0033c84c)
  9 0x007446dc in wow (+0x3446dc) (0x0033fbc8)
  10 0x007bf22e in wow (+0x3bf22e) (0x0033fca0)
  11 0x004734ef in wow (+0x734ef) (0x0033fcc4)
  12 0x007b5a57 in wow (+0x3b5a57) (0x0033fce8)
  13 0x007b430c in wow (+0x3b430c) (0x0033fcf4)
  14 0x0044306e in wow (+0x4306e) (0x0033fdbc)
  15 0x004250a0 in wow (+0x250a0) (0x0033fdf0)
  16 0x00421a5f in wow (+0x21a5f) (0x0033fe60)
  17 0x004215e1 in wow (+0x215e1) (0x0033fe78)
  18 0x0040448e in wow (+0x448e) (0x0033ff08)
  19 0x7b87023e in kernel32 (+0x5023e) (0x0033ffe8)
  20 0xb7e35587 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7e09aa03: movzwl      0x0(%ecx,%edx,2),%eax
Modules:
Module  Address                 Debug info      Name (97 modules)
PE      340000-3d0000   Deferred        fmod
PE      400000-d8d000   Export          wow
PE      10000000-10069000       Deferred        divxdecoder
ELF     73098000-730df000       Deferred        dbghelp<elf>
  \-PE  730a0000-730df000       \               dbghelp
ELF     7b800000-7b91b000       Export          kernel32<elf>
  \-PE  7b820000-7b91b000       \               kernel32
ELF     7bc00000-7bc83000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d3b3000-7d3c8000       Deferred        psapi<elf>
  \-PE  7d3c0000-7d3c8000       \               psapi
ELF     7d3e9000-7d3ef000       Deferred        libnss_dns.so.2
ELF     7d3f9000-7d40d000       Deferred        mswsock<elf>
  \-PE  7d400000-7d40d000       \               mswsock
ELF     7d875000-7d88a000       Deferred        midimap<elf>
  \-PE  7d880000-7d88a000       \               midimap
PE      7d890000-7d8a2000       --none--        msacm32
ELF     7d8a2000-7d8de000       Deferred        wineoss<elf>
  \-PE  7d8b0000-7d8de000       \               wineoss
ELF     7d90b000-7d93d000       Deferred        uxtheme<elf>
  \-PE  7d910000-7d93d000       \               uxtheme
ELF     7d93f000-7d944000       Deferred        libxfixes.so.3
ELF     7d944000-7d94d000       Deferred        libxcursor.so.1
ELF     7d94d000-7d96b000       Deferred        ximcp.so.2
ELF     7d96b000-7d96d000       Deferred        xlcutf8load.so.2
ELF     7d96d000-7d970000       Deferred        libxrandr.so.2
ELF     7d970000-7d978000       Deferred        libxrender.so.1
ELF     7d978000-7d97b000       Deferred        libxinerama.so.1
ELF     7e06e000-7e286000       Export          r300_dri.so
ELF     7e286000-7e313000       Deferred        winex11<elf>
  \-PE  7e2a0000-7e313000       \               winex11
ELF     7e313000-7e331000       Deferred        libexpat.so.1
ELF     7e331000-7e360000       Deferred        libfontconfig.so.1
ELF     7e360000-7e374000       Deferred        libz.so.1
ELF     7e374000-7e3de000       Deferred        libfreetype.so.6
ELF     7e3de000-7e3fd000       Deferred        mpr<elf>
  \-PE  7e3f0000-7e3fd000       \               mpr
ELF     7e3fd000-7e444000       Deferred        wininet<elf>
  \-PE  7e410000-7e444000       \               wininet
ELF     7e444000-7e4a8000       Deferred        msvcrt<elf>
  \-PE  7e450000-7e4a8000       \               msvcrt
ELF     7e4a8000-7e4ce000       Deferred        msacm32<elf>
ELF     7e4ce000-7e4e2000       Deferred        lz32<elf>
  \-PE  7e4d0000-7e4e2000       \               lz32
ELF     7e4e2000-7e4fb000       Deferred        version<elf>
  \-PE  7e4f0000-7e4fb000       \               version
ELF     7e4fb000-7e589000       Deferred        winmm<elf>
  \-PE  7e510000-7e589000       \               winmm
ELF     7e589000-7e5a5000       Deferred        imm32<elf>
  \-PE  7e590000-7e5a5000       \               imm32
ELF     7e5a5000-7e5ac000       Deferred        libdrm.so.2
ELF     7e5ac000-7e5b1000       Deferred        libxdmcp.so.6
ELF     7e5b1000-7e5b4000       Deferred        libxau.so.6
ELF     7e5b4000-7e62e000       Deferred        libglu.so.1
ELF     7e62e000-7e69d000       Export          libgl.so.1
ELF     7e69d000-7e766000       Deferred        libx11.so.6
ELF     7e766000-7e773000       Deferred        libxext.so.6
ELF     7e773000-7e778000       Deferred        libxxf86vm.so.1
ELF     7e778000-7e790000       Deferred        libice.so.6
ELF     7e790000-7e809000       Export          opengl32<elf>
  \-PE  7e7b0000-7e809000       \               opengl32
ELF     7e809000-7e835000       Deferred        ws2_32<elf>
  \-PE  7e810000-7e835000       \               ws2_32
ELF     7e835000-7e84f000       Deferred        wsock32<elf>
  \-PE  7e840000-7e84f000       \               wsock32
ELF     7e84f000-7e862000       Deferred        libresolv.so.2
ELF     7e862000-7e880000       Deferred        iphlpapi<elf>
  \-PE  7e870000-7e880000       \               iphlpapi
ELF     7e880000-7e8d4000       Deferred        rpcrt4<elf>
  \-PE  7e890000-7e8d4000       \               rpcrt4
ELF     7e8d4000-7e969000       Deferred        ole32<elf>
  \-PE  7e8e0000-7e969000       \               ole32
ELF     7e969000-7e9c1000       Deferred        shlwapi<elf>
  \-PE  7e980000-7e9c1000       \               shlwapi
ELF     7e9c1000-7eab3000       Deferred        shell32<elf>
  \-PE  7e9d0000-7eab3000       \               shell32
ELF     7eab3000-7eabe000       Deferred        libgcc_s.so.1
ELF     7eabf000-7eac8000       Deferred        libsm.so.6
ELF     7eba7000-7ec5d000       Deferred        gdi32<elf>
  \-PE  7ebc0000-7ec5d000       \               gdi32
ELF     7ec5d000-7ed95000       Deferred        user32<elf>
  \-PE  7ec80000-7ed95000       \               user32
ELF     7ed95000-7ee55000       Deferred        comctl32<elf>
  \-PE  7eda0000-7ee55000       \               comctl32
ELF     7ee55000-7ee9b000       Deferred        advapi32<elf>
  \-PE  7ee60000-7ee9b000       \               advapi32
ELF     7efa5000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efba000       Deferred        libnss_nis.so.2
ELF     7efba000-7efd0000       Deferred        libnsl.so.1
ELF     7efd0000-7eff6000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7cd8000-b7cdc000       Deferred        libdl.so.2
ELF     b7cdc000-b7e10000       Deferred        libc.so.6
ELF     b7e11000-b7e24000       Deferred        libpthread.so.0
ELF     b7e2e000-b7f3f000       Export          libwine.so.1
ELF     b7f41000-b7f5c000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\yange\Programs\World_of_Warcraft\wow.exe
        00000018    0
        00000017    0
        00000016    0
        00000015    0
        00000014    0
        00000013    0
        00000012    2
        00000011   15
        00000010   15
        0000000f    0
        0000000e    0
        0000000d    1
        00000009    0 <==

```

---

### Post by Afoot on 2006-12-25
I get the impression you are running it from your NTFS drive, in which case you must copy the "World of Warcraft" directory to somewhere inside your 'fake c-drive', which resides in your home folder. For instance, you could copy the folder so it would look something like this in your non-windows partition:
```
/home/userName/.wine/drive_c/Program Files/World of Warcraft/
```

Then, it should work fine by just running:
```
wine WoW.exe -opengl
```
...while in your WoW folder.

**yange:** I think you do not have your graphics drivers installed. Run this command to check whether you have them or not:
```
glxinfo | grep direct
```

If you don't have direct rendering, please install the drivers:
**Nvidia:** [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)
**ATI:** [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29)
**Intel:** [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28Intel.29)

Don't expect miracles from the Intel drivers, though.

---

### Post by Sammi on 2006-12-25
Or the ATI ones :-?

If you like gaming in Linux then you should stick to Nvidia, because they have developed the best Linux drivers out of those three.

---

### Post by dyzzy on 2006-12-25
Well I feel like an idiot. I thought I had installed my graphics driver beforehand but after checking, I found out that I forgot to. WoW worked fine after I did that.

---

### Post by Ferrat on 2006-12-26
> **Sammi said:**
> Or the ATI ones :-?

If you like gaming in Linux then you should stick to Nvidia, because they have developed the best Linux drivers out of those three.

Since the new WoW Patch with the ATi fixes I get just the same FPS with my X800 card as my friend gets with his 7800 series, I had about 2/3 of his FPS before that so it's not just the drivers since I havn't changed those..

---

