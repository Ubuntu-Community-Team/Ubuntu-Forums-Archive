---
title: "SIlkroad Online"
date: 2006-03-23
forum: Gaming &amp; Leisure
---

### Post by juaduve on 2006-03-23
Hi all!! 

I am trying to play this greatt game under linux with wine or cedega:

With wine game install fine, update fine and it runs.... but when you are writting your username and pass, always says disconected from the server, never in.

With cedega is worst, i cant load that game it crash, tested with cedega 5.03, 5.1 and 5.1.1.


Have anyone another greatt experience or better luck with this greatt free MMORG?

---

### Post by Dropknee on 2006-04-07
I try this with the latest wine but the game wont start, the game luncher work, but when you try to luch the game this simply wont start

any help???

---

### Post by Dropknee on 2006-04-07
This is what I get when try to start Silkroad 

```
WineDbg starting on pid 0x10
Unhandled exception: page fault on read access to 0xc0001001 in 32-bit code (0x7c8e1470).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7c8e1470 ESP:7faefd84 EBP:7faefec4 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000001 EBX:00000000 ECX:c0001001 EDX:00000007
 ESI:c0001000 EDI:7c8e6374
Stack dump:
0x7faefd84:  7c8e7a74 7faefe00 7c8d0000 7c7c039c
0x7faefd94:  7c7c0d40 7c8e3bbb 7faeff2c 7c8e3f4b
0x7faefda4:  7faefec4 7c8d0000 7d9c0000 7c8e4138
0x7faefdb4:  00000000 00000000 00000000 00000000
0x7faefdc4:  00000000 00000000 00000000 00000000
0x7faefdd4:  00000000 00000000 00000000 00000000
0200: sel=1007 base=7fec2000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7c8e1470 (0x7c8e1470)
  2 0x7c8e26bc (0x7c8e26bc)
  3 0x00000000 (0x00000000)
0x7c8e1470: movb        0x0(%ecx),%cl
Modules:
Module  Address                 Debug info      Name (86 modules)
PE      0x00400000-00c31000     Deferred        sro_client
PE      0x65340000-653d2000     Deferred        oleaut32
PE      0x65f00000-65fc2000     Deferred        ole32
ELF     0x735f1000-735f3000     Deferred        xlcutf8load.so.2
ELF     0x7be86000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7d9eb000-7da00000     Deferred        midimap<elf>
  \-PE  0x7d9f0000-7da00000     \               midimap
ELF     0x7db19000-7db3d000     Deferred        msacm32<elf>
  \-PE  0x7db20000-7db3d000     \               msacm32
ELF     0x7db3d000-7db54000     Deferred        msacm<elf>
  \-PE  0x7db40000-7db54000     \               msacm
ELF     0x7db54000-7dc07000     Deferred        libasound.so.2
ELF     0x7dc07000-7dc30000     Deferred        winealsa<elf>
  \-PE  0x7dc10000-7dc30000     \               winealsa
ELF     0x7dcca000-7dcfb000     Deferred        uxtheme<elf>
  \-PE  0x7dcd0000-7dcfb000     \               uxtheme
ELF     0x7dd19000-7dd35000     Deferred        ximcp.so.2
ELF     0x7dd35000-7dd3e000     Deferred        librt.so.1
ELF     0x7dd48000-7dd4c000     Deferred        libxfixes.so.3
ELF     0x7de06000-7e6e9000     Deferred        fglrx_dri.so
ELF     0x7e6e9000-7e768000     Deferred        winex11<elf>
  \-PE  0x7e700000-7e768000     \               winex11
ELF     0x7e768000-7e787000     Deferred        libexpat.so.1
ELF     0x7e787000-7e7b5000     Deferred        libfontconfig.so.1
ELF     0x7e7b5000-7e7c9000     Deferred        libz.so.1
ELF     0x7e7c9000-7e833000     Deferred        libfreetype.so.6
ELF     0x7e833000-7e8bf000     Deferred        wined3d<elf>
  \-PE  0x7e850000-7e8bf000     \               wined3d
ELF     0x7e8bf000-7e935000     Deferred        libglu.so.1
ELF     0x7e935000-7e9d4000     Deferred        libgl.so.1
ELF     0x7e9d4000-7ea02000     Deferred        d3d9<elf>
  \-PE  0x7e9e0000-7ea02000     \               d3d9
ELF     0x7ea02000-7eac2000     Deferred        libx11.so.6
ELF     0x7eac2000-7eadb000     Deferred        libice.so.6
ELF     0x7eadb000-7eb56000     Deferred        ddraw<elf>
  \-PE  0x7eb00000-7eb56000     \               ddraw
ELF     0x7eb56000-7eb6a000     Deferred        lz32<elf>
  \-PE  0x7eb60000-7eb6a000     \               lz32
ELF     0x7eb6a000-7eb83000     Deferred        version<elf>
  \-PE  0x7eb70000-7eb83000     \               version
ELF     0x7eb83000-7ec0a000     Deferred        winmm<elf>
  \-PE  0x7eb90000-7ec0a000     \               winmm
ELF     0x7ec0a000-7ec5b000     Deferred        dsound<elf>
  \-PE  0x7ec20000-7ec5b000     \               dsound
ELF     0x7ec5b000-7ec79000     Deferred        iphlpapi<elf>
  \-PE  0x7ec60000-7ec79000     \               iphlpapi
ELF     0x7ec79000-7eca2000     Deferred        ws2_32<elf>
  \-PE  0x7ec80000-7eca2000     \               ws2_32
ELF     0x7eca2000-7ed57000     Deferred        comctl32<elf>
  \-PE  0x7ecb0000-7ed57000     \               comctl32
ELF     0x7ed57000-7edaf000     Deferred        shlwapi<elf>
  \-PE  0x7ed70000-7edaf000     \               shlwapi
ELF     0x7edaf000-7ee7b000     Deferred        shell32<elf>
  \-PE  0x7edd0000-7ee7b000     \               shell32
ELF     0x7ee7b000-7ee97000     Deferred        imm32<elf>
  \-PE  0x7ee80000-7ee97000     \               imm32
ELF     0x7ee97000-7efb9000     Deferred        user32<elf>
  \-PE  0x7eeb0000-7efb9000     \               user32
ELF     0x7efb9000-7eff7000     Deferred        advapi32<elf>
  \-PE  0x7efc0000-7eff7000     \               advapi32
ELF     0x7f0dd000-7f9e0000     Deferred        gdi32<elf>
  \-PE  0x7f120000-7f9e0000     \               gdi32
ELF     0x7faf0000-7faf9000     Deferred        libxcursor.so.1
ELF     0x7fc41000-7fd40000     Deferred        kernel32<elf>
  \-PE  0x7fc60000-7fd40000     \               kernel32
ELF     0x7fd43000-7fd50000     Deferred        libxext.so.6
ELF     0x7fd53000-7fd5b000     Deferred        libxrender.so.1
ELF     0x7fd5b000-7fd60000     Deferred        libxxf86vm.so.1
ELF     0x7fe70000-7fe74000     Deferred        libxdmcp.so.6
ELF     0x7fe74000-7fe7f000     Deferred        libgcc_s.so.1
ELF     0x7fe7f000-7fe8a000     Deferred        libnss_files.so.2
ELF     0x7fe8a000-7fe94000     Deferred        libnss_nis.so.2
ELF     0x7fe94000-7feaa000     Deferred        libnsl.so.1
ELF     0x7feaa000-7feb4000     Deferred        libnss_compat.so.2
ELF     0x7feb6000-7febb000     Deferred        libxxf86dga.so.1
ELF     0x7febb000-7fec2000     Deferred        libsm.so.6
ELF     0x7fec6000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7dc0000-b7dc3000     Deferred        libxau.so.6
ELF     0xb7dc8000-b7dcc000     Deferred        libdl.so.2
ELF     0xb7dcc000-b7efa000     Deferred        libc.so.6
ELF     0xb7efa000-b7f0d000     Deferred        libpthread.so.0
ELF     0xb7f1c000-b7f36000     Deferred        libwine.so.1
ELF     0xb7f38000-b7f4e000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000010 (D) C:\Program Files\Silkroad\sro_client.exe
        00000011    0 <==
00000008
        0000000f    0
        0000000e   15
        0000000d    0
0000000a
        0000000b    0
00000008
        00000009    0


```

Maybe the program hang when try to use the nProtect anti-cheat program

---

### Post by Dropknee on 2006-04-08
This is another update for those who follow this game. I try Cedega and the game install but the auto update when start to patch the game, this message apperar

> Patching is not complete. Please try again [Error code(4) ] 

 I really dont know how to fix this :(

---

### Post by Toxicity999 on 2006-04-11
youll learn from being a Linux user that just because theres a new version doesnt mean you needto jump to it... work with the version that worked some and pastethe output... probably a native DLL or two will help you.

---

### Post by Adrian_b on 2006-04-11
In MMORPGS, you're somewhat forced to have the latest version.

---

### Post by malcolmb on 2006-04-18
I still think its pretty garbage that you cant even go to the silkroad website unless your running windows

---

### Post by blastermaster on 2006-05-02
[QUOTE=malcolmb]I still think its pretty garbage that you cant even go to the silkroad website unless your running windows[/QUOTE]

You Can enter the website if you use firefox extention user agetn switcher! :D 

And I still trying to get silkroad to work with wine but not luck, if i do winecfg and set it up tp win98 it runs but hangs at the gameguard, any ideas as how to bypass or fix this thanks.

---

### Post by Engnome on 2006-05-02
*With wine game install fine, update fine and it runs.... but when you are writting your username and pass, always says disconected from the server, never in.*

This happens to me on Windows to so its probably not wine. Its been a while since I played now though but usually I could try a couple of times and it worked.

---

### Post by Artist22405 on 2006-05-02
I havent played silkroad in a while either I switched to linux complety silkroad on windows willnot workunless you are using ie6 I had too install ie7 when I was using windows to get it to work I loev that game if you can figure out how to use ie6 and get the game running I think that would be the 1 and only non linux thing I would install on my pc but as I am a noob to linux I dont know if you can even get ie6 to work with lets say wine I wish the best of luck if you get it to work plz let me and the rest of us know its a great free game

---

