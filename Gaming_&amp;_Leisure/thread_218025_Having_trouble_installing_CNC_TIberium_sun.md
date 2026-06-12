---
title: "Having trouble installing CNC TIberium sun"
date: 2006-07-18
forum: Gaming &amp; Leisure
---

### Post by Qwerty_ on 2006-07-18
Hi i am having trouble installing tiberium sun i have been to the winehq and had a look at the Howto but i just cant seem to do it properly everytime i try to i get stuck in a loop of wanting to restart wine. Then i try to use the file located in /setup/setup.exe on the disc and it asks me to insert the disc when it is already inserted, So downloaded the no-cd and i dont know how to install it so that i can install the game.

Any help is appreciated thanks.

---

### Post by Qwerty_ on 2006-07-18
sorry about the double post.

---

### Post by kraz on 2006-07-18
I havent tried installing C&C TS, but I once had RA2 running on my box. Im not sure that you can actually run an installer in wine.

The way I did it was to creat a no-cd installation in windows, using a crack, that was applied after installation. The crack was so well-made that RA2 was able to start without any registry-settings present. Im not sure there is such a thing for C&C TS, but I hope you get it working.

So,,

1) Install game in windows
2) apply crack
3) try to copy all files to your ubuntu installation
4) If the game complains about missing files, or reinstalling, you need to move some registry settings to your wine installation.

Hope you get it working!Q

---

### Post by kraz on 2006-07-18
Take a look here, it might help you:

[http://www.liflg.org/?catid=7&gameid=22](http://www.liflg.org/?catid=7&gameid=22)

---

### Post by Qwerty_ on 2006-07-18
> **kraz said:**
> Take a look here, it might help you:

[http://www.liflg.org/?catid=7&gameid=22](http://www.liflg.org/?catid=7&gameid=22)

thanks i am try it out now just gotta find both my CD's ill let you know how it goes thanks for your help.

---

### Post by Qwerty_ on 2006-07-18
Ok well i managed to get it to run off a disc on my windows even without copying the stuff required on disc 2 however when i try to run it in wine i get the following.. and i also copied it onto my linux box so it would have somewhere to dump game info as required.

fixme:exec:SHELL_execute flags ignored: 0x00000500
fixme:ole:ITypeInfo_fnRelease destroy child objects
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7e8dda0 (thread 001d), starting debugger...
WineDbg starting on pid 0x1c
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7e8dda0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:b7e8dda0 ESP:7fb8ef54 EBP:7fb8ef58 EFLAGS:00210206(   - 00      - RIP1)
 EAX:7fd6caa0 EBX:7f1f5f98 ECX:7fd6ca9f EDX:00000000
 ESI:7fd6caa0 EDI:00000000
Stack dump:
0x7fb8ef54:  7fd6ca8c 7fb8f198 7f1942b7 7fd6caa0
0x7fb8ef64:  00000000 00004c30 7ffd5850 7fcf0000
0x7fb8ef74:  7fdbb268 7fb8ef98 7ff970d0 7fd4d2b8
0x7fb8ef84:  000d0000 7fdbb3d0 7ff89619 7fdbb268
0x7fb8ef94:  7ffd5850 7fb8eff8 7ff97766 7fcf0020
0x7fb8efa4:  0000ffff 7fb8efe8 7fc75214 7f93d820
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0xb7e8dda0 strcpy+0x20 in libc.so.6 (0xb7e8dda0)
  2 0x7f1942b7 IWineD3DImpl_FillGLCaps+0x5f in wined3d (0x7f1942b7)
  3 0x7f197b44 in wined3d (+0x37b44) (0x7f197b44)
  4 0x7f31e859 in ddraw (+0x1e859) (0x7f31e859)
  5 0x7f31f39f DirectDrawCreate+0xf0 in ddraw (0x7f31f39f)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file tSunFS.dbg ("")
  6 0x00472c58 in game (+0x72c58) (0x00472c58)
0xb7e8dda0 strcpy+0x20 in libc.so.6: movzbl     0x0(%edx),%eax
Modules:
Module  Address                 Debug info      Name (87 modules)
PE      400000-86d000   Export          game
PE      10000000-1001e000       Deferred        language
PE      11000000-1102b000       Deferred        blowfish
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e40b000-7e420000       Deferred        midimap<elf>
  \-PE  7e410000-7e420000       \               midimap
ELF     7e55c000-7e574000       Deferred        msacm32<elf>
  \-PE  7e560000-7e574000       \               msacm32
ELF     7e574000-7e5b0000       Deferred        wineoss<elf>
  \-PE  7e580000-7e5b0000       \               wineoss
ELF     7e61c000-7e64d000       Deferred        uxtheme<elf>
  \-PE  7e620000-7e64d000       \               uxtheme
ELF     7e64d000-7e656000       Deferred        libxcursor.so.1
ELF     7e656000-7e672000       Deferred        imm32<elf>
  \-PE  7e660000-7e672000       \               imm32
ELF     7e672000-7e6f5000       Deferred        winex11<elf>
  \-PE  7e680000-7e6f5000       \               winex11
ELF     7e6f5000-7e714000       Deferred        libexpat.so.1
ELF     7e714000-7e742000       Deferred        libfontconfig.so.1
ELF     7e742000-7e756000       Deferred        libz.so.1
ELF     7e756000-7e7bf000       Deferred        libfreetype.so.6
ELF     7e7bf000-7e7d3000       Deferred        lz32<elf>
  \-PE  7e7d0000-7e7d3000       \               lz32
ELF     7e7d3000-7e7ec000       Deferred        version<elf>
  \-PE  7e7e0000-7e7ec000       \               version
ELF     7e7ec000-7e835000       Deferred        dsound<elf>
  \-PE  7e7f0000-7e835000       \               dsound
ELF     7e896000-7f058000       Deferred        libglcore.so.1
ELF     7f058000-7f0ce000       Deferred        libglu.so.1
ELF     7f0ce000-7f153000       Deferred        libgl.so.1
ELF     7f153000-7f1f7000       Export          wined3d<elf>
  \-PE  7f160000-7f1f7000       \               wined3d
ELF     7f1f7000-7f2dd000       Deferred        libx11.so.6
ELF     7f2dd000-7f2f5000       Deferred        libice.so.6
ELF     7f2f5000-7f33e000       Export          ddraw<elf>
  \-PE  7f300000-7f33e000       \               ddraw
ELF     7f33e000-7f368000       Deferred        ws2_32<elf>
  \-PE  7f350000-7f368000       \               ws2_32
ELF     7f368000-7f382000       Deferred        wsock32<elf>
  \-PE  7f370000-7f382000       \               wsock32
ELF     7f382000-7f40a000       Deferred        winmm<elf>
  \-PE  7f390000-7f40a000       \               winmm
ELF     7f40a000-7f49a000       Deferred        oleaut32<elf>
  \-PE  7f420000-7f49a000       \               oleaut32
ELF     7f49a000-7f55c000       Deferred        comctl32<elf>
  \-PE  7f4a0000-7f55c000       \               comctl32
ELF     7f55c000-7f57b000       Deferred        iphlpapi<elf>
  \-PE  7f560000-7f57b000       \               iphlpapi
ELF     7f57b000-7f5c8000       Deferred        rpcrt4<elf>
  \-PE  7f590000-7f5c8000       \               rpcrt4
ELF     7f5c8000-7f657000       Deferred        ole32<elf>
  \-PE  7f5e0000-7f657000       \               ole32
ELF     7f657000-7f6ad000       Deferred        shlwapi<elf>
  \-PE  7f670000-7f6ad000       \               shlwapi
ELF     7f6ad000-7f786000       Deferred        shell32<elf>
  \-PE  7f6c0000-7f786000       \               shell32
ELF     7f786000-7f7c8000       Deferred        advapi32<elf>
  \-PE  7f790000-7f7c8000       \               advapi32
ELF     7f89d000-7f94e000       Deferred        gdi32<elf>
  \-PE  7f8b0000-7f94e000       \               gdi32
ELF     7f94e000-7fa80000       Deferred        user32<elf>
  \-PE  7f970000-7fa80000       \               user32
ELF     7fb90000-7fb94000       Deferred        libxfixes.so.3
ELF     7fb94000-7fb9c000       Deferred        libxrender.so.1
ELF     7fbcf000-7fcd0000       Deferred        kernel32<elf>
  \-PE  7fbf0000-7fcd0000       \               kernel32
ELF     7fcd3000-7fce0000       Deferred        libxext.so.6
ELF     7fce1000-7fce6000       Deferred        libxxf86vm.so.1
ELF     7fce6000-7fcf0000       Deferred        libgcc_s.so.1
ELF     7fe01000-7fe04000       Deferred        libxrandr.so.2
ELF     7fe04000-7fe09000       Deferred        libxxf86dga.so.1
ELF     7fe09000-7fe13000       Deferred        libnss_files.so.2
ELF     7fe13000-7fe1c000       Deferred        libnss_nis.so.2
ELF     7fe1c000-7fe31000       Deferred        libnsl.so.1
ELF     7fe31000-7fe3a000       Deferred        libnss_compat.so.2
ELF     7fe3c000-7fe44000       Deferred        libsm.so.6
ELF     7fe48000-7fe6a000       Deferred        libm.so.6
ELF     7fe6a000-7ff62000       Deferred        libwine_unicode.so.1
ELF     7ff62000-7ffe0000       Deferred        ntdll<elf>
  \-PE  7ff70000-7ffe0000       \               ntdll
ELF     b7e10000-b7e13000       Deferred        libxau.so.6
ELF     b7e21000-b7e24000       Deferred        libdl.so.2
ELF     b7e24000-b7f53000       Export          libc.so.6
ELF     b7f53000-b7f65000       Deferred        libpthread.so.0
ELF     b7f65000-b7f67000       Deferred        libnvidia-tls.so.1
ELF     b7f6f000-b7f89000       Deferred        libwine.so.1
ELF     b7f8c000-b7fa2000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000001c (D) Z:\home\mike\TS\SUN\Game.exe
        00000021    0
        0000001d    0 <==
00000017
        00000019   -2
        00000018    0
00000022
        00000024   -2
        00000023    0
00000014
        00000015    0


i have noidea what that means but nothing seems to happen after i get that.

---

### Post by Qwerty_ on 2006-07-19
Ok well i have managed to get it to run off my external hdd now and i can start it up in wine aslong as the Windows type is ME or lower but as soon as it loads up the game it just quits and changes my resolution to 800X600 i am now using wine 0.9.16 any ideas what the problem could be?

EDIT: i just checked [http://appdb.winehq.org](http://appdb.winehq.org) and .9.16 does not run Tiberian sun. I might roll back to .9.12 that seems to work from what i have read.

---

### Post by Qwerty_ on 2006-07-20
OK i rolled back wine to 0.9.12 and TS works fine now. Just thought some of you would like to know.

---

### Post by vem0m on 2006-07-20
before that did u attempt to try version 0.9.17?

---

### Post by Perfect Storm on 2006-07-20
> Xlib: extension "GLX" missing on display ":0.0".
That does looks like that the driver for your graphic isn't installed or setup wrongly.

---

### Post by Qwerty_ on 2006-07-20
> **vem0m said:**
> before that did u attempt to try version 0.9.17?

I tried both .9.17 and 0.9.16 both with no luck.

---

