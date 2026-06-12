---
title: "Oblivion Under Linux Ubuntu/Mpeis"
date: 2007-04-09
forum: Gaming &amp; Leisure
---

### Post by Kiwi-Hawk on 2007-04-09
Hi

I have a structure under my user name Kiwi-Hawk as in:
Kiwi-Hawk/Desktop
Kiwi-Hawk/Documents
Kiwi-Hawk/ Music
Kiwi-Hawk/My Pictures
Kiwi-Hawk/My Videos

The ini is now found

Is there away to track whats happening,. I get to start screen and can set screen size
etc; I get a direct HAL video driver ( not sure this is right ) but I press play I get the window close and a new one open and that close's

I have a 3.2gig Intel Aus p5w dh board with 2gig ram and a wee EN7950GT 512 ram nvidia video card.

I run Mepis 6.5 final and wine 0.9.9 OUbuntu2 all update done.

I should mention too the sound work but as set itself on oss sound in wine cfg.
I did not think this would be a problem as it works

this is a screen dump from running off of this script:

--------------------------------------------------------------------
#!/bin/sh
# This script disables all the text output for Wine
# debugging for improved performace.
export WINEDEBUG=fixme-all,err-all,warn-all,trace-all
OBLIVION_DIR=/opt/games/Oblivion
cd ${OBLIVION_DIR}
wine OblivionLauncher.exe
----------------------------------------------------------------------
----------------------------------------------------------------------
Kiwi-Hawk@2[~]$ ./Oblivion
Kiwi-Hawk@2[~]$ wine: Unhandled page fault on read access to 0x000002a0 at address 0x7ee0a466
(thread 0012), starting debugger...
WineDbg starting on pid 0xd
Unhandled exception: page fault on read access to 0x000002a0 in 32-bit code (0x7ee0a466).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:1137 GS:0033
EIP:7ee0a466 ESP:6beea9c4 EBP:6beeaa60 EFLAGS:00210206( - 00 - RIP1)
EAX:00000000 EBX:6bddaaf4 ECX:6bdd90a0 EDX:7ef8f224
ESI:ff000000 EDI:00000001
Stack dump:
0x6beea9c4: 6bd79e68 00000c11 00000000 00000400
0x6beea9d4: 00000500 00000500 000002cf 00000400
0x6beea9e4: 00000400 00000000 010d6677 00000000
0x6beea9f4: 00000400 00000058 6bddaaf4 5c9b3938
0x6beeaa04: 00000000 6beeaa48 00e1c878 00000000
0x6beeaa14: 6beeaa54 7ffbe3ac 5c9b3938 00000000
0226: sel=1137 base=7da36000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ee0a466 glTexImage2D+0x406 in libgl.so.1 (0x7ee0a466)
2 0x7c6edab5 IDirect3DDevice9Impl_Clear+0x85 in d3d9 (0x7c6edab5)
fixme:dbghelp:sffip_cb NIY on 'E:\NetworkProjectsPC\OblivionSE\Oblivion\Game\Oblivion.pdb'
3 0x00410727 in oblivion (+0x10727) (0x00410727)
4 0x7fd490c0 (0x7fd490c0)
5 0x000002d0 (0x000002d0)
6 0x00000000 (0x00000000)
0x7ee0a466 glTexImage2D+0x406 in libgl.so.1: jmp *0x2a0(%eax)
Modules:
Module Address Debug info Name (93 modules)
PE 0x00400000-00baf000 Export oblivion
PE 0x18000000-18068000 Deferred binkw32
ELF 0x6bd49000-6bddc000 Deferred wined3d<elf>
\-PE 0x6bd60000-6bddc000 \ wined3d
ELF 0x7bf00000-7bf03000 Deferred <wine-loader>
ELF 0x7bf8a000-7c000000 Deferred libglu.so.1
ELF 0x7c6d2000-7c700000 Export d3d9<elf>
\-PE 0x7c6e0000-7c700000 \ d3d9
ELF 0x7da3b000-7da50000 Deferred midimap<elf>
\-PE 0x7da40000-7da50000 \ midimap
ELF 0x7db70000-7db96000 Deferred msacm32<elf>
\-PE 0x7db80000-7db96000 \ msacm32
ELF 0x7db96000-7dbae000 Deferred msacm<elf>
\-PE 0x7dba0000-7dbae000 \ msacm
ELF 0x7dbae000-7dbf2000 Deferred wineoss<elf>
\-PE 0x7dbc0000-7dbf2000 \ wineoss
ELF 0x7dbf2000-7dc23000 Deferred uxtheme<elf>
\-PE 0x7dc00000-7dc23000 \ uxtheme
ELF 0x7e3ed000-7e3f1000 Deferred libxfixes.so.3
ELF 0x7e3f1000-7e40d000 Deferred imm32<elf>
\-PE 0x7e400000-7e40d000 \ imm32
ELF 0x7e40d000-7ed7f000 Deferred libglcore.so.1
ELF 0x7ed7f000-7ee13000 Export libgl.so.1
ELF 0x7ee13000-7eef9000 Deferred libx11.so.6
ELF 0x7eef9000-7ef11000 Deferred libice.so.6
ELF 0x7ef11000-7ef94000 Deferred winex11<elf>
\-PE 0x7ef20000-7ef94000 \ winex11
ELF 0x7ef94000-7efb3000 Deferred libexpat.so.1
ELF 0x7efb3000-7efe1000 Deferred libfontconfig.so.1
ELF 0x7efe1000-7eff5000 Deferred libz.so.1
ELF 0x7eff5000-7f05f000 Deferred libfreetype.so.6
ELF 0x7f05f000-7f0c0000 Deferred msvcrt<elf>
\-PE 0x7f070000-7f0c0000 \ msvcrt
PE 0x7f0c0000-7f30f000 Deferred d3dx9_27
ELF 0x7f310000-7f33b000 Deferred ws2_32<elf>
\-PE 0x7f320000-7f33b000 \ ws2_32
ELF 0x7f33b000-7f355000 Deferred wsock32<elf>
\-PE 0x7f340000-7f355000 \ wsock32
ELF 0x7f355000-7f369000 Deferred lz32<elf>
\-PE 0x7f360000-7f369000 \ lz32
ELF 0x7f369000-7f382000 Deferred version<elf>
\-PE 0x7f370000-7f382000 \ version
ELF 0x7f382000-7f3dd000 Deferred shlwapi<elf>
\-PE 0x7f3a0000-7f3dd000 \ shlwapi
ELF 0x7f3dd000-7f4a9000 Deferred shell32<elf>
\-PE 0x7f3f0000-7f4a9000 \ shell32
ELF 0x7f4a9000-7f4fb000 Deferred dsound<elf>
\-PE 0x7f4c0000-7f4fb000 \ dsound
ELF 0x7f4fb000-7f583000 Deferred winmm<elf>
\-PE 0x7f510000-7f583000 \ winmm
ELF 0x7f583000-7f5a2000 Deferred iphlpapi<elf>
\-PE 0x7f590000-7f5a2000 \ iphlpapi
ELF 0x7f5a2000-7f5eb000 Deferred rpcrt4<elf>
\-PE 0x7f5b0000-7f5eb000 \ rpcrt4
ELF 0x7f5eb000-7f67c000 Deferred ole32<elf>
\-PE 0x7f600000-7f67c000 \ ole32
ELF 0x7f67c000-7f6bd000 Deferred dinput<elf>
\-PE 0x7f690000-7f6bd000 \ dinput
ELF 0x7f6bd000-7f6d1000 Deferred dinput8<elf>
\-PE 0x7f6c0000-7f6d1000 \ dinput8
ELF 0x7f6d1000-7f711000 Deferred advapi32<elf>
\-PE 0x7f6e0000-7f711000 \ advapi32
ELF 0x7f711000-7f71b000 Deferred libgcc_s.so.1
ELF 0x7f71d000-7f725000 Deferred libxrender.so.1
ELF 0x7f725000-7f72e000 Deferred libxcursor.so.1
ELF 0x7f803000-7f8b4000 Deferred gdi32<elf>
\-PE 0x7f820000-7f8b4000 \ gdi32
ELF 0x7f8b4000-7f9e0000 Deferred user32<elf>
\-PE 0x7f8d0000-7f9e0000 \ user32
ELF 0x7f9e0000-7faa0000 Deferred comctl32<elf>
\-PE 0x7f9f0000-7faa0000 \ comctl32
ELF 0x7fbde000-7fce0000 Deferred kernel32<elf>
\-PE 0x7fc00000-7fce0000 \ kernel32
ELF 0x7fce1000-7fce3000 Deferred iso8859-1.so
ELF 0x7fce3000-7fcf0000 Deferred libxext.so.6
ELF 0x7fe01000-7fe06000 Deferred libxxf86vm.so.1
ELF 0x7fe06000-7fe10000 Deferred libnss_files.so.2
ELF 0x7fe10000-7fe19000 Deferred libnss_nis.so.2
ELF 0x7fe19000-7fe2e000 Deferred libnsl.so.1
ELF 0x7fe2e000-7fe37000 Deferred libnss_compat.so.2
ELF 0x7fe3b000-7fe40000 Deferred libxxf86dga.so.1
ELF 0x7fe42000-7fe4a000 Deferred libsm.so.6
ELF 0x7fe4c000-7fe4e000 Deferred libnvidia-tls.so.1
ELF 0x7fe4e000-7fe70000 Deferred libm.so.6
ELF 0x7fe70000-7ff66000 Deferred libwine_unicode.so.1
ELF 0x7ff66000-7ffe0000 Deferred ntdll<elf>
\-PE 0x7ff80000-7ffe0000 \ ntdll
ELF 0xb7e6d000-b7e70000 Deferred libdl.so.2
ELF 0xb7e70000-b7f9f000 Deferred libc.so.6
ELF 0xb7f9f000-b7fb0000 Deferred libpthread.so.0
ELF 0xb7fb1000-b7fb4000 Deferred libxau.so.6
ELF 0xb7fc4000-b7fde000 Deferred libwine.so.1
ELF 0xb7fe1000-b7ff7000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
0000000d (D) Z:\opt\games\Oblivion\Oblivion.exe
00000012 1 <==
0000000f 0
0000000e 0
Kiwi-Hawk@2[~]$
--------------------------------------------------------------------------------------
All wine cfg is according the thread here on the forum by Mongoose

thanks to his help so far 


cheers
Kiwi-Hawk

---

### Post by H3g3m0n on 2007-04-10
From memory you need a patched version of Oblivion with the newer shaders removed [http://www.oldblivion.com/](http://www.oldblivion.com/)

2ndly you need Cedega not Wine.

---

### Post by hikaricore on 2007-04-10
Original Post:
> 
You **can** run Oblivion with wine.... stop lying.

There's even a thread around here about it somewhere if you search for it.

My update on this post:

It has come to my attention that some may have taken my post which I've quoted
above in a way other than my intent.

At the time I posted here earlier today, this post:
[http://ubuntuforums.org/showthread.php?t=349764](http://ubuntuforums.org/showthread.php?t=349764)

About howto run Oblivion in wine, was located exactly 5 Posts below this thread
when looking at the gaming and leisure section of the fourms.

So it's not like I was saying "stfu and lrn2search"... i was actually just making a joke and
noting to myself how funny it was there was a thread covering the topic right below this post.

My semirash response was a knee-jerk reaction to:

> **H3g3m0n said:**
> 
2ndly you need Cedega not Wine.

Now personally I know Oblivion can be run under Wine.

It's not the greatest experience you'll ever have and it loves to crash
under certain circumstances, but it is playable and has been played
by several people.

I'm just getting a little tired of the Cedega vs. Wine battles on forums lately.

Maybe I havn't been the most open minded in the topic, but in my opinion,
if you need Cedega then please by all means, use it.  However just because
Cedega works for you and your game, doesn't mean it will work for everyone.

All and all it doesn't matter.  I enjoy using WINE to make my various windows 
based software titles work, and someone else enjoys using Cedega.  But knowing
that some software works in both and telling everyone that one is better than
the other without backing it up in any way, makes us all go crazy on each other.
It makes me act like a smeghead, and starts useless rants like this one.

So all I'm asking here is please if you're going to tell someone what they need
to make something work, back it up with some info and save all of us from ourselves.

I'm terribly sorry if I offended anyone, there's just so much I can take.

---

### Post by hikaricore on 2007-04-10
^ modified my post heavily

---

