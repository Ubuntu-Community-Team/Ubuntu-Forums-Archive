---
title: "Open Beta Client of Enemy Territory: Quake Wars"
date: 2007-06-22
forum: Gaming &amp; Leisure
---

### Post by ubu-for on 2007-06-22
You can download [here](http://www.gameupdates.org/details.php?id=1163) the Open Beta Client of Enemy Territory: Quake Wars via BitTorrent.

Have fun!

---

### Post by ArieT on 2007-06-22
Windows version ....

---

### Post by Rafty on 2007-06-22
possible to get it running on linux?

---

### Post by MonkeyBoy on 2007-06-22
Some guy on the Gentoo forums seems to think it works under wine.

I tried to apply for a keycode but it asked about my hardware and then refused me a key!  The beta test  hardware requirements are quite demanding so I lied about some stuff anyway but it still wouldn't give me a code.

I would be interested to know if anyone gets it running under wine though.  

Hopefully the demo won't be too long now.  I want to see if I need a new graphics card to run the game.  :(

---

### Post by Rafty on 2007-06-22
yep, i didn't get a key too  :(
this procedure is anoying...

---

### Post by ubu-for on 2007-06-22
I've installed the game without a problem and without key, but every time I try to start Quake Wars, I get the runtime error "R6034" from the "Microsft Visual C++ Runtime Library".

---

### Post by a12ctic on 2007-06-23
The beta is open to everyone now. Just fyi. Still no linux ports.

---

### Post by Mongoose on 2007-06-24
You need that msv*80 pak with the Microsoft.VC80.CRT.manifest:

<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<!-- Copyright © 1981-2001 Microsoft Corporation -->
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    <noInheritable/>
    <assemblyIdentity 
        type="win32" 
        name="Microsoft.VC80.CRT" 
        version="8.0.50608.0" 
        processorArchitecture="x86" 
        publicKeyToken="1fc8b3b9a1e18e3b"
    />
    <file name="msvcr80.dll"/>
    <file name="msvcp80.dll"/>
    <file name="msvcm80.dll"/>
</assembly>

You can place in the quake wars directory.  You also need to patch a workaround for the 32bpp depth bug.  If I was awake I might be more help...


Edit:

Ah, yes.  

Howto get wine git:
[http://wiki.winehq.org/GitWine](http://wiki.winehq.org/GitWine)

32bpp workaround patch:  ( if needed )
[http://bugs.winehq.org/show_bug.cgi?id=4278](http://bugs.winehq.org/show_bug.cgi?id=4278)

Edit 2.. ZZ.z.z.Z...

Edit wtsapi32.spec

+ @ stdcall WTSRegisterSessionNotification(long ptr long)

Edit wtsapi32.c
/************************************************************
 *                WTSRegisterSessionNotification  (WTSAPI32.@)
 */
BOOL WINAPI WTSRegisterSessionNotification(HWND hServer, DWORD SessionId)
{
    FIXME("Stub %p 0x%08x\n", hServer, SessionId); // quakewars hack
    return TRUE;
}

I might take a nap now...

---

### Post by ubu-for on 2007-06-24
> **Mongoose said:**
> You need that msv*80 pak with the Microsoft.VC80.CRT.manifest:

I've added the msvcr80.dll to "/.wine/drive_c/windows/system32" and "/.wine/drive_c/Programme/Enemy Territory Quake Wars Beta", but I still get the following error message.

```
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x1c57bac
err:module:LdrInitializeThunk "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Programme\\Enemy Territory Quake Wars Beta\\etqw.exe" failed, status c0000142
```

I've only found the msvcr80.dll and the msvcp80.dll on the web and Ubuntu doesn't find anything on the Windows partition.

> **Mongoose said:**
> You also need to patch a workaround for the 32bpp depth bug.  If I was awake I might be more help...

Please wake up. ;)

---

### Post by ubu-for on 2007-06-24
> **Rafty said:**
> possible to get it running on linux?

[Here](http://appdb.winehq.org/appview.php?iVersionId=8366) are the first HOWTOs.

---

### Post by Mongoose on 2007-06-24
It about melts my 6800 in a SFF case, and it's pretty choppy.  I'm sure tweaking would help, but it doesn't run as well as Oblivion in wine.  Can't wait for native builds, personally.

---

### Post by sharkcohen on 2007-06-24
It runs, but only for about a minute, and then wine crashes with a page fault error.

```

wine: Unhandled page fault on write access to 0x00000000 at address 0x521110 (thread 0009)
```

Also, no luck with sound yet.

---

### Post by Mongoose on 2007-06-24
You should use the native dlls as suggested on the wine app db site -- what I posted was a quick hack to avoid using as many native dlls.  Also I didn't mention the keyboard patch, but since I saw it on app db it's not worth mentioning here.

I was able to get in a game and shoot someone, but it was slow on my poor little GPU.  I think it's time I try to get a 8600 GTS now that BIOSTAR is making a 512MB model.

Edit:

Oh, looks like that 512MB model is using DDR2.  What a loser that is... I guess I'll have to roll a die for a 8600 GTS, 7900 GS or 7950 GT.  Sucks that the GTS has such a horrible memory bandwidth, but it's better in general than the 6800 GS.  Aside from the memory bandwidth being the same on reference cards anyway.  =)

---

### Post by MonkeyBoy on 2007-06-25
Dammitt!!!

They have stopped doing keys now!  I'm gonna have to wait for the public beta. 

I really need to see if I'm going to need a hardware upgrade for this game...

---

### Post by sharkcohen on 2007-06-25
> **Mongoose said:**
> You should use the native dlls as suggested on the wine app db site -- what I posted was a quick hack to avoid using as many native dlls.  Also I didn't mention the keyboard patch, but since I saw it on app db it's not worth mentioning here.

I was able to get in a game and shoot someone, but it was slow on my poor little GPU.  I think it's time I try to get a 8600 GTS now that BIOSTAR is making a 512MB model.

I am using the native dlls, I followed the instructions on the Wine site to the letter.  I didn't use anything from what you had posted.

---

### Post by B0rsuk on 2007-06-25
There's a new **sticky** on the official Public Beta forum. It reads:

[How to play ETQW public beta on Ubuntu 7.04](http://community.enemyterritory.com/forums/showthread.php?t=3134)

---

### Post by rejser on 2007-06-25
Quite good game, but not that different from old et. which is good.
But quite choppy even in win at the moment, event with powerfull. gpu. But it is a beta so should be expected. Of playing again.
Used the howto above to play it in ubuntu.

---

### Post by hikaricore on 2007-06-25
Incase you were all wondering there will more than likely be no linux beta: [http://www.linuxgames.com/news/feedback.php?identiferID=9261&action=flatview](http://www.linuxgames.com/news/feedback.php?identiferID=9261&action=flatview)
And right now they're just too darn busy to even bother with a native linux client at all.
But they're working on it, though they don't plan to include it on the DVD releases...

We're getting the long end of the broomstick again folks.

---

### Post by sharkcohen on 2007-06-25
> **B0rsuk said:**
> There's a new **sticky** on the official Public Beta forum. It reads:

[How to play ETQW public beta on Ubuntu 7.04](http://community.enemyterritory.com/forums/showthread.php?t=3134)

Heh, same steps as on WineHQ, just more verbose description.  Doesn't work well at all on my box, but I am running Dapper and 2.6.20, not Feisty (not sure if that matters, though).  Oh well, too entrenched in my current install to try a reinstall with Feisty.

---

### Post by racoq on 2007-06-25
> **hikaricore said:**
> 
We're getting the long end of the broomstick again folks.

Do not complain... at least they  are developing a native linux version...

Do complain about other game company's don't release a linux version at all..

---

### Post by sharkcohen on 2007-06-25
I might as well post the wine debug output, maybe someone can help here, I've never used wine before now.  I can connect to online servers and the game will run for about a minute before wine crashes and dumps this output.  Also, no sound.

```

sharkcohen@sharkdesk:~/.wine/drive_c/Program Files/id Software/Enemy Territory - QUAKE Wars Beta$ wine etqw.exe 
fixme:advapi:RegisterEventSourceW ((null),L"PDH"): stub
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x1c57bac
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:AnimateWindow partial stub
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x1c5ed70,0x00000000), stub!
fixme:win:AnimateWindow partial stub
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 40000025
fixme:dbghelp:SymInitializeW what to do ??
wine: Unhandled page fault on write access to 0x00000000 at address 0x521110 (thread 000d), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x00521110).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00521110 ESP:01c5c93c EBP:01c5ca88 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000001 EBX:7d6fb1e0 ECX:00000004 EDX:00000000
 ESI:01c5cb60 EDI:01c5cae0
Stack dump:
0x01c5c93c:  7d6edb82 ffffffff 7ffdc0c0 00000000
0x01c5c94c:  01c5cb34 00000004 00000000 42a61fe0
0x01c5c95c:  3f800000 40203fd7 c020bb66 42a61fe0
0x01c5c96c:  00000000 40c543c1 3fd5d410 429a2968
0x01c5c97c:  3f800000 40c543c1 3fd5d410 429a2968
0x01c5c98c:  00000000 40a8e16f 01c5cae0 01c5cb60
Backtrace:
=>1 0x00521110 in etqw (+0x121110) (0x01c5ca88)
  2 0x7d6eead1 StackWalk64+0x1ec(MachineType=0x14c, hProcess=0xffffffff, hThread=0xfffffffe, frame64=<register ESI not in topmost frame>, ctx=<register EAX not in topmost frame>, f_read_mem=0x5210e0, FunctionTableAccessRoutine=0x7d6f1e55, GetModuleBaseRoutine=0x7d6dee5c, f_xlat_adr=0x0) [/usr/src/wine-0.9.39/dlls/dbghelp/stack.c:547] in dbghelp (0x01c5cb88)
  3 0x005220db in etqw (+0x1220db) (0x01c5ea60)
  4 0x005225f9 in etqw (+0x1225f9) (0x7ee65d98)
  5 0x10ec8353 (0x56e58955)
  6 0x00000000 (0x00000000)
0x00521110: movl        %ecx,0x0(%edx)
Modules:
Module  Address                 Debug info      Name (126 modules)
PE        400000-  c4b000       Export          etqw
PE       24e0000- 2558000       Deferred        pbcl
PE       2910000- 2b1a000       Deferred        cgx86
PE       56b0000- 5f24000       Deferred        gamex86
PE       7690000- 7752000       Deferred        pbsv
PE       f9e0000- fc73000       Deferred        compiledscriptx86
PE      10000000-1002b000       Deferred        mac3r
PE      711a0000-711a6000       Deferred        odbcbcp
PE      74000000-74056000       Deferred        pdh
PE      76360000-76370000       Deferred        winsta
PE      76f50000-76f58000       Deferred        wtsapi32
PE      78130000-781cb000       Deferred        msvcr80
ELF     7bf00000-7bf03000       Deferred        <wine-loader>ELF     7c5e6000-7c5f6000       Deferred        libtasn1.so.2
ELF     7c5f6000-7c623000       Deferred        libcrypt.so.1
ELF     7c623000-7c68c000       Deferred        libgnutls.so.12
ELF     7c68c000-7c6ba000       Deferred        libcups.so.2
ELF     7c6c5000-7c6ca000       Deferred        libnss_dns.so.2
ELF     7c6f5000-7c727000       Deferred        uxtheme<elf>
  \-PE  7c700000-7c727000       \               uxtheme
ELF     7c727000-7c74d000       Deferred        msacm32<elf>
  \-PE  7c730000-7c74d000       \               msacm32
ELF     7c74d000-7c789000       Deferred        wineoss<elf>
  \-PE  7c750000-7c789000       \               wineoss
ELF     7ca19000-7ca1d000       Deferred        libgpg-error.so.0
ELF     7ca22000-7ca3a000       Deferred        msacm32<elf>
  \-PE  7ca30000-7ca3a000       \               msacm32
ELF     7ca3a000-7ca43000       Deferred        libxcursor.so.1
ELF     7ca43000-7ca5f000       Deferred        imm32<elf>
  \-PE  7ca50000-7ca5f000       \               imm32
ELF     7ca5f000-7ca62000       Deferred        libxinerama.so.1
ELF     7ca62000-7ca77000       Deferred        midimap<elf>
  \-PE  7ca70000-7ca77000       \               midimap
ELF     7d4a3000-7d52f000       Deferred        winex11<elf>
  \-PE  7d4b0000-7d52f000       \               winex11
ELF     7d52f000-7d54e000       Deferred        libexpat.so.1
ELF     7d54e000-7d57c000       Deferred        libfontconfig.so.1
ELF     7d57c000-7d590000       Deferred        libz.so.1
ELF     7d590000-7d5f9000       Deferred        libfreetype.so.6
ELF     7d5fa000-7d5fe000       Deferred        libxfixes.so.3
ELF     7d5fe000-7d601000       Deferred        libxrandr.so.2
ELF     7d601000-7d609000       Deferred        libxrender.so.1
ELF     7d610000-7d658000       Deferred        dsound<elf>
  \-PE  7d620000-7d658000       \               dsound
ELF     7d658000-7d68e000       Deferred        dinput<elf>
  \-PE  7d660000-7d68e000       \               dinput
ELF     7d68e000-7d6a7000       Deferred        dinput8<elf>
  \-PE  7d690000-7d6a7000       \               dinput8
ELF     7d6a7000-7d6bc000       Deferred        psapi<elf>
  \-PE  7d6b0000-7d6bc000       \               psapi
ELF     7d6bc000-7d704000       Dwarf           dbghelp<elf>
  \-PE  7d6d0000-7d704000       \               dbghelp
ELF     7d704000-7d754000       Deferred        crypt32<elf>
  \-PE  7d710000-7d754000       \               crypt32
ELF     7d754000-7d76d000       Deferred        version<elf>
  \-PE  7d760000-7d76d000       \               version
ELF     7d76d000-7d793000       Deferred        odbc32<elf>
  \-PE  7d780000-7d793000       \               odbc32
ELF     7d793000-7d82b000       Deferred        oleaut32<elf>
  \-PE  7d7a0000-7d82b000       \               oleaut32
ELF     7d82b000-7d8c4000       Deferred        ole32<elf>
  \-PE  7d840000-7d8c4000       \               ole32
ELF     7d8c4000-7d8f6000       Deferred        winspool<elf>
  \-PE  7d8d0000-7d8f6000       \               winspool
ELF     7d8f6000-7d9b4000       Deferred        comctl32<elf>
  \-PE  7d900000-7d9b4000       \               comctl32
ELF     7d9b4000-7daac000       Deferred        shell32<elf>
  \-PE  7d9c0000-7daac000       \               shell32
ELF     7daac000-7db4c000       Deferred        comdlg32<elf>
  \-PE  7dab0000-7db4c000       \               comdlg32
ELF     7db4c000-7dba3000       Deferred        shlwapi<elf>
  \-PE  7db60000-7dba3000       \               shlwapi
ELF     7dba3000-7dbbd000       Deferred        wsock32<elf>
  \-PE  7dbb0000-7dbbd000       \               wsock32
ELF     7dc25000-7dc2f000       Deferred        libgcc_s.so.1
ELF     7dd04000-7e675000       Deferred        libglcore.so.1
ELF     7e675000-7e6eb000       Deferred        libglu.so.1
ELF     7e6eb000-7e77f000       Deferred        libgl.so.1
ELF     7e77f000-7e865000       Deferred        libx11.so.6
ELF     7e865000-7e872000       Deferred        libxext.so.6
ELF     7e872000-7e88a000       Deferred        libice.so.6
ELF     7e88a000-7e904000       Deferred        opengl32<elf>
  \-PE  7e8a0000-7e904000       \               opengl32
ELF     7e904000-7e991000       Deferred        winmm<elf>
  \-PE  7e910000-7e991000       \               winmm
ELF     7e991000-7ea24000       Deferred        gdi32<elf>
  \-PE  7e9a0000-7ea24000       \               gdi32
ELF     7ea24000-7eb5a000       Deferred        user32<elf>
  \-PE  7ea40000-7eb5a000       \               user32
ELF     7eb5a000-7eb85000       Deferred        ws2_32<elf>
  \-PE  7eb60000-7eb85000       \               ws2_32
ELF     7eb85000-7ebaa000       Deferred        netapi32<elf>
  \-PE  7eb90000-7ebaa000       \               netapi32
ELF     7ebaa000-7ebef000       Deferred        advapi32<elf>
  \-PE  7ebc0000-7ebef000       \               advapi32
ELF     7ebef000-7ec02000       Deferred        libresolv.so.2
ELF     7ec03000-7ec17000       Deferred        lz32<elf>
  \-PE  7ec10000-7ec17000       \               lz32
ELF     7ec19000-7ec38000       Deferred        iphlpapi<elf>
  \-PE  7ec20000-7ec38000       \               iphlpapi
ELF     7ec38000-7ec8c000       Deferred        rpcrt4<elf>
  \-PE  7ec40000-7ec8c000       \               rpcrt4
ELF     7ec8c000-7ecee000       Deferred        msvcrt<elf>
  \-PE  7eca0000-7ecee000       \               msvcrt
ELF     7edf8000-7ef19000       Deferred        kernel32<elf>
  \-PE  7ee10000-7ef19000       \               kernel32
ELF     7ef19000-7ef23000       Deferred        libnss_files.so.2
ELF     7ef23000-7ef2c000       Deferred        libnss_nis.so.2
ELF     7ef2c000-7ef41000       Deferred        libnsl.so.1
ELF     7ef41000-7ef4a000       Deferred        libnss_compat.so.2
ELF     7ef4a000-7ef6c000       Deferred        libm.so.6
ELF     7ef6c000-7f000000       Deferred        ntdll<elf>
  \-PE  7ef80000-7f000000       \               ntdll
ELF     b7cc2000-b7cc5000       Deferred        libdl.so.2
ELF     b7cc5000-b7df4000       Deferred        libc.so.6
ELF     b7df4000-b7e06000       Deferred        libpthread.so.0
ELF     b7e07000-b7e09000       Deferred        libnvidia-tls.so.1
ELF     b7e09000-b7e0c000       Deferred        libxau.so.6
ELF     b7e0c000-b7e14000       Deferred        libsm.so.6
ELF     b7e1e000-b7f32000       Deferred        libwine.so.1
ELF     b7f35000-b7f4b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e 
        0000000f    0
0000000c (D) C:\Program Files\id Software\Enemy Territory - QUAKE Wars Beta\etqw.exe
        00000019   -2
        00000017    1
        00000016    0
        00000015   -2
        00000014   -2
        00000013    0
        00000012   -1
        00000011    0
        0000000d    0 <==

```

---

### Post by Mongoose on 2007-06-26
Hey man, ttimo is working as fast as he can.  It's pretty hard when you're the entire linux development departement.  You just better pray he doesn't get hit by a stale bagette.    ^^

sharkguy: Try using GIT instead of 0.9.39 or whatever source you used.  It's pretty clear how, but not why you're crashing there.  &#12362;&#12420;&#12377;&#12415; (goodnight).

---

### Post by hikaricore on 2007-06-26
> **racoq said:**
> Do not complain... at least they  are developing a native linux version...

Do complain about other game company's don't release a linux version at all..

... no I will complain thank you.

I'm just getting really tired of developers hyping a linux release then not even bothering to put it on the actual game disc(s).

It's just getting old.

> **Mongoose said:**
> Hey man, ttimo is working as fast as he can.  It's pretty hard when you're the entire linux development departement.  You just better pray he doesn't get hit by a stale bagette.    ^^

I wasn't aware it was a 1 man army.  I guess things make a little more sense in that light.

---

### Post by hype on 2007-06-26
Hi there, 
i managed to install ETQW following your how to, but in game (from the login screen) i cant just move the cursor: my mouse seems inactive.
 I can use ctrl +alt + 2 to open a console and "quit", but nothing more.
Any hints?

im running feisty with amd athlon XP 3000+ geforce 7600GT nvidia-glx drivers (from repos)

---

### Post by primski on 2007-06-27
Did you use the native dinput8.dll ? Check wine site for details.

Also, to get rid of choppiness and freezy thingy, try running etqw.exe with high priority. If you have a reasonably powerfull CPU it works OK then.

```

nice -19 wine etqw.exe

```

[Check this bug](http://bugs.winehq.org/show_bug.cgi?id=8786)

I got it running on my system, tho my poor cpu and gpu specs forbid me to run it above 5 fps :s

---

### Post by hype on 2007-06-27
Primski, 
i did try to copy both dinout.dll et dinput8.dll from an existing Xp install.
When i do so, ETQW crashes before it comes to the login menu. And i've marked these dll's as "native" , using winecfg.

Is there a "newer" version of these dinput.dll et dinput8.dll on wine website?

---

### Post by primski on 2007-06-27
Hm actually i just copied dinput8.dll and NOT dinput.dll, though my game did not crash, just mouse was unusable. Some have also reported using the dll from the ie. dll-files.com rather than XP install could help, due to different version of the file. try that too.

Other than that i dunno what else could be wrong :s

---

### Post by Sockerdrickan on 2007-06-27
This is so going to rock with my GeForce 8800

---

### Post by Mongoose on 2007-06-27
You might be surprised to know a majority of the Linux ports and many OS X ports are done by one man -- Ryan Gordan.  

Learn more about the native linux gaming clut of Ryan Gordon:
[http://icculus.org](http://icculus.org)

You need to support this guy's OSS projects too:  
[http://icculus.org/~mongoose](http://icculus.org/~mongoose)  

I can always use more souls... I mean testers... ;)

---

### Post by hype on 2007-06-28
Is that...you? :D

Well, anyway i think i'll wait for the linux installer to come out; i still cant move my mouse in-game. :(

---

### Post by Ferrat on 2007-06-28
> **hikaricore said:**
> 
I'm just getting really tired of developers hyping a linux release then not even bothering to put it on the actual game disc(s).

It's just getting old.


That won't change, that is much because of legal issues, the Linux version works on most disps. ect. but not all and they can't garantie that, there for the linux client version is just a free download  and you need to buy the Win/Mac version CDs.
If they put the Linux version on the CD it might backfire, say som dists. change something that messed things up or something and they would have to fix it since you paid for the Linux version and it's their job then to fix it. 
Also, he is alone in working on it that's why the linux version often comes out a little later than the real release. 
Just the fact that IDsoftware puts one out should be hyped, they have done this for a long time for the linux community while other companies just ignore that linux even exists.

---

