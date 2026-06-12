---
title: "Warcraft III and Wine"
date: 2007-05-15
forum: Gaming &amp; Leisure
---

### Post by Memory.Dump on 2007-05-15
ok, so I have wine installed, I installed w III no problem, disc in tray, check, nvidia drivers installed (nvidia screen even loads up before ubuntu screen so I know its working) but...

when I go to run warcraft III all I get is a black screen and the computer seems to lock up I can't get out of it short of resetting the computer, any ideas as to why?

---

### Post by Frem on 2007-05-15
No clue. Are you running Warcraft III with the -gl flag? (aka, "wine warcraft3.exe -gl")
Using that flag solves a lot of problems you can have running Blizzard games under Linux.

---

### Post by Memory.Dump on 2007-05-15
I was just running it as the default icon it creates when you install it through, wine, I'll check that when I get home, thanks for the input

---

### Post by Hobo Joe on 2007-05-15
Could you link me to a howto for installing WC3 in WINE?

That would be great, thanks. :)

---

### Post by Matthaeus on 2007-05-15
Have you tried disabling 3d-desktop effects before starting the game? IE If your running beryl, switch to metacity.

Also, wine used to freeze when trying to play the intro movie.....so you would have to delete all of the files in the movie folder. This issue has apparently been fixed though.

[http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)
[http://appdb.winehq.org/appview.php?iVersionId=3126](http://appdb.winehq.org/appview.php?iVersionId=3126)


RHCP.

---

### Post by Hobo Joe on 2007-05-15
I installed WC3 then WC3:FT and this is the error I get when I try to run FT:

```

joseph@Schoolroom:~$ wine /media/cdrom0/install.exe
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
joseph@Schoolroom:~$ fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
err:ole:CoCreateInstance apartment not initialised
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1b14d0) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:quartz:AVISplitter_InputPin_PreConnect process ODML header
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0xd90020) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1c4398)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
err:ole:CoGetClassObject class {e30629d1-27e5-11ce-875d-00608cb78066} not registered
err:ole:CoGetClassObject no class object {e30629d1-27e5-11ce-875d-00608cb78066} could be created for context 0x1
err:quartz:GraphBuilder_Render Unable to create filter (80040154), trying next one
err:quartz:DSoundRender_create Cannot create Direct Sound object (88780078)
fixme:ole:CoCreateInstance no instance created for interface {56a86895-0ad4-11ce-b03a-0020af0ba770} of class {79376820-07d0-11cf-a24d-0020afd79767}, hres is 0x88780078
err:quartz:GraphBuilder_Render Unable to create filter (88780078), trying next one
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:PullPin_Seek (0x1b0b48)->(000000000, 7fffffffffffffff)
fixme:quartz:PullPin_BeginFlush (0x1b0b48)->()
fixme:quartz:PullPin_EndFlush (0x1b0b48)->()
wine: Unhandled page fault on read access to 0x00000000 at address 0x6f0c7930 (thread 0059), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x6f0c7930).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6f0c7930 ESP:0034f470 EBP:0034f480 EFLAGS:00010213(   - 00      -RIA1C)
 EAX:00000006 EBX:7b863ad0 ECX:00000000 EDX:7c0118d8
 ESI:00000001 EDI:7b8656d0
Stack dump:
0x0034f470:  00000000 0034f498 6f0c7b2d 003f00b8
0x0034f480:  0034f5b4 6f0066f3 6f7b404c 00000000
0x0034f490:  0034f59c 6f000000 505c3a43 72676f72
0x0034f4a0:  46206d61 73656c69 7261575c 66617263
0x0034f4b0:  49492074 6f4d5c49 73656976 7475545c
0x0034f4c0:  6169726f 2e6e496c 0071706d 0034f4d4
Backtrace:
=>1 0x6f0c7930 in game (+0xc7930) (0x0034f480)
  2 0x6f0066f3 in game (+0x66f3) (0x0034f5b4)
  3 0x6f006013 in game (+0x6013) (0x0034f6c4)
  4 0x00401219 in war3 (+0x1219) (0x0034f770)
  5 0x00401d68 in war3 (+0x1d68) (0x0034f80c)
  6 0x0034fef8 (0x0034fe7c)
  7 0x004ce968 in war3 (+0xce968) (0x0034ff08)
  8 0x7b873d5e in kernel32 (+0x53d5e) (0x0034ffe8)
  9 0xb7e29877 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x6f0c7930: movl        0x0(%ecx),%edx
Modules:
Module  Address                 Debug info      Name (106 modules)
PE        400000-  56a000       Export          war3
PE      10000000-10016000       Deferred        cmdlineext02
PE      15000000-15064000       Deferred        storm
PE      21100000-2115f000       Deferred        mss32
PE      60000000-6005d000       Deferred        ijl15
PE      6f000000-6f878000       Export          game
ELF     7b800000-7b927000       Export          kernel32<elf>
  \-PE  7b820000-7b927000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c85a000-7c91f000       Deferred        wined3d<elf>
  \-PE  7c870000-7c91f000       \               wined3d
ELF     7cda7000-7ce27000       Deferred        libglu.so.1
ELF     7ce27000-7cea8000       Deferred        opengl32<elf>
  \-PE  7ce40000-7cea8000       \               opengl32
ELF     7cea8000-7cf43000       Deferred        oleaut32<elf>
  \-PE  7cec0000-7cf43000       \               oleaut32
ELF     7cf43000-7cf58000       Deferred        midimap<elf>
  \-PE  7cf50000-7cf58000       \               midimap
ELF     7cf58000-7cf7e000       Deferred        msacm32<elf>
  \-PE  7cf60000-7cf7e000       \               msacm32
ELF     7cf7e000-7cf96000       Deferred        msacm32<elf>
  \-PE  7cf80000-7cf96000       \               msacm32
ELF     7cf96000-7cfd2000       Deferred        wineoss<elf>
  \-PE  7cfa0000-7cfd2000       \               wineoss
ELF     7cfd2000-7d023000       Deferred        libgcrypt.so.11
ELF     7d023000-7d038000       Deferred        libtasn1.so.3
ELF     7d038000-7d066000       Deferred        libcrypt.so.1
ELF     7d074000-7d0e4000       Deferred        libgnutls.so.13
ELF     7d0e4000-7d115000       Deferred        libcups.so.2
ELF     7d139000-7d18e000       Deferred        rpcrt4<elf>
  \-PE  7d150000-7d18e000       \               rpcrt4
ELF     7d18e000-7d22b000       Deferred        ole32<elf>
  \-PE  7d1a0000-7d22b000       \               ole32
ELF     7d4da000-7d4de000       Deferred        libgpg-error.so.0
ELF     7d4de000-7d510000       Deferred        uxtheme<elf>
  \-PE  7d4f0000-7d510000       \               uxtheme
ELF     7d512000-7d517000       Deferred        libxfixes.so.3
ELF     7d517000-7d520000       Deferred        libxcursor.so.1
ELF     7d520000-7d526000       Deferred        libxrandr.so.2
ELF     7d526000-7d52e000       Deferred        libxrender.so.1
ELF     7d925000-7e297000       Deferred        libglcore.so.1
ELF     7e297000-7e32b000       Deferred        libgl.so.1
ELF     7e32b000-7e330000       Deferred        libxdmcp.so.6
ELF     7e330000-7e421000       Deferred        libx11.so.6
ELF     7e421000-7e42f000       Deferred        libxext.so.6
ELF     7e42f000-7e434000       Deferred        libxxf86vm.so.1
ELF     7e434000-7e44c000       Deferred        libice.so.6
ELF     7e44c000-7e455000       Deferred        libsm.so.6
ELF     7e455000-7e4e4000       Deferred        winex11<elf>
  \-PE  7e460000-7e4e4000       \               winex11
ELF     7e57d000-7e59d000       Deferred        libexpat.so.1
ELF     7e59d000-7e5c8000       Deferred        libfontconfig.so.1
ELF     7e5c8000-7e5dc000       Deferred        libz.so.1
ELF     7e5dc000-7e647000       Deferred        libfreetype.so.6
ELF     7e647000-7e666000       Deferred        mpr<elf>
  \-PE  7e650000-7e666000       \               mpr
ELF     7e666000-7e6ae000       Deferred        wininet<elf>
  \-PE  7e670000-7e6ae000       \               wininet
ELF     7e6ae000-7e6cb000       Deferred        imm32<elf>
  \-PE  7e6c0000-7e6cb000       \               imm32
ELF     7e6cb000-7e6de000       Deferred        libresolv.so.2
ELF     7e6de000-7e6fc000       Deferred        iphlpapi<elf>
  \-PE  7e6f0000-7e6fc000       \               iphlpapi
ELF     7e6fc000-7e729000       Deferred        ws2_32<elf>
  \-PE  7e710000-7e729000       \               ws2_32
ELF     7e729000-7e743000       Deferred        wsock32<elf>
  \-PE  7e730000-7e743000       \               wsock32
ELF     7e743000-7e757000       Deferred        lz32<elf>
  \-PE  7e750000-7e757000       \               lz32
ELF     7e757000-7e770000       Deferred        version<elf>
  \-PE  7e760000-7e770000       \               version
ELF     7e770000-7e7d7000       Deferred        msvcrt<elf>
  \-PE  7e780000-7e7d7000       \               msvcrt
ELF     7e7d7000-7e866000       Deferred        winmm<elf>
  \-PE  7e7e0000-7e866000       \               winmm
ELF     7e866000-7e899000       Deferred        winspool<elf>
  \-PE  7e870000-7e899000       \               winspool
ELF     7e899000-7e955000       Deferred        comctl32<elf>
  \-PE  7e8a0000-7e955000       \               comctl32
ELF     7e955000-7e9ad000       Deferred        shlwapi<elf>
  \-PE  7e960000-7e9ad000       \               shlwapi
ELF     7e9ad000-7eaa8000       Deferred        shell32<elf>
  \-PE  7e9c0000-7eaa8000       \               shell32
ELF     7eaa8000-7eb48000       Deferred        comdlg32<elf>
  \-PE  7eab0000-7eb48000       \               comdlg32
ELF     7eb48000-7eb8f000       Deferred        advapi32<elf>
  \-PE  7eb50000-7eb8f000       \               advapi32
ELF     7eb8f000-7eb9b000       Deferred        libgcc_s.so.1
ELF     7ec85000-7ed44000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed44000       \               gdi32
ELF     7ed44000-7ee80000       Deferred        user32<elf>
  \-PE  7ed60000-7ee80000       \               user32
ELF     7ee80000-7ee8b000       Deferred        libnss_files.so.2
ELF     7ee8b000-7eea2000       Deferred        libnsl.so.1
ELF     7eea2000-7eeab000       Deferred        libnss_compat.so.2
ELF     7efcb000-7eff2000       Deferred        libm.so.6
ELF     7eff4000-7eff6000       Deferred        libnvidia-tls.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cb0000-b7cb3000       Deferred        libxau.so.6
ELF     b7cb7000-b7cbb000       Deferred        libdl.so.2
ELF     b7cbb000-b7dfc000       Deferred        libc.so.6
ELF     b7dfd000-b7e14000       Deferred        libpthread.so.0
ELF     b7e22000-b7f33000       Export          libwine.so.1
ELF     b7f35000-b7f50000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000058 (D) C:\Program Files\Warcraft III\War3.exe
        0000005e    0
        0000005c    0
        0000005b    1
        0000005a    0
        00000059    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000042    0
        00000041    0
        00000040    1
        0000003f    0
        0000003e    1
        0000003c    0
        00000038    0
        00000035    0
        00000034    0
        00000033    0
        00000032    0
        00000031    0
        00000030    0
        0000002f    0
        0000002e    1
        0000002d    0
        0000002c    1
        0000002b    0
        0000002a    1
        00000029    0
        00000028    1
        00000027    0
        00000026    1
        00000025    0
        00000024    1
        00000020    0
        0000001f    0
        0000001d    0
        0000001c    1
        0000001a    0
        00000019    0
        00000017    0
        00000016    0
        00000015    1
        00000014    0
        00000013    0
        00000012    0
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        00000009    0

```

And ideas? I'm stumped. :/

---

### Post by Memory.Dump on 2007-05-16
yeah it worked fine after I added the -opengl thing, thanks, as for your issue hobo, I dunno, I just go to apps and accessories open the wine viewer and run it from the explorer, it works fine from that for me

---

### Post by Nehvrook on 2007-05-23
> **Hobo Joe said:**
> I installed WC3 then WC3:FT and this is the error I get when I try to run FT:

```

joseph@Schoolroom:~$ wine /media/cdrom0/install.exe
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
joseph@Schoolroom:~$ fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
err:ole:CoCreateInstance apartment not initialised
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1b14d0) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:quartz:AVISplitter_InputPin_PreConnect process ODML header
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0xd90020) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1c4398)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
err:ole:CoGetClassObject class {e30629d1-27e5-11ce-875d-00608cb78066} not registered
err:ole:CoGetClassObject no class object {e30629d1-27e5-11ce-875d-00608cb78066} could be created for context 0x1
err:quartz:GraphBuilder_Render Unable to create filter (80040154), trying next one
err:quartz:DSoundRender_create Cannot create Direct Sound object (88780078)
fixme:ole:CoCreateInstance no instance created for interface {56a86895-0ad4-11ce-b03a-0020af0ba770} of class {79376820-07d0-11cf-a24d-0020afd79767}, hres is 0x88780078
err:quartz:GraphBuilder_Render Unable to create filter (88780078), trying next one
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:PullPin_Seek (0x1b0b48)->(000000000, 7fffffffffffffff)
fixme:quartz:PullPin_BeginFlush (0x1b0b48)->()
fixme:quartz:PullPin_EndFlush (0x1b0b48)->()
wine: Unhandled page fault on read access to 0x00000000 at address 0x6f0c7930 (thread 0059), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x6f0c7930).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6f0c7930 ESP:0034f470 EBP:0034f480 EFLAGS:00010213(   - 00      -RIA1C)
 EAX:00000006 EBX:7b863ad0 ECX:00000000 EDX:7c0118d8
 ESI:00000001 EDI:7b8656d0
Stack dump:
0x0034f470:  00000000 0034f498 6f0c7b2d 003f00b8
0x0034f480:  0034f5b4 6f0066f3 6f7b404c 00000000
0x0034f490:  0034f59c 6f000000 505c3a43 72676f72
0x0034f4a0:  46206d61 73656c69 7261575c 66617263
0x0034f4b0:  49492074 6f4d5c49 73656976 7475545c
0x0034f4c0:  6169726f 2e6e496c 0071706d 0034f4d4
Backtrace:
=>1 0x6f0c7930 in game (+0xc7930) (0x0034f480)
  2 0x6f0066f3 in game (+0x66f3) (0x0034f5b4)
  3 0x6f006013 in game (+0x6013) (0x0034f6c4)
  4 0x00401219 in war3 (+0x1219) (0x0034f770)
  5 0x00401d68 in war3 (+0x1d68) (0x0034f80c)
  6 0x0034fef8 (0x0034fe7c)
  7 0x004ce968 in war3 (+0xce968) (0x0034ff08)
  8 0x7b873d5e in kernel32 (+0x53d5e) (0x0034ffe8)
  9 0xb7e29877 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x6f0c7930: movl        0x0(%ecx),%edx
Modules:
Module  Address                 Debug info      Name (106 modules)
PE        400000-  56a000       Export          war3
PE      10000000-10016000       Deferred        cmdlineext02
PE      15000000-15064000       Deferred        storm
PE      21100000-2115f000       Deferred        mss32
PE      60000000-6005d000       Deferred        ijl15
PE      6f000000-6f878000       Export          game
ELF     7b800000-7b927000       Export          kernel32<elf>
  \-PE  7b820000-7b927000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c85a000-7c91f000       Deferred        wined3d<elf>
  \-PE  7c870000-7c91f000       \               wined3d
ELF     7cda7000-7ce27000       Deferred        libglu.so.1
ELF     7ce27000-7cea8000       Deferred        opengl32<elf>
  \-PE  7ce40000-7cea8000       \               opengl32
ELF     7cea8000-7cf43000       Deferred        oleaut32<elf>
  \-PE  7cec0000-7cf43000       \               oleaut32
ELF     7cf43000-7cf58000       Deferred        midimap<elf>
  \-PE  7cf50000-7cf58000       \               midimap
ELF     7cf58000-7cf7e000       Deferred        msacm32<elf>
  \-PE  7cf60000-7cf7e000       \               msacm32
ELF     7cf7e000-7cf96000       Deferred        msacm32<elf>
  \-PE  7cf80000-7cf96000       \               msacm32
ELF     7cf96000-7cfd2000       Deferred        wineoss<elf>
  \-PE  7cfa0000-7cfd2000       \               wineoss
ELF     7cfd2000-7d023000       Deferred        libgcrypt.so.11
ELF     7d023000-7d038000       Deferred        libtasn1.so.3
ELF     7d038000-7d066000       Deferred        libcrypt.so.1
ELF     7d074000-7d0e4000       Deferred        libgnutls.so.13
ELF     7d0e4000-7d115000       Deferred        libcups.so.2
ELF     7d139000-7d18e000       Deferred        rpcrt4<elf>
  \-PE  7d150000-7d18e000       \               rpcrt4
ELF     7d18e000-7d22b000       Deferred        ole32<elf>
  \-PE  7d1a0000-7d22b000       \               ole32
ELF     7d4da000-7d4de000       Deferred        libgpg-error.so.0
ELF     7d4de000-7d510000       Deferred        uxtheme<elf>
  \-PE  7d4f0000-7d510000       \               uxtheme
ELF     7d512000-7d517000       Deferred        libxfixes.so.3
ELF     7d517000-7d520000       Deferred        libxcursor.so.1
ELF     7d520000-7d526000       Deferred        libxrandr.so.2
ELF     7d526000-7d52e000       Deferred        libxrender.so.1
ELF     7d925000-7e297000       Deferred        libglcore.so.1
ELF     7e297000-7e32b000       Deferred        libgl.so.1
ELF     7e32b000-7e330000       Deferred        libxdmcp.so.6
ELF     7e330000-7e421000       Deferred        libx11.so.6
ELF     7e421000-7e42f000       Deferred        libxext.so.6
ELF     7e42f000-7e434000       Deferred        libxxf86vm.so.1
ELF     7e434000-7e44c000       Deferred        libice.so.6
ELF     7e44c000-7e455000       Deferred        libsm.so.6
ELF     7e455000-7e4e4000       Deferred        winex11<elf>
  \-PE  7e460000-7e4e4000       \               winex11
ELF     7e57d000-7e59d000       Deferred        libexpat.so.1
ELF     7e59d000-7e5c8000       Deferred        libfontconfig.so.1
ELF     7e5c8000-7e5dc000       Deferred        libz.so.1
ELF     7e5dc000-7e647000       Deferred        libfreetype.so.6
ELF     7e647000-7e666000       Deferred        mpr<elf>
  \-PE  7e650000-7e666000       \               mpr
ELF     7e666000-7e6ae000       Deferred        wininet<elf>
  \-PE  7e670000-7e6ae000       \               wininet
ELF     7e6ae000-7e6cb000       Deferred        imm32<elf>
  \-PE  7e6c0000-7e6cb000       \               imm32
ELF     7e6cb000-7e6de000       Deferred        libresolv.so.2
ELF     7e6de000-7e6fc000       Deferred        iphlpapi<elf>
  \-PE  7e6f0000-7e6fc000       \               iphlpapi
ELF     7e6fc000-7e729000       Deferred        ws2_32<elf>
  \-PE  7e710000-7e729000       \               ws2_32
ELF     7e729000-7e743000       Deferred        wsock32<elf>
  \-PE  7e730000-7e743000       \               wsock32
ELF     7e743000-7e757000       Deferred        lz32<elf>
  \-PE  7e750000-7e757000       \               lz32
ELF     7e757000-7e770000       Deferred        version<elf>
  \-PE  7e760000-7e770000       \               version
ELF     7e770000-7e7d7000       Deferred        msvcrt<elf>
  \-PE  7e780000-7e7d7000       \               msvcrt
ELF     7e7d7000-7e866000       Deferred        winmm<elf>
  \-PE  7e7e0000-7e866000       \               winmm
ELF     7e866000-7e899000       Deferred        winspool<elf>
  \-PE  7e870000-7e899000       \               winspool
ELF     7e899000-7e955000       Deferred        comctl32<elf>
  \-PE  7e8a0000-7e955000       \               comctl32
ELF     7e955000-7e9ad000       Deferred        shlwapi<elf>
  \-PE  7e960000-7e9ad000       \               shlwapi
ELF     7e9ad000-7eaa8000       Deferred        shell32<elf>
  \-PE  7e9c0000-7eaa8000       \               shell32
ELF     7eaa8000-7eb48000       Deferred        comdlg32<elf>
  \-PE  7eab0000-7eb48000       \               comdlg32
ELF     7eb48000-7eb8f000       Deferred        advapi32<elf>
  \-PE  7eb50000-7eb8f000       \               advapi32
ELF     7eb8f000-7eb9b000       Deferred        libgcc_s.so.1
ELF     7ec85000-7ed44000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed44000       \               gdi32
ELF     7ed44000-7ee80000       Deferred        user32<elf>
  \-PE  7ed60000-7ee80000       \               user32
ELF     7ee80000-7ee8b000       Deferred        libnss_files.so.2
ELF     7ee8b000-7eea2000       Deferred        libnsl.so.1
ELF     7eea2000-7eeab000       Deferred        libnss_compat.so.2
ELF     7efcb000-7eff2000       Deferred        libm.so.6
ELF     7eff4000-7eff6000       Deferred        libnvidia-tls.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cb0000-b7cb3000       Deferred        libxau.so.6
ELF     b7cb7000-b7cbb000       Deferred        libdl.so.2
ELF     b7cbb000-b7dfc000       Deferred        libc.so.6
ELF     b7dfd000-b7e14000       Deferred        libpthread.so.0
ELF     b7e22000-b7f33000       Export          libwine.so.1
ELF     b7f35000-b7f50000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000058 (D) C:\Program Files\Warcraft III\War3.exe
        0000005e    0
        0000005c    0
        0000005b    1
        0000005a    0
        00000059    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000042    0
        00000041    0
        00000040    1
        0000003f    0
        0000003e    1
        0000003c    0
        00000038    0
        00000035    0
        00000034    0
        00000033    0
        00000032    0
        00000031    0
        00000030    0
        0000002f    0
        0000002e    1
        0000002d    0
        0000002c    1
        0000002b    0
        0000002a    1
        00000029    0
        00000028    1
        00000027    0
        00000026    1
        00000025    0
        00000024    1
        00000020    0
        0000001f    0
        0000001d    0
        0000001c    1
        0000001a    0
        00000019    0
        00000017    0
        00000016    0
        00000015    1
        00000014    0
        00000013    0
        00000012    0
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        00000009    0

```

And ideas? I'm stumped. :/

I have the same problem, almost the exact same errors in the terminal. This is with the -gl on the end, before that it just went to a black screen then back to the desktop sitting in the terminal doing nothing.

---

### Post by Memory.Dump on 2007-05-25
when I did -gl it didn't help but when I did -opengl it worked, not sure what the diff is but theres that

---

### Post by Nehvrook on 2007-05-26
Yup adding -opengl worked fine. Thanks for the help :)

---

### Post by Kzap333 on 2007-06-22
> **Nehvrook said:**
> Yup adding -opengl worked fine. Thanks for the help :)
DOH!!! I found this just after I figerd out I had to add -opengl on the end.
I most screen shots I've seen Warcraft 3 is running in a window how do  you do this or at least how do you stop it flickering with the ubuntu menu and the bar at the top. (I hope you know what I mean)

---

### Post by reflexsa on 2010-03-14
Well I got mine to run fullscreen and it does not show the menu bar.

I installed that "compiz" thing which lets you open a thing called "Advance Desktop Effects Settings" from the system preferences menu.

In that program you can select "Window rules" and where is says "Fullscreen" put this in there: class=wine

Hope this helps

---

