---
title: "Still Can't get CIV4 to work."
date: 2007-08-22
forum: Gaming &amp; Leisure
---

### Post by phr0ze on 2007-08-22
I have tried with the default Feisty Wine (0.9.3.3 I think) and the newest Wine version 0.9.4.3. I have tried the tips from the AppDB including replacing the two XML DLLs and adding the d3dx9_26.dll into the system32 folder. However I still get these errors. I have warlords version 2.0.8 installed and it gives the same error message.

```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
err:ole:CoCreateInstance apartment not initialised
fixme:shell:DllCanUnloadNow stub
err:ole:CoCreateInstance apartment not initialised
fixme:shell:DllCanUnloadNow stub
err:ole:CoCreateInstance apartment not initialised
fixme:shell:DllCanUnloadNow stub
err:ole:CoCreateInstance apartment not initialised
fixme:shell:DllCanUnloadNow stub
err:ole:CoCreateInstance apartment not initialised
fixme:shell:DllCanUnloadNow stub
err:ole:CoCreateInstance apartment not initialised
fixme:shell:DllCanUnloadNow stub
err:ole:CoCreateInstance apartment not initialised
fixme:shell:DllCanUnloadNow stub
err:ole:CoCreateInstance apartment not initialised
fixme:shell:DllCanUnloadNow stub
err:ole:CoCreateInstance apartment not initialised
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:ole:CoCreateInstance apartment not initialised
fixme:shell:DllCanUnloadNow stub
fixme:msxml:schema_cache_add (0x179190)->(L"x-schema:CIV4GameInfoSchema.xml", var(vt 9)): stub
fixme:msxml:domdoc_putref_schemas (0x1791a8): semi-stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Saves.lnk
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\CivilizationIV.ini.lnk
fixme:msxml:domdoc_putref_schemas (0x1791a8): semi-stub
wine: Unhandled page fault on read access to 0x00000040 at address 0x18e1ea0 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000040 in 32-bit code (0x018e1ea0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:018e1ea0 ESP:0033fa64 EBP:009aa155 EFLAGS:00010216(   - 00      -RIAP1)
 EAX:018e1ea0 EBX:00000000 ECX:00000000 EDX:00000000
 ESI:0118fa58 EDI:00000000
Stack dump:
0x0033fa64:  004bcfc4 0118e514 0118fa58 011852e4
0x0033fa74:  01185258 009b01fb 004bce26 011852e4
0x0033fa84:  0033fa9c 00ae79e3 00000006 004bcf61
0x0033fa94:  0118fa58 0118fa58 0033fbe4 00ad34ab
0x0033faa4:  00000000 00409bf8 01185258 01185360
0x0033fab4:  01185258 011852e4 0118e584 0118e4b4
Backtrace:
=>1 0x018e1ea0 ?getDefault@CvForceControlInfo@@QBE_NXZ() in cvgamecoredll (0x009aa155)
0x018e1ea0 ?getDefault@CvForceControlInfo@@QBE_NXZ in cvgamecoredll: movb       0x40(%ecx),%al
Modules:
Module  Address                 Debug info      Name (103 modules)
PE        340000-  34e000       Deferred        hapdbg
PE        350000-  363000       Deferred        zlib1
PE        400000-  e14000       Deferred        civilization4
PE        e20000- 106a000       Deferred        d3dx9_26
PE       1850000- 1be1000       Export          cvgamecoredll
PE      10000000-1002b000       Deferred        boost_python-vc71-mt-1_32
PE      18000000-18038000       Deferred        binkw32
PE      1e000000-1e1ca000       Deferred        python24
PE      21100000-2118c000       Deferred        mss32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c340000-7c396000       Deferred        msvcr71
PE      7c3a0000-7c41b000       Deferred        msvcp71
ELF     7c98f000-7c9af000       Deferred        mpr<elf>
  \-PE  7c9a0000-7c9af000       \               mpr
ELF     7c9af000-7c9f9000       Deferred        wininet<elf>
  \-PE  7c9c0000-7c9f9000       \               wininet
ELF     7c9f9000-7ca33000       Deferred        urlmon<elf>
  \-PE  7ca00000-7ca33000       \               urlmon
ELF     7ca33000-7ca67000       Deferred        libxslt.so.1
ELF     7ca67000-7cb84000       Deferred        libxml2.so.2
ELF     7cb84000-7cbb1000       Deferred        msxml3<elf>
  \-PE  7cb90000-7cbb1000       \               msxml3
ELF     7cc5f000-7cc91000       Deferred        uxtheme<elf>
  \-PE  7cc70000-7cc91000       \               uxtheme
ELF     7cc91000-7cca6000       Deferred        midimap<elf>
  \-PE  7cca0000-7cca6000       \               midimap
ELF     7cca6000-7cccc000       Deferred        msacm32<elf>
  \-PE  7ccb0000-7cccc000       \               msacm32
ELF     7cccc000-7cce4000       Deferred        msacm32<elf>
  \-PE  7ccd0000-7cce4000       \               msacm32
ELF     7cce4000-7cda9000       Deferred        libasound.so.2
ELF     7cda9000-7cddb000       Deferred        winealsa<elf>
  \-PE  7cdb0000-7cddb000       \               winealsa
ELF     7d073000-7d078000       Deferred        libxfixes.so.3
ELF     7d078000-7d081000       Deferred        libxcursor.so.1
ELF     7d081000-7d09e000       Deferred        imm32<elf>
  \-PE  7d090000-7d09e000       \               imm32
ELF     7d09e000-7d0a4000       Deferred        libxrandr.so.2
ELF     7d0a4000-7d0ac000       Deferred        libxrender.so.1
ELF     7d876000-7d878000       Deferred        libnvidia-tls.so.1
ELF     7d878000-7e210000       Deferred        libglcore.so.1
ELF     7e210000-7e2a6000       Deferred        libgl.so.1
ELF     7e2a6000-7e2ab000       Deferred        libxdmcp.so.6
ELF     7e2ab000-7e2ae000       Deferred        libxau.so.6
ELF     7e2ae000-7e39f000       Deferred        libx11.so.6
ELF     7e39f000-7e3ad000       Deferred        libxext.so.6
ELF     7e3ad000-7e3c5000       Deferred        libice.so.6
ELF     7e3c5000-7e3ce000       Deferred        libsm.so.6
ELF     7e3dc000-7e466000       Deferred        winex11<elf>
  \-PE  7e3f0000-7e466000       \               winex11
ELF     7e500000-7e520000       Deferred        libexpat.so.1
ELF     7e520000-7e54b000       Deferred        libfontconfig.so.1
ELF     7e54b000-7e55f000       Deferred        libz.so.1
ELF     7e55f000-7e5ca000       Deferred        libfreetype.so.6
ELF     7e5ca000-7e631000       Deferred        msvcrt<elf>
  \-PE  7e5e0000-7e631000       \               msvcrt
ELF     7e631000-7e65e000       Deferred        ws2_32<elf>
  \-PE  7e640000-7e65e000       \               ws2_32
ELF     7e65e000-7e672000       Deferred        lz32<elf>
  \-PE  7e660000-7e672000       \               lz32
ELF     7e672000-7e68c000       Deferred        version<elf>
  \-PE  7e680000-7e68c000       \               version
ELF     7e68c000-7e749000       Deferred        comctl32<elf>
  \-PE  7e6a0000-7e749000       \               comctl32
ELF     7e749000-7e7a2000       Deferred        shlwapi<elf>
  \-PE  7e760000-7e7a2000       \               shlwapi
ELF     7e7a2000-7e8a5000       Deferred        shell32<elf>
  \-PE  7e7b0000-7e8a5000       \               shell32
ELF     7e8a5000-7e943000       Deferred        oleaut32<elf>
  \-PE  7e8c0000-7e943000       \               oleaut32
ELF     7e943000-7e956000       Deferred        libresolv.so.2
ELF     7e956000-7e974000       Deferred        iphlpapi<elf>
  \-PE  7e960000-7e974000       \               iphlpapi
ELF     7e974000-7e9cd000       Deferred        rpcrt4<elf>
  \-PE  7e980000-7e9cd000       \               rpcrt4
ELF     7e9cd000-7ea6c000       Deferred        ole32<elf>
  \-PE  7e9e0000-7ea6c000       \               ole32
ELF     7ea6c000-7ea78000       Deferred        libgcc_s.so.1
ELF     7eb63000-7eb68000       Deferred        libxxf86vm.so.1
ELF     7eb70000-7ec30000       Deferred        gdi32<elf>
  \-PE  7eb90000-7ec30000       \               gdi32
ELF     7ec30000-7ed6e000       Deferred        user32<elf>
  \-PE  7ec50000-7ed6e000       \               user32
ELF     7ed6e000-7edfc000       Deferred        winmm<elf>
  \-PE  7ed80000-7edfc000       \               winmm
ELF     7edfc000-7ee45000       Deferred        dsound<elf>
  \-PE  7ee00000-7ee45000       \               dsound
ELF     7ee45000-7ee8d000       Deferred        advapi32<elf>
  \-PE  7ee50000-7ee8d000       \               advapi32
ELF     7ef9f000-7efaa000       Deferred        libnss_files.so.2
ELF     7efaa000-7efb4000       Deferred        libnss_nis.so.2
ELF     7efb4000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff2000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d56000-b7d5a000       Deferred        libdl.so.2
ELF     b7d5a000-b7e9b000       Deferred        libc.so.6
ELF     b7e9c000-b7eb3000       Deferred        libpthread.so.0
ELF     b7ec1000-b7fd5000       Deferred        libwine.so.1
ELF     b7fd7000-b7ff2000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\civilization4.exe
        00000009    0 <==

```

I am really itching to play this game again. Thanx

---

### Post by splintercellguy on 2007-08-22
From the AppDb, it mentions a list of native DLLs that you need: [http://appdb.winehq.org/appview.php?iVersionId=8699](http://appdb.winehq.org/appview.php?iVersionId=8699)

---

### Post by billT on 2007-08-22
The only dll override I've had to use was msxml3.dll.

Are you getting any popups giving more information on the problem?

---

### Post by phr0ze on 2007-08-23
Seems like a complete reinstall of wine and civ4 and 1.61 patch did the trick. How do I put the override in for Civ 4 permanently (or in a link)?

Thanks.

BTW: I got the game working at about 10PM and I didn't get to bed until 2AM. Now I remember why I stopped playing. :)

---

