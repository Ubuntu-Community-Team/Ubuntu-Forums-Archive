---
title: "How to install Half life 2 with wine"
date: 2006-10-31
forum: Gaming &amp; Leisure
---

### Post by rekahsoft on 2006-10-31
Hey all i was wondering how to install half life 2 and steam games (cs,hl1,etc...) with wine on edgy...i have tried to how-to on linux-gamers.com and it could not get it to work...i want to install install it from my cds if possible :) thanks for the help.

---

### Post by electricshoes on 2006-10-31
What happened when you tryed that howto on linux-gamers ?

---

### Post by rekahsoft on 2006-10-31
well...i want to install it from my disk if possable...and when i```
wine msiexec /i steam.msi
```it installs steam fine but when i try to install hl2,cs,etc... the installer freezes and takes up 100% cpu...i execute the installer by doing this:```
wine msiexec /i hl2.msi
```

---

### Post by benzies on 2006-11-01
I Get this problem... HELP!!

err:module:map_image Could not map section .data, file probably truncated
err:module:map_image Could not map section .data, file probably truncated
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:mshtml:PersistMoniker_Load bscallback->nschannel == NULL
Shutting down. . .
300client callback thread error
wine: Unhandled page fault on read access to 0x00000000 at address 0x60169e3b (thread 003b), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x60169e3b).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:60169e3b ESP:0033cb28 EBP:0033cb78 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c41a62c ECX:0033cb14 EDX:00110024
 ESI:0e7d27e0 EDI:0e7a4290
Stack dump:
0x0033cb28:  0033cb68 0b550584 60c7251a 0e7d27e0
0x0033cb38:  0033cb68 7c3dc858 0e7d14cc 0033cb68
0x0033cb48:  0033cb94 0e7a1b30 0033cb80 7c489294
0x0033cb58:  0e7a4290 7c4929f4 00000000 00002920
0x0033cb68:  7b8a5ca0 7c493a88 0b550584 0e7a1958
0x0033cb78:  01950fe0 0d66aeab 0e7a4290 0033cb9c
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x60169e3b in docshell (+0x9e3b) (0x0033cb78)
  2 0x0d66aeab in vgui2 (+0xaeab) (0x01950fe0)
  3 0x05951a40 (0x0d6ce4a8)
  4 0x0d6690d0 in vgui2 (+0x90d0) (0x0d6690c0)
  5 0x8b04408b (0x0424448b)
  6 0x00000000 (0x00000000)
0x60169e3b: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (163 modules)
PE      380000-3bf000   Deferred        tier0_s
PE      3c0000-3d0000   Deferred        steam_api
PE      400000-538000   Deferred        steam
PE      760000-849000   Deferred        vstdlib_s
PE      850000-88a000   Deferred        filesystem_steam
PE      d660000-d711000 Export          vgui2
PE      e670000-e790000 Deferred        steamclient
PE      10000000-1037e000       Deferred        steamui
PE      60000000-60021000       Deferred        cserhelper
PE      600a0000-600d9000       Deferred        appcomps
PE      60160000-6018c000       Export          docshell
PE      60200000-6021e000       Deferred        embedcomponents
PE      60230000-60254000       Deferred        gkgfxwin
PE      60260000-6052d000       Deferred        gklayout
PE      605a0000-605c5000       Deferred        gkwidget
PE      605d0000-605fe000       Deferred        i18n
PE      60610000-60635000       Deferred        imglib2
PE      60940000-609bb000       Deferred        necko
PE      60a00000-60a18000       Deferred        palmsync
PE      60a90000-60a9e000       Deferred        profile
PE      60aa0000-60aba000       Deferred        rdf
PE      60af0000-60af7000       Deferred        sroaming
PE      60b40000-60b4c000       Deferred        typeaheadfind
PE      60b50000-60c0b000       Deferred        uconv
PE      60c70000-60c7e000       Deferred        webbrwsr
PE      60cf0000-60d22000       Deferred        xpc3250
PE      60d30000-60d37000       Deferred        xpcom_compat_c
PE      60d70000-60d7c000       Deferred        xppref32
PE      60d80000-60d96000       Deferred        gkgfx
PE      60da0000-60e09000       Deferred        js3250
PE      60e10000-60e23000       Deferred        jsj3250
PE      60ec0000-60ed1000       Deferred        mozz
PE      60ee0000-60f14000       Deferred        msgbsutl
PE      60f60000-60f87000       Deferred        nspr4
PE      60f90000-60fe9000       Deferred        nss3
PE      60ff0000-6102a000       Deferred        nssckbi
PE      61030000-61037000       Deferred        palmsyncproxy
PE      61040000-61047000       Deferred        plc4
PE      61050000-61056000       Deferred        plds4
PE      61060000-61068000       Deferred        npnul32
PE      61070000-6108a000       Deferred        smime3
PE      61090000-610ea000       Deferred        softokn3
PE      610f0000-6110b000       Deferred        ssl3
PE      61110000-61116000       Deferred        xpcom
PE      61120000-61134000       Deferred        xpcom_compat
PE      61140000-611a5000       Deferred        xpcom_core
PE      611b0000-611b6000       Deferred        xpistub
ELF     7b800000-7b917000       Deferred        kernel32<elf>
  \-PE  7b820000-7b917000       \               kernel32
ELF     7bc00000-7bc7f000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc7f000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c302000-7c348000       Deferred        dbghelp<elf>
  \-PE  7c310000-7c348000       \               dbghelp
ELF     7c348000-7c3aa000       Deferred        msvcrt<elf>
  \-PE  7c360000-7c3aa000       \               msvcrt
ELF     7c3aa000-7c3c4000       Deferred        wsock32<elf>
  \-PE  7c3b0000-7c3c4000       \               wsock32
ELF     7c3c4000-7c431000       Deferred        mshtml<elf>
  \-PE  7c3d0000-7c431000       \               mshtml
ELF     7c431000-7c464000       Deferred        urlmon<elf>
  \-PE  7c440000-7c464000       \               urlmon
ELF     7c466000-7c4a0000       Deferred        shdocvw<elf>
  \-PE  7c470000-7c4a0000       \               shdocvw
ELF     7c82b000-7c84a000       Deferred        mpr<elf>
  \-PE  7c830000-7c84a000       \               mpr
ELF     7c84a000-7c891000       Deferred        wininet<elf>
  \-PE  7c850000-7c891000       \               wininet
ELF     7cbc6000-7cbda000       Deferred        msimg32<elf>
  \-PE  7cbd0000-7cbda000       \               msimg32
ELF     7cbda000-7cc28000       Deferred        crypt32<elf>
  \-PE  7cbe0000-7cc28000       \               crypt32
ELF     7cc28000-7cc5c000       Deferred        rsaenh<elf>
  \-PE  7cc30000-7cc5c000       \               rsaenh
ELF     7cc5c000-7cc71000       Deferred        psapi<elf>
  \-PE  7cc60000-7cc71000       \               psapi
ELF     7cc71000-7cc86000       Deferred        midimap<elf>
  \-PE  7cc80000-7cc86000       \               midimap
ELF     7ccac000-7ccc4000       Deferred        msacm32<elf>
  \-PE  7ccb0000-7ccc4000       \               msacm32
ELF     7ccc4000-7cd00000       Deferred        wineoss<elf>
  \-PE  7ccd0000-7cd00000       \               wineoss
ELF     7cd00000-7cd88000       Deferred        winmm<elf>
  \-PE  7cd10000-7cd88000       \               winmm
ELF     7d1cc000-7d1d1000       Deferred        libnss_dns.so.2
ELF     7d1dc000-7d1f0000       Deferred        mswsock<elf>
  \-PE  7d1e0000-7d1f0000       \               mswsock
ELF     7d548000-7d57a000       Deferred        uxtheme<elf>
  \-PE  7d550000-7d57a000       \               uxtheme
ELF     7d57a000-7d5c6000       Deferred        libgcrypt.so.11
ELF     7d5c6000-7d5f3000       Deferred        libcrypt.so.1
ELF     7d5f3000-7d65c000       Deferred        libgnutls.so.12
ELF     7d65c000-7d68a000       Deferred        libcups.so.2
ELF     7d89f000-7d8a3000       Deferred        libgpg-error.so.0
ELF     7d8a3000-7d8b3000       Deferred        libtasn1.so.2
ELF     7d8c0000-7d8c5000       Deferred        libxfixes.so.3
ELF     7d8c5000-7d8ce000       Deferred        libxcursor.so.1
ELF     7d8ce000-7d8ea000       Deferred        imm32<elf>
  \-PE  7d8e0000-7d8ea000       \               imm32
ELF     7d8ea000-7d8ed000       Deferred        libxrandr.so.2
ELF     7d8ed000-7d8f5000       Deferred        libxrender.so.1
ELF     7d8f5000-7d8f8000       Deferred        libxinerama.so.1
ELF     7dcd2000-7e494000       Deferred        libglcore.so.1
ELF     7e494000-7e519000       Deferred        libgl.so.1
ELF     7e519000-7e5ff000       Deferred        libx11.so.6
ELF     7e5ff000-7e60c000       Deferred        libxext.so.6
ELF     7e60c000-7e624000       Deferred        libice.so.6
ELF     7e624000-7e6b0000       Deferred        winex11<elf>
  \-PE  7e630000-7e6b0000       \               winex11
ELF     7e6b0000-7e6cf000       Deferred        libexpat.so.1
ELF     7e6cf000-7e6fd000       Deferred        libfontconfig.so.1
ELF     7e6fd000-7e711000       Deferred        libz.so.1
ELF     7e711000-7e77a000       Deferred        libfreetype.so.6
ELF     7e77a000-7e78e000       Deferred        oleacc<elf>
  \-PE  7e780000-7e78e000       \               oleacc
ELF     7e78e000-7e7a2000       Deferred        lz32<elf>
  \-PE  7e790000-7e7a2000       \               lz32
ELF     7e7a2000-7e7bb000       Deferred        version<elf>
  \-PE  7e7b0000-7e7bb000       \               version
ELF     7e7bb000-7e7dc000       Deferred        oledlg<elf>
  \-PE  7e7c0000-7e7dc000       \               oledlg
ELF     7e7dc000-7e871000       Deferred        oleaut32<elf>
  \-PE  7e7f0000-7e871000       \               oleaut32
ELF     7e871000-7e932000       Deferred        comctl32<elf>
  \-PE  7e880000-7e932000       \               comctl32
ELF     7e932000-7e984000       Deferred        rpcrt4<elf>
  \-PE  7e940000-7e984000       \               rpcrt4
ELF     7e984000-7ea15000       Deferred        ole32<elf>
  \-PE  7e990000-7ea15000       \               ole32
ELF     7ea15000-7ea6b000       Deferred        shlwapi<elf>
  \-PE  7ea20000-7ea6b000       \               shlwapi
ELF     7ea6b000-7eb52000       Deferred        shell32<elf>
  \-PE  7ea80000-7eb52000       \               shell32
ELF     7eb52000-7ebee000       Deferred        comdlg32<elf>
  \-PE  7eb60000-7ebee000       \               comdlg32
ELF     7ebee000-7ec1d000       Deferred        winspool<elf>
  \-PE  7ec00000-7ec1d000       \               winspool
ELF     7ec1d000-7ec27000       Deferred        libgcc_s.so.1
ELF     7ecfc000-7edaf000       Deferred        gdi32<elf>
  \-PE  7ed10000-7edaf000       \               gdi32
ELF     7edaf000-7eee1000       Deferred        user32<elf>
  \-PE  7edd0000-7eee1000       \               user32
ELF     7eee1000-7ef25000       Deferred        advapi32<elf>
  \-PE  7eef0000-7ef25000       \               advapi32
ELF     7ef25000-7ef38000       Deferred        libresolv.so.2
ELF     7ef38000-7ef57000       Deferred        iphlpapi<elf>
  \-PE  7ef40000-7ef57000       \               iphlpapi
ELF     7ef57000-7ef81000       Deferred        ws2_32<elf>
  \-PE  7ef60000-7ef81000       \               ws2_32
ELF     7efb4000-7efbe000       Deferred        libnss_files.so.2
ELF     7efbe000-7efd3000       Deferred        libnsl.so.1
ELF     7efd3000-7eff5000       Deferred        libm.so.6
ELF     7eff5000-7eff7000       Deferred        libnvidia-tls.so.1
ELF     7eff7000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c90000-b7c95000       Deferred        libxxf86vm.so.1
ELF     b7c95000-b7c9e000       Deferred        libnss_compat.so.2
ELF     b7c9f000-b7ca2000       Deferred        libdl.so.2
ELF     b7ca2000-b7dd1000       Deferred        libc.so.6
ELF     b7dd1000-b7de3000       Deferred        libpthread.so.0
ELF     b7de4000-b7de7000       Deferred        libxau.so.6
ELF     b7de7000-b7def000       Deferred        libsm.so.6
ELF     b7def000-b7f00000       Deferred        libwine.so.1
ELF     b7f03000-b7f19000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000003c (D) F:\Games (Windows)\Steam\Steam.exe
        0000002e    0
        0000000f    0
        0000002b    0
        0000002a    0
        00000047    0
        00000045    0
        0000003d    0
        0000003e    0
        0000003b    0 <==
00000011
        0000002f    0
        00000016    0
        00000015    0
        00000014    0
        00000013    0
        00000012    0
0000000a
        0000000c    0

---

### Post by benzies on 2006-11-01
Nope wait now its changed....

fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:process:IsWow64Process (0xffffffff 0x3b741c) stub!
fixme:shdocvw:ViewObject_SetAdvise (0xd8a66e8)->(1 00000002 0x11618d0)
fixme:shdocvw:PersistStreamInit_InitNew (0xd8a66e8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xd8a66e8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xd8a66e8)->(ffffffff)
err:module:map_image Could not map section .data, file probably truncated
err:module:map_image Could not map section .data, file probably truncated
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd8a6784)->((null) 1 0x33d624 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd8a6784)->((null) 25 2 0x33d638 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd8a6784)->((null) 26 2 0x33d638 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd8a6784)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClDispatch_Invoke (0xd8a6784)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d54c 0x33d598 (nil) 0x33d55c)
fixme:shdocvw:ClDispatch_Invoke (0xd8a6784)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClDispatch_Invoke (0xd8a6784)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d54c 0x33d598 (nil) 0x33d55c)
fixme:shdocvw:ClDispatch_Invoke (0xd8a6784)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClDispatch_Invoke (0xd8a6784)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClDispatch_Invoke (0xd8a6784)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClientSite_GetContainer (0xd8a6784)->(0x33d664)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd8a6784)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d768 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0xd93e490)->(L"" L"" 0 0x33d77c)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0xd93e490)->(0x33d780 0x33d6c4)
err:mshtml:PersistMoniker_Load bscallback->nschannel == NULL
fixme:shdocvw:ViewObject_SetAdvise (0xf040668)->(1 00000002 0x11620d0)
fixme:shdocvw:PersistStreamInit_InitNew (0xf040668)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xf040668)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xf040668)->(ffffffff)
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xf040704)->((null) 1 0x33ae48 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xf040704)->((null) 25 2 0x33ae5c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xf040704)->((null) 26 2 0x33ae5c (nil))
fixme:shdocvw:ClDispatch_Invoke (0xf040704)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33adb0 0x33adfc (nil) 0x33adc0)
fixme:shdocvw:ClDispatch_Invoke (0xf040704)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33ad70 0x33adbc (nil) 0x33ad80)
fixme:shdocvw:ClDispatch_Invoke (0xf040704)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33adb0 0x33adfc (nil) 0x33adc0)
fixme:shdocvw:ClDispatch_Invoke (0xf040704)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33ad70 0x33adbc (nil) 0x33ad80)
fixme:shdocvw:ClDispatch_Invoke (0xf040704)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33adb0 0x33adfc (nil) 0x33adc0)
fixme:shdocvw:ClDispatch_Invoke (0xf040704)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33adb0 0x33adfc (nil) 0x33adc0)
fixme:shdocvw:ClDispatch_Invoke (0xf040704)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33adb0 0x33adfc (nil) 0x33adc0)
fixme:shdocvw:ClientSite_GetContainer (0xf040704)->(0x33ae88)
fixme:shdocvw:ClOleCommandTarget_Exec (0xf040704)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33af8c (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0xf040c20)->(L"" L"" 0 0x33afa0)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0xf040c20)->(0x33afa4 0x33aee8)
err:mshtml:PersistMoniker_Load bscallback->nschannel == NULL
fixme:shdocvw:ClOleCommandTarget_Exec (0xd8a6784)->((null) 29 2 0x33d73c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0xd8a6784)
fixme:shdocvw:ClOleCommandTarget_Exec (0xf040704)->((null) 29 2 0x33d73c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0xf040704)
Shutting down. . .
300client callback thread error
fixme:dbghelp:fetch_thread_info Couldn't open thread 64 (87)
fixme:dbghelp:fetch_thread_info Couldn't open thread 37 (87)
wine: Unhandled page fault on read access to 0x00000000 at address 0x60169e3b (thread 002b), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x60169e3b).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:60169e3b ESP:0033c02c EBP:0033c07c EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7b07262c ECX:0033c018 EDX:00110024
 ESI:0f041478 EDI:0f040d98
Stack dump:
0x0033c02c:  0033c06c 0b564200 60c7251a 0f041478
0x0033c03c:  0033c06c 7b034858 0f040f04 0033c06c
0x0033c04c:  0033c07c 7b9d8294 0f040d98 7b9e19f4
0x0033c05c:  0033c098 01161cc8 00000000 00000030
0x0033c06c:  0d6e36dc 0d6e36dc 0b564200 0033c0c4
0x0033c07c:  00000233 0d67b106 0f040d98 0033c090
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x60169e3b in docshell (+0x9e3b) (0x0033c07c)
  2 0x0d67b106 in vgui2 (+0xb106) (0x00000233)
  3 0x00000000 (0x00000000)
0x60169e3b: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (164 modules)
PE      380000-3bf000   Deferred        tier0_s
PE      3c0000-3d0000   Deferred        steam_api
PE      400000-538000   Deferred        steam
PE      760000-849000   Deferred        vstdlib_s
PE      850000-88a000   Deferred        filesystem_steam
PE      d670000-d721000 Export          vgui2
PE      e8c0000-e9e0000 Deferred        steamclient
PE      f250000-f572000 Deferred        friendsui
PE      f580000-f6f2000 Deferred        serverbrowser
PE      10000000-1037e000       Deferred        steamui
PE      60000000-60021000       Deferred        cserhelper
PE      600a0000-600d9000       Deferred        appcomps
PE      60160000-6018c000       Export          docshell
PE      60200000-6021e000       Deferred        embedcomponents
PE      60230000-60254000       Deferred        gkgfxwin
PE      60260000-6052d000       Deferred        gklayout
PE      605a0000-605c5000       Deferred        gkwidget
PE      605d0000-605fe000       Deferred        i18n
PE      60610000-60635000       Deferred        imglib2
PE      60940000-609bb000       Deferred        necko
PE      60a00000-60a18000       Deferred        palmsync
PE      60a90000-60a9e000       Deferred        profile
PE      60aa0000-60aba000       Deferred        rdf
PE      60af0000-60af7000       Deferred        sroaming
PE      60b40000-60b4c000       Deferred        typeaheadfind
PE      60c70000-60c7e000       Deferred        webbrwsr
PE      60cf0000-60d22000       Deferred        xpc3250
PE      60d30000-60d37000       Deferred        xpcom_compat_c
PE      60d70000-60d7c000       Deferred        xppref32
PE      60d80000-60d96000       Deferred        gkgfx
PE      60da0000-60e09000       Deferred        js3250
PE      60e10000-60e23000       Deferred        jsj3250
PE      60ec0000-60ed1000       Deferred        mozz
PE      60ee0000-60f14000       Deferred        msgbsutl
PE      60f60000-60f87000       Deferred        nspr4
PE      60f90000-60fe9000       Deferred        nss3
PE      60ff0000-6102a000       Deferred        nssckbi
PE      61030000-61037000       Deferred        palmsyncproxy
PE      61040000-61047000       Deferred        plc4
PE      61050000-61056000       Deferred        plds4
PE      61060000-61068000       Deferred        npnul32
PE      61070000-6108a000       Deferred        smime3
PE      61090000-610ea000       Deferred        softokn3
PE      610f0000-6110b000       Deferred        ssl3
PE      61110000-61116000       Deferred        xpcom
PE      61120000-61134000       Deferred        xpcom_compat
PE      61140000-611a5000       Deferred        xpcom_core
PE      611b0000-611b6000       Deferred        xpistub
ELF     7ab30000-7ab76000       Deferred        dbghelp<elf>
  \-PE  7ab40000-7ab76000       \               dbghelp
ELF     7afba000-7b01c000       Deferred        msvcrt<elf>
  \-PE  7afd0000-7b01c000       \               msvcrt
ELF     7b01c000-7b089000       Deferred        mshtml<elf>
  \-PE  7b030000-7b089000       \               mshtml
ELF     7b800000-7b917000       Deferred        kernel32<elf>
  \-PE  7b820000-7b917000       \               kernel32
ELF     7b921000-7b954000       Deferred        urlmon<elf>
  \-PE  7b930000-7b954000       \               urlmon
ELF     7b9b5000-7b9ef000       Deferred        shdocvw<elf>
  \-PE  7b9c0000-7b9ef000       \               shdocvw
ELF     7bc00000-7bc7f000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc7f000       \               ntdll
ELF     7beb9000-7bf00000       Deferred        wininet<elf>
  \-PE  7bec0000-7bf00000       \               wininet
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf0d000-7bf27000       Deferred        wsock32<elf>
  \-PE  7bf10000-7bf27000       \               wsock32
ELF     7bf29000-7bf48000       Deferred        mpr<elf>
  \-PE  7bf30000-7bf48000       \               mpr
ELF     7cb12000-7cb26000       Deferred        msimg32<elf>
  \-PE  7cb20000-7cb26000       \               msimg32
ELF     7cb26000-7cb74000       Deferred        crypt32<elf>
  \-PE  7cb30000-7cb74000       \               crypt32
ELF     7cb74000-7cba8000       Deferred        rsaenh<elf>
  \-PE  7cb80000-7cba8000       \               rsaenh
ELF     7cba8000-7cbbd000       Deferred        psapi<elf>
  \-PE  7cbb0000-7cbbd000       \               psapi
ELF     7cbbd000-7cbd2000       Deferred        midimap<elf>
  \-PE  7cbc0000-7cbd2000       \               midimap
ELF     7cbf8000-7cc10000       Deferred        msacm32<elf>
  \-PE  7cc00000-7cc10000       \               msacm32
ELF     7cc10000-7cc4c000       Deferred        wineoss<elf>
  \-PE  7cc20000-7cc4c000       \               wineoss
ELF     7cc4c000-7ccd4000       Deferred        winmm<elf>
  \-PE  7cc60000-7ccd4000       \               winmm
ELF     7d118000-7d12c000       Deferred        mswsock<elf>
  \-PE  7d120000-7d12c000       \               mswsock
ELF     7d542000-7d574000       Deferred        uxtheme<elf>
  \-PE  7d550000-7d574000       \               uxtheme
ELF     7d574000-7d5c0000       Deferred        libgcrypt.so.11
ELF     7d5c0000-7d5ed000       Deferred        libcrypt.so.1
ELF     7d5ed000-7d656000       Deferred        libgnutls.so.12
ELF     7d656000-7d684000       Deferred        libcups.so.2
ELF     7d893000-7d898000       Deferred        libnss_dns.so.2
ELF     7d898000-7d89c000       Deferred        libgpg-error.so.0
ELF     7d89c000-7d8ac000       Deferred        libtasn1.so.2
ELF     7d8b9000-7d8be000       Deferred        libxfixes.so.3
ELF     7d8be000-7d8c7000       Deferred        libxcursor.so.1
ELF     7d8c7000-7d8e3000       Deferred        imm32<elf>
  \-PE  7d8d0000-7d8e3000       \               imm32
ELF     7d8e3000-7d8e6000       Deferred        libxrandr.so.2
ELF     7d8e6000-7d8ee000       Deferred        libxrender.so.1
ELF     7d8ee000-7d8f1000       Deferred        libxinerama.so.1
ELF     7dcc9000-7e48b000       Deferred        libglcore.so.1
ELF     7e48b000-7e510000       Deferred        libgl.so.1
ELF     7e510000-7e5f6000       Deferred        libx11.so.6
ELF     7e5f6000-7e603000       Deferred        libxext.so.6
ELF     7e603000-7e61b000       Deferred        libice.so.6
ELF     7e61b000-7e6a7000       Deferred        winex11<elf>
  \-PE  7e630000-7e6a7000       \               winex11
ELF     7e6a7000-7e6c6000       Deferred        libexpat.so.1
ELF     7e6c6000-7e6f4000       Deferred        libfontconfig.so.1
ELF     7e6f4000-7e708000       Deferred        libz.so.1
ELF     7e708000-7e771000       Deferred        libfreetype.so.6
ELF     7e771000-7e785000       Deferred        oleacc<elf>
  \-PE  7e780000-7e785000       \               oleacc
ELF     7e785000-7e799000       Deferred        lz32<elf>
  \-PE  7e790000-7e799000       \               lz32
ELF     7e799000-7e7b2000       Deferred        version<elf>
  \-PE  7e7a0000-7e7b2000       \               version
ELF     7e7b2000-7e7d3000       Deferred        oledlg<elf>
  \-PE  7e7c0000-7e7d3000       \               oledlg
ELF     7e7d3000-7e868000       Deferred        oleaut32<elf>
  \-PE  7e7e0000-7e868000       \               oleaut32
ELF     7e868000-7e929000       Deferred        comctl32<elf>
  \-PE  7e870000-7e929000       \               comctl32
ELF     7e929000-7e97b000       Deferred        rpcrt4<elf>
  \-PE  7e940000-7e97b000       \               rpcrt4
ELF     7e97b000-7ea0c000       Deferred        ole32<elf>
  \-PE  7e990000-7ea0c000       \               ole32
ELF     7ea0c000-7ea62000       Deferred        shlwapi<elf>
  \-PE  7ea20000-7ea62000       \               shlwapi
ELF     7ea62000-7eb49000       Deferred        shell32<elf>
  \-PE  7ea70000-7eb49000       \               shell32
ELF     7eb49000-7ebe5000       Deferred        comdlg32<elf>
  \-PE  7eb50000-7ebe5000       \               comdlg32
ELF     7ebe5000-7ec14000       Deferred        winspool<elf>
  \-PE  7ebf0000-7ec14000       \               winspool
ELF     7ec14000-7ec1e000       Deferred        libgcc_s.so.1
ELF     7ecf3000-7eda6000       Deferred        gdi32<elf>
  \-PE  7ed10000-7eda6000       \               gdi32
ELF     7eda6000-7eed8000       Deferred        user32<elf>
  \-PE  7edc0000-7eed8000       \               user32
ELF     7eed8000-7ef1c000       Deferred        advapi32<elf>
  \-PE  7eee0000-7ef1c000       \               advapi32
ELF     7ef1c000-7ef2f000       Deferred        libresolv.so.2
ELF     7ef2f000-7ef4e000       Deferred        iphlpapi<elf>
  \-PE  7ef40000-7ef4e000       \               iphlpapi
ELF     7ef4e000-7ef78000       Deferred        ws2_32<elf>
  \-PE  7ef60000-7ef78000       \               ws2_32
ELF     7efab000-7efb5000       Deferred        libnss_files.so.2
ELF     7efb5000-7efbe000       Deferred        libnss_nis.so.2
ELF     7efbe000-7efd3000       Deferred        libnsl.so.1
ELF     7efd3000-7eff5000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7cc1000-b7cc3000       Deferred        libnvidia-tls.so.1
ELF     b7cc3000-b7cc8000       Deferred        libxxf86vm.so.1
ELF     b7cc9000-b7ccc000       Deferred        libdl.so.2
ELF     b7ccc000-b7dfb000       Deferred        libc.so.6
ELF     b7dfb000-b7e0d000       Deferred        libpthread.so.0
ELF     b7e0e000-b7e11000       Deferred        libxau.so.6
ELF     b7e11000-b7e19000       Deferred        libsm.so.6
ELF     b7e19000-b7f2a000       Deferred        libwine.so.1
ELF     b7f2d000-b7f43000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000003f (D) F:\Games (Windows)\Steam\steam.exe
        00000043    0
        0000002c    0
        00000037    0
        00000030    0
        00000042    0
        0000000e    0
        00000032    0
        00000039    0
        00000010    0
        00000026    0
        00000024    0
        0000002b    0 <==
00000011
        0000002f    0
        00000016    0
        00000015    0
        00000014    0
        00000013    0
        00000012    0
0000000a
        0000000c    0
        0000000b    0

---

### Post by electricshoes on 2006-11-01
Benzies, did you install steam with Wine, or are you trying to run it from a windows partition ?

---

### Post by rekahsoft on 2006-11-02
can anybody answer my orignal ? ...thanks :)

---

### Post by shaggly on 2007-02-02
Funny enough, I also get the same error regarding the Class Object when I try and use the Photoshop CS2 installer. Whilst, the program is not related, I cannot help but wonder if that object class is causing a lot of the problems. My error looks like this:

"xxxx@xxxx-dapper:~/isotempfiles/Adobe(R) Photoshop(R) CS2$ wine msiexec /i Adobe\ Photoshop\ CS2.msi
fixme:advapi:LookupAccountNameW (null) L"xxxx" (nil) 0x34f808 (nil) 0x34f804 0x34f810 - stub
fixme:advapi:LookupAccountNameW (null) L"xxxx" 0x17fa88 0x34f808 0x17faa0 0x34f804 0x34f810 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
fixme:keyboard:X11DRV_GetKeyboardLayout couldn't return keyboard layout for thread 000e
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x8090809, 0000: stub!
fixme:ole:OleCreate
        {8856f961-340a-11d0-a96b-00c04fd705a2}
        {00000112-0000-0000-c000-000000000046} semi-stub!
fixme:shdocvw:PersistStorage_InitNew (0x6d9268)->(0x8e6470)
fixme:shdocvw:WebBrowser_QueryInterface (0x6d9268)->({0000011e-0000-0000-c000-000000000046} 0x7d54d9d4) interface not supported
fixme:shdocvw:OleObject_SetHostNames (0x6d9268)->(L"My Host Name", (null))
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
wine: Unhandled page fault on write access to 0xfaa9aea8 at address 0x6d9cc5 (thread 0019), starting debugger...
Unhandled exception: page fault on write access to 0xfaa9aea8 in 32-bit code (0x006d9cc5).
Register dump:....."

Obviously, the xxxx is substituted for user name.

I am investigating this problem a little further as I type, so any results, I will post back here.

---

