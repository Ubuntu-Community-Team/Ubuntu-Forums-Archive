---
title: "what does this regression gibberish mean!"
date: 2006-04-19
forum: Gaming &amp; Leisure
---

### Post by glassgloss on 2006-04-19
I get something very similar to this message everytime I try to wine IWD2.exe
this is for Icewind Dale II.  Any thoughts?

BEGIN LOGGING SESSION
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel
(0x7fe0ea10)->(00010022,00000011)
fixme:mmtime:timeBeginPeriod Stub; we set our timer resolution at minimum
fixme:wave:DSD_CreateSecondaryBuffer
(0x7fe0c7d8,0x7facab2c,12,0,0x7fe2f5c4,0x7fe2f6b4,0x7fe2f5a0): stub
err:x11settings:X11DRV_ChangeDisplaySettingsExW No matching mode found!
(NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsExW No matching mode found!
(NoRes)
fixme:ddraw:Main_DirectDraw_CreateSurface failed surface creation with code
0x88760078
err:x11settings:X11DRV_ChangeDisplaySettingsExW No matching mode found!
(NoRes)
fixme:ddraw:Main_DirectDraw_CreateSurface failed surface creation with code
0x88760078
fixme:mmtime:timeBeginPeriod Stub; we set our timer resolution at minimum
fixme:mmtime:timeEndPeriod Stub; we set our timer resolution at minimum
fixme:mmtime:timeEndPeriod Stub; we set our timer resolution at minimum

Also, a messagebox appears: "An assertion failed in ChVideo.cpp at line
8466".

Hope someone can take a look at this.

Thanks!

On 1/8/06, James Trotter <james.trotter at gmail.com> wrote:
>
> I've been trying to run the game Icewind Dale II under wine 0.9.4, but it
> crashes before the game starts. In earlier versions of wine it worked fine.
> I've found that the regression was caused by this patch:
> [http://cvs.winehq.org/patch.py?id=17222](http://cvs.winehq.org/patch.py?id=17222)
>
> Here's the output from running the game in wine 0.9.4:
>
> james at james:~/Wine/Games/Icewind Dale II$ wine IWD2.exe
>
> BEGIN LOGGING SESSION
> wine: Unhandled page fault on read access to 0x31303635 at address
> 0x7ab8f1 (thread 0009), starting debugger...
> WineDbg starting on pid 0x8
> Unhandled exception: page fault on read access to 0x31303635 in 32-bit
> code (0x007ab8f1).
> In 32 bit mode.
> Register dump:
>  CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
>  EIP:007ab8f1 ESP:7fabab94 EBP:00000000 EFLAGS:00210246(   - 00
> -RIZP1)
>  EAX:31303635 EBX:00000001 ECX:7fabb444 EDX:00000000
>  ESI:7fabb31c EDI:7beb3820
> Stack dump:
> 0x7fabab94:  31303635 00002711 00000000 7fabb31c
> 0x7fababa4:  7fababd4 007aaf30 7fabb20c 7fabaf54
> 0x7fababb4:  00000000 00002711 40c38800 7fabb31c
> 0x7fababc4:  7fabac84 0084566a 00000007 7fcf0690
> 0x7fababd4:  7fcf0690 0078e3ca 00000000 7fabaf54
> 0x7fababe4:  00400000 7fd12606 7fabaf54 00010000
> 0200: sel=1007 base=7fec4000 limit=00001fff 32-bit rw-
> Backtrace:
> =>1 0x007ab8f1 in iwd2 (+0x3ab8f1) (0x007ab8f1)
> 0x007ab8f1: movl        0x0(%eax),%ecx
> Modules:
> Module  Address                 Debug info      Name (95 modules)
> PE      0x00400000-00a21000     Export          iwd2
> ELF     0x7391a000-73922000     Deferred        libxrender.so.1
> ELF     0x7be8c000-7bf00000     Deferred        ntdll<elf>
>   \-PE  0x7bea0000-7bf00000     \               ntdll
> ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
> ELF     0x7c9b5000-7ca01000     Deferred        libgcrypt.so.11
> ELF     0x7ca01000-7ca11000     Deferred        libtasn1.so.2
> ELF     0x7ca11000-7ca73000     Deferred        libgnutls.so.11
> ELF     0x7ca73000-7ca90000     Deferred        libcups.so.2
> ELF     0x7db8b000-7dbbb000     Deferred        uxtheme<elf>
>   \-PE  0x7db90000-7dbbb000     \               uxtheme
> ELF     0x7dbbb000-7dbd0000     Deferred        midimap<elf>
>   \-PE  0x7dbc0000-7dbd0000     \               midimap
> ELF     0x7dce6000-7dd08000     Deferred        msacm32<elf>
>   \-PE  0x7dcf0000-7dd08000     \               msacm32
> ELF     0x7dd08000-7dd1f000     Deferred        msacm<elf>
>   \-PE  0x7dd10000-7dd1f000     \               msacm
> ELF     0x7dd1f000-7ddd2000     Deferred        libasound.so.2
> ELF     0x7ddd2000-7ddfa000     Deferred        winealsa<elf>
>   \-PE  0x7dde0000-7ddfa000     \               winealsa
> ELF     0x7de18000-7de21000     Deferred        libxcursor.so.1
> ELF     0x7de2c000-7de48000     Deferred        ximcp.so.2
> ELF     0x7de48000-7de50000     Deferred        librt.so.1
> ELF     0x7df0a000-7e64d000     Deferred        fglrx_dri.so
> ELF     0x7e64d000-7e6ec000     Deferred        libgl.so.1
> ELF     0x7e6ec000-7e769000     Deferred        winex11<elf>
>   \-PE  0x7e700000-7e769000     \               winex11
> ELF     0x7e769000-7e788000     Deferred        libexpat.so.1
> ELF     0x7e788000-7e7b6000     Deferred        libfontconfig.so.1
> ELF     0x7e7b6000-7e7ca000     Deferred        libz.so.1
> ELF     0x7e7ca000-7e834000     Deferred        libfreetype.so.6
> ELF     0x7e834000-7e85c000     Deferred        winspool<elf>
>   \-PE  0x7e840000-7e85c000     \               winspool
> ELF     0x7e85c000-7e90b000     Deferred        comctl32<elf>
>   \-PE  0x7e870000-7e90b000     \               comctl32
> ELF     0x7e90b000-7e960000     Deferred        shlwapi<elf>
>   \-PE  0x7e920000-7e960000     \               shlwapi
> ELF     0x7e960000-7ea1f000     Deferred        shell32<elf>
>   \-PE  0x7e980000-7ea1f000     \               shell32
> ELF     0x7ea1f000-7eab1000     Deferred        comdlg32<elf>
>   \-PE  0x7ea30000-7eab1000     \               comdlg32
> ELF     0x7eab1000-7eada000     Deferred        ws2_32<elf>
>   \-PE  0x7eac0000-7eada000     \               ws2_32
> ELF     0x7eada000-7eaf5000     Deferred        imm32<elf>
>   \-PE  0x7eae0000-7eaf5000     \               imm32
> ELF     0x7eaf5000-7eb09000     Deferred        lz32<elf>
>   \-PE  0x7eb00000-7eb09000     \               lz32
> ELF     0x7eb09000-7eb21000     Deferred        version<elf>
>   \-PE  0x7eb10000-7eb21000     \               version
> ELF     0x7eb21000-7eb25000     Deferred        libxdmcp.so.6
> ELF     0x7eb25000-7ebe5000     Deferred        libx11.so.6
> ELF     0x7ebe5000-7ebf2000     Deferred        libxext.so.6
> ELF     0x7ebf2000-7ebf7000     Deferred        libxxf86vm.so.1
> ELF     0x7ebf7000-7ec10000     Deferred        libice.so.6
> ELF     0x7ec10000-7ec88000     Deferred        ddraw<elf>
>   \-PE  0x7ec30000-7ec88000     \               ddraw
> ELF     0x7ec88000-7ecd3000     Deferred        dsound<elf>
>   \-PE  0x7eca0000-7ecd3000     \               dsound
> ELF     0x7ecd3000-7ecf1000     Deferred        iphlpapi<elf>
>   \-PE  0x7ece0000-7ecf1000     \               iphlpapi
> ELF     0x7ecf1000-7ed35000     Deferred        rpcrt4<elf>
>   \-PE  0x7ed00000-7ed35000     \               rpcrt4
> ELF     0x7ed35000-7edbb000     Deferred        ole32<elf>
>   \-PE  0x7ed50000-7edbb000     \               ole32
> ELF     0x7edbb000-7edf7000     Deferred        advapi32<elf>
>   \-PE  0x7edd0000-7edf7000     \               advapi32
> ELF     0x7eedd000-7f7dd000     Deferred        gdi32<elf>
>   \-PE  0x7ef20000-7f7dd000     \               gdi32
> ELF     0x7f7dd000-7f8f6000     Deferred        user32<elf>
>   \-PE  0x7f800000-7f8f6000     \               user32
> ELF     0x7f8f6000-7f977000     Deferred        winmm<elf>
>   \-PE  0x7f900000-7f977000     \               winmm
> ELF     0x7f977000-7f9b0000     Deferred        dplayx<elf>
>   \-PE  0x7f990000-7f9b0000     \               dplayx
> ELF     0x7fac0000-7fac5000     Deferred        libxxf86dga.so.1
> ELF     0x7fac5000-7fad0000     Deferred        libgcc_s.so.1
> ELF     0x7fc74000-7fd70000     Deferred        kernel32<elf>
>   \-PE  0x7fc90000-7fd70000     \               kernel32
> ELF     0x7fe81000-7fe88000     Deferred        libsm.so.6
> ELF     0x7fe88000-7fe92000     Deferred        libnss_files.so.2
> ELF     0x7fe92000-7fe9b000     Deferred        libnss_nis.so.2
> ELF     0x7fe9b000-7feb0000     Deferred        libnsl.so.1
> ELF     0x7feb0000-7feb9000     Deferred        libnss_compat.so.2
> ELF     0x7feba000-7febe000     Deferred        libgpg-error.so.0
> ELF     0x7febe000-7fec2000     Deferred        libxfixes.so.3
> ELF     0x7fec2000-7fec4000     Deferred        xlcutf8load.so.2
> ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
> ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
> ELF     0xb7e00000-b7e03000     Deferred        libxrandr.so.2
> ELF     0xb7e11000-b7e14000     Deferred        libdl.so.2
> ELF     0xb7e14000-b7f42000     Deferred        libc.so.6
> ELF     0xb7f42000-b7f54000     Deferred        libpthread.so.0
> ELF     0xb7f54000-b7f6e000     Deferred        libwine.so.1
> ELF     0xb7f6e000-b7f71000     Deferred        libxau.so.6
> ELF     0xb7f7c000-b7f92000     Deferred        ld-linux.so.2
> Threads:
> process  tid      prio (all id:s are in hex)
> 00000008 (D) C:\Games\Icewind Dale II\IWD2.exe
>         00000009    0 <==
> WineDbg terminated on pid 0x8

---

