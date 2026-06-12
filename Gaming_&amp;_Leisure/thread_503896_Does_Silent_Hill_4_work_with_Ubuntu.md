---
title: "Does Silent Hill 4 work with Ubuntu?"
date: 2007-07-18
forum: Gaming &amp; Leisure
---

### Post by Dark Aspect on 2007-07-18
I have Wine,Cedega, and VMware and all appears to fail to emulate silent hill 4 correctly.I have gotten a few unsupported games to work well with Ubuntu Linux so if there is ANYBODY that knows how to play silent hill 4 on Ubuntu please help.This is actually the only game I have that 100% does not work,some games work with issues.Having said that I find Linux too be as good windows with most games.Silent hill 3 (I think) works with cedega 4.2.I have tried disabling sound on both wine and cedega,I have tried a NO-CD crack and I have tried various DLL overrides.

The game boots on wine but crashes 5 seconds into the main menu.Any ideas would be helpful.

And will quick if nobody's heard of the silent hill series or silent hill 4 [here is a Wiki link]("http://en.wikipedia.org/wiki/Silent_Hill_4:_The_Room")

---

### Post by adam_kimber on 2007-07-18
After a quick peruse of the Cedega games database and the Wine App DB i discover that SH4 is not listed in Cedega, so is not supported as of yet and has not been tested on Ubuntu with Wine. Has been tested with Debian SID and the result was garbage, so probably the same will be in Ubuntu. 

Wine App node for SH4 - [http://appdb.winehq.org/appview.php?iVersionId=7189]("http://appdb.winehq.org/appview.php?iVersionId=7189")

For future reference :D

Cedega Games DB - [http://games.cedega.com/gamesdb/]("http://games.cedega.com/gamesdb/")
Wine App DB - [http://appdb.winehq.org/]("http://appdb.winehq.org/")

Wine App DB - [http://appdb.winehq.org/]("http://appdb.winehq.org/")

Hope this helps, sorry not better news :(

---

### Post by Dark Aspect on 2007-07-18
um I have tested Silent hill 4 on Ubunut with wine 0.9.37 and it was a no go with several attempts.I guess I should probably submit my test result with the wine DB.Just for the fun of it not really expecting it to work I guess I should try it with the new wine 0.9.41.

---

### Post by Dark Aspect on 2007-07-19
I tried Silent hill 4 on wine 0.9.41 and it worked to a degree!!!!!

I could give this a platinum ranting,its game play is prefect,sounds great,detected my controller when I booted it.

BUT

It crashes when when I click new game.I can fix this by deleting the DLL's out of its directory but it still crash later when you finish the very first level.I am still working with the registry and the DLL's I am sure I can get this to work.I don't mind if some body go ahead and sends wine AB what I have but I am going to wait a few days I am sure I can get this working.It would be nice if some with this game helped with ideas on the registry and DLL overrides.I have fixed several crashes with different setting.  

Here a picture that I could never got on the older version because it crashed before the main menu:

[IMG]http://i183.photobucket.com/albums/x72/Dark_Aspect/Screenshot-1-2.png[/IMG]

EDIT

Ok I am now working on trying to fixed the third and hopefully the last crash I encounter at the end of the first level.I booted the game up under command line and I have the code it gives just before it crashes.here is is if anyone else is curious:

> err:ole:CoGetClassObject class {4a2286e0-7bef-11ce-9bd9-0000e202599c} not registered
err:ole:CoGetClassObject no class object {4a2286e0-7bef-11ce-9bd9-0000e202599c} could be created for context 0x1
err:ole:CoGetClassObject class {feb50740-7bef-11ce-9bd9-0000e202599c} not registered
err:ole:CoGetClassObject no class object {feb50740-7bef-11ce-9bd9-0000e202599c} could be created for context 0x1
wine: Unhandled page fault on read access to 0x00000000 at address 0x7bfcedf2 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7bfcedf2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bfcedf2 ESP:0033f8e0 EBP:0033f938 EFLAGS:00210202(   - 00      - -RI1)
 EAX:07f77430 EBX:7bffea8c ECX:00000000 EDX:00000004
 ESI:019b1c58 EDI:07b6d820
Stack dump:
0x0033f8e0:  019b1c58 07e8cf50 00000008 e436eb84
0x0033f8f0:  11ce524f 2000539f 70a70baf 00000001
0x0033f900:  00000000 00000000 0f6417d6 11d0c318
0x0033f910:  07e8cf50 003122c9 00000000 07b6d820
0x0033f920:  00000004 ff0a0000 00000002 0150c138
0x0033f930:  0150c130 0150c134 0150c140 00413a4d
Backtrace:
=>1 0x7bfcedf2 in quartz (+0x1edf2) (0x0033f938)
  2 0x00413a4d in silent hill 4 (+0x13a4d) (0x0150c140)
  3 0x07ba3f90 (0x00000000)
0x7bfcedf2: movl        0x0(%ecx),%eax
Modules:
Module  Address                 Debug info      Name (84 modules)
PE        400000- 13e2b28       Export          silent hill 4
ELF     7a515000-7a5d2000       Deferred        comctl32<elf>
  \-PE  7a520000-7a5d2000       \               comctl32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7b934000-7b9d2000       Deferred        oleaut32<elf>
  \-PE  7b950000-7b9d2000       \               oleaut32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf4b000-7bf7d000       Deferred        uxtheme<elf>
  \-PE  7bf50000-7bf7d000       \               uxtheme
ELF     7bf7d000-7bfa4000       Deferred        msvfw32<elf>
  \-PE  7bf80000-7bfa4000       \               msvfw32
ELF     7bfa4000-7c000000       Export          quartz<elf>
  \-PE  7bfb0000-7c000000       \               quartz
ELF     7d203000-7d229000       Deferred        msacm32<elf>
  \-PE  7d210000-7d229000       \               msacm32
ELF     7d229000-7d241000       Deferred        msacm32<elf>
  \-PE  7d230000-7d241000       \               msacm32
ELF     7d241000-7d306000       Deferred        libasound.so.2
ELF     7d552000-7d567000       Deferred        midimap<elf>
  \-PE  7d560000-7d567000       \               midimap
ELF     7d567000-7d599000       Deferred        winealsa<elf>
  \-PE  7d570000-7d599000       \               winealsa
ELF     7d59b000-7d5a0000       Deferred        libxfixes.so.3
ELF     7d5a0000-7d5a9000       Deferred        libxcursor.so.1
ELF     7d5a9000-7d5af000       Deferred        libxrandr.so.2
ELF     7d5af000-7d5b7000       Deferred        libxrender.so.1
ELF     7dadd000-7db66000       Deferred        winex11<elf>
  \-PE  7daf0000-7db66000       \               winex11
ELF     7dc0f000-7dc2f000       Deferred        libexpat.so.1
ELF     7dc2f000-7dc5a000       Deferred        libfontconfig.so.1
ELF     7dc5a000-7dc6e000       Deferred        libz.so.1
ELF     7dc6e000-7dcd9000       Deferred        libfreetype.so.6
ELF     7dcd9000-7dcf6000       Deferred        imm32<elf>
  \-PE  7dce0000-7dcf6000       \               imm32
ELF     7dcf6000-7dd3e000       Deferred        dsound<elf>
  \-PE  7dd00000-7dd3e000       \               dsound
ELF     7dd3e000-7dd74000       Deferred        dinput<elf>
  \-PE  7dd50000-7dd74000       \               dinput
ELF     7dd74000-7dd8d000       Deferred        dinput8<elf>
  \-PE  7dd80000-7dd8d000       \               dinput8
ELF     7dd8d000-7de1b000       Deferred        winmm<elf>
  \-PE  7dda0000-7de1b000       \               winmm
ELF     7de80000-7e706000       Deferred        libglcore.so.1
ELF     7e706000-7e786000       Deferred        libglu.so.1
ELF     7e786000-7e812000       Deferred        libgl.so.1
ELF     7e812000-7e903000       Deferred        libx11.so.6
ELF     7e903000-7e911000       Deferred        libxext.so.6
ELF     7e911000-7e929000       Deferred        libice.so.6
ELF     7e929000-7e9f4000       Deferred        wined3d<elf>
  \-PE  7e940000-7e9f4000       \               wined3d
ELF     7e9f4000-7ea1f000       Deferred        d3d8<elf>
  \-PE  7ea00000-7ea1f000       \               d3d8
ELF     7ea1f000-7ea32000       Deferred        libresolv.so.2
ELF     7ea32000-7ea50000       Deferred        iphlpapi<elf>
  \-PE  7ea40000-7ea50000       \               iphlpapi
ELF     7ea50000-7eaa9000       Deferred        rpcrt4<elf>
  \-PE  7ea60000-7eaa9000       \               rpcrt4
ELF     7eaa9000-7eb48000       Deferred        ole32<elf>
  \-PE  7eac0000-7eb48000       \               ole32
ELF     7eb48000-7eb90000       Deferred        advapi32<elf>
  \-PE  7eb50000-7eb90000       \               advapi32
ELF     7eb90000-7eb9c000       Deferred        libgcc_s.so.1
ELF     7eb9c000-7eba1000       Deferred        libxdmcp.so.6
ELF     7eba1000-7eba4000       Deferred        libxau.so.6
ELF     7eba4000-7ebad000       Deferred        libsm.so.6
ELF     7ec97000-7ed57000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed57000       \               gdi32
ELF     7ed57000-7ee94000       Deferred        user32<elf>
  \-PE  7ed70000-7ee94000       \               user32
ELF     7efa6000-7efb1000       Deferred        libnss_files.so.2
ELF     7efb1000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efef000       Deferred        libm.so.6
ELF     7efef000-7eff1000       Deferred        libnvidia-tls.so.1
ELF     7eff1000-7eff6000       Deferred        libxxf86vm.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c61000-b7c6a000       Deferred        libnss_compat.so.2
ELF     b7c6b000-b7c6f000       Deferred        libdl.so.2
ELF     b7c6f000-b7db0000       Deferred        libc.so.6
ELF     b7db1000-b7dc8000       Deferred        libpthread.so.0
ELF     b7dd9000-b7eed000       Deferred        libwine.so.1
ELF     b7eef000-b7f0a000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Konami\SILENT HILL 4\SILENT HILL 4.exe
        0000000e   15
        0000000d    0
        00000009    0 <==
[email]administrator@Asus-A8N-E:~/.wine[/email]/drive_c/Program Files/Konami/SILENT HILL 4$ 


---

