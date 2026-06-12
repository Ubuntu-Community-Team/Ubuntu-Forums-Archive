---
title: "KOTOR2 and Edgy"
date: 2007-02-01
forum: Gaming &amp; Leisure
---

### Post by lololga on 2007-02-01
I'm currently running Ubuntu Edgy, with wine version 0.9.30; my graphics card is a ATI Radeon 9600XT with the latest drivers. I can't seem to get KOTOR2 to work for the life of me, when I try to run it I get this error log:

```
****@Saber2:~/.wine/drive_c/Program Files/LucasArts/SWKotOR2$ wine swkotor2.exe
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:wave:DSD_CreateSecondaryBuffer (0x15c0500,0x1aefcc,18000,0,0x1afb54,0x17df5c,0x1afb30): stub
err:ole:get_inproc_class_object couldn't load in-process dll L"a3dapi.dll"
err:ole:CoGetClassObject no class object {92fa2c24-253c-11d2-90fb-006008a1f441} could be created for context 0x1
fixme:wave:DSD_CreateSecondaryBuffer (0x17e4d0,0x1aefcc,18000,0,0x1601cec,0x1601ddc,0x1601cc8): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x17e4a8,0x1aefcc,18000,0,0x15b0b34,0x15b0c24,0x15b0b10): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x17e4a8,0xb0f424,12,0,0x1601e84,0x1611f9c,0x1601e60): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x17e4a8,0xb0f424,12,0,0x1601e6c,0x16123bc,0x1601e48): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x17e4a8,0xb0f424,12,0,0x1601e6c,0x16127dc,0x1601e48): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x17e4a8,0x16c034c,4000,0,0x1612fbc,0x16130cc,0x1612f98): stub
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=12248 < primary_done=12252)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=6392 < primary_done=6396)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=4744 < primary_done=4748)
err:wgl:X11DRV_wglGetProcAddress (wglAllocateMemoryNV) - not found
err:wgl:X11DRV_wglGetProcAddress (wglFreeMemoryNV) - not found
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreateBufferRegionARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDeleteBufferRegionARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglSaveBufferRegionARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglRestoreBufferRegionARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglSwapIntervalEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetSwapIntervalEXT) - not found
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 2129138996
err:wgl:X11DRV_wglCreatePbufferARB (0x20c): unexpected iPixelFormat(2129138996) > nFormats(1), returns NULL
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 11591412
err:wgl:X11DRV_wglCreatePbufferARB (0x20c): unexpected iPixelFormat(11591412) > nFormats(1), returns NULL
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 11591412
err:wgl:X11DRV_wglCreatePbufferARB (0x20c): unexpected iPixelFormat(11591412) > nFormats(1), returns NULL
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 11591412
err:wgl:X11DRV_wglCreatePbufferARB (0x20c): unexpected iPixelFormat(11591412) > nFormats(1), returns NULL
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 11591412
err:wgl:X11DRV_wglCreatePbufferARB (0x20c): unexpected iPixelFormat(11591412) > nFormats(1), returns NULL
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 11591412
err:wgl:X11DRV_wglCreatePbufferARB (0x20c): unexpected iPixelFormat(11591412) > nFormats(1), returns NULL
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 11591412
err:wgl:X11DRV_wglCreatePbufferARB (0x20c): unexpected iPixelFormat(11591412) > nFormats(1), returns NULL
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:00b0f748 EBP:00b0f904 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000000 EBX:00000000 ECX:00000001 EDX:7e5a6101
 ESI:ffffffff EDI:7ee6a790
Stack dump:
0x00b0f748:  00462542 00000001 00010026 00000001
0x00b0f758:  007b9630 00000000 00e096a8 00000000
0x00b0f768:  00d77ac8 00000001 00000000 00000000
0x00b0f778:  00000320 00000258 00010028 00000025
0x00b0f788:  18082000 08081008 00000008 18000000
0x00b0f798:  00000008 00000000 00000000 00000000
Backtrace:
=>1 0x00000000 (0x00b0f904)
  2 0x00403ad1 in swkotor2 (+0x3ad1) (0x00b0f9a4)
  3 0x0063caf7 in swkotor2 (+0x23caf7) (0x00b0fa90)
  4 0x0064147c in swkotor2 (+0x24147c) (0x00b0fb80)
  5 0x00644b15 in swkotor2 (+0x244b15) (0x00b0fd34)
  6 0x004044e4 in swkotor2 (+0x44e4) (0x00b0fde0)
  7 0x0076e45e in swkotor2 (+0x36e45e) (0x00b0ff08)
  8 0x7b8702be in kernel32 (+0x502be) (0x00b0ffe8)
  9 0xb7e79587 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00000000: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (89 modules)
PE      350000-388000   Deferred        msseax.m3d
PE      400000-8f2000   Export          swkotor2
PE      21100000-21164000       Deferred        mss32
PE      22100000-2211d000       Deferred        mssa3d.m3d
PE      22300000-22315000       Deferred        mssds3d.m3d
PE      22400000-22419000       Deferred        msssoft.m3d
PE      22600000-22618000       Deferred        mssdx7.m3d
PE      22700000-22768000       Deferred        mssrsx.m3d
PE      24100000-24120000       Deferred        mssdsp.flt
PE      26400000-26439000       Deferred        mssvoice.asi
PE      26f00000-26f2e000       Deferred        mssmp3.asi
PE      30000000-3006d000       Deferred        binkw32
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc94000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc94000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c48d000-7c4d6000       Deferred        dsound<elf>
  \-PE  7c4a0000-7c4d6000       \               dsound
ELF     7c6ec000-7c701000       Deferred        midimap<elf>
  \-PE  7c6f0000-7c701000       \               midimap
ELF     7c727000-7c73f000       Deferred        msacm32<elf>
  \-PE  7c730000-7c73f000       \               msacm32
ELF     7c73f000-7c77b000       Deferred        wineoss<elf>
  \-PE  7c750000-7c77b000       \               wineoss
ELF     7c77b000-7c780000       Deferred        libxfixes.so.3
ELF     7c780000-7c79e000       Deferred        ximcp.so.2
ELF     7d1c7000-7d1d0000       Deferred        libxcursor.so.1
ELF     7d2d1000-7d2d3000       Deferred        xlcutf8load.so.2
ELF     7db63000-7db6c000       Deferred        librt.so.1
ELF     7db6c000-7db6f000       Deferred        libxrandr.so.2
ELF     7db6f000-7db77000       Deferred        libxrender.so.1
ELF     7db77000-7db7a000       Deferred        libxinerama.so.1
ELF     7dc3c000-7e51f000       Deferred        fglrx_dri.so
ELF     7e51f000-7e5ac000       Deferred        winex11<elf>
  \-PE  7e530000-7e5ac000       \               winex11
ELF     7e5ac000-7e5ca000       Deferred        libexpat.so.1
ELF     7e5ca000-7e5f9000       Deferred        libfontconfig.so.1
ELF     7e5f9000-7e60d000       Deferred        libz.so.1
ELF     7e60d000-7e67b000       Deferred        libfreetype.so.6
ELF     7e67b000-7e697000       Deferred        imm32<elf>
  \-PE  7e680000-7e697000       \               imm32
ELF     7e697000-7e6ab000       Deferred        lz32<elf>
  \-PE  7e6a0000-7e6ab000       \               lz32
ELF     7e6ab000-7e6c4000       Deferred        version<elf>
  \-PE  7e6b0000-7e6c4000       \               version
ELF     7e6c4000-7e6fa000       Deferred        dinput<elf>
  \-PE  7e6d0000-7e6fa000       \               dinput
ELF     7e6fa000-7e713000       Deferred        dinput8<elf>
  \-PE  7e700000-7e713000       \               dinput8
ELF     7e713000-7e7a1000       Deferred        winmm<elf>
  \-PE  7e720000-7e7a1000       \               winmm
ELF     7e7a1000-7e7b4000       Deferred        libresolv.so.2
ELF     7e7b4000-7e7d2000       Deferred        iphlpapi<elf>
  \-PE  7e7c0000-7e7d2000       \               iphlpapi
ELF     7e7d2000-7e827000       Deferred        rpcrt4<elf>
  \-PE  7e7e0000-7e827000       \               rpcrt4
ELF     7e827000-7e8c0000       Deferred        ole32<elf>
  \-PE  7e840000-7e8c0000       \               ole32
ELF     7e8c0000-7e906000       Deferred        advapi32<elf>
  \-PE  7e8d0000-7e906000       \               advapi32
ELF     7e906000-7e9bd000       Deferred        gdi32<elf>
  \-PE  7e920000-7e9bd000       \               gdi32
ELF     7e9bd000-7eaf6000       Deferred        user32<elf>
  \-PE  7e9e0000-7eaf6000       \               user32
ELF     7eaf6000-7eb01000       Deferred        libgcc_s.so.1
ELF     7eb01000-7eb17000       Deferred        glu32<elf>
  \-PE  7eb10000-7eb17000       \               glu32
ELF     7ebf6000-7ebfb000       Deferred        libxdmcp.so.6
ELF     7ebfb000-7ec75000       Deferred        libglu.so.1
ELF     7ec75000-7ed15000       Deferred        libgl.so.1
ELF     7ed15000-7edde000       Deferred        libx11.so.6
ELF     7edde000-7edeb000       Deferred        libxext.so.6
ELF     7edeb000-7ee03000       Deferred        libice.so.6
ELF     7ee03000-7ee0c000       Deferred        libsm.so.6
ELF     7ee0c000-7ee86000       Deferred        opengl32<elf>
  \-PE  7ee20000-7ee86000       \               opengl32
ELF     7ef90000-7ef9b000       Deferred        libnss_files.so.2
ELF     7ef9b000-7efa5000       Deferred        libnss_nis.so.2
ELF     7efa5000-7efbb000       Deferred        libnsl.so.1
ELF     7efbb000-7efc4000       Deferred        libnss_compat.so.2
ELF     7efc4000-7efea000       Deferred        libm.so.6
ELF     7efed000-7eff2000       Deferred        libxxf86vm.so.1
ELF     b7d11000-b7d15000       Deferred        libdl.so.2
ELF     b7d15000-b7e49000       Deferred        libc.so.6
ELF     b7e49000-b7e5c000       Deferred        libpthread.so.0
ELF     b7e5c000-b7e5f000       Deferred        libxau.so.6
ELF     b7e72000-b7f83000       Export          libwine.so.1
ELF     b7f85000-b7fa0000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\LucasArts\SWKotOR2\swkotor2.exe
        00000013   15
        00000010   15
        0000000e    0
        0000000d   -2
        00000009    0 <==
```

Anyone know what might be up?

---

### Post by Mongoose on 2007-02-01
Run glxinfo to make sure your OpenGL is working ok, and if that is the case try rolling back to 0.9.29 and my other suggestions in my Oblivion HOWTO:

[http://ubuntuforums.org/showpost.php?p=2084780&postcount=1](http://ubuntuforums.org/showpost.php?p=2084780&postcount=1)

Wine 0.9.30 introducted more shader caps support in d3d, which broke a lot of games.  I can't wait until all the issues exposed by this are sorted out hopefully in time for the next release.  Aside from render errors in meshes 0.9.30 renders much better -- assuming you can see anything with the bad skinning. ;)

---

### Post by lololga on 2007-02-01
I tried downgrading to 0.9.29 and playing but I've had no luck there.

Also, I get this when using "Scan Hardware" in the KOTOR2 settings:
[http://img525.imageshack.us/img525/4057/kotor2jm0.jpg](http://img525.imageshack.us/img525/4057/kotor2jm0.jpg)

Not sure if that's abnormal or not.

---

### Post by Mongoose on 2007-02-02
Well, I honestly can't tell you what to expect with ATi.  Depending on which driver you're using you'll see mixed results.  I didn't get much else out of that utility.   =)

---

