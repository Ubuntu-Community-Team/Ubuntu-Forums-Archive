---
title: "WarCraft Problems"
date: 2006-12-13
forum: Gaming &amp; Leisure
---

### Post by parradux on 2006-12-13
I'am having trouble running warcraft 3. I've installed it using wine, and whenever i try to run it I get this message. I try to run it by: wine war3.exe -opengl 

```
 
err:ole:CoCreateInstance apartment not initialised
wine: Call from 0x4117fb to unimplemented function Storm.dll.570, aborting
wine: Unimplemented function Storm.dll.570 called at address 0x4117fb (thread 0009), starting debugger...
Unhandled exception: unimplemented function Storm.dll.570 called in 32-bit code (0x7bc37b17).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc37b17 ESP:0033fc3c EBP:0033fca0 EFLAGS:00000216(   - 00      - IAP1)
 EAX:0000023a EBX:7bc76284 ECX:0033fcbc EDX:0011005c
 ESI:0033fc48 EDI:00398618
Stack dump:
0x0033fc3c:  00000002 7b8a6900 0017ae30 80000100
0x0033fc4c:  00000001 00000000 004117fb 00000002
0x0033fc5c:  0044de56 0000023a 7b8a6900 7b8a6900
0x0033fc6c:  0033fc9c 7b85f6c2 00110000 00000000
0x0033fc7c:  0017ae30 00000104 00000000 b7efb3fc
0x0033fc8c:  00000000 7b85ea70 0033fcbc 7b85ea70
Backtrace:
=>1 0x7bc37b17 call_dll_entry_point+0x67() in ntdll (0x0033fca0)
  2 0x004117fb in war3 (+0x117fb) (0x0033fdc0)
  3 0x00401219 in war3 (+0x1219) (0x0033fe6c)
  4 0x00401d68 in war3 (+0x1d68) (0x0033ff08)
  5 0x7b86d51f in kernel32 (+0x4d51f) (0x0033ffe8)
  6 0xb7e053b7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc37b17 call_dll_entry_point+0x67 in ntdll: subl     $4,%esp
Modules:
Module  Address                 Debug info      Name (109 modules)
PE      390000-3a2000   Deferred        blizzard
PE      400000-46f000   Export          war3
PE      15000000-15050000       Deferred        storm
PE      21100000-2115f000       Deferred        mss32
PE      60000000-6005d000       Deferred        ijl15
PE      6f000000-6f78f000       Deferred        game
ELF     7b800000-7b918000       Export          kernel32<elf>
  \-PE  7b820000-7b918000       \               kernel32
ELF     7bc00000-7bc81000       Export          ntdll<elf>
  \-PE  7bc10000-7bc81000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf86000-7c000000       Deferred        libglu.so.1
ELF     7c38c000-7c3a0000       Deferred        avicap32<elf>
  \-PE  7c390000-7c3a0000       \               avicap32
ELF     7c3a0000-7c3be000       Deferred        devenum<elf>
  \-PE  7c3b0000-7c3be000       \               devenum
ELF     7c40f000-7c483000       Deferred        opengl32<elf>
  \-PE  7c430000-7c483000       \               opengl32
ELF     7c483000-7c518000       Deferred        oleaut32<elf>
  \-PE  7c490000-7c518000       \               oleaut32
ELF     7c518000-7c52d000       Deferred        midimap<elf>
  \-PE  7c520000-7c52d000       \               midimap
ELF     7c553000-7c56b000       Deferred        msacm32<elf>
  \-PE  7c560000-7c56b000       \               msacm32
ELF     7c56b000-7c5a7000       Deferred        wineoss<elf>
  \-PE  7c570000-7c5a7000       \               wineoss
ELF     7c5a7000-7c5ab000       Deferred        libgpg-error.so.0
ELF     7c5ab000-7c5f9000       Deferred        libgcrypt.so.11
ELF     7c5f9000-7c60c000       Deferred        libtasn1.so.3
ELF     7c60c000-7c63a000       Deferred        libcrypt.so.1
ELF     7c647000-7c6b6000       Deferred        libgnutls.so.13
ELF     7c6b6000-7c6e5000       Deferred        libcups.so.2
ELF     7c712000-7c744000       Deferred        uxtheme<elf>
  \-PE  7c720000-7c744000       \               uxtheme
ELF     7c744000-7c74d000       Deferred        libxcursor.so.1
ELF     7c74d000-7c76b000       Deferred        ximcp.so.2
ELF     7cf65000-7cf6d000       Deferred        libxrender.so.1
ELF     7d06b000-7d070000       Deferred        libxfixes.so.3
ELF     7d902000-7d90b000       Deferred        librt.so.1
ELF     7d90b000-7d90e000       Deferred        libxrandr.so.2
ELF     7d90e000-7d911000       Deferred        libxinerama.so.1
ELF     7d9d2000-7e2b5000       Deferred        fglrx_dri.so
ELF     7e2b5000-7e355000       Deferred        libgl.so.1
ELF     7e355000-7e35a000       Deferred        libxdmcp.so.6
ELF     7e35a000-7e423000       Deferred        libx11.so.6
ELF     7e423000-7e430000       Deferred        libxext.so.6
ELF     7e430000-7e435000       Deferred        libxxf86vm.so.1
ELF     7e435000-7e44d000       Deferred        libice.so.6
ELF     7e44d000-7e4d9000       Deferred        winex11<elf>
  \-PE  7e460000-7e4d9000       \               winex11
ELF     7e4d9000-7e4f7000       Deferred        libexpat.so.1
ELF     7e4f7000-7e526000       Deferred        libfontconfig.so.1
ELF     7e526000-7e53a000       Deferred        libz.so.1
ELF     7e53a000-7e5a4000       Deferred        libfreetype.so.6
ELF     7e5a4000-7e5c3000       Deferred        mpr<elf>
  \-PE  7e5b0000-7e5c3000       \               mpr
ELF     7e5c3000-7e60a000       Deferred        wininet<elf>
  \-PE  7e5d0000-7e60a000       \               wininet
ELF     7e60a000-7e626000       Deferred        imm32<elf>
  \-PE  7e610000-7e626000       \               imm32
ELF     7e626000-7e651000       Deferred        ws2_32<elf>
  \-PE  7e630000-7e651000       \               ws2_32
ELF     7e651000-7e66b000       Deferred        wsock32<elf>
  \-PE  7e660000-7e66b000       \               wsock32
ELF     7e66b000-7e67f000       Deferred        lz32<elf>
  \-PE  7e670000-7e67f000       \               lz32
ELF     7e67f000-7e698000       Deferred        version<elf>
  \-PE  7e690000-7e698000       \               version
ELF     7e698000-7e6fa000       Deferred        msvcrt<elf>
  \-PE  7e6b0000-7e6fa000       \               msvcrt
ELF     7e6fa000-7e787000       Deferred        winmm<elf>
  \-PE  7e710000-7e787000       \               winmm
ELF     7e787000-7e7b8000       Deferred        winspool<elf>
  \-PE  7e790000-7e7b8000       \               winspool
ELF     7e7b8000-7e87a000       Deferred        comctl32<elf>
  \-PE  7e7c0000-7e87a000       \               comctl32
ELF     7e87a000-7e88d000       Deferred        libresolv.so.2
ELF     7e88d000-7e8ac000       Deferred        iphlpapi<elf>
  \-PE  7e890000-7e8ac000       \               iphlpapi
ELF     7e8ac000-7e8ff000       Deferred        rpcrt4<elf>
  \-PE  7e8c0000-7e8ff000       \               rpcrt4
ELF     7e8ff000-7e991000       Deferred        ole32<elf>
  \-PE  7e910000-7e991000       \               ole32
ELF     7e991000-7e9e8000       Deferred        shlwapi<elf>
  \-PE  7e9a0000-7e9e8000       \               shlwapi
ELF     7e9e8000-7ead6000       Deferred        shell32<elf>
  \-PE  7ea00000-7ead6000       \               shell32
ELF     7ead6000-7eb75000       Deferred        comdlg32<elf>
  \-PE  7eae0000-7eb75000       \               comdlg32
ELF     7eb75000-7ebb9000       Deferred        advapi32<elf>
  \-PE  7eb80000-7ebb9000       \               advapi32
ELF     7ebb9000-7ebc4000       Deferred        libgcc_s.so.1
ELF     7ebc4000-7ebc6000       Deferred        xlcutf8load.so.2
ELF     7ebc8000-7ebd1000       Deferred        libsm.so.6
ELF     7ecb0000-7ed64000       Deferred        gdi32<elf>
  \-PE  7ecd0000-7ed64000       \               gdi32
ELF     7ed64000-7ee98000       Deferred        user32<elf>
  \-PE  7ed80000-7ee98000       \               user32
ELF     7efa2000-7efad000       Deferred        libnss_files.so.2
ELF     7efad000-7efb7000       Deferred        libnss_nis.so.2
ELF     7efb7000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff3000       Deferred        libm.so.6
ELF     7eff4000-7eff7000       Deferred        libxau.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ca5000-b7ca9000       Deferred        libdl.so.2
ELF     b7ca9000-b7ddd000       Deferred        libc.so.6
ELF     b7dde000-b7df1000       Deferred        libpthread.so.0
ELF     b7dfe000-b7f0f000       Export          libwine.so.1
ELF     b7f11000-b7f2c000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Warcraft III\war3.exe
        00000009    0 <==

```

---

### Post by catlett on 2006-12-13
Try checking out this post [http://www.ubuntuforums.org/showthread.php?t=300253](http://www.ubuntuforums.org/showthread.php?t=300253)

---

### Post by parradux on 2006-12-13
Ok. I've removed wine, and re-installed it from the source. I try doing the same thing that this guide says, and yet I still get the same error. 

Btw, i've heard that you have the crack the .exe file, so I do that. I'am also wondering how I would go about updating this guy to the latest versions.

---

