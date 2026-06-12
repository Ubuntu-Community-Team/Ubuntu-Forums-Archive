---
title: "Diablo under wine in windowed mode"
date: 2006-03-21
forum: Gaming &amp; Leisure
---

### Post by PsychoTrauma on 2006-03-21
Diablo runs under wine pretty well but I can't figure out how to make it run in windowed mode instead of full screen. I used google to search and I read that there is a setting in wine.conf but I can't seem to find that file. I am using wine 9.10 in case that helps as well. 

Edit: I found the way to make it run in windowed mode but now it crashes for some reason. Here is the output I get:

```
$ wine diablo.exe
$ fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd54b68)->(0x10024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:x11drv:X11DRV_DDHAL_CreatePalette stub
fixme:ddraw:Main_DirectDraw_WaitForVerticalBlank (0x7fd54b68)->(flags=0x00000001,handle=(nil))
fixme:ddraw:Main_DirectDraw_WaitForVerticalBlank (0x7fd54b68)->(flags=0x00000001,handle=(nil))
wine: Unhandled page fault on write access to 0x7caac000 at address 0x7dba05a4 (thread 000b), starting debugger...
WineDbg starting on pid 0xa
Unhandled exception: page fault on write access to 0x7caac000 in 32-bit code (0x7dba05a4).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7dba05a4 ESP:7faaf310 EBP:7faaf3d0 EFLAGS:00010206(   - 00      - RIP1)
 EAX:205f5f5f EBX:7dba019c ECX:00000000 EDX:00000015
 ESI:7ae71014 EDI:7caac000
Stack dump:
0x7faaf310:  00000000 7caab000 7caab000 00000000
0x7faaf320:  7ae70010 00000000 7fd54ec0 0000002d
0x7faaf330:  00cc0020 00000001 7faaf3c4 7faaf36c
0x7faaf340:  7d011084 7fd54ec0 00000000 00000001
0x7faaf350:  7faaf3c4 7ffd383c 0000005d 7c22c3f0
0x7faaf360:  7faaf4ec 00000000 00000000 7faaf39c
0200: sel=1007 base=7fe46000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7dba05a4 (0x7dba05a4)
fixme:dbghelp:sffip_cb NIY on 'P:\Projects\Storm\Storm-SWAR\bin\Storm.pdb'
  2 0x1500719d in storm (+0x719d) (0x1500719d)
  3 0x00000000 (0x00000000)
0x7dba05a4: movl        %eax,0x0(%edi)
Modules:
Module  Address                 Debug info      Name (93 modules)
PE      0x00400000-006b2000     Deferred        diablo
PE      0x10000000-1004b000     Deferred        diabloui
PE      0x15000000-15045000     Export          storm
ELF     0x7b719000-7b7a0000     Deferred        winmm<elf>
  \-PE  0x7b720000-7b7a0000     \               winmm
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7bf2f000-7bf80000     Deferred        dsound<elf>
  \-PE  0x7bf40000-7bf80000     \               dsound
PE      0x7c240000-7c25a000     Deferred        smackw32
ELF     0x7ca27000-7ca3c000     Deferred        midimap<elf>
  \-PE  0x7ca30000-7ca3c000     \               midimap
ELF     0x7ca3c000-7ca60000     Deferred        msacm32<elf>
  \-PE  0x7ca40000-7ca60000     \               msacm32
ELF     0x7cfb5000-7d02f000     Deferred        ddraw<elf>
  \-PE  0x7cfd0000-7d02f000     \               ddraw
ELF     0x7dbe2000-7dbf9000     Deferred        msacm<elf>
  \-PE  0x7dbf0000-7dbf9000     \               msacm
ELF     0x7dcb0000-7dd95000     Deferred        libdb-4.3.so
ELF     0x7dd95000-7dd9a000     Deferred        libnss_db.so.2
ELF     0x7dd9a000-7dd9e000     Deferred        libgpg-error.so.0
ELF     0x7dd9e000-7ddec000     Deferred        libgcrypt.so.11
ELF     0x7ddec000-7de54000     Deferred        libgnutls.so.12
ELF     0x7de54000-7de70000     Deferred        libcups.so.2
ELF     0x7deb0000-7dec0000     Deferred        libtasn1.so.2
ELF     0x7ded6000-7df07000     Deferred        uxtheme<elf>
  \-PE  0x7dee0000-7df07000     \               uxtheme
ELF     0x7df07000-7df10000     Deferred        libxrender.so.1
ELF     0x7df10000-7df19000     Deferred        libxcursor.so.1
ELF     0x7df19000-7df35000     Deferred        imm32<elf>
  \-PE  0x7df20000-7df35000     \               imm32
ELF     0x7df35000-7df52000     Deferred        ximcp.so.2
ELF     0x7dfaf000-7e76d000     Deferred        libglcore.so.1
ELF     0x7e76d000-7e7f0000     Deferred        libgl.so.1
ELF     0x7e7f0000-7e8bb000     Deferred        libx11.so.6
ELF     0x7e8bb000-7e8c9000     Deferred        libxext.so.6
ELF     0x7e8c9000-7e8e1000     Deferred        libice.so.6
ELF     0x7e8e1000-7e960000     Deferred        winex11<elf>
  \-PE  0x7e8f0000-7e960000     \               winex11
ELF     0x7e960000-7e980000     Deferred        libexpat.so.1
ELF     0x7e980000-7e9af000     Deferred        libfontconfig.so.1
ELF     0x7e9af000-7e9c3000     Deferred        libz.so.1
ELF     0x7e9c3000-7ea30000     Deferred        libfreetype.so.6
ELF     0x7ea30000-7ea44000     Deferred        lz32<elf>
  \-PE  0x7ea40000-7ea44000     \               lz32
ELF     0x7ea44000-7ea5d000     Deferred        version<elf>
  \-PE  0x7ea50000-7ea5d000     \               version
ELF     0x7ea5d000-7ea87000     Deferred        winspool<elf>
  \-PE  0x7ea70000-7ea87000     \               winspool
ELF     0x7ea87000-7eb1f000     Deferred        comdlg32<elf>
  \-PE  0x7ea90000-7eb1f000     \               comdlg32
ELF     0x7eb1f000-7eb81000     Deferred        msvcrt<elf>
  \-PE  0x7eb30000-7eb81000     \               msvcrt
ELF     0x7eb81000-7eb9b000     Deferred        crtdll<elf>
  \-PE  0x7eb90000-7eb9b000     \               crtdll
ELF     0x7eb9b000-7ec50000     Deferred        comctl32<elf>
  \-PE  0x7eba0000-7ec50000     \               comctl32
ELF     0x7ec50000-7ec6e000     Deferred        iphlpapi<elf>
  \-PE  0x7ec60000-7ec6e000     \               iphlpapi
ELF     0x7ec6e000-7ecb6000     Deferred        rpcrt4<elf>
  \-PE  0x7ec80000-7ecb6000     \               rpcrt4
ELF     0x7ecb6000-7ed42000     Deferred        ole32<elf>
  \-PE  0x7ecd0000-7ed42000     \               ole32
ELF     0x7ed42000-7ed9a000     Deferred        shlwapi<elf>
  \-PE  0x7ed60000-7ed9a000     \               shlwapi
ELF     0x7ed9a000-7ee60000     Deferred        shell32<elf>
  \-PE  0x7edb0000-7ee60000     \               shell32
ELF     0x7ee60000-7ee9e000     Deferred        advapi32<elf>
  \-PE  0x7ee70000-7ee9e000     \               advapi32
ELF     0x7ef7b000-7f87e000     Deferred        gdi32<elf>
  \-PE  0x7efc0000-7f87e000     \               gdi32
ELF     0x7f87e000-7f9a0000     Deferred        user32<elf>
  \-PE  0x7f8a0000-7f9a0000     \               user32
ELF     0x7fbd2000-7fcd0000     Deferred        kernel32<elf>
  \-PE  0x7fbf0000-7fcd0000     \               kernel32
ELF     0x7fcd2000-7fcd7000     Deferred        libxxf86vm.so.1
ELF     0x7fcd7000-7fce0000     Deferred        libsm.so.6
ELF     0x7fce5000-7fcf0000     Deferred        libgcc_s.so.1
ELF     0x7fe01000-7fe06000     Deferred        libxxf86dga.so.1
ELF     0x7fe06000-7fe12000     Deferred        libnss_files.so.2
ELF     0x7fe12000-7fe1c000     Deferred        libnss_nis.so.2
ELF     0x7fe1c000-7fe32000     Deferred        libnsl.so.1
ELF     0x7fe32000-7fe3b000     Deferred        libnss_compat.so.2
ELF     0x7fe42000-7fe44000     Deferred        xlcutf8load.so.2
ELF     0x7fe49000-7fe6f000     Deferred        libm.so.6
ELF     0x7fe6f000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7d75000-b7d79000     Deferred        libdl.so.2
ELF     0xb7d79000-b7eb1000     Deferred        libc.so.6
ELF     0xb7eb1000-b7ec4000     Deferred        libpthread.so.0
ELF     0xb7ec6000-b7ec8000     Deferred        libnvidia-tls.so.1
ELF     0xb7ed0000-b7eea000     Deferred        libwine.so.1
ELF     0xb7eec000-b7f04000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) C:\Program Files\Diablo\Diablo.exe
        00000010    1
        0000000f    0
        0000000e    0
0000000c
        0000000d    0
0000000a (D) C:\Program Files\Diablo\Diablo.exe
        0000000b    0 <==

```

---

### Post by Stewart on 2006-03-21
I just installed Diablo II lastnight. When I ran the video setup, it came up with 4 choices. It wanted to use Direct 3D, that ran in a window. I re-ran setup and choose DRI or Glide (I think it was the second one down the list). Hope this helps. I'm at work now and it was late last night. :-? 

Stewart

---

### Post by PsychoTrauma on 2006-03-21
[QUOTE=Stewart]I just installed Diablo II lastnight. When I ran the video setup, it came up with 4 choices. It wanted to use Direct 3D, that ran in a window. I re-ran setup and choose DRI or Glide (I think it was the second one down the list). Hope this helps. I'm at work now and it was late last night. :-? 

Stewart[/QUOTE]

Thanks for the help but i'm trying to play the original diablo.

---

### Post by Master Shake on 2006-03-22
OUt of curiosity, how did you install Diablo with wine?  I've been wanting to test this in Ubuntu for some time.

---

### Post by PsychoTrauma on 2006-03-28
I installed it the usual way of inserting the disk and running the install program. I seem to have messed something up now though because it won't play at all.

---

### Post by trotski on 2006-03-28
Mine installed just like it did in Windows.
I then run it just like this:

**wine "C:\Program Files\Diablo II\Diablo II.exe" -d3d**

I haven't installed LoD (lost CD key, I think), so the resolution is 640x480.  So, in order to play, X "zooms in" on the upper left corner and overlays the game there.  It *is* fullscreen, but you can accidentally move the mouse out into your zoomed desktop.  I've minimized the game more than once by clicking beyond the game's box.  I bet if I had LoD, this wouldn't happen (higher res).

The game plays fine in standard window mode.  It is a bit too dark for me, though.  You use the -w switch instead of -d3d.

---

