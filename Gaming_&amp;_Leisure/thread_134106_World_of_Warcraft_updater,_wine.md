---
title: "World of Warcraft updater, wine"
date: 2006-02-21
forum: Gaming &amp; Leisure
---

### Post by lungdart on 2006-02-21
Installed Wow. Wouldnt install from the CD's had to copy all of cd1 and the tome.mpq's from 2-5 in a folder and set it up as a drive in wine and run it from the hdd. Warcraft runs perfectly

Went to go login, and it has to patch, of course. Downloads the patch fine. Try to hit restart and it takes about 5 minutes, then the patch downloader runs, but it has to wait another 5 minutes before WoW actually closes out to try and install the patch. the patch seems to install fine, But when i boot up WoW again, and try to login it brings me to the "patch downloaded sucsesfully" screen and click restart to install it, which it does the same thing again.

So i kill of the wine server using wineserver -k and switch back to X using alt+ctrl+f7

i run the downloader from a terminal no problem but when the patch trys to run, i get errors. Try running the patch all by itself w/o the downloader and get the same errors. Seems to be trying to debug something not sure.

This is the output from typing running the downloader (theres quite a bit)

```

shawn@Lung-Zilla:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW-1.5.1.4449-to-1.9.0.4937-enUS-downloader.exe
err:x11drv:X11DRV_CreateBitmap Trying to make bitmap with planes=1, bpp=32
I see Connection Info
I see 100% - Blizzard Downloader
I see Log
I see Connection Info
I see 100% - Blizzard Downloader
I see Log
shawn@Lung-Zilla:~/.wine/drive_c/Program Files/World of Warcraft$ fixme:actctx:CreateActCtxW stub!
wine: Unhandled exception (thread 0025), starting debugger...
WineDbg starting on pid 0x23
Unhandled exception: page fault on read access to 0x7c7aaebc in 32-bit code (0x7ee3f3b4).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:120f GS:0033
 EIP:7ee3f3b4 ESP:7c79d58c EBP:7c79d5b0 EFLAGS:00210202(   - 00      - -RI1)
 EAX:0000d78c EBX:7ee87168 ECX:0000d78c EDX:7c7aaebc
 ESI:7c79d730 EDI:00000002
Stack dump:
0x7c79d58c:  7ee4bfe9 7fe1f924 7fe1f8f8 00000000
0x7c79d59c:  7c79d5c8 65f143c4 7ee87168 7fe19300
0x7c79d5ac:  00000000 7c79d5dc 7ee3f3e9 7c79d730
0x7c79d5bc:  7ef7e312 7c79d5d4 7ef7ebab 00030046
0x7c79d5cc:  fffffff0 7c79d730 7fe19300 00000000
0x7c79d5dc:  7c79d5f8 7103601a 7c79d730 7fe19300
0241: sel=120f base=7fd93000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ee3f3b4 ILGetSize+0x78 in shell32 (0x7c79d5b0)
  2 0x7ee3f3e9 ILClone+0x28 in shell32 (0x7c79d5dc)
fixme:dbghelp:sffip_cb NIY on 'C:\Lego\opt\SHDOCVW.pdb'
  3 0x7103601a in shdocvw (+0x3601a) (0x7c79d5f8)
  4 0x7108e5d5 in shdocvw (+0x8e5d5) (0x7c79d614)
  5 0x7108bb85 in shdocvw (+0x8bb85) (0x7c79d6a4)
fixme:dbghelp:sffip_cb NIY on 'E:\8665\vc98\mfc\mfc.bbt\src\mfc42.pdb'
  6 0x5f422d69 2242+0x1d5 in mfc42 (0x7c79d730)
  7 0x5f4226dc 424+0xfbb in mfc42 (0x7c79d78c)
  8 0x5f421961 424+0x240 in mfc42 (0x7c79d7e4)
  9 0x5f4218d6 424+0x1b5 in mfc42 (0x7c79d83c)
  10 0x5f4211a5 1134+0x80c in mfc42 (0x7c79d904)
  11 0x5f420e29 1134+0x490 in mfc42 (0x7c79d950)
  12 0x5f420d2c 1134+0x393 in mfc42 (0x7c79d970)
  13 0x5f45d828 325+0x154 in mfc42 (0x7c79da08)
  14 0x5f401cea 540+0x35c in mfc42 (0x7c79da28)
  15 0x5f401c73 540+0x2e5 in mfc42 (0x7c79da88)
  16 0x5f401bfb 540+0x26d in mfc42 (0x7c79daa4)
  17 0x5f401bba 540+0x22c in mfc42 (0x7c79dad0)
  18 0x7ef84727 WINPROC_wrapper+0x17 in user32 (0x7c79daf4)
  19 0x7ef85234 in user32 (+0x95234) (0x7c79db30)
  20 0x7ef8adee CallWindowProcW+0x132 in user32 (0x7c79dfec)
  21 0x7ef55787 in user32 (+0x65787) (0x7c79e044)
  22 0x7ef59560 SendMessageTimeoutW+0x180 in user32 (0x7c79e09c)
  23 0x7ef595ba SendMessageW+0x50 in user32 (0x7c79e0c8)
  24 0x7ef28165 in user32 (+0x38165) (0x7c79e234)
  25 0x7ef29288 CreateDialogIndirectParamAorW+0x3e in user32 (0x7c79e250)
  26 0x7ef2939d CreateDialogIndirectParamA+0x41 in user32 (0x7c79e274)
  27 0x5f40a1a1 939+0x124 in mfc42 (0x7c79e2dc)
  28 0x5f40a35e 939+0x2e1 in mfc42 (0x7c79e528)
  29 0x7ef85234 in user32 (+0x95234) (0x7c79e564)
  30 0x7ef889ae CallWindowProcA+0x1b5 in user32 (0x7c79e5a8)
  31 0x7ef556f8 in user32 (+0x656f8) (0x7c79e600)
  32 0x7ef567b4 in user32 (+0x667b4) (0x7c79e8e0)
  33 0x7ef57fdb PeekMessageW+0x9a in user32 (0x7c79e930)
  34 0x7ef581e1 GetMessageW+0xdf in user32 (0x7c79e9e0)
  35 0x7ef58351 GetMessageA+0x33 in user32 (0x7c79ea00)
  36 0x00417327 EntryPoint+0x617 in bnupdate (0x7c79ec04)
  37 0x7bedcc61 in ntdll (+0x3cc61) (0x7c79f448)
  38 0xb7ee2361 start_thread+0x81 in libpthread.so.0 (0x7c79f4c8)
  39 0xb7e76bde __clone+0x5e in libc.so.6 (0x00000000)
0x7ee3f3b4 ILGetSize+0x78 in shell32: movzwl    0x0(%edx),%eax
Modules:
Module  Address                 Debug info      Name (69 modules)
PE      0x00400000-00491000     Export          bnupdate
PE      0x5a800000-5a80f000     Deferred        pstorec
PE      0x5e380000-5e3a5000     Deferred        msoss
PE      0x5f400000-5f4f2000     Export          mfc42
PE      0x65340000-653d2000     Deferred        oleaut32
PE      0x65f00000-65fc2000     Deferred        ole32
PE      0x70100000-70153000     Deferred        rpcrt4
PE      0x70200000-70295000     Deferred        wininet
PE      0x70bd0000-70c35000     Deferred        shlwapi
PE      0x71000000-71149000     Export          shdocvw
PE      0x71450000-714ae000     Deferred        crypt32
PE      0x78000000-78044000     Deferred        msvcrt
ELF     0x7be87000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7c4c7000-7c528000     Deferred        winedos<elf>
  \-PE  0x7c4d0000-7c528000     \               winedos
ELF     0x7c528000-7c53c000     Deferred        vwin32.vxd<elf>
  \-PE  0x7c530000-7c53c000     \               vwin32.vxd
ELF     0x7e09c000-7e0b9000     Deferred        imm32<elf>
  \-PE  0x7e0a0000-7e0b9000     \               imm32
ELF     0x7e0b9000-7e0d5000     Deferred        ximcp.so.2
ELF     0x7e0d5000-7e83e000     Deferred        libglcore.so.1
ELF     0x7e83e000-7e8bd000     Deferred        libgl.so.1
ELF     0x7e8bd000-7e97d000     Deferred        libx11.so.6
ELF     0x7e97d000-7e996000     Deferred        libice.so.6
ELF     0x7e996000-7ea18000     Deferred        winex11.drv<elf>
  \-PE  0x7e9b0000-7ea18000     \               winex11.drv
ELF     0x7ea18000-7ea37000     Deferred        libexpat.so.1
ELF     0x7ea37000-7ea65000     Deferred        libfontconfig.so.1
ELF     0x7ea72000-7ea86000     Deferred        libz.so.1
ELF     0x7ea86000-7eaf0000     Deferred        libfreetype.so.6
ELF     0x7ed12000-7ed16000     Deferred        libxfixes.so.3
ELF     0x7ed16000-7ed2a000     Deferred        lz32<elf>
  \-PE  0x7ed20000-7ed2a000     \               lz32
ELF     0x7ed2a000-7ed45000     Deferred        version<elf>
  \-PE  0x7ed30000-7ed45000     \               version
ELF     0x7ed45000-7ee04000     Deferred        comctl32<elf>
  \-PE  0x7ed50000-7ee04000     \               comctl32
ELF     0x7ee04000-7eeca000     Export          shell32<elf>
  \-PE  0x7ee20000-7eeca000     \               shell32
ELF     0x7eeca000-7eff6000     Export          user32<elf>
  \-PE  0x7eef0000-7eff6000     \               user32
ELF     0x7eff6000-7f037000     Deferred        advapi32<elf>
  \-PE  0x7f010000-7f037000     \               advapi32
ELF     0x7f11d000-7fa20000     Deferred        gdi32<elf>
  \-PE  0x7f170000-7fa20000     \               gdi32
ELF     0x7fb23000-7fb30000     Deferred        libxext.so.6
ELF     0x7fb34000-7fb3d000     Deferred        libxcursor.so.1
ELF     0x7fc85000-7fd90000     Deferred        kernel32<elf>
  \-PE  0x7fcb0000-7fd90000     \               kernel32
ELF     0x7fd95000-7fd99000     Deferred        libxdmcp.so.6
ELF     0x7fd99000-7fda0000     Deferred        libsm.so.6
ELF     0x7feb0000-7feb3000     Deferred        libxau.so.6
ELF     0x7feb3000-7febe000     Deferred        libgcc_s.so.1
ELF     0x7febe000-7fed3000     Deferred        libnsl.so.1
ELF     0x7fed3000-7fedc000     Deferred        libnss_compat.so.2
ELF     0x7fedd000-7fee5000     Deferred        libxrender.so.1
ELF     0x7fee5000-7fee7000     Deferred        xlcutf8load.so.2
ELF     0x7fee9000-7ff0b000     Deferred        libm.so.6
ELF     0x7ff0b000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7da0000-b7daa000     Deferred        libnss_files.so.2
ELF     0xb7dab000-b7dae000     Deferred        libdl.so.2
ELF     0xb7dae000-b7edc000     Export          libc.so.6
ELF     0xb7edd000-b7eef000     Export          libpthread.so.0
ELF     0xb7eef000-b7f08000     Deferred        libwine.so.1
ELF     0xb7f08000-b7f0a000     Deferred        libnvidia-tls.so.1
ELF     0xb7f0a000-b7f13000     Deferred        libnss_nis.so.2
ELF     0xb7f18000-b7f2e000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000023 (D) C:\Program Files\World of Warcraft\BNUpdate.exe
        00000025    0 <==
        00000024    0
0000000a
        00000022    0
        00000021    0
        0000000d    0
        0000000c    0
        0000000b    0
WineDbg terminated on pid 0x23

```

im using wine 20050725, I also run starcraft and Diablo II (big blizzard fan!) They run fine - sound problems due to sound emulation but thats fine.

Any ideas?

---

### Post by MacV on 2006-02-21
If I may ask, why are you using such an old version of wine?

---

### Post by lungdart on 2006-02-21
Because when I got it it was new?

When i added the wine repo to apt, my repo list bugged out on me and i replaced it, and never added wine again. Think an update would help?

**EDIT**: Updated to wine 0.9.8 and the same problem exists. Tried running wine BNUpdate.exe, and it couldnt find a patch so i tried wine BNUpdate WoW-1.5.1.4449=to-1.9.0.4937-enUS-patch.exe at which point it gave the error "patch.mpq not found, aborting update"
I do have a install on a windows machine thats fully upto date. I wonder if copying the files over from there would work. But that would be a horrible way to have to patch WoW for every update

---

### Post by Perfect Storm on 2006-02-21
You should try with the newest. Wow is everchanging so older version of wine might not work.

---

### Post by lungdart on 2006-02-21
I did, thus the edit on my last post.

Anyone else care to add there opinion on what i could do?

---

### Post by MacV on 2006-02-21
Since it says it's only missing the patch.mpq file, try copying the file from windows and putting it into the Linux comp. See if it can update afterwords.

---

### Post by lungdart on 2006-02-22
To get it working i coppied the entire contents of my windows install to my linux box after installing normally. Overwriting everything. (removing then copying would work just as good for anyone who reads this and gets stuck)

It wouldnt run because of a problematic "glow" setting in the WTF/Config.wtf file, with a quick swap with one i found on google (search for 'filletype:wtf Config' and right click and save one) it was up and running. Put back in the required wine settings to get it running correctly

```

SET gxApi "opengl"
SET SoundOutputSystem "1"
SET SoundBufferSize "100"

```

loaded it up and it worked flawlessly except i couldnt click on anything, which is a documented error that requires a manual compile of wine. I also lowered all the settings in the video menu and changed all my interface options to the way i like them.

Now im having no luck compiling my own wine with the correct patches. After doing so wine cant even load winecfg, and WoW gives me opengl.dll errors. Had to do a make uninstall and make distclean, and reinstall from apt. to get wine back up and running.

I did here that CVS now has the patches implemented by default. I might try doing that next. I don't want to get rid of my current wine though, I would like it if I had wine, and winecvs as seperate commands. Not sure how to do this though.

Help?

---

