---
title: "Freezes when running Wine."
date: 2007-08-07
forum: Gaming &amp; Leisure
---

### Post by SyrussScaleskin on 2007-08-07
For some reason, whenever I try to run anything on Wine, it completely freezes the entire system, I then have to turn the power off in order to reboot.

Originally I got xserver errors, until I set up OpenChrome on here, as it seemed to be the only way to deal with issues with my graphics chipset (Unichrome Pro S3 via chipset, K8M800 )

The setup works until I reach the test...

 glxinfo | grep render

at which point, the same thing happens.. ie. system locks up.

Does anyone else have this problem, or a suggestion as to how I can get round it?

---

### Post by hikaricore on 2007-08-07
If glxinfo is crashing your system, there is definately a hardware or driver issue related to your video card.
Your driver/card may not support direct rendering under Linux.  Or possibly you need to adjust some settings or use a different driver.

I'm not familiar with your card, just throwing it out there for ya.

---

### Post by SyrussScaleskin on 2007-08-07
Any suggestions on a different driver to OpenChrome? ... I've had no luck with finding any.

EDIT: I just found something which I installed from elsewhere on these forums..

The system no longer completely locks up upon glxinfo | grep render

Instead I get this:

do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.
direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome (K8M800) 20060710 x86/MMX+/3DNow!+/SSE2


Anyone know how to solve this one?

(And I am starting to think at this point I probably posted this topic in the wrong section by mistake... apologies for that)

---

### Post by reloadSE on 2007-08-07
I have the same problem but I'm running a nvidia  GeForce 6100 nForce 430 and it says i have the latest drivers anyone help?:confused: :)

---

### Post by SyrussScaleskin on 2007-08-08
Completely at random... it's working.. the test gives me the following:

direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome (K8M800) 20060710 x86/MMX+/3DNow!+/SSE2


However, if I try to run games via Wine, I either get:

Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.

and nothing... not even a prompt after that...
or:

fixme:wave:DSD_CreateSecondaryBuffer (0x179150,0x696f80,80,0,0x18a820,0x18a90c,0x18a800): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x179150,0x696f80,80,0,0x19a9f8,0x19aae4,0x19a9d8): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x179150,0x696f80,80,0,0x1aabb8,0x1aaca4,0x1aab98): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x179150,0x696f80,80,0,0x1bad78,0x1bae64,0x1bad58): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x179150,0x696f80,80,0,0x1caf38,0x1cb024,0x1caf18): stub
main/renderbuffer.c:2041: _mesa_add_renderbuffer: Assertion `bufferName == BUFFER_DEPTH || bufferName == BUFFER_STENCIL || fb->Attachment[bufferName].Renderbuffer == ((void *)0)' failed.
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...
Unhandled exception: assertion failed in 32-bit code (0xffffe410).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:ffffe410 ESP:0032f3a4 EBP:0032f3bc EFLAGS:00000206(   - 00      - -IP1)
 EAX:00000000 EBX:000016e8 ECX:000016e8 EDX:00000006
 ESI:0032f45c EDI:b7da5ff4
Stack dump:
0x0032f3a4:  0032f3bc 00000006 000016e8 b7c92df0
0x0032f3b4:  b7da5ff4 b7c646c0 0032f4e8 b7c94641
0x0032f3c4:  00000006 0032f45c 00000000 00000130
0x0032f3d4:  7c1afce8 00000000 00000000 b7ccddfd
0x0032f3e4:  0032f420 7c1afc80 7c1afce4 0032f4f8
0x0032f3f4:  b7da5ff4 000000bb 000000bc 0032f4cc
Backtrace:
=>1 0xffffe410 (0x0032f3bc)
  2 0xb7c94641 abort+0x101() in libc.so.6 (0x0032f4e8)
  3 0xb7c8c43b __assert_fail+0xfb() in libc.so.6 (0x0032f52c)
  4 0x7e3bcb9b _mesa_add_renderbuffer+0x13b() in unichrome_dri.so (0x0032f54c)
  5 0x7e356c75 in unichrome_dri.so (+0x5bc75) (0x0032f57c)
  6 0x7e35755a viaMakeCurrent+0x1ba() in unichrome_dri.so (0x0032f5ac)
  7 0x7e353859 in unichrome_dri.so (+0x58859) (0x0032f5ec)
  8 0x7e55e0ce glXMakeContextCurrent+0xbe() in libgl.so.1 (0x0032f65c)
  9 0x7e55e3b3 glXMakeCurrent+0x23() in libgl.so.1 (0x0032f67c)
  10 0x77464a40 in wined3d (+0x34a40) (0x0032f74c)
  11 0x774696c3 InitAdapters+0xd3() in wined3d (0x0032f78c)
  12 0x774c718f WineDirect3DCreate+0x1f() in wined3d (0x0032f7bc)
  13 0x7ea71293 in ddraw (+0x21293) (0x0032f82c)
  14 0x7ea71942 DirectDrawCreate+0x102() in ddraw (0x0032f87c)
  15 0x005b4609 in ra95 (+0x1b4609) (0x0032f8a4)
  16 0x0032fac4 (0x0032fdf8)
  17 0x005c5b6d in ra95 (+0x1c5b6d) (0x0032fefc)
  18 0x00000000 (0x0032ffe8)
  19 0xb7dd8af7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0xffffe410: popl        %ebp
Modules:
Module  Address                 Debug info      Name (76 modules)
PE        330000-  339000       Deferred        thipx32
PE        400000-  740000       Export          ra95
ELF     77422000-774ed000       Export          wined3d<elf>
  \-PE  77430000-774ed000       \               wined3d
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf80000-7c000000       Deferred        libglu.so.1
ELF     7c3c6000-7c426000       Deferred        winedos<elf>
  \-PE  7c3d0000-7c426000       \               winedos
ELF     7c426000-7c43b000       Deferred        midimap<elf>
  \-PE  7c430000-7c43b000       \               midimap
ELF     7c43b000-7c461000       Deferred        msacm32<elf>
  \-PE  7c440000-7c461000       \               msacm32
ELF     7c461000-7c479000       Deferred        msacm32<elf>
  \-PE  7c470000-7c479000       \               msacm32
ELF     7c479000-7c4b5000       Deferred        wineoss<elf>
  \-PE  7c480000-7c4b5000       \               wineoss
ELF     7c4b7000-7c4bc000       Deferred        libxfixes.so.3
ELF     7c4bc000-7c4c5000       Deferred        libxcursor.so.1
ELF     7c4c5000-7c4e2000       Deferred        imm32<elf>
  \-PE  7c4d0000-7c4e2000       \               imm32
ELF     7c4e2000-7c4e8000       Deferred        libxrandr.so.2
ELF     7c4e8000-7c4f0000       Deferred        libxrender.so.1
ELF     7e2fb000-7e533000       Export          unichrome_dri.so
ELF     7e533000-7e53c000       Deferred        libdrm.so.2
ELF     7e53c000-7e59c000       Export          libgl.so.1
ELF     7e59c000-7e5a1000       Deferred        libxdmcp.so.6
ELF     7e5a1000-7e5a4000       Deferred        libxau.so.6
ELF     7e5a4000-7e695000       Deferred        libx11.so.6
ELF     7e695000-7e6a3000       Deferred        libxext.so.6
ELF     7e6a3000-7e6a8000       Deferred        libxxf86vm.so.1
ELF     7e6a8000-7e6c0000       Deferred        libice.so.6
ELF     7e6c0000-7e6c9000       Deferred        libsm.so.6
ELF     7e6c9000-7e752000       Deferred        winex11<elf>
  \-PE  7e6e0000-7e752000       \               winex11
ELF     7e7be000-7e7de000       Deferred        libexpat.so.1
ELF     7e7de000-7e809000       Deferred        libfontconfig.so.1
ELF     7e809000-7e81d000       Deferred        libz.so.1
ELF     7e81d000-7e888000       Deferred        libfreetype.so.6
ELF     7e888000-7e8b5000       Deferred        ws2_32<elf>
  \-PE  7e890000-7e8b5000       \               ws2_32
ELF     7e8b5000-7e8cf000       Deferred        wsock32<elf>
  \-PE  7e8c0000-7e8cf000       \               wsock32
ELF     7e8cf000-7e917000       Deferred        dsound<elf>
  \-PE  7e8e0000-7e917000       \               dsound
ELF     7e917000-7e92a000       Deferred        libresolv.so.2
ELF     7e92a000-7e948000       Deferred        iphlpapi<elf>
  \-PE  7e930000-7e948000       \               iphlpapi
ELF     7e948000-7e9a1000       Deferred        rpcrt4<elf>
  \-PE  7e950000-7e9a1000       \               rpcrt4
ELF     7e9a1000-7ea40000       Deferred        ole32<elf>
  \-PE  7e9b0000-7ea40000       \               ole32
ELF     7ea40000-7ea95000       Export          ddraw<elf>
  \-PE  7ea50000-7ea95000       \               ddraw
ELF     7ea95000-7eadd000       Deferred        advapi32<elf>
  \-PE  7eaa0000-7eadd000       \               advapi32
ELF     7eadd000-7eae9000       Deferred        libgcc_s.so.1
ELF     7ebe2000-7eca2000       Deferred        gdi32<elf>
  \-PE  7ec00000-7eca2000       \               gdi32
ELF     7eca2000-7eddf000       Deferred        user32<elf>
  \-PE  7ecc0000-7eddf000       \               user32
ELF     7eddf000-7ee6d000       Deferred        winmm<elf>
  \-PE  7edf0000-7ee6d000       \               winmm
ELF     7ef9e000-7efa9000       Deferred        libnss_files.so.2
ELF     7efa9000-7efb3000       Deferred        libnss_nis.so.2
ELF     7efb3000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7eff1000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c65000-b7c69000       Deferred        libdl.so.2
ELF     b7c69000-b7daa000       Export          libc.so.6
ELF     b7dab000-b7dc2000       Deferred        libpthread.so.0
ELF     b7dd1000-b7ee5000       Export          libwine.so.1
ELF     b7ee7000-b7f02000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\WESTWOOD\REDALERT\ra95.exe
        0000000e   15
        0000000c   15
        00000009    0 <==


Not sure exactly what is going on with either of these.

---

