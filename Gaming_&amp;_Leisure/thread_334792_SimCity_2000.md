---
title: "SimCity 2000"
date: 2007-01-09
forum: Gaming &amp; Leisure
---

### Post by Josh1 on 2007-01-09
Hi all!

Decided to get out my old games from a few years ago since I am bored and wanted to see if they worked in ubuntu (considering most require 4megs of video ram, I'm guessing they would :rolleyes: ), and SimCity 2000 showed up!

So I insert the disk, l open command line and I type the following commands (and the following shows up):
```

josh@JOSH:~$ cd /media/cdrom0/
josh@JOSH:/media/cdrom0$ ls
ARJ.EXE       INSTALL.COM   MAXISLND.SC2  SC2000.DAT    VDETECT.EXE
GM1.BNK       INSTALL.EXE   MW_ATIUP.EXE  SC2000.EXE    VESA
GM2.BNK       INSTALL.MXS   POSTCARD.CIM  SCENARIO      VOLCANO.SC2
HAPPYLND.SC2  LAKELAND.SC2  README.TXT    SERPENTI.SC2  VRF_DLL.EXE
INFO.EXE      MAXIS.CIM     SC2000.CFG    SOUND
josh@JOSH:/media/cdrom0$ wine install.exe
libGL warning: 3D driver claims to not support visual 0x4b
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.
wine: Unhandled page fault on read access to 0xffffffff at address 0x7bc6583f (thread 000c), starting debugger...
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0x7bc6583f).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc6583f ESP:7dd84358 EBP:7dd843f8 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000007 EBX:7bc788c4 ECX:7dd847d0 EDX:7dd8462c
 ESI:00000007 EDI:7dd847d0
Stack dump:
0x7dd84358:  0000211b 7bc56fbc 7dd847d0 00000021
0x7dd84368:  7dee4cc9 7dee4a4c 00000021 00001091
0x7dd84378:  0000000c 00003000 00000000 00000000
0x7dd84388:  00000000 00000000 00000000 00000000
0x7dd84398:  00000080 00001081 00001081 00000000
0x7dd843a8:  00000000 000b0202 00000002 7dd843cc
Backtrace:
=>1 0x7bc6583f in ntdll (+0x5583f) (0x7dd843f8)
  2 0x7bc5c182 NtSetContextThread+0x112() in ntdll (0x7dd84518)
  3 0x7bc566af in ntdll (+0x466af) (0x7dd84538)
  4 0x7bc57429 __wine_enter_vm86+0x129() in ntdll (0x7dd84688)
  5 0x7b8982f3 K32WOWCallback16Ex+0x2a3() in kernel32 (0x7dd846e8)
  6 0x7debcfcb DOSVM_Enter+0xeb() in winedos (0x7dd847b8)
  7 0x7ded9e42 in winedos (+0x29e42) (0x7dd84aa8)
  8 0x7b88ae38 in kernel32 (+0x6ae38) (0x7dd84b78)
  9 0x7bc5c030 in ntdll (+0x4c030) (0x7dd85478)
  10 0xb7e11504 start_thread+0x84() in libpthread.so.0 (0x7dd854e8)
  11 0xb7da451e __clone+0x5e() in libc.so.6 (0x00000000)
0x7bc6583f: pop %es
Modules:
Module  Address                 Debug info      Name (59 modules)
ELF     7b800000-7b91b000       Export          kernel32<elf>
  \-PE  7b820000-7b91b000       \               kernel32
ELF     7bc00000-7bc83000       Export          ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7dd86000-7dd9b000       Deferred        midimap<elf>
  \-PE  7dd90000-7dd9b000       \               midimap
ELF     7ddc1000-7ddd9000       Deferred        msacm32<elf>
  \-PE  7ddd0000-7ddd9000       \               msacm32
ELF     7ddd9000-7de15000       Deferred        wineoss<elf>
  \-PE  7dde0000-7de15000       \               wineoss
ELF     7de15000-7dea3000       Deferred        winmm<elf>
  \-PE  7de20000-7dea3000       \               winmm
ELF     7dea3000-7df02000       Export          winedos<elf>
  \-PE  7deb0000-7df02000       \               winedos
ELF     7df04000-7df09000       Deferred        libxfixes.so.3
ELF     7df09000-7df12000       Deferred        libxcursor.so.1
ELF     7df12000-7df2e000       Deferred        imm32<elf>
  \-PE  7df20000-7df2e000       \               imm32
ELF     7df2e000-7df4c000       Deferred        ximcp.so.2
ELF     7df4c000-7df4e000       Deferred        xlcutf8load.so.2
ELF     7df4e000-7df51000       Deferred        libxrandr.so.2
ELF     7df51000-7df59000       Deferred        libxrender.so.1
ELF     7df59000-7df5c000       Deferred        libxinerama.so.1
ELF     7e64d000-7e894000       Deferred        r200_dri.so
ELF     7e894000-7e89b000       Deferred        libdrm.so.2
ELF     7e89b000-7e90a000       Deferred        libgl.so.1
ELF     7e90a000-7e90f000       Deferred        libxdmcp.so.6
ELF     7e90f000-7e9d8000       Deferred        libx11.so.6
ELF     7e9d8000-7e9e5000       Deferred        libxext.so.6
ELF     7e9e5000-7e9fd000       Deferred        libice.so.6
ELF     7e9fd000-7ea8a000       Deferred        winex11<elf>
  \-PE  7ea10000-7ea8a000       \               winex11
ELF     7ea8a000-7eaa8000       Deferred        libexpat.so.1
ELF     7eaa8000-7ead7000       Deferred        libfontconfig.so.1
ELF     7ead7000-7eaeb000       Deferred        libz.so.1
ELF     7eaeb000-7eb55000       Deferred        libfreetype.so.6
ELF     7eb55000-7eb9b000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb9b000       \               advapi32
ELF     7eb9b000-7eba6000       Deferred        libgcc_s.so.1
ELF     7ec85000-7ed3b000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed3b000       \               gdi32
ELF     7ed3b000-7ee73000       Deferred        user32<elf>
  \-PE  7ed60000-7ee73000       \               user32
ELF     7ee73000-7ee88000       Deferred        winevdm<elf>
  \-PE  7ee80000-7ee88000       \               winevdm
ELF     7ee88000-7ee93000       Deferred        libnss_files.so.2
ELF     7ee93000-7eea9000       Deferred        libnsl.so.1
ELF     7eea9000-7eeb2000       Deferred        libnss_compat.so.2
ELF     7eeb5000-7eeb8000       Deferred        libxau.so.6
ELF     7eeb8000-7eec1000       Deferred        libsm.so.6
ELF     7efcb000-7eff1000       Deferred        libm.so.6
ELF     7eff1000-7eff6000       Deferred        libxxf86vm.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cd3000-b7cd7000       Deferred        libdl.so.2
ELF     b7cd7000-b7e0b000       Export          libc.so.6
ELF     b7e0c000-b7e1f000       Export          libpthread.so.0
ELF     b7e2e000-b7f3f000       Deferred        libwine.so.1
ELF     b7f41000-b7f5c000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) c:\windows\system32\winevdm.exe
        0000000c    0 <==
        0000000b    0
josh@JOSH:/media/cdrom0$ 

```

---

### Post by hikaricore on 2007-01-09
Here's the wine application database page for SimCity 2000:

[http://appdb.winehq.org/appview.php?iVersionId=947](http://appdb.winehq.org/appview.php?iVersionId=947)

Make sure you have a fairly decent version of wine installed, the ones in the repos are usually a bit dated.  From a terminal run:

```
wine --version
```

It should return a version number.

Compare it to the version at the top of this list:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

And decide for yourself if updating it is worth a shot.

Current version as of today is - Wine 0.9.29

This version isn't up as a ubuntu package on the archive page yet but will be shortly.

Some users on the wine app db site mentioned running it in a windowed mode which may help somewhat.  But it looks as if you're having trouble with the installer.

Are you sure that install.exe is a windows setup program?  I seem to remember the first version of S2K I ever owned being a dos mode game, but I could be wrong.  Anyway there may be some hints on the wine site I linked you on how to set this up.  One more idea, filenames in linux are case sensitive, running it as:

```
wine INSTALL.EXE
```

May work, but don't quote me on that :P

Good luck and hopefully you can get this running.  :)  If all else fails you could install it on a windows machine and copy the installed files cd or something to try in linux.  >.<  But that's kinda a last resort type thing.

---

### Post by Josh1 on 2007-01-10
> **hikaricore said:**
> Here's the wine application database page for SimCity 2000:

[http://appdb.winehq.org/appview.php?iVersionId=947](http://appdb.winehq.org/appview.php?iVersionId=947)

Make sure you have a fairly decent version of wine installed, the ones in the repos are usually a bit dated.  From a terminal run:

```
wine --version
```

It should return a version number.

Compare it to the version at the top of this list:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

And decide for yourself if updating it is worth a shot.

Current version as of today is - Wine 0.9.29

This version isn't up as a ubuntu package on the archive page yet but will be shortly.

Some users on the wine app db site mentioned running it in a windowed mode which may help somewhat.  But it looks as if you're having trouble with the installer.

Are you sure that install.exe is a windows setup program?  I seem to remember the first version of S2K I ever owned being a dos mode game, but I could be wrong.  Anyway there may be some hints on the wine site I linked you on how to set this up.  One more idea, filenames in linux are case sensitive, running it as:

```
wine INSTALL.EXE
```

May work, but don't quote me on that :P

Good luck and hopefully you can get this running.  :)  If all else fails you could install it on a windows machine and copy the installed files cd or something to try in linux.  >.<  But that's kinda a last resort type thing.

Cheers for your reply! This is the updated version from 1999 (original was indeed made in 1993).
I currently have "wine-0.9.28" installed, I will install the latest and see how that goes. Might change videocard as well and see how that goes - I've got an nVidia 6600le 256mb lieing around somewhere.

But yeah, I'm thinking about installing this on my sisters windows laptop then putting it onto my computer...

---

