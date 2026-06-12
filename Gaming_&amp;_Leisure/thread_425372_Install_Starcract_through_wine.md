---
title: "Install Starcract through wine"
date: 2007-04-27
forum: Gaming &amp; Leisure
---

### Post by Bènve on 2007-04-27
I cannot install starcraft cause terminal report an error
```
user@ubuntu:~$ wine '/media/cdrom0/install.exe' 
wine: Unhandled page fault on write access to 0x00000000 at address 0x423a20 (thread 0009), starting debugger...
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
err:virtual:NtMapViewOfSection map_file_into_view 0x680000 23d88000 000000000 failed
couldn't load main module (31)
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
err:virtual:NtMapViewOfSection map_file_into_view 0x8a0000 23d88000 000000000 failed
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x00423a20).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00423a20 ESP:0033ff0c EBP:0033ffe8 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7b8abaa0 ECX:00000000 EDX:00000000
 ESI:00423a20 EDI:7ffdf000
Stack dump:
0x0033ff0c:  7b87036e 7ffdf000 00000000 00000000
0x0033ff1c:  00000000 00000000 00000000 00000000
0x0033ff2c:  ffffffff 7b82bf28 7b840880 7b8abaa0
0x0033ff3c:  7ffdc000 00001000 0033ffe8 ff39ff10
0x0033ff4c:  848d02e0 00000001 10012a03 00000000
0x0033ff5c:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x00423a20 (0x0033ffe8)
  2 0xb7ebc587 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00423a20: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (83 modules)
ELF     7b800000-7b924000       Deferred        kernel32<elf>
  \-PE  7b820000-7b924000       \               kernel32
ELF     7bc00000-7bc96000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc96000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e15b000-7e15f000       Deferred        libgpg-error.so.0
ELF     7e15f000-7e1ad000       Deferred        libgcrypt.so.11
ELF     7e1ad000-7e1c0000       Deferred        libtasn1.so.3
ELF     7e1c0000-7e1ee000       Deferred        libcrypt.so.1
ELF     7e1fc000-7e26b000       Deferred        libgnutls.so.13
ELF     7e26b000-7e29a000       Deferred        libcups.so.2
ELF     7e2c7000-7e2f9000       Deferred        uxtheme<elf>
  \-PE  7e2d0000-7e2f9000       \               uxtheme
ELF     7e2f9000-7e30e000       Deferred        midimap<elf>
  \-PE  7e300000-7e30e000       \               midimap
ELF     7e30e000-7e334000       Deferred        msacm32<elf>
  \-PE  7e320000-7e334000       \               msacm32
ELF     7e334000-7e34c000       Deferred        msacm32<elf>
  \-PE  7e340000-7e34c000       \               msacm32
ELF     7e34c000-7e388000       Deferred        wineoss<elf>
  \-PE  7e350000-7e388000       \               wineoss
ELF     7e38a000-7e38f000       Deferred        libxfixes.so.3
ELF     7e38f000-7e398000       Deferred        libxcursor.so.1
ELF     7e398000-7e3a0000       Deferred        libxrender.so.1
ELF     7e3a0000-7e3bd000       Deferred        imm32<elf>
  \-PE  7e3b0000-7e3bd000       \               imm32
ELF     7e3bd000-7e3db000       Deferred        ximcp.so.2
ELF     7e3db000-7e3dd000       Deferred        xlcutf8load.so.2
ELF     7e3dd000-7e3e4000       Deferred        libdrm.so.2
ELF     7e3e4000-7e453000       Deferred        libgl.so.1
ELF     7e453000-7e458000       Deferred        libxdmcp.so.6
ELF     7e458000-7e521000       Deferred        libx11.so.6
ELF     7e521000-7e52e000       Deferred        libxext.so.6
ELF     7e52e000-7e546000       Deferred        libice.so.6
ELF     7e546000-7e5d3000       Deferred        winex11<elf>
  \-PE  7e560000-7e5d3000       \               winex11
ELF     7e5d3000-7e5f1000       Deferred        libexpat.so.1
ELF     7e5f1000-7e620000       Deferred        libfontconfig.so.1
ELF     7e620000-7e634000       Deferred        libz.so.1
ELF     7e634000-7e6a1000       Deferred        libfreetype.so.6
ELF     7e6a1000-7e6b4000       Deferred        libresolv.so.2
ELF     7e6b4000-7e6d2000       Deferred        iphlpapi<elf>
  \-PE  7e6c0000-7e6d2000       \               iphlpapi
ELF     7e6d2000-7e727000       Deferred        rpcrt4<elf>
  \-PE  7e6e0000-7e727000       \               rpcrt4
ELF     7e727000-7e7c3000       Deferred        ole32<elf>
  \-PE  7e740000-7e7c3000       \               ole32
ELF     7e7c3000-7e7f6000       Deferred        winspool<elf>
  \-PE  7e7d0000-7e7f6000       \               winspool
ELF     7e7f6000-7e8b2000       Deferred        comctl32<elf>
  \-PE  7e800000-7e8b2000       \               comctl32
ELF     7e8b2000-7e90a000       Deferred        shlwapi<elf>
  \-PE  7e8c0000-7e90a000       \               shlwapi
ELF     7e90a000-7ea04000       Deferred        shell32<elf>
  \-PE  7e920000-7ea04000       \               shell32
ELF     7ea04000-7eaa4000       Deferred        comdlg32<elf>
  \-PE  7ea10000-7eaa4000       \               comdlg32
ELF     7eaa4000-7eae9000       Deferred        advapi32<elf>
  \-PE  7eab0000-7eae9000       \               advapi32
ELF     7eae9000-7eaf4000       Deferred        libgcc_s.so.1
ELF     7eaf4000-7eaf9000       Deferred        libxxf86vm.so.1
ELF     7eaf9000-7eb02000       Deferred        libsm.so.6
ELF     7ebe1000-7ec9a000       Deferred        gdi32<elf>
  \-PE  7ec00000-7ec9a000       \               gdi32
ELF     7ec9a000-7edd4000       Deferred        user32<elf>
  \-PE  7ecb0000-7edd4000       \               user32
ELF     7edd4000-7ee62000       Deferred        winmm<elf>
  \-PE  7ede0000-7ee62000       \               winmm
ELF     7ee62000-7ee76000       Deferred        lz32<elf>
  \-PE  7ee70000-7ee76000       \               lz32
ELF     7ee76000-7ee8f000       Deferred        version<elf>
  \-PE  7ee80000-7ee8f000       \               version
ELF     7efab000-7efb6000       Deferred        libnss_files.so.2
ELF     7efb6000-7efcc000       Deferred        libnsl.so.1
ELF     7efcc000-7eff2000       Deferred        libm.so.6
ELF     7eff2000-7eff5000       Deferred        libxau.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d52000-b7d5b000       Deferred        libnss_compat.so.2
ELF     b7d5c000-b7d60000       Deferred        libdl.so.2
ELF     b7d60000-b7e94000       Deferred        libc.so.6
ELF     b7e94000-b7ea7000       Deferred        libpthread.so.0
ELF     b7eb5000-b7fc6000       Export          libwine.so.1
ELF     b7fc8000-b7fe3000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\install.exe
        00000009    0 <==
```

how can I resolve the issue?
thank you

---

### Post by cogadh on 2007-04-27
What is your default OS emulation in Wine? Are you using native or builtin DLLs?

---

### Post by joebanana on 2007-04-27
Try wiping CD. My instalation had error and then I cleaned CD and it worked. I know its a stupid advice but... Sometimes solution is simple and sometimes.... :)

---

### Post by Bènve on 2007-04-27
I try as emulated OS windows 2000 and Xp, but doesn't work in each of them.
thank you for the support
thank you joebanana but the cd is new

---

### Post by cogadh on 2007-04-27
Whenever I am trying to run a game that was made prior to 2000 in Wine, I always start with Windows 98 emulation first, it is somewhat more stable than 2000 or XP.

What about the DLL question?

---

