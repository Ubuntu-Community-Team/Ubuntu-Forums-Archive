---
title: "4x4 Evolution won't run in wine"
date: 2007-03-04
forum: Gaming &amp; Leisure
---

### Post by 8bit on 2007-03-04
I followed the instructions on Frank's Corner but I get the folling errors when I try to run it in wine. 3D is working correctly since Castle Wolfenstien plays fine (though I don't run it in wine). I'm running dapper with an nvidia card. I also noticed that when I run winecfg that when I click the audio tab, winecfg dies. But Diablo 2 runs fine with sound.

Please help. Thanks,

```
user@linuxbox:~/.wine/drive_c/Program Files/4x4 Evolution$ wine 4x4.exe -w
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:wave:DSD_CreateSecondaryBuffer (0x7fd67678,0x7fbaf5dc,12,0,0x7fd67b3c,0x7fd67c2c,0x7fd67b18): stub
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd684d8)->(0x10022,00000011)
fixme:ddraw:DirectDrawEnumerateExA no non-display devices supported.
fixme:ddraw:DirectDrawEnumerateExA no non-display devices supported.
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
wine: Unhandled page fault on read access to 0x00000000 at address 0x59756e (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0059756e).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:0059756e ESP:7fbaf5b8 EBP:00000000 EFLAGS:00210212(   - 00      - RIA1)
 EAX:00000000 EBX:00000020 ECX:7fbaf5c8 EDX:0000006c
 ESI:00ba507c EDI:00d6d175
Stack dump:
0x7fbaf5b8:  00000000 7fbaf5c8 00000001 00000000
0x7fbaf5c8:  0000006c 00000000 00000000 00000000
0x7fbaf5d8:  00000000 00000000 00000000 00000000
0x7fbaf5e8:  00000000 00000000 00000000 00000000
0x7fbaf5f8:  00000000 00000000 00000000 00000000
0x7fbaf608:  00000000 00000000 00000000 00000000
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x0059756e in 4x4 (+0x19756e) (0x0059756e)
0x0059756e: movl        0x0(%eax),%edx
Modules:
Module  Address                 Debug info      Name (74 modules)
PE      0x00400000-00dd6000     Export          4x4
PE      0x10000000-10057000     Deferred        binkw32
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
PE      0x7cca0000-7d643000     Deferred        tridx7
ELF     0x7e84b000-7e860000     Deferred        midimap<elf>
  \-PE  0x7e850000-7e860000     \               midimap
ELF     0x7e977000-7e99d000     Deferred        msacm32<elf>
  \-PE  0x7e980000-7e99d000     \               msacm32
ELF     0x7e99d000-7e9b5000     Deferred        msacm<elf>
  \-PE  0x7e9a0000-7e9b5000     \               msacm
ELF     0x7e9b5000-7e9f9000     Deferred        wineoss<elf>
  \-PE  0x7e9d0000-7e9f9000     \               wineoss
ELF     0x7ea17000-7ea20000     Deferred        libxcursor.so.1
ELF     0x7ea20000-7ea3c000     Deferred        imm32<elf>
  \-PE  0x7ea30000-7ea3c000     \               imm32
ELF     0x7ea3c000-7f1ff000     Deferred        libglcore.so.1
ELF     0x7f1ff000-7f284000     Deferred        libgl.so.1
ELF     0x7f284000-7f307000     Deferred        winex11<elf>
  \-PE  0x7f290000-7f307000     \               winex11
ELF     0x7f307000-7f326000     Deferred        libexpat.so.1
ELF     0x7f326000-7f354000     Deferred        libfontconfig.so.1
ELF     0x7f354000-7f368000     Deferred        libz.so.1
ELF     0x7f368000-7f3d1000     Deferred        libfreetype.so.6
ELF     0x7f3d1000-7f412000     Deferred        dinput<elf>
  \-PE  0x7f3e0000-7f412000     \               dinput
ELF     0x7f412000-7f464000     Deferred        dsound<elf>
  \-PE  0x7f420000-7f464000     \               dsound
ELF     0x7f464000-7f48f000     Deferred        ws2_32<elf>
  \-PE  0x7f470000-7f48f000     \               ws2_32
ELF     0x7f48f000-7f4a9000     Deferred        wsock32<elf>
  \-PE  0x7f4a0000-7f4a9000     \               wsock32
ELF     0x7f4a9000-7f4c8000     Deferred        iphlpapi<elf>
  \-PE  0x7f4b0000-7f4c8000     \               iphlpapi
ELF     0x7f4c8000-7f511000     Deferred        rpcrt4<elf>
  \-PE  0x7f4e0000-7f511000     \               rpcrt4
ELF     0x7f511000-7f5a2000     Deferred        ole32<elf>
  \-PE  0x7f530000-7f5a2000     \               ole32
ELF     0x7f5a2000-7f688000     Deferred        libx11.so.6
ELF     0x7f688000-7f6a0000     Deferred        libice.so.6
ELF     0x7f6a0000-7f71b000     Deferred        ddraw<elf>
  \-PE  0x7f6c0000-7f71b000     \               ddraw
ELF     0x7f71b000-7f847000     Deferred        user32<elf>
  \-PE  0x7f740000-7f847000     \               user32
ELF     0x7f847000-7f8cf000     Deferred        winmm<elf>
  \-PE  0x7f850000-7f8cf000     \               winmm
ELF     0x7f8cf000-7f8d9000     Deferred        libgcc_s.so.1
ELF     0x7f8d9000-7f8dd000     Deferred        libxfixes.so.3
ELF     0x7f8dd000-7f8ea000     Deferred        libxext.so.6
ELF     0x7f9bf000-7fa70000     Deferred        gdi32<elf>
  \-PE  0x7f9d0000-7fa70000     \               gdi32
ELF     0x7fa70000-7fab0000     Deferred        advapi32<elf>
  \-PE  0x7fa80000-7fab0000     \               advapi32
ELF     0x7fbb3000-7fbbb000     Deferred        libxrender.so.1
ELF     0x7fbee000-7fcf0000     Deferred        kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe00000-7fe03000     Deferred        libxrandr.so.2
ELF     0x7fe03000-7fe08000     Deferred        libxxf86vm.so.1
ELF     0x7fe08000-7fe12000     Deferred        libnss_files.so.2
ELF     0x7fe12000-7fe1b000     Deferred        libnss_nis.so.2
ELF     0x7fe1b000-7fe30000     Deferred        libnsl.so.1
ELF     0x7fe30000-7fe39000     Deferred        libnss_compat.so.2
ELF     0x7fe3b000-7fe40000     Deferred        libxxf86dga.so.1
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4c000-7fe4e000     Deferred        libnvidia-tls.so.1
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7d80000-b7d83000     Deferred        libxau.so.6
ELF     0xb7d84000-b7d87000     Deferred        libdl.so.2
ELF     0xb7d87000-b7eb6000     Deferred        libc.so.6
ELF     0xb7eb6000-b7ec8000     Deferred        libpthread.so.0
ELF     0xb7eda000-b7ef4000     Deferred        libwine.so.1
ELF     0xb7ef7000-b7f0d000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\4x4 Evolution\4x4.exe
        0000000f   15
        0000000d   15
        00000009    0 <==

```

---

### Post by 2dere on 2007-04-03
I'm sharing the 
```
fixme:ddraw:DirectDrawEnumerateExA no non-display devices supported.
```
problem with you, expect its for another game.

---

