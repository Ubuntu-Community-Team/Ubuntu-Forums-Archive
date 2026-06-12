---
title: "Dungeon Seige II Launching error"
date: 2007-06-02
forum: Gaming &amp; Leisure
---

### Post by Memory.Dump on 2007-06-02
ok, so I borrowe DS II from y bro tonight, I after some tweaking and installing MFC42.dll into the system part managed to get the bloody thing to install but now however I get error 005D whenever I try to run it I'm not sure what it means even, I've been searching around the web and the only thing I can find is it seems to somehow be related to reading a disc? I dunno


anybody have any ideas?

---

### Post by Memory.Dump on 2007-06-02
I ran it in the Terminal and got the following output:
```
memorydump@memorydump-desktop:~/.wine/drive_c/Program Files/Microsoft Games/Dungeon Siege 2$ wine DungeonSiege2.exe
fixme:atl:AtlAxWinInit semi-stub
wine: Call from 0x10001028 to unimplemented function MFC42.DLL.6467, aborting
wine: Unhandled page fault on write access to 0x0000025a at address 0x7e030003 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x0000025a in 32-bit code (0x7e030003).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e030003 ESP:0033fed0 EBP:01109fff EFLAGS:00010202(   - 00      - -RI1)
 EAX:7e030001 EBX:0110e38f ECX:0000025a EDX:0110be48
 ESI:7b8b23dc EDI:00000000
Stack dump:
0x0033fed0:  7e030000 0110e38f 7bc30370 0110a7db
0x0033fee0:  00000206 7ffdf000 0110a000 0110a000
0x0033fef0:  0033ff04 7b8ad908 00000000 00000000
0x0033ff00:  0110a000 0110a000 0033ffe8 7b87221e
0x0033ff10:  7ffdf000 00000000 00000000 00000000
0x0033ff20:  00000000 00000000 00000000 ffffffff
Backtrace:
=>1 0x7e030003 in user32 (+0x3) (0x01109fff)
  2 0x05000000 (0x0315eb00)
  3 0x00000000 (0x00000000)
0x7e030003: addb        %al,0x0(%ecx)
Modules:
Module  Address                 Debug info      Name (95 modules)
PE      400000-1631000  Deferred        dungeonsiege2
PE      4d4f0000-4d548000       Deferred        winhttp
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cf28000-7cf3d000       Deferred        midimap<elf>
  \-PE  7cf30000-7cf3d000       \               midimap
ELF     7cf3d000-7cf63000       Deferred        msacm32<elf>
  \-PE  7cf40000-7cf63000       \               msacm32
ELF     7cf63000-7cf7b000       Deferred        msacm32<elf>
  \-PE  7cf70000-7cf7b000       \               msacm32
ELF     7cf7b000-7cfb7000       Deferred        wineoss<elf>
  \-PE  7cf80000-7cfb7000       \               wineoss
ELF     7d239000-7d26b000       Deferred        uxtheme<elf>
  \-PE  7d240000-7d26b000       \               uxtheme
ELF     7d26d000-7d272000       Deferred        libxfixes.so.3
ELF     7d272000-7d27b000       Deferred        libxcursor.so.1
ELF     7d27b000-7d281000       Deferred        libxrandr.so.2
ELF     7d281000-7d289000       Deferred        libxrender.so.1
ELF     7d289000-7d28c000       Deferred        libxinerama.so.1
ELF     7d7b2000-7d840000       Deferred        winex11<elf>
  \-PE  7d7c0000-7d840000       \               winex11
ELF     7d8a6000-7d8c6000       Deferred        libexpat.so.1
ELF     7d8c6000-7d8f1000       Deferred        libfontconfig.so.1
ELF     7d8f1000-7d905000       Deferred        libz.so.1
ELF     7d905000-7d970000       Deferred        libfreetype.so.6
ELF     7d970000-7d99d000       Deferred        ws2_32<elf>
  \-PE  7d980000-7d99d000       \               ws2_32
ELF     7d99d000-7d9b7000       Deferred        wsock32<elf>
  \-PE  7d9a0000-7d9b7000       \               wsock32
ELF     7d9b7000-7da06000       Deferred        crypt32<elf>
  \-PE  7d9c0000-7da06000       \               crypt32
ELF     7da06000-7da24000       Deferred        wintrust<elf>
  \-PE  7da10000-7da24000       \               wintrust
ELF     7da24000-7dab3000       Deferred        winmm<elf>
  \-PE  7da30000-7dab3000       \               winmm
ELF     7dab3000-7db1a000       Deferred        msvcrt<elf>
  \-PE  7dac0000-7db1a000       \               msvcrt
ELF     7db1a000-7db2e000       Deferred        lz32<elf>
  \-PE  7db20000-7db2e000       \               lz32
ELF     7db2e000-7db47000       Deferred        version<elf>
  \-PE  7db30000-7db47000       \               version
ELF     7db47000-7dc03000       Deferred        comctl32<elf>
  \-PE  7db50000-7dc03000       \               comctl32
ELF     7dc03000-7dc5c000       Deferred        shlwapi<elf>
  \-PE  7dc10000-7dc5c000       \               shlwapi
ELF     7dc5c000-7dd51000       Deferred        shell32<elf>
  \-PE  7dc70000-7dd51000       \               shell32
ELF     7dd51000-7dd6a000       Deferred        rasapi32<elf>
  \-PE  7dd60000-7dd6a000       \               rasapi32
ELF     7dd6a000-7de05000       Deferred        oleaut32<elf>
  \-PE  7dd80000-7de05000       \               oleaut32
ELF     7de05000-7de18000       Deferred        libresolv.so.2
ELF     7de27000-7de45000       Deferred        iphlpapi<elf>
  \-PE  7de30000-7de45000       \               iphlpapi
ELF     7de45000-7de9a000       Deferred        rpcrt4<elf>
  \-PE  7de50000-7de9a000       \               rpcrt4
ELF     7de9a000-7df34000       Deferred        ole32<elf>
  \-PE  7deb0000-7df34000       \               ole32
ELF     7df34000-7df51000       Deferred        imm32<elf>
  \-PE  7df40000-7df51000       \               imm32
ELF     7df51000-7e00e000       Deferred        gdi32<elf>
  \-PE  7df70000-7e00e000       \               gdi32
ELF     7e00e000-7e14a000       Export          user32<elf>
  \-PE  7e030000-7e14a000       \               user32
ELF     7e1ad000-7e1b9000       Deferred        libgcc_s.so.1
ELF     7e2b2000-7e2b4000       Deferred        libnvidia-tls.so.1
ELF     7e2b4000-7eb3a000       Deferred        libglcore.so.1
ELF     7eb3a000-7eb3f000       Deferred        libxdmcp.so.6
ELF     7eb3f000-7ebbf000       Deferred        libglu.so.1
ELF     7ebbf000-7ec4b000       Deferred        libgl.so.1
ELF     7ec4b000-7ed3c000       Deferred        libx11.so.6
ELF     7ed3c000-7ed4a000       Deferred        libxext.so.6
ELF     7ed4a000-7ed62000       Deferred        libice.so.6
ELF     7ed62000-7ed6b000       Deferred        libsm.so.6
ELF     7ed6b000-7ee25000       Deferred        wined3d<elf>
  \-PE  7ed80000-7ee25000       \               wined3d
ELF     7ee25000-7ee50000       Deferred        d3d9<elf>
  \-PE  7ee30000-7ee50000       \               d3d9
ELF     7ee50000-7ee96000       Deferred        advapi32<elf>
  \-PE  7ee60000-7ee96000       \               advapi32
ELF     7efa8000-7efb3000       Deferred        libnss_files.so.2
ELF     7efb3000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7eff1000       Deferred        libm.so.6
ELF     7eff1000-7eff6000       Deferred        libxxf86vm.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d21000-b7d24000       Deferred        libxau.so.6
ELF     b7d26000-b7d2f000       Deferred        libnss_compat.so.2
ELF     b7d30000-b7d34000       Deferred        libdl.so.2
ELF     b7d34000-b7e75000       Deferred        libc.so.6
ELF     b7e76000-b7e8d000       Deferred        libpthread.so.0
ELF     b7e9c000-b7fad000       Deferred        libwine.so.1
ELF     b7faf000-b7fca000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000019 
        0000001d    0
        0000001a    0
0000000b 
        00000016    0
        00000012    0
        00000011    0
        00000010    0
        0000000c    0
00000008 (D) C:\Program Files\Microsoft Games\Dungeon Siege 2\DungeonSiege2.exe
        00000015    0
        00000014    0
        00000013    0
        0000000f    0
        00000009    0 <==
memorydump@memorydump-desktop:~/.wine/drive_c/Program Files/Microsoft Games/Dungeon Siege 2$ 


```
now the MFC42.dll is in both my system and system32 in wine as I needed to put it there in order to be able to install the game in the fist place, so I'm totally out of ideas

---

### Post by Memory.Dump on 2007-06-02
ok, it was actually the version of MFC I was using, I installed a post 6.X version and it worked

---

### Post by cisforcojo on 2007-06-03
Haha thought someone else should write in this thread. Glad you solved it yourself

---

### Post by Memory.Dump on 2007-06-03
ok so the game launches now but I'm getting really weird errors, I've tried running with -opengl and -windowed and w/o each option

in full screen mode, I just get a black screen and a cursor then eventually the cursor disapears

in windowed mode it loads up but it won't accept kb input and my mouse for some reason is constantly trying to scroll up, I had to alt+f4 to close it because everytime I dragged the mouse down it shot back up, I did however get vid

didn't seem to be any sound either but I'm not sure has I didn't get passed teh menu...any ideas why these extremely strange errors are happening? its not even consitant between windowed and full screen mode

---

### Post by Memory.Dump on 2007-06-03
does anybody have any clues as to this strange behavior?

---

### Post by Memory.Dump on 2007-06-03
I've been far and wide on the net and I can't find anybody who has this error, I have a logitech wireless mouse, it seems to operate it will move and click but it seems to be constantly set to go up when I not moving it in windowed mode, when I run in full screen mode I just get a black screen

---

### Post by Memory.Dump on 2007-06-04
ok, last attempt at some assistance then I guess I'll just have to give up and use it in windows or something, blah

---

### Post by Josey on 2007-06-04
The lack of help might have something to do with the publisher of DS2.

Just a guess.  :)

---

### Post by cutterjohn on 2007-06-05
> **Memory.Dump said:**
> ok, last attempt at some assistance then I guess I'll just have to give up and use it in windows or something, blahI just did a drag and drop install from my windows installation, in my case.  The game DOES work under wine, although it MAY we looking for a d3dx9_xx.dll, but I already had _27 installed as I use Oblivious as a test app for wine.

In any event, without monkeying with the mfcxx.dll the game worked in wine for me, although alot of texture in wine just don't seem to render in 0.9.37, along with a bunch of animation problems.  So, I decided to try Cedega 6.x, in which it works almost perfectly, although I wasn't able to load my save game that I used under wine, but it didn't have anything I cared about as I was just testing.

Beyond that, the game is OK for an ARPG, but nothing horribly great.  Very linear, with messed up save system as in yo get re-started in town with everything re-spawned, but it's just another game that I have that I can run under linux in some fashion, along with NWN, Devil Whiskey, Minions of Mirth, Fate, and the Valve Gold and Source engine games.

NWN & Devil Whiskey I use the native linux versions.

Oblivious, if you really want to play it, works slight better in Cedega 6.x, but wine 0.9.38 seems to have fixed the effect channel sound static problem, and improved the SM3 shader effect performance.

DSII: Cedega 6.x

Fate: Cedega 6.x, unless you want to manually monkey around getting in running under wine.  )EXTREMEMLY simplistic ARPG)

Minions of Mirth:  works in either, but I usually run it under wine.  see Prairiegames.com, works perfectly, but if you can't update look in the wine thread in their general forum.

Valve games:  seem to work just as well in either, so I use plain wine again

Go look up appdb.winehq.org (I think, but may be .net or .com) for more info on various games, apps, and related workarounds or for info that they just don't work yet, and there is [http://cedegawiki.sweetleafstudios.com/wiki/Main_Page](http://cedegawiki.sweetleafstudios.com/wiki/Main_Page) for Cedega apps.  Transgaming also has a forum, but it's not very heavily trafficed, but you'd likely get some help.  Wine appears to only have a mailing list, but there may be some independent forums somewhere that I overlooked.

---

