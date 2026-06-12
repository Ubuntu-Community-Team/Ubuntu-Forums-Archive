---
title: "Starcraft"
date: 2006-06-10
forum: Gaming &amp; Leisure
---

### Post by Harold P on 2006-06-10
Okay, I'm trying to get Starcraft installed. (just the first one). But, when I run the install I get this (see attachment)

If I press OK, it just terminates; no output. If I press Cancel, I get this output:

```
harold@ubuntu:~$ wine /media/cdrom/install.exe
wine: Unhandled exception 0x80000003 at address 0x4166fb (thread 0009), starting debugger...
WineDbg starting on pid 0x8
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
err:virtual:NtMapViewOfSection map_file_into_view 0x58170000 23d88000 000000000 failed
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image Z:\media\cdrom\install.exe
0x004166fc: pushl       $0x1
Modules:
Module  Address                 Debug info      Name (84 modules)
PE      0x00400000-0044c000     --none--        install
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7d331000-7d37d000     Deferred        libgcrypt.so.11
ELF     0x7d37d000-7d38d000     Deferred        libtasn1.so.2
ELF     0x7d38d000-7d3ba000     Deferred        libcrypt.so.1
ELF     0x7d3ba000-7d423000     Deferred        libgnutls.so.12
ELF     0x7d423000-7d450000     Deferred        libcups.so.2
ELF     0x7d4ea000-7d51b000     Deferred        uxtheme<elf>
  \-PE  0x7d4f0000-7d51b000     \               uxtheme
ELF     0x7d51b000-7d530000     Deferred        midimap<elf>
  \-PE  0x7d520000-7d530000     \               midimap
ELF     0x7d642000-7d646000     Deferred        libgpg-error.so.0
ELF     0x7d64e000-7d674000     Deferred        msacm32<elf>
  \-PE  0x7d660000-7d674000     \               msacm32
ELF     0x7d674000-7d68c000     Deferred        msacm<elf>
  \-PE  0x7d680000-7d68c000     \               msacm
ELF     0x7d68c000-7d741000     Deferred        libasound.so.2
ELF     0x7d741000-7d76a000     Deferred        winealsa<elf>
  \-PE  0x7d750000-7d76a000     \               winealsa
ELF     0x7d788000-7d78c000     Deferred        libxfixes.so.3
ELF     0x7d78c000-7d794000     Deferred        libxrender.so.1
ELF     0x7d794000-7d79d000     Deferred        libxcursor.so.1
ELF     0x7d79d000-7d7b9000     Deferred        imm32<elf>
  \-PE  0x7d7a0000-7d7b9000     \               imm32
ELF     0x7ee9d000-7f088000     Deferred        r128_dri.so
ELF     0x7f088000-7f08f000     Deferred        libdrm.so.2
ELF     0x7f08f000-7f0f5000     Deferred        libgl.so.1
ELF     0x7f0f5000-7f1db000     Deferred        libx11.so.6
ELF     0x7f1db000-7f1f3000     Deferred        libice.so.6
ELF     0x7f1f3000-7f276000     Deferred        winex11<elf>
  \-PE  0x7f200000-7f276000     \               winex11
ELF     0x7f276000-7f295000     Deferred        libexpat.so.1
ELF     0x7f295000-7f2c3000     Deferred        libfontconfig.so.1
ELF     0x7f2c3000-7f2d7000     Deferred        libz.so.1
ELF     0x7f2d7000-7f340000     Deferred        libfreetype.so.6
ELF     0x7f340000-7f36c000     Deferred        winspool<elf>
  \-PE  0x7f350000-7f36c000     \               winspool
ELF     0x7f36c000-7f42c000     Deferred        comctl32<elf>
  \-PE  0x7f380000-7f42c000     \               comctl32
ELF     0x7f42c000-7f44b000     Deferred        iphlpapi<elf>
  \-PE  0x7f430000-7f44b000     \               iphlpapi
ELF     0x7f44b000-7f494000     Deferred        rpcrt4<elf>
  \-PE  0x7f460000-7f494000     \               rpcrt4
ELF     0x7f494000-7f525000     Deferred        ole32<elf>
  \-PE  0x7f4b0000-7f525000     \               ole32
ELF     0x7f525000-7f580000     Deferred        shlwapi<elf>
  \-PE  0x7f540000-7f580000     \               shlwapi
ELF     0x7f580000-7f64c000     Deferred        shell32<elf>
  \-PE  0x7f5a0000-7f64c000     \               shell32
ELF     0x7f64c000-7f6e9000     Deferred        comdlg32<elf>
  \-PE  0x7f660000-7f6e9000     \               comdlg32
ELF     0x7f6e9000-7f729000     Deferred        advapi32<elf>
  \-PE  0x7f6f0000-7f729000     \               advapi32
ELF     0x7f7fe000-7f8af000     Deferred        gdi32<elf>
  \-PE  0x7f810000-7f8af000     \               gdi32
ELF     0x7f8af000-7f9db000     Deferred        user32<elf>
  \-PE  0x7f8d0000-7f9db000     \               user32
ELF     0x7f9db000-7fa63000     Deferred        winmm<elf>
  \-PE  0x7f9f0000-7fa63000     \               winmm
ELF     0x7fa63000-7fa77000     Deferred        lz32<elf>
  \-PE  0x7fa70000-7fa77000     \               lz32
ELF     0x7fa77000-7fa90000     Deferred        version<elf>
  \-PE  0x7fa80000-7fa90000     \               version
ELF     0x7fba3000-7fbb0000     Deferred        libxext.so.6
ELF     0x7fbb3000-7fbb6000     Deferred        libxau.so.6
ELF     0x7fbb6000-7fbbb000     Deferred        libxxf86vm.so.1
ELF     0x7fbee000-7fcf0000     Deferred        kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe01000-7fe0b000     Deferred        libgcc_s.so.1
ELF     0x7fe0b000-7fe15000     Deferred        libnss_files.so.2
ELF     0x7fe15000-7fe1e000     Deferred        libnss_nis.so.2
ELF     0x7fe1e000-7fe33000     Deferred        libnsl.so.1
ELF     0x7fe33000-7fe3c000     Deferred        libnss_compat.so.2
ELF     0x7fe3d000-7fe42000     Deferred        libxxf86dga.so.1
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e53000-b7e56000     Deferred        libdl.so.2
ELF     0xb7e56000-b7f85000     Deferred        libc.so.6
ELF     0xb7f85000-b7f97000     Deferred        libpthread.so.0
ELF     0xb7fa5000-b7fbf000     Deferred        libwine.so.1
ELF     0xb7fc2000-b7fd8000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\media\cdrom\install.exe
        0000000a    0
        00000009    0 <==
harold@ubuntu:~$


``` 
What's wrong? :(

---

### Post by Sukarn on 2006-06-10
I get a similar thing in another game. Are you running prelink as well? Just checking to see whether that is causing the problem.

---

### Post by r3st on 2006-06-10
nvm

---

### Post by r3st on 2006-06-10
type wine Wincfg go to drivers tab and click auto detect.

worked for me

---

### Post by Sukarn on 2006-06-10
You mean the drives tab or the Libraries tab? There is no autodetect in the libraries tab.

I was talking about **winecfg**. Running **wine Wincfg** just gives a not found error

---

### Post by Harold P on 2006-06-10
[quote=Sukarn]I get a similar thing in another game. Are you running prelink as well? Just checking to see whether that is causing the problem.[/quote]
I am running prelink.

---

### Post by patrick295767 on 2006-06-10
that's strange

I can run starcraft with Wine without any problem.
You should put the original cd in the pc, then, chekc that it can read the cdrom

> winecfg 
can be useful to configure wine

---

