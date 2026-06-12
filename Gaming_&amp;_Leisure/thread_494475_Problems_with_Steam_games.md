---
title: "Problems with Steam games"
date: 2007-07-06
forum: Gaming &amp; Leisure
---

### Post by Mike7171 on 2007-07-06
All right, I searched through the forums, and there is none for this specific problem, or at least any that help. My problem is that when I launch a Steam game, the loading screen comes up for the game, but just before the menu should show up, it stops/crashes (steam window comes up again). I see that other people have mentioned this problem, but no one has helped them, so hopefully this thread will be helpful to everyone in my shoes. So, any ideas? Thanks

---

### Post by marpstar on 2007-07-07
Is it any particular game?  I've only tried CounterStrike 1.6, but it installed and played with a fair amount of ease.  I'm using Wine0.9.33 and have played without issue 4 or 5 times.

---

### Post by Mike7171 on 2007-07-07
They're Counter Strike: Source, and Half-Life 2.

---

### Post by marpstar on 2007-07-07
Tomorrow I'll get one of those installed and give it a shot and I'll let you know how they work for me.

---

### Post by Mike7171 on 2007-07-07
Thanks, Appreciate it.

---

### Post by marpstar on 2007-07-09
When running Half-Life 2 in full screen, I got the exact same result as you.  When I chose to run in in a window, I actually did get the menu up, but went into the video options and my system totally froze shortly after...I'm going to try a couple more things and I'll let you know if I get it working...


-Cody

---

### Post by Mike7171 on 2007-07-09
Thanks again. When I was in the demo earlier, i went into video options and mine froze too.

---

### Post by Ziggyz on 2007-07-09
Yes, I am getting this same error, but with source mods.

---

### Post by Mike7171 on 2007-07-09
I tried to run CSS again, and I actually made it into the server selection menu before it crashed.  I ran it through terminal to see if any errors came up. This is a big hunk of everything it said. I'll bold the only thing that looks suspicious to me:
> 
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:avifile:AVIFileExit (): stub!
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
[B]wine: Unhandled page fault on read access to 0x0d35a1a0 at address 0xe2d3e2c (thread 0043), starting debugger...
Unhandled exception: page fault on read access to 0x0d35a1a0 in 32-bit code (0x0e2d3e2c).
Register dump:[/B]
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0e2d3e2c ESP:0034fc24 EBP:0034fc5c EFLAGS:00210202(   - 00      - -RI1)
 EAX:0d35a1a0 EBX:00000001 ECX:05240180 EDX:ffffffff
 ESI:05240180 EDI:0e2e6050
Stack dump:
0x0034fc24:  00000001 00000000 00000001 0e2e604c
0x0034fc34:  0e2d82e7 00000000 00000000 00000001
0x0034fc44:  0034fc38 0034f798 0034fca4 0e2d83d4
0x0034fc54:  0e2e3518 00000000 0034fc78 0e2d836b
0x0034fc64:  00000000 00000000 00000001 0e2d69b8
0x0034fc74:  00000000 0034fcb4 0e2d6ac4 0e2d0000
Backtrace:
=>1 0x0e2d3e2c in scenefilecache (+0x3e2c) (0x0034fc5c)
  2 0x0e2d836b in scenefilecache (+0x836b) (0x0034fc78)
  3 0x0e2d6ac4 in scenefilecache (+0x6ac4) (0x0034fcb4)
  4 0x7bc392a5 call_dll_entry_point+0x15() in ntdll (0x0034fcd4)
  5 0x7bc3ac3d in ntdll (+0x2ac3d) (0x0034fd64)
  6 0x7bc3b07f in ntdll (+0x2b07f) (0x0034fd84)
  7 0x7b8720ff ExitProcess+0x1f() in kernel32 (0x0034fda4)
  8 0x00401abe in hl2 (+0x1abe) (0x0034fddc)
  9 0x00401c41 in hl2 (+0x1c41) (0x0034ff08)
  10 0x7b874c6e in kernel32 (+0x54c6e) (0x0034ffe8)
  11 0xb7e93af7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0e2d3e2c: call        *0x0(%eax)
Modules:
Module  Address                 Debug info      Name (124 modules)
PE        350000-  386000       Deferred        tier0
PE        390000-  3ae000       Deferred        vstdlib
PE        400000-  41c000       Export          hl2
PE       d690000- dc7d000       Deferred        engine
PE       dc80000- dc94000       Deferred        steam_api
PE       e010000- e01f000       Deferred        unicode
PE       e290000- e2c6000       Deferred        soundemittersystem
PE       e2d0000- e2eb000       Export          scenefilecache
PE       e2f0000- e46c000       Deferred        steamclient
PE       e470000- e4b0000       Deferred        tier0_s
PE       e4b0000- e529000       Deferred        vstdlib_s
PE       e650000- e833000       Deferred        gameui
PE       f680000- f690000       Deferred        vaudio_miles
PE       ff10000- ffd4000       Deferred        friendsui
PE      10000000-10030000       Deferred        launcher
PE      1cbe0000-1ccab000       Deferred        serverbrowser
PE      20000000-2031e000       Deferred        steam
PE      21100000-21164000       Deferred        mss32
PE      22000000-22642000       Deferred        server
PE      24000000-24476000       Deferred        client
PE      26400000-26439000       Deferred        mssvoice.asi
PE      26f00000-26f2e000       Deferred        mssmp3.asi
PE      60000000-60021000       Deferred        cserhelper
ELF     7abb4000-7abfd000       Deferred        dsound<elf>
  \-PE  7abc0000-7abfd000       \               dsound
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7b965000-7b9af000       Deferred        dbghelp<elf>
  \-PE  7b970000-7b9af000       \               dbghelp
ELF     7bc00000-7bc97000       Export          ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bcb5000-7bcef000       Deferred        shdocvw<elf>
  \-PE  7bcc0000-7bcef000       \               shdocvw
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c679000-7c68e000       Deferred        psapi<elf>
  \-PE  7c680000-7c68e000       \               psapi
ELF     7cd20000-7cd72000       Deferred        crypt32<elf>
  \-PE  7cd30000-7cd72000       \               crypt32
ELF     7cd72000-7cda7000       Deferred        rsaenh<elf>
  \-PE  7cd80000-7cda7000       \               rsaenh
ELF     7cda7000-7cdbe000       Deferred        mcicda<elf>
  \-PE  7cdb0000-7cdbe000       \               mcicda
ELF     7cdbe000-7cdd2000       Deferred        winejoystick<elf>
  \-PE  7cdc0000-7cdd2000       \               winejoystick
ELF     7d169000-7d189000       Deferred        mpr<elf>
  \-PE  7d170000-7d189000       \               mpr
ELF     7d189000-7d1d2000       Deferred        wininet<elf>
  \-PE  7d190000-7d1d2000       \               wininet
ELF     7d1d2000-7d26f000       Deferred        oleaut32<elf>
  \-PE  7d1e0000-7d26f000       \               oleaut32
ELF     7d2d0000-7d2e5000       Deferred        midimap<elf>
  \-PE  7d2e0000-7d2e5000       \               midimap
ELF     7d2e5000-7d30b000       Deferred        msacm32<elf>
  \-PE  7d2f0000-7d30b000       \               msacm32
ELF     7d30b000-7d323000       Deferred        msacm32<elf>
  \-PE  7d310000-7d323000       \               msacm32
ELF     7d323000-7d35f000       Deferred        wineoss<elf>
  \-PE  7d330000-7d35f000       \               wineoss
ELF     7d35f000-7d3ed000       Deferred        winmm<elf>
  \-PE  7d370000-7d3ed000       \               winmm
ELF     7d56e000-7d5a0000       Deferred        uxtheme<elf>
  \-PE  7d580000-7d5a0000       \               uxtheme
ELF     7d5a0000-7d5b4000       Deferred        mswsock<elf>
  \-PE  7d5b0000-7d5b4000       \               mswsock
ELF     7d5b4000-7d5c8000       Deferred        lz32<elf>
  \-PE  7d5c0000-7d5c8000       \               lz32
ELF     7d5c8000-7d5e2000       Deferred        version<elf>
  \-PE  7d5d0000-7d5e2000       \               version
ELF     7d5e2000-7d69f000       Deferred        comctl32<elf>
  \-PE  7d5f0000-7d69f000       \               comctl32
ELF     7d69f000-7d6f7000       Deferred        shlwapi<elf>
  \-PE  7d6b0000-7d6f7000       \               shlwapi
ELF     7d6f7000-7d7f5000       Deferred        shell32<elf>
  \-PE  7d710000-7d7f5000       \               shell32
ELF     7d7f5000-7d84d000       Deferred        rpcrt4<elf>
  \-PE  7d800000-7d84d000       \               rpcrt4
ELF     7d84d000-7d8ec000       Deferred        ole32<elf>
  \-PE  7d860000-7d8ec000       \               ole32
ELF     7d8ec000-7d8ff000       Deferred        libresolv.so.2
ELF     7d8ff000-7d91d000       Deferred        iphlpapi<elf>
  \-PE  7d910000-7d91d000       \               iphlpapi
ELF     7d91d000-7d94a000       Deferred        ws2_32<elf>
  \-PE  7d930000-7d94a000       \               ws2_32
ELF     7dbba000-7dbd4000       Deferred        wsock32<elf>
  \-PE  7dbc0000-7dbd4000       \               wsock32
ELF     7dbd6000-7dbdb000       Deferred        libxfixes.so.3
ELF     7dbdb000-7dbe4000       Deferred        libxcursor.so.1
ELF     7dbe4000-7dc01000       Deferred        imm32<elf>
  \-PE  7dbf0000-7dc01000       \               imm32
ELF     7dc01000-7dc07000       Deferred        libxrandr.so.2
ELF     7dc07000-7dc0f000       Deferred        libxrender.so.1
ELF     7df38000-7df3a000       Deferred        libnvidia-tls.so.1
ELF     7df3a000-7e7c0000       Deferred        libglcore.so.1
ELF     7e7c0000-7e84c000       Deferred        libgl.so.1
ELF     7e84c000-7e851000       Deferred        libxdmcp.so.6
ELF     7e851000-7e854000       Deferred        libxau.so.6
ELF     7e854000-7e945000       Deferred        libx11.so.6
ELF     7e945000-7e953000       Deferred        libxext.so.6
ELF     7e953000-7e958000       Deferred        libxxf86vm.so.1
ELF     7e958000-7e970000       Deferred        libice.so.6
ELF     7e970000-7e979000       Deferred        libsm.so.6
ELF     7e979000-7ea09000       Deferred        winex11<elf>
  \-PE  7e990000-7ea09000       \               winex11
ELF     7ea7b000-7ea9b000       Deferred        libexpat.so.1
ELF     7ea9b000-7eac6000       Deferred        libfontconfig.so.1
ELF     7eac6000-7eada000       Deferred        libz.so.1
ELF     7eada000-7eb45000       Deferred        libfreetype.so.6
ELF     7eb45000-7eb8d000       Deferred        advapi32<elf>
  \-PE  7eb50000-7eb8d000       \               advapi32
ELF     7eb8d000-7eb99000       Deferred        libgcc_s.so.1
ELF     7ec83000-7ed43000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed43000       \               gdi32
ELF     7ed43000-7ee80000       Deferred        user32<elf>
  \-PE  7ed60000-7ee80000       \               user32
ELF     7ee80000-7ee8b000       Deferred        libnss_files.so.2
ELF     7ee8b000-7eea2000       Deferred        libnsl.so.1
ELF     7eea2000-7eeab000       Deferred        libnss_compat.so.2
ELF     7efcb000-7eff2000       Deferred        libm.so.6
ELF     7eff4000-7effe000       Deferred        libnss_nis.so.2
ELF     b7d22000-b7d26000       Deferred        libdl.so.2
ELF     b7d26000-b7e67000       Deferred        libc.so.6
ELF     b7e67000-b7e7e000       Deferred        libpthread.so.0
ELF     b7e8c000-b7fa0000       Export          libwine.so.1
ELF     b7fa2000-b7fbd000       Deferred        ld-linux.so.2


Those smiley faces shouldn't be there.

---

### Post by Ziggyz on 2007-07-24
lol your errors have smilies in them!

---

