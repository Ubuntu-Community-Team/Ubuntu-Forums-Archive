---
title: "Wine is completely, permanently broken."
date: 2006-06-24
forum: Gaming &amp; Leisure
---

### Post by keithjr on 2006-06-24
Well, this will most likely be my last post on this forum.  If you've seen any of my threads, you'll know that nothing I've tried to do has gone right.  Well, this new brick wall has proven to be insurmountable. 
My attempts to run a few older games were all failing, but were failing predictably, usually getting somewhere into the game and crashing out.  But today, after several attempts to get other apps working, I came back to find that any game executable I tried to run generated a page fault (some other smaller exes, setup ones mostly, still work). 
Confused, I try uninstalling and reinstalling wine.  Immediately after, I run the obligatory wineprefixcreate, and get the SAME EXACT fault error.  Here it is in all of its glory, on the off-chance that somebody can recognize it.

```
keithjr@ubuntu:~/wine$ wineprefixcreate
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7e6f260 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7e6f260).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:b7e6f260 ESP:7fb8d254 EBP:7fb8d27c EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:b7f2dadc ECX:00000000 EDX:00000000
 ESI:7fb8d298 EDI:00000000
Stack dump:
0x7fb8d254:  00000000 b7e64615 00000000 00000000
0x7fb8d264:  b7e63892 7fb8d298 00008000 b7f2dadc
0x7fb8d274:  7fb8d298 00000076 7fb8d340 b7e594cd
0x7fb8d284:  7fb8d298 00000000 00000000 00000000
0x7fb8d294:  00000000 fbad8000 00000000 00000000
0x7fb8d2a4:  00000000 00000000 00000000 00000000
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0xb7e6f260 rawmemchr+0x40 in libc.so.6 (0xb7e6f260)
  2 0xb7e594cd __vsscanf+0x6d in libc.so.6 (0xb7e594cd)
  3 0xb7e5479b _IO_sscanf+0x2b in libc.so.6 (0xb7e5479b)
  4 0x7d692bbc d3ddevice_init_at_startup+0x2cc in ddraw (0x7d692bbc)
  5 0x7d6aea92 DllMain+0x10b2 in ddraw (0x7d6aea92)
  6 0x7d6baaec in ddraw (+0x3aaec) (0x7d6baaec)
  7 0x7ff97ff5 call_dll_entry_point+0x15 in ntdll (0x7ff97ff5)
  8 0x7ff999fa in ntdll (+0x299fa) (0x7ff999fa)
  9 0x7ff99cdc in ntdll (+0x29cdc) (0x7ff99cdc)
  10 0x7ff9cac7 LdrLoadDll+0x87 in ntdll (0x7ff9cac7)
  11 0x7fc501f0 in kernel32 (+0x401f0) (0x7fc501f0)
  12 0x7fc5037f LoadLibraryExW+0x4f in kernel32 (0x7fc5037f)
  13 0x7d999817 in setupapi (+0x19817) (0x7d999817)
  14 0x7d99ad2c in setupapi (+0x1ad2c) (0x7d99ad2c)
  15 0x7d99af7d SetupInstallFromInfSectionW+0x11d in setupapi (0x7d99af7d)
  16 0x7d99b70e InstallHinfSectionW+0x1de in setupapi (0x7d99b70e)
  17 0x7fbae5c4 main+0x334 in rundll32 (0x7fbae5c4)
  18 0x7fbaeb7e in rundll32 (+0xeb7e) (0x7fbaeb7e)
  19 0x7fc5d15f in kernel32 (+0x4d15f) (0x7fc5d15f)
  20 0xb7f58637 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f58637)
0xb7e6f260 rawmemchr+0x40 in libc.so.6: movl    0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (69 modules)
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7d4fa000-7d50f000     Deferred        midimap<elf>
  \-PE  0x7d500000-7d50f000     \               midimap
ELF     0x7d526000-7d56a000     Deferred        wineoss<elf>
  \-PE  0x7d540000-7d56a000     \               wineoss
ELF     0x7d5ca000-7d65b000     Deferred        ole32<elf>
  \-PE  0x7d5e0000-7d65b000     \               ole32
ELF     0x7d65b000-7d6d6000     Export          ddraw<elf>
  \-PE  0x7d680000-7d6d6000     \               ddraw
ELF     0x7d6d6000-7d75c000     Deferred        winmm<elf>
  \-PE  0x7d6e0000-7d75c000     \               winmm
ELF     0x7d75c000-7d780000     Deferred        msacm32<elf>
  \-PE  0x7d760000-7d780000     \               msacm32
ELF     0x7d8d7000-7d8f5000     Deferred        iphlpapi<elf>
  \-PE  0x7d8e0000-7d8f5000     \               iphlpapi
ELF     0x7d8f5000-7d948000     Deferred        rpcrt4<elf>
  \-PE  0x7d910000-7d948000     \               rpcrt4
ELF     0x7d948000-7d95c000     Deferred        lz32<elf>
  \-PE  0x7d950000-7d95c000     \               lz32
ELF     0x7d95c000-7d975000     Deferred        version<elf>
  \-PE  0x7d960000-7d975000     \               version
ELF     0x7d975000-7d9ca000     Export          setupapi<elf>
  \-PE  0x7d980000-7d9ca000     \               setupapi
ELF     0x7d9ca000-7d9d3000     Deferred        libxcursor.so.1
ELF     0x7d9d3000-7d9ef000     Deferred        imm32<elf>
  \-PE  0x7d9e0000-7d9ef000     \               imm32
ELF     0x7e27f000-7e287000     Deferred        librt.so.1
ELF     0x7e28e000-7e296000     Deferred        libxrender.so.1
ELF     0x7e350000-7ec4b000     Deferred        fglrx_dri.so
ELF     0x7ec4b000-7eceb000     Deferred        libgl.so.1
ELF     0x7eceb000-7edd1000     Deferred        libx11.so.6
ELF     0x7edd1000-7edde000     Deferred        libxext.so.6
ELF     0x7edde000-7edf6000     Deferred        libice.so.6
ELF     0x7edf6000-7ee75000     Deferred        winex11<elf>
  \-PE  0x7ee10000-7ee75000     \               winex11
ELF     0x7ee75000-7ee94000     Deferred        libexpat.so.1
ELF     0x7ee94000-7eec2000     Deferred        libfontconfig.so.1
ELF     0x7eec2000-7eed6000     Deferred        libz.so.1
ELF     0x7eed6000-7ef3f000     Deferred        libfreetype.so.6
ELF     0x7ef3f000-7ef7d000     Deferred        advapi32<elf>
  \-PE  0x7ef50000-7ef7d000     \               advapi32
ELF     0x7f052000-7f957000     Deferred        gdi32<elf>
  \-PE  0x7f0a0000-7f957000     \               gdi32
ELF     0x7f957000-7fa80000     Deferred        user32<elf>
  \-PE  0x7f970000-7fa80000     \               user32
ELF     0x7fb97000-7fb9c000     Deferred        libxxf86vm.so.1
ELF     0x7fb9c000-7fbb0000     Export          rundll32<elf>
  \-PE  0x7fba0000-7fbb0000     \               rundll32
ELF     0x7fbb1000-7fbb5000     Deferred        libxfixes.so.3
ELF     0x7fbb5000-7fbbf000     Deferred        libgcc_s.so.1
ELF     0x7fbf2000-7fcf0000     Export          kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe01000-7fe04000     Deferred        libxrandr.so.2
ELF     0x7fe04000-7fe0e000     Deferred        libnss_files.so.2
ELF     0x7fe0e000-7fe17000     Deferred        libnss_nis.so.2
ELF     0x7fe17000-7fe2c000     Deferred        libnsl.so.1
ELF     0x7fe2c000-7fe35000     Deferred        libnss_compat.so.2
ELF     0x7fe37000-7fe3c000     Deferred        libxxf86dga.so.1
ELF     0x7fe3c000-7fe44000     Deferred        libsm.so.6
ELF     0x7fe47000-7fe69000     Deferred        libm.so.6
ELF     0x7fe69000-7ff62000     Deferred        libwine_unicode.so.1
ELF     0x7ff62000-7ffe0000     Export          ntdll<elf>
  \-PE  0x7ff70000-7ffe0000     \               ntdll
ELF     0xb7e00000-b7e03000     Deferred        libdl.so.2
ELF     0xb7e03000-b7f32000     Export          libc.so.6
ELF     0xb7f32000-b7f44000     Deferred        libpthread.so.0
ELF     0xb7f44000-b7f47000     Deferred        libxau.so.6
ELF     0xb7f53000-b7f6d000     Export          libwine.so.1
ELF     0xb7f70000-b7f86000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000b    0
00000008 (D) c:\windows\system32\rundll32.exe
        00000009    0 <==
/home/keithjr/.wine updated successfully.

```

I can only assume at this point that one of the packages or custom programs I've built over the past week to try, in vain, to get at least ONE game to work correctly has messed up some important library wine depends upon.  The only solution I can see to this, however, is a full re-install since I do not know if I can even undo the damage.  If it comes to that, I really see no reason why I shouldn't go back to windows.  At least there I got the chance to PLAY games, not just spend two weeks of my free time TRYING to play them.

So, final question... what went wrong?

---

### Post by manicka on 2006-06-24
I'd suggest using cedega. [http://www.transgaming.com/](http://www.transgaming.com/)

It's  version of wine built specifcally to run games. It's not freeware but it aint expensive either

---

### Post by lotusleaf on 2006-06-24
[QUOTE=keithjr]I can only assume at this point that one of the packages or custom programs I've built over the past week to try, in vain, to get at least ONE game to work correctly has messed up some important library wine depends upon.[/QUOTE]

What packages or custom programs are you building to try and get games to work in Wine? Which games have you tried to get working? Which games did you get working? Have you looked these games up beforehand on the [Wine App DB?](http://appdb.winehq.org)

Wine also has [live support chat](http://www.winehq.com/site/irc) and [mailing lists](http://www.winehq.com/site/forums).

Edit: I second manicka's suggestion, give Cedega a try if you can't get things running in Wine.

---

### Post by keithjr on 2006-06-24
[QUOTE=lotusleaf]What packages or custom programs are you building to try and get games to work in Wine? Which games have you tried to get working? Which games did you get working? Have you looked these games up beforehand on the [Wine App DB?](http://appdb.winehq.org)

Wine also has [live support chat](http://www.winehq.com/site/irc) and [mailing lists](http://www.winehq.com/site/forums).

Edit: I second manicka's suggestion, give Cedega a try if you can't get things running in Wine.[/QUOTE]

Well, I didn't want to make the post ramble on forever so I was somewhat terse with the details.  So let's let the cat out of the bag.

I tried building Cedega from CVS but ran into a [strange error that stumped the forum]("http://www.ubuntuforums.org/showthread.php?t=200836").  I'm not going to pay for software that I know won't work on my system, so I've been trying to go the wine way since then.  Most of the games I want to play are old enough so that I thought it wouldn't be so bad...

The first game I tried to get working was mechwarrior 2.  I realized of course by now that this was futile since mech2 is a dos game.  Dosbox, however, isn't powerful enough to run such a late-era game well, so this didn't go very far.

I then tried to get even more nostalgic and get Mechwarrior (orig) to run.  This required me to try to build an older version of dosbox, and [that didn't go very well either]("http://www.ubuntuforums.org/showthread.php?t=201486").  To solve this I tried installing a few libgl packages, but nothing helped nor harmed the situation.

Next on my list was Dungeon Keeper.  [This game is listed in the wine apps database]("http://appdb.winehq.org/appview.php?appId=1978"), but there are very few comments and most of them bad.  I thought I'd try my hand, regardless.  Of course, this failed, due to graphical reasons that are not really related to the question at hand.  Oddly enough I wound up getting even worse results than the people posting using the solutions they offered.

I heard that Dungeon Keeper 2 got better results in wine, so I made one last attempt to playing a good game, and this is where things started to go awry.  I own a legal copy of the game, but it is 800 miles away.  I managed to get a hold of an image created a while ago, but it is in ccd/img/sub format (all three files present). [ Attempts to mount the image directly failed]("http://www.ubuntuforums.org/showpost.php?p=1178306&postcount=6").  I found that I could use a little utility called ccd2iso to convert the image to a more friendly iso format.  [Attempts to install ccd2iso failed]("http://www.ubuntuforums.org/showpost.php?p=1178306&").  The program, as it turns out, is dependent on a package called automake 1.6.  The ubuntu repos have automake, but the versions skip 1.4 and 1.7 (wow...), so I was forced to get the source and build it myself.  I did so, (./configure, make, sudo make install rigamarole), but the installation seemed to have no effect, and I did not have any way of removing whatever had been created. 

 Out of ideas of how to get the cd mounted, I thought I'd just try to download the dk2 demo and go from there.

I know there were other libraries and packages I tried to install out of desperation (they look enough like an error message, stuff like that) but I'm going to have to go through the synaptic History and see what might have done it.  I'll post those tomorrow.

It's been a ...long... week, that much is all I know.

---

### Post by manicka on 2006-06-24
why cedega from cvs? why not try the stable version?

---

### Post by LordRaiden on 2006-06-25
If you are trying to reinstall wine do the following.

```
sudo apt-get remove --purge wine
```

```
sudo apt-get clean
```

```
sudo apt-get wine
```

I hope you are also getting the latest version of wine (at the moment 0.9.16).

A lot of games will not work because wine still has issues with directx. Direct3d games seem to work much better than older DirectDraw ones.

---

### Post by keithjr on 2006-06-25
[QUOTE=LordRaiden]If you are trying to reinstall wine do the following.

```
sudo apt-get remove --purge wine
```

```
sudo apt-get clean
```

```
sudo apt-get wine
```

I hope you are also getting the latest version of wine (at the moment 0.9.16).

A lot of games will not work because wine still has issues with directx. Direct3d games seem to work much better than older DirectDraw ones.[/QUOTE]


Oddly enough, the purge removal does not delete the .wine directoy.  That has to be done manually, I guess, but isn't the root of my problem.

I was getting 0.9.15, I had the wrong link in my sources.list for wine, should have been "
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main"  Perhaps the older one was created by an older version of automatix?  *shrug*

Trying 0.9.16 now.

---

### Post by seth0x2b on 2006-06-25
[quote=keithjr]Oddly enough, the purge removal does not delete the .wine directoy.  That has to be done manually, I guess, but isn't the root of my problem.
[/quote] As far as I know, whatever settings a package keeps in your home directory(".wine" folder for W.I.N.E. and so on), do not get removed when you remove the package that saved/generated them.This is a Linux issue, not W.I.N.E..
As for your problem, follow LordRaiden's advice and it should work.There's no such thing as "permanently broken" when it comes to Linux in general, and Ubuntu in particular :)

Cheers and good luck

---

### Post by keithjr on 2006-06-25
It seems to have made some progress, getting wine 0.9.16, now I don't segfault anymore whenever I run wine!  Progress indeed!

However, running the DK2 demo still yields a fairly verbose bunch of errors.  At least now I have something to work with...

```

fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x7fd4f5d0) : stub, emulating 64MB for now, returning 64MB
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd4ef38)->((nil),00000008)fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd4ef38)->((nil),00000015)fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd4ef38)->((nil),00000008)fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd4ef38)->((nil),00000008)fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd722b8)->((nil),00000008)fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd722b8)->(0x1002c,00000851)fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_MULTISAMPLEMASK,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_PATCHEDGESTYLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_PATCHSEGMENTS,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_DEBUGMONITORTOKEN,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_POSITIONDEGREE,3) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_NORMALDEGREE,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_MINTESSELLATIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_MAXTESSELLATIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ADAPTIVETESS_X,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ADAPTIVETESS_Y,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ADAPTIVETESS_Z,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ADAPTIVETESS_W,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ENABLEADAPTIVETESSELLATION,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_COLORWRITEENABLE1,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_COLORWRITEENABLE2,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_COLORWRITEENABLE3,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_BLENDFACTOR,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_SRGBWRITEENABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_SEPARATEALPHABLENDENABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_SRCBLENDALPHA,2) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_DESTBLENDALPHA,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_BLENDOPALPHA,1) not handled yet
err:ole:CoGetClassObject class {92fa2c24-253c-11d2-90fb-006008a1f441} not registered
err:ole:CoGetClassObject no class object {92fa2c24-253c-11d2-90fb-006008a1f441}could be created for context 0x1
fixme:dsound:DllCanUnloadNow (void): stub
Calculating Julian date for today (25/6/2006)
Today's Julian date is 2453912 + 0.090556
The moon is 29.371683 days old
fixme:dplay:DirectPlay3WImpl_EnumConnections (0x7fd8e420)->((nil),0x10008750,0x7fb9ce8c,0x00000001): stub
fixme:dsound:DllCanUnloadNow (void): stub
fixme:dsound:DllCanUnloadNow (void): stub
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd722b8)->(0x1002c,00000008)fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd722b8)->(0x1002c,00000851)fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_MULTISAMPLEMASK,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_PATCHEDGESTYLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_PATCHSEGMENTS,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_DEBUGMONITORTOKEN,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_POSITIONDEGREE,3) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_NORMALDEGREE,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_MINTESSELLATIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_MAXTESSELLATIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ADAPTIVETESS_X,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ADAPTIVETESS_Y,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ADAPTIVETESS_Z,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ADAPTIVETESS_W,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ENABLEADAPTIVETESSELLATION,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_COLORWRITEENABLE1,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_COLORWRITEENABLE2,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_COLORWRITEENABLE3,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_BLENDFACTOR,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_SRGBWRITEENABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_SEPARATEALPHABLENDENABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_SRCBLENDALPHA,2) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_DESTBLENDALPHA,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_BLENDOPALPHA,1) not handled yet
err:ole:CoGetClassObject class {92fa2c24-253c-11d2-90fb-006008a1f441} not registered
err:ole:CoGetClassObject no class object {92fa2c24-253c-11d2-90fb-006008a1f441}could be created for context 0x1
fixme:dplay:DirectPlay3WImpl_EnumConnections (0x7fd8e180)->((nil),0x10008750,0x7fb9cc70,0x00000001): stub
fixme:dsound:DllCanUnloadNow (void): stub
fixme:dsound:DllCanUnloadNow (void): stub
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd722b8)->(0x1002c,00000008)fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd722b8)->(0x1002c,00000851)fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_MULTISAMPLEMASK,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_PATCHEDGESTYLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_PATCHSEGMENTS,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_DEBUGMONITORTOKEN,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_POSITIONDEGREE,3) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_NORMALDEGREE,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_MINTESSELLATIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_MAXTESSELLATIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ADAPTIVETESS_X,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ADAPTIVETESS_Y,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ADAPTIVETESS_Z,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ADAPTIVETESS_W,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_ENABLEADAPTIVETESSELLATION,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_COLORWRITEENABLE1,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_COLORWRITEENABLE2,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_COLORWRITEENABLE3,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_BLENDFACTOR,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_SRGBWRITEENABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_SEPARATEALPHABLENDENABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_SRCBLENDALPHA,2) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_DESTBLENDALPHA,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd9dd30)->(WINED3DRS_BLENDOPALPHA,1) not handled yet
err:ole:CoGetClassObject class {92fa2c24-253c-11d2-90fb-006008a1f441} not registered
err:ole:CoGetClassObject no class object {92fa2c24-253c-11d2-90fb-006008a1f441} could be created for context 0x1
err:seh:setup_exception stack overflow 88 bytes in thread 0009 eip 7ff8ff56 esp 7fa90fa8 stack 0x7fa91000-0x7fba0000

```

The reason I'm still posting in this "wine broken" thread is because I've gotten the "cannot change BPP" error before and could never resolve it.  The odd thing is that I regedit-ed and changed the colordepth setting to 24-bit to try to step around it, in vain.  

It seems to be complaining about emulating 64 MB of texture mem.  I know this can be changed in cedega, but where to I set this in wine myself?  I have 128, perhaps the 64MB emulation is killing things?  

Or maybe I should just pick another game...

---

### Post by ZylGadis on 2006-06-25
keithjr, I will try my copy of DK2 sometime today and see what I can do with it. I have had a fair amount of success with wine so far, and I'm quite happy with it.
By all means, do not buy Cedega. If you have a legal copy of Windows, there is absolutely no reason to give more money to people with the same mindset as Bill Gates and co. If you can't play the games you like, dual-boot is the way to go.

Edit: tried it. I get exactly the same errors, and no combination of no-cd cracks and version patches does the trick.

---

### Post by RJARRRPCGP on 2006-07-11
Thumbs down for Cedega! It ain't freeware! :mad: 

Is there a freeware alternative to Wine? It there isn't, is it possible to get most games to be playable?

---

### Post by manicka on 2006-07-12
> **RJARRRPCGP said:**
> 
Is there a freeware alternative to Wine? 

Wine is freeware

---

### Post by christhemonkey on 2006-07-12
If you were having problems converting the ccd to an iso as you couldnt compile automake, you should see [this]("http://www.ubuntuforums.org/showthread.php?t=204687") thread.

Especially see post number 2.

---

