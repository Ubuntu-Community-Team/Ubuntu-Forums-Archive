---
title: "Having Trouble Running an old game on Wine"
date: 2007-03-12
forum: Gaming &amp; Leisure
---

### Post by adarkmethod on 2007-03-12
Im trying to run an old Magic game using Wine. The here's the output if anyone has any ideas for me

adarkmethod@adarkmethod:~$ wine /home/adarkmethod/magic/magic.exe
adarkmethod@adarkmethod:~$ 
adarkmethod@adarkmethod:~$ adarkmethod@adarkmethod:~$ wine /home/adarkmethod/magic/magic.exe
bash: adarkmethod@adarkmethod:~$: command not found
adarkmethod@adarkmethod:~$ wine /home/adarkmethod/magic/magic.exe
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
wine: Unhandled page fault on write access to 0x003c2000 at address 0xab537c (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x003c2000 in 32-bit code (0x00ab537c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00ab537c ESP:00986967 EBP:00ab533c EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000018 EBX:00000dfe ECX:00000485 EDX:000004ab
 ESI:00a53426 EDI:003c2000
Stack dump:
0x00986967:  0000030a 00000bc3 00000d86 00000000
0x00986977:  6f6f5400 6e616d20 706f2079 43206e65
0x00986987:  6c617461 3a73676f 78614d20 0a642520
0x00986997:  5c3a4400 6d77654e 63696761 756f735c
0x009869a7:  73656372 64654e5c 64726143 7461435c
0x009869b7:  676f6c61 0000632e 00627200 70754400
Backtrace:
=>1 0x00ab537c in drawcardlib (+0x15537c) (0x00ab533c)
  2 0x5da290b0 (0x0975c00a)
  3 0x00000000 (0x00000000)
0x00ab537c: stosb       %es:(%edi)
Modules:
Module  Address                 Debug info      Name (94 modules)
PE      340000-357000   Deferred        cdtools
PE      400000-95b000   Deferred        magic
PE      960000-ab9000   Export          drawcardlib
PE      ac0000-be8000   Deferred        cardartlib
PE      bf0000-df1000   Deferred        deckdll
PE      10000000-10010000       Deferred        manalinkinterface
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc94000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc94000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d2b6000-7d2ba000       Deferred        libgpg-error.so.0
ELF     7d2ba000-7d308000       Deferred        libgcrypt.so.11
ELF     7d308000-7d31b000       Deferred        libtasn1.so.3
ELF     7d31b000-7d349000       Deferred        libcrypt.so.1
ELF     7d358000-7d3c7000       Deferred        libgnutls.so.13
ELF     7d3c7000-7d3f6000       Deferred        libcups.so.2
ELF     7d423000-7d438000       Deferred        midimap<elf>
  \-PE  7d430000-7d438000       \               midimap
ELF     7d45e000-7d476000       Deferred        msacm32<elf>
  \-PE  7d460000-7d476000       \               msacm32
ELF     7d476000-7d4b2000       Deferred        wineoss<elf>
  \-PE  7d480000-7d4b2000       \               wineoss
ELF     7d4b2000-7d4e4000       Deferred        uxtheme<elf>
  \-PE  7d4c0000-7d4e4000       \               uxtheme
ELF     7d4e6000-7d4eb000       Deferred        libxfixes.so.3
ELF     7d4eb000-7d4f4000       Deferred        libxcursor.so.1
ELF     7d4f4000-7d510000       Deferred        imm32<elf>
  \-PE  7d500000-7d510000       \               imm32
ELF     7d510000-7d52e000       Deferred        ximcp.so.2
ELF     7d52e000-7d530000       Deferred        xlcutf8load.so.2
ELF     7d530000-7d533000       Deferred        libxrandr.so.2
ELF     7d533000-7d53b000       Deferred        libxrender.so.1
ELF     7d53b000-7d53e000       Deferred        libxinerama.so.1
ELF     7e13e000-7e369000       Deferred        i915_dri.so
ELF     7e369000-7e370000       Deferred        libdrm.so.2
ELF     7e370000-7e3df000       Deferred        libgl.so.1
ELF     7e3df000-7e4a8000       Deferred        libx11.so.6
ELF     7e4a8000-7e4b5000       Deferred        libxext.so.6
ELF     7e4b5000-7e4cd000       Deferred        libice.so.6
ELF     7e4cd000-7e55a000       Deferred        winex11<elf>
  \-PE  7e4e0000-7e55a000       \               winex11
ELF     7e55a000-7e578000       Deferred        libexpat.so.1
ELF     7e578000-7e5a7000       Deferred        libfontconfig.so.1
ELF     7e5a7000-7e5bb000       Deferred        libz.so.1
ELF     7e5bb000-7e625000       Deferred        libfreetype.so.6
ELF     7e625000-7e689000       Deferred        msvcrt<elf>
  \-PE  7e630000-7e689000       \               msvcrt
ELF     7e689000-7e69d000       Deferred        lz32<elf>
  \-PE  7e690000-7e69d000       \               lz32
ELF     7e69d000-7e6b6000       Deferred        version<elf>
  \-PE  7e6a0000-7e6b6000       \               version
ELF     7e6b6000-7e6e9000       Deferred        winspool<elf>
  \-PE  7e6c0000-7e6e9000       \               winspool
ELF     7e6e9000-7e6fc000       Deferred        libresolv.so.2
ELF     7e6fc000-7e71a000       Deferred        iphlpapi<elf>
  \-PE  7e700000-7e71a000       \               iphlpapi
ELF     7e71a000-7e76f000       Deferred        rpcrt4<elf>
  \-PE  7e730000-7e76f000       \               rpcrt4
ELF     7e76f000-7e808000       Deferred        ole32<elf>
  \-PE  7e780000-7e808000       \               ole32
ELF     7e808000-7e860000       Deferred        shlwapi<elf>
  \-PE  7e820000-7e860000       \               shlwapi
ELF     7e860000-7e952000       Deferred        shell32<elf>
  \-PE  7e870000-7e952000       \               shell32
ELF     7e952000-7e9f2000       Deferred        comdlg32<elf>
  \-PE  7e960000-7e9f2000       \               comdlg32
ELF     7e9f2000-7ea19000       Deferred        msvfw32<elf>
  \-PE  7ea00000-7ea19000       \               msvfw32
ELF     7ea19000-7eaa7000       Deferred        winmm<elf>
  \-PE  7ea20000-7eaa7000       \               winmm
ELF     7eaa7000-7eaed000       Deferred        advapi32<elf>
  \-PE  7eab0000-7eaed000       \               advapi32
ELF     7eaed000-7eaf8000       Deferred        libgcc_s.so.1
ELF     7eaf9000-7eafe000       Deferred        libxdmcp.so.6
ELF     7eafe000-7eb07000       Deferred        libsm.so.6
ELF     7ebe6000-7ec9d000       Deferred        gdi32<elf>
  \-PE  7ec00000-7ec9d000       \               gdi32
ELF     7ec9d000-7edd6000       Deferred        user32<elf>
  \-PE  7ecc0000-7edd6000       \               user32
ELF     7edd6000-7ee96000       Deferred        comctl32<elf>
  \-PE  7ede0000-7ee96000       \               comctl32
ELF     7efa0000-7efab000       Deferred        libnss_files.so.2
ELF     7efab000-7efb5000       Deferred        libnss_nis.so.2
ELF     7efb5000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff1000       Deferred        libm.so.6
ELF     7eff4000-7eff7000       Deferred        libxau.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ce1000-b7ce6000       Deferred        libxxf86vm.so.1
ELF     b7ce9000-b7ced000       Deferred        libdl.so.2
ELF     b7ced000-b7e21000       Deferred        libc.so.6
ELF     b7e22000-b7e35000       Deferred        libpthread.so.0
ELF     b7e44000-b7f55000       Deferred        libwine.so.1
ELF     b7f57000-b7f72000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\adarkmethod\magic\magic.exe
        00000009    0 <==

---

### Post by K.Mandla on 2007-03-12
(I just shifted this to the Gaming and Leisure forum, where it's more likely to get attention from people who have experience with this. ;) )

---

### Post by yabbadabbadont on 2007-03-12
It might help if you told everyone exactly which game and which version of that game you are trying to play.  Also, have you checked the wine appdb to see if the game is supported?

[http://appdb.winehq.org/search.php?sSearchQuery=magic](http://appdb.winehq.org/search.php?sSearchQuery=magic)

---

### Post by adarkmethod on 2007-03-12
[http://appdb.winehq.org/appview.php?iVersionId=2853](http://appdb.winehq.org/appview.php?iVersionId=2853)

thats the game

edit: sorry, was trying to hide my nerdiness

---

### Post by yabbadabbadont on 2007-03-12
> **adarkmethod said:**
> [http://appdb.winehq.org/appview.php?iVersionId=2853](http://appdb.winehq.org/appview.php?iVersionId=2853)

thats the game

edit: sorry, was trying to hide my nerdiness

According to the only entry for that game, it doesn't work in wine.  Not all games do.  You may be out of luck.  Have you ever gotten it to run under any version of wine before?  What version of wine are you trying to use now?

---

### Post by adarkmethod on 2007-03-12
im using.. the newest stable release, i just got it from the site today, and the only thing i've ever even tried to run in it is utorrent. I really dont know anything about using WINE

---

### Post by anaconda on 2007-03-12
Wine is wrong tool for dos-games.. wine is meant for windows programs.

I bet it would work with Dosbox without any problems... just remember the Ctrl-F12 for increasing the emulated "processor" speed..

at least if you mean this game.. which is a DOS game.. 
*link removed*

Dosbox is great..

---

### Post by adarkmethod on 2007-03-12
that was a kool idea, but its not supported there either. Thanx anyways

---

