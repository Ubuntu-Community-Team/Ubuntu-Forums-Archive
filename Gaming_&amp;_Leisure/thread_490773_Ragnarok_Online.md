---
title: "Ragnarok Online"
date: 2007-07-02
forum: Gaming &amp; Leisure
---

### Post by TreeFinger on 2007-07-02
I am trying to get RO to work through Wine. I thought I almost had it, I got the patcher to actually open. 

Then Wine told me I needed to download wine_gecko for HTML viewing.

I did that but now I am getting a new error and I think it has to do with gecko.

```

:~/.wine/drive_c/Program Files/Gravity/RO$ wine Ragnarok.exe
fixme:shdocvw:PersistStreamInit_InitNew (0x174a40)
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x174a40)->(0)
fixme:shdocvw:navigate_url Unsupported arguments
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x174ad4)->((null) 1 0x33e57c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x174ad4)->((null) 25 2 0x33e590 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x174ad4)->((null) 26 2 0x33e590 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x174ad4)->(0x33e5cc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x174ad4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33e6f0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x1983b0)->(L"" L"" 0 0x33e704)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x1983b0)->(0x33e708 0x33e62c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x174ad4)->((null) 29 2 0x33ec74 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x174ad4)
fixme:shdocvw:ClientSite_GetContainer (0x174ad4)->(0x33ef20)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x174ad4)->(0xb7e45f49)
fixme:shdocvw:ClOleCommandTarget_Exec (0x174ad4)->((null) 25 2 0x33ee5c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x174ad4)->((null) 26 2 0x33ee5c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x174ad4)->(0x33ec84)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x174ad4)->(0xb7e45f49)
fixme:shdocvw:ClOleCommandTarget_Exec (0x174ad4)->((null) 25 2 0x33ebc0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x174ad4)->((null) 26 2 0x33ebc0 (nil))
err:wininet:FTP_DoPassive unknown response 'Entering passive mode', aborting
wine: Unhandled page fault on read access to 0x0000000b at address 0x7ee61a17 (thread 000d), starting debugger...
Unhandled exception: page fault on read access to 0x0000000b in 32-bit code (0x7ee61a17).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ee61a17 ESP:7d7ce410 EBP:7d7ce4a8 EFLAGS:00010217(   - 00      RIAP1C)
 EAX:00000000 EBX:7ee84794 ECX:00000002 EDX:00000001
 ESI:00000000 EDI:00000000
Stack dump:
0x7d7ce410:  00000037 7d7ce43c b7d150b6 7c148870
0x7d7ce420:  7eff00e7 00000015 7c105688 00000015
0x7d7ce430:  00000338 000001d0 b7de3880 7d7ce460
0x7d7ce440:  b7d15001 7c148870 7c105688 7ee6bf24
0x7d7ce450:  0000000a 00000001 b7d1fab1 7bc29ba1
0x7d7ce460:  7d7ce488 b7d1fab1 7c148870 7bc2951f
Backtrace:
=>1 0x7ee61a17 FTP_FtpFindFirstFileW+0x57() in wininet (0x7d7ce4a8)
  2 0x7ee62929 FtpFindFirstFileW+0x129() in wininet (0x7d7ce4f8)
  3 0x7ee63708 FtpFindFirstFileA+0xf8() in wininet (0x7d7ce788)
  4 0x00403c6d in ragnarok (+0x3c6d) (0x0041f890)
  5 0x00000000 (0x0041ac88)
  6 0x00408830 in ragnarok (+0x8830) (0x00408590)
0x7ee61a17 FTP_FtpFindFirstFileW+0x57 in wininet: testb $0x10,0xb(%edi)
Modules:
Module  Address                 Debug info      Name (145 modules)
PE      400000-424000   Export          ragnarok
PE      600a0000-600d9000       Deferred        appcomps
PE      600e0000-600f0000       Deferred        appshell
PE      60120000-6012f000       Deferred        caps
PE      60130000-60140000       Deferred        chrome
PE      60150000-60159000       Deferred        cookie
PE      60160000-6018c000       Deferred        docshell
PE      60200000-6021e000       Deferred        embedcomponents
PE      60230000-60254000       Deferred        gkgfxwin
PE      60260000-6052d000       Deferred        gklayout
PE      60530000-60568000       Deferred        gkparser
PE      605a0000-605c5000       Deferred        gkwidget
PE      605d0000-605fe000       Deferred        i18n
PE      60610000-60635000       Deferred        imglib2
PE      606d0000-606dd000       Deferred        jar50
PE      606e0000-606ef000       Deferred        jsd3250
PE      60940000-609bb000       Deferred        necko
PE      609e0000-609ec000       Deferred        oji
PE      60a00000-60a18000       Deferred        palmsync
PE      60a20000-60a27000       Deferred        perms
PE      60a30000-60a38000       Deferred        pipboot
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
PE      73dd0000-73ece000       Deferred        mfc42
PE      780c0000-78121000       Deferred        msvcp60
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d139000-7d13d000       Deferred        libgpg-error.so.0
ELF     7d13d000-7d18e000       Deferred        libgcrypt.so.11
ELF     7d18e000-7d1a3000       Deferred        libtasn1.so.3
ELF     7d1a3000-7d1d1000       Deferred        libcrypt.so.1
ELF     7d1d1000-7d241000       Deferred        libgnutls.so.13
ELF     7d241000-7d272000       Deferred        libcups.so.2
ELF     7d272000-7d312000       Deferred        comdlg32<elf>
  \-PE  7d280000-7d312000       \               comdlg32
ELF     7d312000-7d345000       Deferred        winspool<elf>
  \-PE  7d320000-7d345000       \               winspool
ELF     7d567000-7d57b000       Deferred        lz32<elf>
  \-PE  7d570000-7d57b000       \               lz32
ELF     7d57b000-7d594000       Deferred        version<elf>
  \-PE  7d580000-7d594000       \               version
ELF     7d594000-7d5c1000       Deferred        ws2_32<elf>
  \-PE  7d5a0000-7d5c1000       \               ws2_32
ELF     7d5c1000-7d5db000       Deferred        wsock32<elf>
  \-PE  7d5d0000-7d5db000       \               wsock32
ELF     7d5db000-7d64d000       Deferred        mshtml<elf>
  \-PE  7d5f0000-7d64d000       \               mshtml
ELF     7d64d000-7d683000       Deferred        urlmon<elf>
  \-PE  7d650000-7d683000       \               urlmon
ELF     7d683000-7d689000       Deferred        libnss_dns.so.2
ELF     7d689000-7d68c000       Deferred        libnss_mdns4_minimal.so.2
ELF     7d7f6000-7d891000       Deferred        oleaut32<elf>
  \-PE  7d810000-7d891000       \               oleaut32
ELF     7d891000-7d8cb000       Deferred        shdocvw<elf>
  \-PE  7d8a0000-7d8cb000       \               shdocvw
ELF     7da0b000-7da3d000       Deferred        uxtheme<elf>
  \-PE  7da10000-7da3d000       \               uxtheme
ELF     7da3f000-7da44000       Deferred        libxfixes.so.3
ELF     7da44000-7da4d000       Deferred        libxcursor.so.1
ELF     7da4d000-7da6a000       Deferred        imm32<elf>
  \-PE  7da50000-7da6a000       \               imm32
ELF     7da6a000-7da70000       Deferred        libxrandr.so.2
ELF     7da70000-7da78000       Deferred        libxrender.so.1
ELF     7da78000-7da7b000       Deferred        libxinerama.so.1
ELF     7e16e000-7e3e3000       Deferred        r200_dri.so
ELF     7e3e3000-7e3ec000       Deferred        libdrm.so.2
ELF     7e3ec000-7e44c000       Deferred        libgl.so.1
ELF     7e44c000-7e451000       Deferred        libxdmcp.so.6
ELF     7e451000-7e454000       Deferred        libxau.so.6
ELF     7e454000-7e545000       Deferred        libx11.so.6
ELF     7e545000-7e553000       Deferred        libxext.so.6
ELF     7e553000-7e558000       Deferred        libxxf86vm.so.1
ELF     7e558000-7e570000       Deferred        libice.so.6
ELF     7e570000-7e579000       Deferred        libsm.so.6
ELF     7e579000-7e607000       Deferred        winex11<elf>
  \-PE  7e590000-7e607000       \               winex11
ELF     7e684000-7e6a4000       Deferred        libexpat.so.1
ELF     7e6a4000-7e6cf000       Deferred        libfontconfig.so.1
ELF     7e6cf000-7e6e3000       Deferred        libz.so.1
ELF     7e6e3000-7e74e000       Deferred        libfreetype.so.6
ELF     7e74e000-7e7b5000       Deferred        msvcrt<elf>
  \-PE  7e760000-7e7b5000       \               msvcrt
ELF     7e7b5000-7e871000       Deferred        comctl32<elf>
  \-PE  7e7c0000-7e871000       \               comctl32
ELF     7e871000-7e966000       Deferred        shell32<elf>
  \-PE  7e880000-7e966000       \               shell32
ELF     7e966000-7e979000       Deferred        libresolv.so.2
ELF     7e979000-7e997000       Deferred        iphlpapi<elf>
  \-PE  7e980000-7e997000       \               iphlpapi
ELF     7e997000-7e9ec000       Deferred        rpcrt4<elf>
  \-PE  7e9a0000-7e9ec000       \               rpcrt4
ELF     7e9ec000-7ea86000       Deferred        ole32<elf>
  \-PE  7ea00000-7ea86000       \               ole32
ELF     7ea86000-7eadf000       Deferred        shlwapi<elf>
  \-PE  7eaa0000-7eadf000       \               shlwapi
ELF     7eadf000-7eb25000       Deferred        advapi32<elf>
  \-PE  7eaf0000-7eb25000       \               advapi32
ELF     7eb25000-7eb31000       Deferred        libgcc_s.so.1
ELF     7ec2b000-7ece8000       Deferred        gdi32<elf>
  \-PE  7ec40000-7ece8000       \               gdi32
ELF     7ece8000-7ee24000       Deferred        user32<elf>
  \-PE  7ed00000-7ee24000       \               user32
ELF     7ee24000-7ee43000       Deferred        mpr<elf>
  \-PE  7ee30000-7ee43000       \               mpr
ELF     7ee43000-7ee8b000       Export          wininet<elf>
  \-PE  7ee50000-7ee8b000       \               wininet
ELF     7ef9d000-7efa8000       Deferred        libnss_files.so.2
ELF     7efa8000-7efb2000       Deferred        libnss_nis.so.2
ELF     7efb2000-7efc9000       Deferred        libnsl.so.1
ELF     7efc9000-7eff0000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7cb9000-b7cbd000       Deferred        libdl.so.2
ELF     b7cbd000-b7dfe000       Deferred        libc.so.6
ELF     b7dfe000-b7e15000       Deferred        libpthread.so.0
ELF     b7e25000-b7f36000       Deferred        libwine.so.1
ELF     b7f38000-b7f53000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Gravity\RO\Ragnarok.exe
        00000014    0
        00000012    0
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0 <==
        00000009    0

```

---

### Post by Lukasz Tarkowski on 2008-03-01
I ge the same error

---

