---
title: "Warcraft III FT: Errors in Wine"
date: 2005-10-20
forum: Gaming &amp; Leisure
---

### Post by jdmpike on 2005-10-20
Hello fellow Ubuntu-ers,

I have desparately wanted to play Warcraft III: FT since installing Horay. There were issues with my kernel not being able install FT. Now those are fixed, I have it installed from original CDs, downloaded the no cd patch (thanks Amadeus), and am trying to run it with the following command:

```
jordan@jdmlaptop:~/.wine/drive_c/Warcraft3$ wine war3.exe -- -opengl -window
wine: Call from 0x41180b to unimplemented function storm.dll.570, aborting
wine: Unhandled exception (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: unimplemented function storm.dll.570 called in 32-bit code (0x7bebfa4c).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7bebfa4c ESP:7fb4fc60 EBP:7fb4fcb8 EFLAGS:00000216(   - 00      - IAP1)
 EAX:0000023a EBX:7bef51d4 ECX:7fb4fcd4 EDX:7befd55c
 ESI:7fb4fc60 EDI:00495020
Stack dump:
0x7fb4fc60:  80000100 00000001 00000000 0041180b
0x7fb4fc70:  00000002 0044ce3e 0000023a 7fcd8c2b
0x7fb4fc80:  7fd90000 00000000 7fdf3810 7fd38ff4
0x7fb4fc90:  7fb4fcb4 7fcec9d6 7fd90000 00000000
0x7fb4fca0:  7fdf3810 00000104 7fcebf80 7fb4fcd4
0x7fb4fcb0:  7fcebf80 7fb4fcd4 7fb4fdd8 0041180b
0200: sel=1007 base=b7ee8000 limit=00001f97 32-bit rw-
Backtrace:
=>1 0x7bebfa4c call_dll_entry_point+0x7c in ntdll (0x7fb4fcb8)
  2 0x0041180b FI+0x80b in war3 (0x7fb4fdd8)
  3 0x00401219 in war3 (+0x1219) (0x7fb4fe84)
  4 0x00401d68 SVW\uffff\uffff3\uffff\uffff+0xa28 in war3 (0x7fb4ff20)
  5 0x7fcf8e63 in kernel32 (+0x48e63) (0x7fb4fff4)
  6 0xb7ecbc45 wine_switch_to_stack+0x11 in libwine.so.1 (0x00000000)
0x7bebfa4c call_dll_entry_point+0x7c in ntdll: subl     $4,%esp
Modules:
Module  Address                 Debug info      Name (105 modules)
PE      0x00400000-0057b740     Export          war3
PE      0x15000000-15064000     Deferred        storm
PE      0x21100000-2115f000     Deferred        mss32
PE      0x60000000-6005d000     Deferred        ijl15
PE      0x6f000000-6f878000     Deferred        game
ELF     0x7be87000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7d6fc000-7d772000     Deferred        libglu.so.1
ELF     0x7d772000-7d786000     Deferred        avicap32<elf>
  \-PE  0x7d780000-7d786000     \               avicap32
ELF     0x7d786000-7d7ac000     Deferred        devenum<elf>
  \-PE  0x7d7a0000-7d7ac000     \               devenum
ELF     0x7d7e4000-7d87b000     Deferred        opengl32<elf>
  \-PE  0x7d820000-7d87b000     \               opengl32
ELF     0x7d87b000-7d910000     Deferred        oleaut32<elf>
  \-PE  0x7d8a0000-7d910000     \               oleaut32
ELF     0x7dbbb000-7dbd0000     Deferred        midimap<elf>
  \-PE  0x7dbc0000-7dbd0000     \               midimap
ELF     0x7dce6000-7dd09000     Deferred        msacm32<elf>
  \-PE  0x7dcf0000-7dd09000     \               msacm32
ELF     0x7dd09000-7dd22000     Deferred        msacm.drv<elf>
  \-PE  0x7dd10000-7dd22000     \               msacm.drv
ELF     0x7dd22000-7dd6e000     Deferred        libgcrypt.so.11
ELF     0x7dd6e000-7ddd0000     Deferred        libgnutls.so.11
ELF     0x7de35000-7de78000     Deferred        wineoss.drv<elf>
  \-PE  0x7de50000-7de78000     \               wineoss.drv
ELF     0x7de78000-7de88000     Deferred        libtasn1.so.2
ELF     0x7de88000-7dea5000     Deferred        libcups.so.2
ELF     0x7df2f000-7df33000     Deferred        libxfixes.so.3
ELF     0x7df33000-7df3c000     Deferred        libxcursor.so.1
ELF     0x7df3c000-7df58000     Deferred        ximcp.so.2
ELF     0x7df58000-7df60000     Deferred        libxrender.so.1
ELF     0x7df66000-7df6a000     Deferred        libgpg-error.so.0
ELF     0x7df6a000-7e6d3000     Deferred        libglcore.so.1
ELF     0x7e6d3000-7e752000     Deferred        libgl.so.1
ELF     0x7e752000-7e812000     Deferred        libx11.so.6
ELF     0x7e812000-7e82b000     Deferred        libice.so.6
ELF     0x7e82b000-7e8ad000     Deferred        winex11.drv<elf>
  \-PE  0x7e840000-7e8ad000     \               winex11.drv
ELF     0x7e8ad000-7e8cc000     Deferred        libexpat.so.1
ELF     0x7e8cc000-7e8fa000     Deferred        libfontconfig.so.1
ELF     0x7e8fa000-7e90e000     Deferred        libz.so.1
ELF     0x7e90e000-7e978000     Deferred        libfreetype.so.6
ELF     0x7e978000-7e997000     Deferred        mpr<elf>
  \-PE  0x7e980000-7e997000     \               mpr
ELF     0x7e997000-7e9db000     Deferred        wininet<elf>
  \-PE  0x7e9a0000-7e9db000     \               wininet
ELF     0x7e9db000-7e9f8000     Deferred        imm32<elf>
  \-PE  0x7e9e0000-7e9f8000     \               imm32
ELF     0x7e9f8000-7ea23000     Deferred        ws2_32<elf>
  \-PE  0x7ea00000-7ea23000     \               ws2_32
ELF     0x7ea23000-7ea40000     Deferred        wsock32<elf>
  \-PE  0x7ea30000-7ea40000     \               wsock32
ELF     0x7ea53000-7ea57000     Deferred        libxdmcp.so.6
ELF     0x7ea57000-7ea6b000     Deferred        lz32<elf>
  \-PE  0x7ea60000-7ea6b000     \               lz32
ELF     0x7ea6b000-7ea86000     Deferred        version<elf>
  \-PE  0x7ea70000-7ea86000     \               version
ELF     0x7ea86000-7eae9000     Deferred        msvcrt<elf>
  \-PE  0x7eaa0000-7eae9000     \               msvcrt
ELF     0x7eae9000-7eb69000     Deferred        winmm<elf>
  \-PE  0x7eb00000-7eb69000     \               winmm
ELF     0x7eb69000-7eb94000     Deferred        winspool.drv<elf>
  \-PE  0x7eb70000-7eb94000     \               winspool.drv
ELF     0x7eb94000-7ec53000     Deferred        comctl32<elf>
  \-PE  0x7eba0000-7ec53000     \               comctl32
ELF     0x7ec53000-7ec74000     Deferred        iphlpapi<elf>
  \-PE  0x7ec60000-7ec74000     \               iphlpapi
ELF     0x7ec74000-7ecbe000     Deferred        rpcrt4<elf>
  \-PE  0x7ec90000-7ecbe000     \               rpcrt4
ELF     0x7ecbe000-7ed48000     Deferred        ole32<elf>
  \-PE  0x7ece0000-7ed48000     \               ole32
ELF     0x7ed48000-7eda4000     Deferred        shlwapi<elf>
  \-PE  0x7ed60000-7eda4000     \               shlwapi
ELF     0x7eda4000-7ee6a000     Deferred        shell32<elf>
  \-PE  0x7edc0000-7ee6a000     \               shell32
ELF     0x7ee6a000-7eefa000     Deferred        comdlg32<elf>
  \-PE  0x7ee80000-7eefa000     \               comdlg32
ELF     0x7eefa000-7ef3b000     Deferred        advapi32<elf>
  \-PE  0x7ef10000-7ef3b000     \               advapi32
ELF     0x7f021000-7f924000     Deferred        gdi32<elf>
  \-PE  0x7f070000-7f924000     \               gdi32
ELF     0x7f924000-7fa50000     Deferred        user32<elf>
  \-PE  0x7f950000-7fa50000     \               user32
ELF     0x7fb53000-7fb60000     Deferred        libxext.so.6
ELF     0x7fc85000-7fd90000     Export          kernel32<elf>
  \-PE  0x7fcb0000-7fd90000     \               kernel32
ELF     0x7fea0000-7fea3000     Deferred        libxau.so.6
ELF     0x7fea3000-7feae000     Deferred        libgcc_s.so.1
ELF     0x7feae000-7feb8000     Deferred        libnss_files.so.2
ELF     0x7feb8000-7fec1000     Deferred        libnss_nis.so.2
ELF     0x7fec1000-7fed6000     Deferred        libnsl.so.1
ELF     0x7fed6000-7fedf000     Deferred        libnss_compat.so.2
ELF     0x7fee2000-7fee4000     Deferred        xlcutf8load.so.2
ELF     0x7fee4000-7fee7000     Deferred        libxrandr.so.2
ELF     0x7fee9000-7ff0b000     Deferred        libm.so.6
ELF     0x7ff0b000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7d80000-b7d82000     Deferred        libnvidia-tls.so.1
ELF     0xb7d83000-b7d86000     Deferred        libdl.so.2
ELF     0xb7d86000-b7eb4000     Deferred        libc.so.6
ELF     0xb7eb5000-b7ec7000     Deferred        libpthread.so.0
ELF     0xb7ec7000-b7ee0000     Export          libwine.so.1
ELF     0xb7ee1000-b7ee8000     Deferred        libsm.so.6
ELF     0xb7eed000-b7f03000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Warcraft3\war3.exe
        00000009    0 <==
WineDbg terminated on pid 0x8

```

Any thoughts or suggestions from you masters-of-linux out there would be great.

I know all of you are up to the challenge of helping me get my geek on with some WAR3!!!

Peace, love, and Ubuntu,

JDMPIKE

---

### Post by claydoh on 2005-10-20
I am not sure how difficult it would be to install this game in Wine, but it definitely works in cedega. 

[There is a how-to for Hoary here]("http://ubuntuforums.org/showthread.php?p=284312#post284312")

[Frank's Corner has a section about the game using Wine]("http://frankscorner.org/index.php?p=warcraft3") It is relative to an old version of wine, so I don't know if it still works in newer versions, and 3d acceleration must be enabled for it to run as well iirc.

That site is a great place for wine related how-tos

---

### Post by jdmpike on 2005-10-20
I used the tutorial from Frank's Corner to get this far... I am going to google the storm.dll error it is balking on and I will get back to you everyone!

Please post if you have mad skills getting warcraft to work!

JDM

---

### Post by maegget on 2005-10-20
Hi, I managed to install Warcraft III and The Frozen Throne last night on Breezy (I had installation errors under Hoary) but it won't load up in wine as it asks for the CD (which is in the drive). I was wondering which version of wine are you using and where did you find the "nocd" files?

I would like to play it with the original .exe on battle.net if at all possible and have heard that this can be possible if you compile the latest version of Wine from CVS (which handles the SecuRom protection on the CD). But if I can just get it running at first (with a nocd exe) that would be a good first start!

---

### Post by jdmpike on 2005-10-20
I downloaded the latest crack from [www.megagames.com](www.megagames.com) - I don't really like using the crack, I may try your suggestion and build wine from CVS.

This is very frustrating and I wish some ubuntu expert would just swoop in and help us get our games going!

-JDM

---

### Post by seethru on 2005-10-20
wine doesn't support cd protection, only cedega does.
infact, and someone can correct me if I'm wrong, not even the cvs of cedega supports cd protection. Thats part of the reason you have to pay for cedega.

---

### Post by jdmpike on 2005-10-22
From the winehq site...

Copy Protection & CD-ROM Access
----------

Warcraft III uses SecuRom protection. As of May or June 2003, Wine was patched -- how, I don't exactly know -- to allow SecuRom games like Warcraft III to work. The requirements for correct functionality follows:

   1. Use wine version 20050830 or newer.
   2. Setting the Wine version to an "NT" version or autodetect.
   3. Have correct read access to your cdrom device node.
   4. Do *NOT* use kernel 2.6.9 or 2.6.10.
   5. Do not use a Wine build compiled with GCC 4.0

So I am using wine 20050930, set my wine version to "Windows 2000", chmod /dev/hdb a+r, kernel is 2.6.12, and compiled wine with gcc-3.4.

I don't know what else I am supposed to do... very frustrating...

I really don't want to play the game with a cracked app - why can blizzard be cool and just release things native to linux, those freaking jerks!!!

Has anyone got this to work? Please share if so!!!

Thanks,

JDM

---

### Post by jdmpike on 2005-10-22
So I have tried recompiling wine with the CC in configure set to gcc-3.4 and gcc-3.3 and neither have worked... can you even believe that...

I would think that it is my drive if it wasn't for the fact that I was playing this awesome game on a much less awesome OS not more than a few weeks ago...

Please ubuntu masters, come to my aide!

-JDM

---

### Post by seethru on 2005-10-22
wish I could suggest more, unfortunately I use cedega for gaming, less of a headache.

---

### Post by RedTziab on 2005-12-15
Guys plz help me. I need to play warcraft 3 FT without cd. Can u tell me where to dl a crack for no cd ? thx :)

---

### Post by polpak on 2005-12-15
[QUOTE=RedTziab]Guys plz help me. I need to play warcraft 3 FT without cd. Can u tell me where to dl a crack for no cd ? thx :)[/QUOTE]

You don't need a crack. The CD protection works fine under wine. All you have to do is run winecfg and go to the drives tab. You have to make sure that your CD rom drive is specified as being of type "CD rom" not just a regular drive.

Works a treat on my system.

I'm also using the latest wine release from winehq.org  A howto for installing the wine repos under ubuntu is available at [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

So lets hear no more of this FUD about needing to use cedega to play CD protected games. (At least not Secure ROM. I don't know what other sorts of CD protections are out there that don't have a driver in Wine)

---

### Post by Minotaurus on 2006-02-09
Hi!

I am using the Gentoo Linux and had the same problems with storm.dll, but i managed to handle it. Well, i think there was a problem with eurobattle patching. I used the this patch (from [www.eurobattle.net](www.eurobattle.net)) BEFORE i patched the game to 1.20b version. So i think the file war3.exe was patched to 1.20b, but storm.dll remained the old version. So i suggest that you download the official patch from blizzard and then use your nocd patch.

And on the latest version campaigns also work (if i rename Movies to Moviesa) :D, maybe i only lag a little bit more and have some problems with sound.

Hm, there was also a problem when i upgraded wine - he couldnt find cdkey. But reinstall helped.

---

