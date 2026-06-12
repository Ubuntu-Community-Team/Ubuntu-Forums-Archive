---
title: "SimCity 4 Deluxe Edition"
date: 2006-05-13
forum: Gaming &amp; Leisure
---

### Post by amitroy5 on 2006-05-13
I really love this game, and I was wondering if it is at all possible to get this game to work on Ubuntu? Thanks!

---

### Post by scooper on 2006-05-13
[QUOTE=amitroy5]I really love this game, and I was wondering if it is at all possible to get this game to work on Ubuntu? Thanks![/QUOTE]

[http://transgaming.org/gamesdb/](http://transgaming.org/gamesdb/)
[http://transgaming.org/gamesdb/games/view.mhtml?game_id=2998](http://transgaming.org/gamesdb/games/view.mhtml?game_id=2998)

Wine is the main tool for providing Windows compatibility.  Transgaming offers Cedega, a Wine variant for gaming.  SimCity 4 seems to be fairly well supported by Cedega (see link above).  Vanilla Wine might be worth a try or you could shell out for Cedega.  I don't have any experience with it myself to make a recommendation for or against.  I just know that games not supported by them probably are not likely to work in emulation.

Cheers,
Steve

---

### Post by graigsmith on 2006-05-23
i got it working under wine, well, i got simcity 4 plus the expansion working.

basically, i copied the contents of the cd to a folder, installed it using the latest version of wine.  then copied the cd contents of the expansion to the drive, and installed it too.  Either the expansion or the game had 2 cd's.  for that one, i copied all the files off one cd to a folder, started the install. removed all the files and then put the files off the second disk in that folder.

after each cd finished installing, it would give an error of some kind. i would click ok, and the program would close.  but it diddn't matter it would install anyways.

You have to crack the game with a no cd patch.  but, besides some sound problems it works pretty good :)  And i diddn't have to install anything other than basic wine from wine's ubuntu apt sources found here.

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

### Post by amitroy5 on 2006-10-25
OK. I was able to install the game, but when I try to lauch it, I get this erorr:

```

amitroy5@Amit:~/Desktop/Disk 1$ wine "c:\\Program Files\Maxis\SimCity 4 Deluxe\A pps\SimCity 4.exe"
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\sy stem32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system3 2\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\sy stem32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system3 2\\drivers\\SECDRV.SYS" failed, status c0000135
amitroy5@Amit:~/Desktop/Disk 1$

```

What does this error mean and what do I need to do in order to get the game to work? Thanks!

---

### Post by Breepee on 2006-10-27
That's because you didn't use the no-cd crack. Copy protection doesn't work in Linux (thank god!), so these cracks are mandatory.

---

### Post by amitroy5 on 2006-10-28
I applied the no-CD crack, and now hav the following error:

```
amitroy5@Amit:~$ wine "C:\\Program Files\Maxis\SimCity 4 Deluxe\Apps\SimCity 4.exe"
wine: Unhandled page fault on write access to 0x00a71b50 at address 0x7cfd00 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00a71b50 in 32-bit code (0x007cfd00).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:007cfd00 ESP:0033fde0 EBP:0033ff08 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00a71b50 EBX:7eec7bc0 ECX:00b21b68 EDX:00badcbc
 ESI:00b0725c EDI:00b07c04
Stack dump:
0x0033fde0:  00a71b5a 009f23b0 7ee7fd99 00000000
0x0033fdf0:  009f1c0f 00000001 00000094 00000005
0x0033fe00:  00000000 00000893 00000002 76726553
0x0033fe10:  20656369 6b636150 00003420 b7d03701
0x0033fe20:  00000000 00000000 0033fe7c 7eff5280
0x0033fe30:  00110000 7ffdf000 0033ff08 7efb7583
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x007cfd00 in simcity 4 (+0x3cfd00) (0x007cfd00)
  2 0x7ee8e48f in kernel32 (+0x4e48f) (0x7ee8e48f)
  3 0xb7e31387 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7e31387)
0x007cfd00: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (86 modules)
PE      400000-bc7e6e   Export          simcity 4
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c9e3000-7c9f8000       Deferred        midimap<elf>
  \-PE  7c9f0000-7c9f8000       \               midimap
ELF     7ca1e000-7ca36000       Deferred        msacm32<elf>
  \-PE  7ca20000-7ca36000       \               msacm32
ELF     7ca36000-7ca72000       Deferred        wineoss<elf>
  \-PE  7ca40000-7ca72000       \               wineoss
ELF     7caa4000-7cad6000       Deferred        uxtheme<elf>
  \-PE  7cab0000-7cad6000       \               uxtheme
ELF     7cad6000-7cada000       Deferred        libxfixes.so.3
ELF     7cada000-7cae3000       Deferred        libxcursor.so.1
ELF     7cae3000-7cae6000       Deferred        libxrandr.so.2
ELF     7cae6000-7caee000       Deferred        libxrender.so.1
ELF     7e036000-7e238000       Deferred        i915_dri.so
ELF     7e238000-7e2c3000       Deferred        winex11<elf>
  \-PE  7e250000-7e2c3000       \               winex11
ELF     7e2c3000-7e2e2000       Deferred        libexpat.so.1
ELF     7e2e2000-7e310000       Deferred        libfontconfig.so.1
ELF     7e310000-7e324000       Deferred        libz.so.1
ELF     7e324000-7e38d000       Deferred        libfreetype.so.6
ELF     7e38d000-7e3a9000       Deferred        imm32<elf>
  \-PE  7e390000-7e3a9000       \               imm32
ELF     7e3a9000-7e3d0000       Deferred        msvfw32<elf>
  \-PE  7e3b0000-7e3d0000       \               msvfw32
ELF     7e3d0000-7e3d7000       Deferred        libdrm.so.2
ELF     7e3d7000-7e44d000       Deferred        libglu.so.1
ELF     7e44d000-7e4b3000       Deferred        libgl.so.1
ELF     7e4b3000-7e599000       Deferred        libx11.so.6
ELF     7e599000-7e5a6000       Deferred        libxext.so.6
ELF     7e5a6000-7e5be000       Deferred        libice.so.6
ELF     7e5be000-7e62f000       Deferred        opengl32<elf>
  \-PE  7e5d0000-7e62f000       \               opengl32
ELF     7e62f000-7e643000       Deferred        lz32<elf>
  \-PE  7e640000-7e643000       \               lz32
ELF     7e643000-7e65c000       Deferred        version<elf>
  \-PE  7e650000-7e65c000       \               version
ELF     7e65c000-7e6e4000       Deferred        winmm<elf>
  \-PE  7e670000-7e6e4000       \               winmm
ELF     7e6e4000-7e72c000       Deferred        dsound<elf>
  \-PE  7e6f0000-7e72c000       \               dsound
ELF     7e72c000-7e7ed000       Deferred        comctl32<elf>
  \-PE  7e740000-7e7ed000       \               comctl32
ELF     7e7ed000-7e8d4000       Deferred        shell32<elf>
  \-PE  7e800000-7e8d4000       \               shell32
ELF     7e8d4000-7e924000       Deferred        rpcrt4<elf>
  \-PE  7e8e0000-7e924000       \               rpcrt4
ELF     7e924000-7e9b5000       Deferred        ole32<elf>
  \-PE  7e930000-7e9b5000       \               ole32
ELF     7e9b5000-7ea0b000       Deferred        shlwapi<elf>
  \-PE  7e9c0000-7ea0b000       \               shlwapi
ELF     7ea0b000-7ea15000       Deferred        libgcc_s.so.1
ELF     7eaea000-7eb9d000       Deferred        gdi32<elf>
  \-PE  7eb00000-7eb9d000       \               gdi32
ELF     7eb9d000-7eccf000       Deferred        user32<elf>
  \-PE  7ebc0000-7eccf000       \               user32
ELF     7eccf000-7ecee000       Deferred        mpr<elf>
  \-PE  7ece0000-7ecee000       \               mpr
ELF     7ecee000-7ed35000       Deferred        wininet<elf>
  \-PE  7ed00000-7ed35000       \               wininet
ELF     7ed35000-7ed48000       Deferred        libresolv.so.2
ELF     7ed48000-7ed67000       Deferred        iphlpapi<elf>
  \-PE  7ed50000-7ed67000       \               iphlpapi
ELF     7ed67000-7ed91000       Deferred        ws2_32<elf>
  \-PE  7ed70000-7ed91000       \               ws2_32
ELF     7ed91000-7edab000       Deferred        wsock32<elf>
  \-PE  7eda0000-7edab000       \               wsock32
ELF     7edab000-7edef000       Deferred        advapi32<elf>
  \-PE  7edc0000-7edef000       \               advapi32
ELF     7ee22000-7ef2e000       Export          kernel32<elf>
  \-PE  7ee40000-7ef2e000       \               kernel32
ELF     7ef2e000-7ef38000       Deferred        libnss_files.so.2
ELF     7ef38000-7ef41000       Deferred        libnss_nis.so.2
ELF     7ef41000-7ef56000       Deferred        libnsl.so.1
ELF     7ef56000-7ef5f000       Deferred        libnss_compat.so.2
ELF     7ef5f000-7ef81000       Deferred        libm.so.6
ELF     7ef81000-7f000000       Deferred        ntdll<elf>
  \-PE  7ef90000-7f000000       \               ntdll
ELF     b7cd4000-b7cd7000       Deferred        libxau.so.6
ELF     b7cd8000-b7cdb000       Deferred        libdl.so.2
ELF     b7cdb000-b7e0a000       Deferred        libc.so.6
ELF     b7e0a000-b7e1c000       Deferred        libpthread.so.0
ELF     b7e1d000-b7e22000       Deferred        libxxf86vm.so.1
ELF     b7e22000-b7e2a000       Deferred        libsm.so.6
ELF     b7e2a000-b7f3b000       Export          libwine.so.1
ELF     b7f3e000-b7f54000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Maxis\SimCity 4 Deluxe\Apps\SimCity 4.exe
        00000009    0 <==
amitroy5@Amit:~$

```

---

### Post by amitroy5 on 2006-11-05
bump

Any ideas?

---

### Post by petriborg on 2007-03-27
I think you may have the wrong no-cd hack, I have the same problem...

---

### Post by hikaricore on 2007-03-27
> **petriborg said:**
> I think you may have the wrong no-cd hack, I have the same problem...

...it's been over 4 months on this thread wth are you digging it up for?

The user you're responding to have posted twice since January, I'm betting
by now they've either solved their problem or moved on.

---

