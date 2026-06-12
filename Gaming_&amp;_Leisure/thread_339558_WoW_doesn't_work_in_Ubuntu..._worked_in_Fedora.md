---
title: "WoW doesn't work in Ubuntu... worked in Fedora"
date: 2007-01-15
forum: Gaming &amp; Leisure
---

### Post by tnunamak on 2007-01-15
I decided to try Ubuntu, so I installed it and have gotten it set up pretty well. I kept my /.wine folder which has my installation of WoW. I reinstalled all of the graphics drivers and configured my xorg.conf as well as I could. Now when I try running WoW, I get this:

 ```
tnunamak@tnunamak:~$ wine '/home/tnunamak/.wine/drive_c/Program Files/World of Warcraft/WoW.exe' -opengl
fixme:advapi:SetSecurityInfo stub
wine: Unhandled page fault on write access to 0x00000000 at address 0x7c77fe28 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x7c77fe28).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7c77fe28 ESP:0032dcd4 EBP:0032dcfc EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000000 EBX:7c78ee60 ECX:0032dcf4 EDX:00000004
 ESI:0032de94 EDI:7c76fe90
Stack dump:
0x0032dcd4:  ffffffff 7ffdc0c0 0033e34c 00000004
0x0032dce4:  0032dcf4 00170d10 00170d20 7c78ee60
0x0032dcf4:  00000004 7c78ee60 0032de4c 7c78028b
0x0032dd04:  ffffffff 7ffdc0c0 0033e34c 00000004
0x0032dd14:  00000000 7c78ee60 00170d68 00170d68
0x0032dd24:  0032dd44 7bc3569e 00000002 7c74e5a0
Backtrace:
=>1 0x7c77fe28 in dbghelp (+0x1fe28) (0x0032dcfc)
  2 0x7c78028b in dbghelp (+0x2028b) (0x0032de4c)
  3 0x7c781b28 StackWalk+0x108() in dbghelp (0x0032debc)
  4 0x006b09bf in wow (+0x2b09bf) (0x0033e3a4)
  5 0x006b04fd in wow (+0x2b04fd) (0x0033e3d8)
  6 0x00691ef8 in wow (+0x291ef8) (0x0033e3ec)
  7 0x00691782 in wow (+0x291782) (0x0033f168)
  8 0x00691309 in wow (+0x291309) (0x0033f990)
  9 0x00691243 in wow (+0x291243) (0x0033f9bc)
  10 0x00691334 in wow (+0x291334) (0x0033f9c8)
  11 0x00403bea in wow (+0x3bea) (0x0033fc10)
  12 0x0040260b in wow (+0x260b) (0x0033fe68)
  13 0x00402477 in wow (+0x2477) (0x0033fe78)
  14 0x0040448e in wow (+0x448e) (0x0033ff08)
  15 0x7b8702ce in kernel32 (+0x502ce) (0x0033ffe8)
  16 0xb7e8a587 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7c77fe28: movl        %edx,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (94 modules)
PE      340000-3d0000   Deferred        fmod
PE      400000-d8d000   Export          wow
PE      10000000-10069000       Deferred        divxdecoder
ELF     7b800000-7b91b000       Export          kernel32<elf>
  \-PE  7b820000-7b91b000       \               kernel32
ELF     7bc00000-7bc83000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c73b000-7c750000       Deferred        psapi<elf>
  \-PE  7c740000-7c750000       \               psapi
ELF     7c750000-7c797000       Export          dbghelp<elf>
  \-PE  7c760000-7c797000       \               dbghelp
ELF     7caca000-7cadf000       Deferred        midimap<elf>
  \-PE  7cad0000-7cadf000       \               midimap
ELF     7cadf000-7cb1b000       Deferred        wineoss<elf>
  \-PE  7caf0000-7cb1b000       \               wineoss
ELF     7cb3b000-7cb6d000       Deferred        uxtheme<elf>
  \-PE  7cb40000-7cb6d000       \               uxtheme
PE      7ce00000-7ce16000       --none--        msacm32
ELF     7ce25000-7ce2a000       Deferred        libxfixes.so.3
ELF     7ce2a000-7ce33000       Deferred        libxcursor.so.1
ELF     7ce33000-7ce51000       Deferred        ximcp.so.2
ELF     7ce51000-7ce53000       Deferred        xlcutf8load.so.2
ELF     7ce53000-7ce56000       Deferred        libxrandr.so.2
ELF     7ce56000-7ce5e000       Deferred        libxrender.so.1
ELF     7ce5e000-7ce61000       Deferred        libxinerama.so.1
ELF     7d88b000-7d918000       Deferred        winex11<elf>
  \-PE  7d8a0000-7d918000       \               winex11
ELF     7d918000-7d936000       Deferred        libexpat.so.1
ELF     7d936000-7d965000       Deferred        libfontconfig.so.1
ELF     7d965000-7d979000       Deferred        libz.so.1
ELF     7d979000-7d9e3000       Deferred        libfreetype.so.6
ELF     7d9e3000-7da02000       Deferred        mpr<elf>
  \-PE  7d9f0000-7da02000       \               mpr
ELF     7da02000-7da49000       Deferred        wininet<elf>
  \-PE  7da10000-7da49000       \               wininet
ELF     7da49000-7daad000       Deferred        msvcrt<elf>
  \-PE  7da60000-7daad000       \               msvcrt
ELF     7daad000-7dad3000       Deferred        msacm32<elf>
ELF     7dad3000-7dae7000       Deferred        lz32<elf>
  \-PE  7dae0000-7dae7000       \               lz32
ELF     7dae7000-7db00000       Deferred        version<elf>
  \-PE  7daf0000-7db00000       \               version
ELF     7db00000-7db8e000       Deferred        winmm<elf>
  \-PE  7db10000-7db8e000       \               winmm
ELF     7db8e000-7dbaa000       Deferred        imm32<elf>
  \-PE  7dba0000-7dbaa000       \               imm32
ELF     7dc12000-7e583000       Deferred        libglcore.so.1
ELF     7e583000-7e5fd000       Deferred        libglu.so.1
ELF     7e5fd000-7e691000       Deferred        libgl.so.1
ELF     7e691000-7e75a000       Deferred        libx11.so.6
ELF     7e75a000-7e767000       Deferred        libxext.so.6
ELF     7e767000-7e77f000       Deferred        libice.so.6
ELF     7e77f000-7e7f8000       Deferred        opengl32<elf>
  \-PE  7e7a0000-7e7f8000       \               opengl32
ELF     7e7f8000-7e824000       Deferred        ws2_32<elf>
  \-PE  7e800000-7e824000       \               ws2_32
ELF     7e824000-7e83e000       Deferred        wsock32<elf>
  \-PE  7e830000-7e83e000       \               wsock32
ELF     7e83e000-7e851000       Deferred        libresolv.so.2
ELF     7e851000-7e86f000       Deferred        iphlpapi<elf>
  \-PE  7e860000-7e86f000       \               iphlpapi
ELF     7e86f000-7e8c3000       Deferred        rpcrt4<elf>
  \-PE  7e880000-7e8c3000       \               rpcrt4
ELF     7e8c3000-7e95b000       Deferred        ole32<elf>
  \-PE  7e8d0000-7e95b000       \               ole32
ELF     7e95b000-7e9b3000       Deferred        shlwapi<elf>
  \-PE  7e970000-7e9b3000       \               shlwapi
ELF     7e9b3000-7eaa5000       Deferred        shell32<elf>
  \-PE  7e9c0000-7eaa5000       \               shell32
ELF     7eaa5000-7eab0000       Deferred        libgcc_s.so.1
ELF     7eab6000-7eab8000       Deferred        libnvidia-tls.so.1
ELF     7eab8000-7eac1000       Deferred        libsm.so.6
ELF     7eba0000-7ec56000       Deferred        gdi32<elf>
  \-PE  7ebc0000-7ec56000       \               gdi32
ELF     7ec56000-7ed8e000       Deferred        user32<elf>
  \-PE  7ec70000-7ed8e000       \               user32
ELF     7ed8e000-7ee4e000       Deferred        comctl32<elf>
  \-PE  7eda0000-7ee4e000       \               comctl32
ELF     7ee4e000-7ee94000       Deferred        advapi32<elf>
  \-PE  7ee60000-7ee94000       \               advapi32
ELF     7ef9e000-7efa9000       Deferred        libnss_files.so.2
ELF     7efa9000-7efb3000       Deferred        libnss_nis.so.2
ELF     7efb3000-7efc9000       Deferred        libnsl.so.1
ELF     7efc9000-7efef000       Deferred        libm.so.6
ELF     7efef000-7eff4000       Deferred        libxdmcp.so.6
ELF     7eff4000-7eff7000       Deferred        libxau.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d20000-b7d25000       Deferred        libxxf86vm.so.1
ELF     b7d26000-b7d2a000       Deferred        libdl.so.2
ELF     b7d2a000-b7e5e000       Deferred        libc.so.6
ELF     b7e5f000-b7e72000       Deferred        libpthread.so.0
ELF     b7e83000-b7f94000       Export          libwine.so.1
ELF     b7f96000-b7fb1000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\World of Warcraft\WoW.exe
        00000010    0
        0000000d    1
        00000009    0 <==

```


Any ideas?

---

### Post by Ferrat on 2007-01-16
> 
Unhandled page fault on write access to 0x00000000 at address 0x7c77fe28 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x7c77fe28).

This is a know bug in wine I belive, check out 
[http://appdb.winehq.org/appview.php?iAppId=1922](http://appdb.winehq.org/appview.php?iAppId=1922)

---

### Post by tnunamak on 2007-01-16
Hmm... The only bug I could find was specific to slackware. Maybe I should just reinstall WoW :(

---

### Post by Z3n0s on 2007-01-17
I know it is Lame but I think reinstalling is the way to go..:mrgreen:

---

