---
title: "problem with wine"
date: 2006-09-21
forum: Desktop Environments
---

### Post by nephish on 2006-09-21
lo there
i followed this tutorial here
[http://ubuntuforums.org/showthread.php?t=149585&highlight=wine](http://ubuntuforums.org/showthread.php?t=149585&highlight=wine)
and got wine up and running microsoft IE ( not what i needed, but wine works ) 

then i ran an installer for a windows app that has been tested with wine and the installer went ok. but then nothing happened when i tried to run the exe after installing.

i tried to run the installer again, and got this.
```
ruwach@razmataz:~$ wine /media/cdrom0/autorun.exe 
fixme:font:WineEngRemoveFontResourceEx :stub

```

running the app gives me this ?
```

ruwach@razmataz:~$ wine .wine/drive_c/Programme/Robinson/robinson.exe 
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7fc33ed0 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: 0x0eedfade in 32-bit code (0x00000000).
In 32 bit mode.
Register dump:
 CS:0000 SS:2600 DS:0000 ES:0000 FS:0000 GS:0000
 EIP:00000000 ESP:00000000 EBP:00000000 EFLAGS:00000000(   - 00      - - - )
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:00000000
 ESI:00000000 EDI:00000000
Stack dump:
0x00000000:  00000000 00000000 00000000 00000000
0x00000010:  00000000 00000000 00000000 00000000
0x00000020:  00000000 00000000 00000000 00000000
0x00000030:  00000000 00000000 00000000 00000000
0x00000040:  00000000 00000000 00000000 00000000
0x00000050:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x00000000 (0x00000000)
0x00000000: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (88 modules)
PE      0x00400000-00681000     Deferred        robinson
PE      0x5f300000-5f329000     Deferred        olepro32
PE      0x65340000-653d2000     Deferred        oleaut32
PE      0x65f00000-65fc2000     Deferred        ole32
PE      0x70bd0000-70c35000     Deferred        shlwapi
PE      0x78000000-78040000     Deferred        msvcrt
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7dba2000-7dbb7000     Deferred        midimap<elf>
  \-PE  0x7dbb0000-7dbb7000     \               midimap
ELF     0x7dbb7000-7dbce000     Deferred        msacm<elf>
  \-PE  0x7dbc0000-7dbce000     \               msacm
ELF     0x7dbce000-7dc10000     Deferred        wineoss<elf>
  \-PE  0x7dbe0000-7dc10000     \               wineoss
ELF     0x7e223000-7e271000     Deferred        libgcrypt.so.11
ELF     0x7e271000-7e284000     Deferred        libtasn1.so.3
ELF     0x7e284000-7e2b2000     Deferred        libcrypt.so.1
ELF     0x7e2b2000-7e321000     Deferred        libgnutls.so.13
ELF     0x7e321000-7e350000     Deferred        libcups.so.2
ELF     0x7e350000-7e380000     Deferred        uxtheme<elf>
  \-PE  0x7e360000-7e380000     \               uxtheme
ELF     0x7e78c000-7e790000     Deferred        libgpg-error.so.0
ELF     0x7e8e7000-7e8f0000     Deferred        libxcursor.so.1
ELF     0x7e8f0000-7e8f8000     Deferred        libxrender.so.1
ELF     0x7e900000-7e91b000     Deferred        imm32<elf>
  \-PE  0x7e910000-7e91b000     \               imm32
ELF     0x7e91b000-7e939000     Deferred        ximcp.so.2
ELF     0x7e939000-7e940000     Deferred        libdrm.so.2
ELF     0x7e940000-7e9af000     Deferred        libgl.so.1
ELF     0x7e9af000-7ea78000     Deferred        libx11.so.6
ELF     0x7ea78000-7ea85000     Deferred        libxext.so.6
ELF     0x7ea85000-7ea9d000     Deferred        libice.so.6
ELF     0x7ea9d000-7eb1a000     Deferred        winex11<elf>
  \-PE  0x7eab0000-7eb1a000     \               winex11
ELF     0x7eb1a000-7eb38000     Deferred        libexpat.so.1
ELF     0x7eb38000-7eb67000     Deferred        libfontconfig.so.1
ELF     0x7eb67000-7eb7b000     Deferred        libz.so.1
ELF     0x7eb7b000-7ebe5000     Deferred        libfreetype.so.6
ELF     0x7ebe5000-7ec09000     Deferred        msvfw32<elf>
  \-PE  0x7ebf0000-7ec09000     \               msvfw32
ELF     0x7ec09000-7ec8a000     Deferred        winmm<elf>
  \-PE  0x7ec10000-7ec8a000     \               winmm
ELF     0x7ec8a000-7ecac000     Deferred        msacm32<elf>
  \-PE  0x7ec90000-7ecac000     \               msacm32
ELF     0x7ecac000-7ece8000     Deferred        avifil32<elf>
  \-PE  0x7ecc0000-7ece8000     \               avifil32
ELF     0x7ece8000-7ed7a000     Deferred        comdlg32<elf>
  \-PE  0x7ed00000-7ed7a000     \               comdlg32
ELF     0x7ed7a000-7ee39000     Deferred        shell32<elf>
  \-PE  0x7ed90000-7ee39000     \               shell32
ELF     0x7ee39000-7ee61000     Deferred        winspool<elf>
  \-PE  0x7ee40000-7ee61000     \               winspool
ELF     0x7ee61000-7ef10000     Deferred        comctl32<elf>
  \-PE  0x7ee70000-7ef10000     \               comctl32
ELF     0x7ef10000-7ef24000     Deferred        lz32<elf>
  \-PE  0x7ef20000-7ef24000     \               lz32
ELF     0x7ef24000-7ef3c000     Deferred        version<elf>
  \-PE  0x7ef30000-7ef3c000     \               version
ELF     0x7ef3c000-7ef5a000     Deferred        mpr<elf>
  \-PE  0x7ef40000-7ef5a000     \               mpr
ELF     0x7ef5a000-7ef96000     Deferred        advapi32<elf>
  \-PE  0x7ef70000-7ef96000     \               advapi32
ELF     0x7f077000-7f977000     Deferred        gdi32<elf>
  \-PE  0x7f0c0000-7f977000     \               gdi32
ELF     0x7f977000-7fa90000     Deferred        user32<elf>
  \-PE  0x7f990000-7fa90000     \               user32
ELF     0x7fba2000-7fba7000     Deferred        libxdmcp.so.6
ELF     0x7fba7000-7fbb0000     Deferred        libsm.so.6
ELF     0x7fbb1000-7fbb6000     Deferred        libxxf86vm.so.1
ELF     0x7fbb6000-7fbc1000     Deferred        libgcc_s.so.1
ELF     0x7fbf4000-7fcf0000     Deferred        kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe00000-7fe03000     Deferred        libxau.so.6
ELF     0x7fe03000-7fe08000     Deferred        libxxf86dga.so.1
ELF     0x7fe09000-7fe0e000     Deferred        libxfixes.so.3
ELF     0x7fe0e000-7fe10000     Deferred        xlcutf8load.so.2
ELF     0x7fe10000-7fe1b000     Deferred        libnss_files.so.2
ELF     0x7fe1b000-7fe25000     Deferred        libnss_nis.so.2
ELF     0x7fe25000-7fe3b000     Deferred        libnsl.so.1
ELF     0x7fe3b000-7fe44000     Deferred        libnss_compat.so.2
ELF     0x7fe4f000-7fe75000     Deferred        libm.so.6
ELF     0x7fe75000-7ff6c000     Deferred        libwine_unicode.so.1
ELF     0x7ff6c000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7df6000-b7dfa000     Deferred        libdl.so.2
ELF     0xb7dfa000-b7f2f000     Deferred        libc.so.6
ELF     0xb7f2f000-b7f42000     Deferred        libpthread.so.0
ELF     0xb7f42000-b7f5c000     Deferred        libwine.so.1
ELF     0xb7f66000-b7f81000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) H:\.wine\drive_c\Programme\Robinson\robinson.exe
        00000009    0 <==
WineDbg terminated on pid 0x8

```

any ideas, i am at a loss here

---

