---
title: "Woes of Wine for ACT!6.0"
date: 2006-12-19
forum: Desktop Environments
---

### Post by shane2peru on 2006-12-19
Ok, here is the problem.  I have finally gotten ACT! 6.0 installed in wine.  I have even gotten it to run!!!  I'm getting excited now!  And - ](*,)   I keep getting these errors when trying to access/open the database:
```
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:atl:AtlModuleInit SEMI-STUB (0x16c7328 0x16c7020 0x16c0000)
fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
err:dc:CreateDCW no driver found for L""
fixme:commdlg:GetFileName95 Flags 0x00800000 not yet implemented

```  Can anyone make any sense out of this?  I would really like to be rid of Windows, but I really need this program, and sorry but there is not a Linux program out there that even comes close to touching this program!  I have used it since version 3 - I think.  Dual booting is getting old, and VMWare is a still buggy.  I changed the permissions on the database to 777 and all the folders so that it can run them how it wants.  I have copied and pasted the whole user file from my Windows over to this one (then changed the permissions), I have tried to restore the database, and it crashes everytime.  The only different output I can get is when I try and open the database it reminds me that I haven't backed up in 57 days, so I start the backup procedure and it goes well, until, it gets toward the end and crashes!  I have tried using the database from a FAT32 partition, I have tried from my /home/shane/ACT file (ext3) and nothing!  Someone please help!  I really really need this program.   I have also tried crossover office, and no luck, it was worse than wine.  I'm running the most up-to-date version of wine from budgetdedicated .  If anyone has any ideas I would GREATLY, super GREATLY really super duper appreciate it!  Thanks.

Shane

ps, here is the error when trying to backup the database ```
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
shane@shane-laptop:~/C/ACT$ wine act.exe 
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:atl:AtlModuleInit SEMI-STUB (0x16c7328 0x16c7020 0x16c0000)
fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
err:dc:CreateDCW no driver found for L""
fixme:commdlg:GetFileName95 Flags 0x00800000 not yet implemented
err:x11drv:X11DRV_CreateWindow invalid window width -15
err:x11drv:X11DRV_CreateWindow invalid window height -20
err:x11drv:X11DRV_CreateWindow invalid window width -15
err:x11drv:X11DRV_CreateWindow invalid window height -20
err:x11drv:X11DRV_CreateWindow invalid window width -15
err:x11drv:X11DRV_CreateWindow invalid window height -20
fixme:shdocvw:PersistStreamInit_InitNew (0x1e5f420)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1e5f420)->(0)
err:x11drv:X11DRV_CreateWindow invalid window width -15
err:x11drv:X11DRV_CreateWindow invalid window height -20
err:x11drv:X11DRV_CreateWindow invalid window width -15
err:x11drv:X11DRV_CreateWindow invalid window height -20
err:x11drv:X11DRV_CreateWindow invalid window width -15
err:x11drv:X11DRV_CreateWindow invalid window height -20
wine: Call from 0x7b840790 to unimplemented function msvcrt.dll._mbsspnp, aborting
fixme:commdlg:GetFileName95 Flags 0x00800000 not yet implemented
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7d389db (thread 000e), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7d389db).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7d389db ESP:0032b20c EBP:0032b264 EFLAGS:00010283(   - 00      -RIS1C)
 EAX:00000000 EBX:b7e3aff4 ECX:00000000 EDX:b7e39f60
 ESI:00400000 EDI:b7e3b380
Stack dump:
0x0032b20c:  00000000 00000000 00000000 00000000
0x0032b21c:  00000000 00000000 00000000 00000000
0x0032b22c:  00000000 00000000 00000000 00000000
0x0032b23c:  00000000 00000000 00000000 00000000
0x0032b24c:  00000000 7ee6c671 00000000 b7e3aff4
0x0032b25c:  00400000 120216f6 0032b284 b7d3873f
Backtrace:
=>1 0xb7d389db in libc.so.6 (+0x2d9db) (0x0032b264)
  2 0xb7d3873f __strtol_internal+0x3f() in libc.so.6 (0x0032b284)
  3 0x7bc581e5 NTDLL_atoi+0x35() in ntdll (0x0032b2a4)
  4 0x01fd1933 in actzip (+0x1933) (0x00000000)
0xb7d389db: movzbl      0x0(%eax),%edx
Modules:
Module  Address                 Debug info      Name (156 modules)
PE      330000-336000   Deferred        actver
PE      340000-351000   Deferred        snprompt
PE      360000-3a6000   Deferred        sharenui
PE      3b0000-3c8000   Deferred        idal
PE      3d0000-3e5000   Deferred        mit
PE      3f0000-3f6000   Deferred        diag
PE      400000-91a000   Deferred        act
PE      920000-9b8000   Deferred        exchange
PE      9c0000-a64000   Deferred        adal
PE      a70000-b04000   Deferred        shareui
PE      b10000-b57000   Deferred        icdllw32
PE      b60000-b8e000   Deferred        pddllw32
PE      b90000-c08000   Deferred        graphsys
PE      c10000-c30000   Deferred        faxreq
PE      c30000-c3d000   Deferred        macrorec
PE      c40000-ccd000   Deferred        rptsys
PE      cd0000-ce9000   Deferred        actparse
PE      cf0000-d01000   Deferred        serial32
PE      d10000-d38000   Deferred        ldap32
PE      f80000-f87000   Deferred        rcsharenui
PE      f90000-fd3000   Deferred        actstr
PE      fe0000-fe7000   Deferred        rcsnprompt
PE      ff0000-ff7000   Deferred        rcidal
PE      1000000-1014000 Deferred        actnoxl8
PE      1020000-102b000 Deferred        rcadal
PE      1030000-1039000 Deferred        rcshareui
PE      1040000-1048000 Deferred        rcexchange
PE      1050000-105c000 Deferred        rcgraphsys
PE      1060000-1066000 Deferred        rcfaxreq
PE      1070000-1076000 Deferred        rcmacrorec
PE      1080000-108a000 Deferred        rcactparse
PE      1090000-109b000 Deferred        rcrptsys
PE      16c0000-16cd000 Deferred        actregistrationmfc
PE      16d0000-16e0000 Deferred        regact
PE      16f0000-1729000 Deferred        rcregact
PE      1730000-18d9000 Deferred        actres
PE      18e0000-1a4d000 Deferred        actdlg
PE      1a50000-1a58000 Deferred        rcoutlook
PE      1c90000-1ca1000 Deferred        res_ie
PE      1cb0000-1d6b000 Deferred        cb.dal
PE      1d70000-1d78000 Deferred        rccb
PE      1d80000-1d8c000 Deferred        actabcache
PE      1fd0000-1fd6000 Export          actzip
PE      2a00000-2a06000 Deferred        rcactzip
PE      10000000-10018000       Deferred        versit
PE      11000000-11020000       Deferred        aunzip32
PE      12000000-1202a000       Deferred        azip32
PE      44000000-4402a000       Deferred        osc61as
PE      4c000000-4c141000       Deferred        ot602as
PE      5f400000-5f4f2000       Deferred        mfc42
PE      780a0000-780b2000       Deferred        msvcirt
PE      780c0000-78121000       Deferred        msvcp60
ELF     7b800000-7b91b000       Deferred        kernel32<elf>
  \-PE  7b820000-7b91b000       \               kernel32
ELF     7bc00000-7bc83000       Export          ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c8f4000-7c930000       Deferred        shdocvw<elf>
  \-PE  7c900000-7c930000       \               shdocvw
ELF     7cd40000-7cd54000       Deferred        sensapi<elf>
  \-PE  7cd50000-7cd54000       \               sensapi
ELF     7cd54000-7cd73000       Deferred        mpr<elf>
  \-PE  7cd60000-7cd73000       \               mpr
ELF     7cd73000-7cdba000       Deferred        wininet<elf>
  \-PE  7cd80000-7cdba000       \               wininet
ELF     7d1be000-7d1d3000       Deferred        midimap<elf>
  \-PE  7d1c0000-7d1d3000       \               midimap
ELF     7d1f9000-7d211000       Deferred        msacm32<elf>
  \-PE  7d200000-7d211000       \               msacm32
ELF     7d211000-7d24d000       Deferred        wineoss<elf>
  \-PE  7d220000-7d24d000       \               wineoss
ELF     7d24d000-7d2db000       Deferred        winmm<elf>
  \-PE  7d260000-7d2db000       \               winmm
ELF     7d2db000-7d302000       Deferred        msvfw32<elf>
  \-PE  7d2e0000-7d302000       \               msvfw32
ELF     7d302000-7d324000       Deferred        atl<elf>
  \-PE  7d310000-7d324000       \               atl
ELF     7d324000-7d328000       Deferred        libgpg-error.so.0
ELF     7d328000-7d376000       Deferred        libgcrypt.so.11
ELF     7d376000-7d389000       Deferred        libtasn1.so.3
ELF     7d389000-7d3b7000       Deferred        libcrypt.so.1
ELF     7d3c6000-7d435000       Deferred        libgnutls.so.13
ELF     7d435000-7d464000       Deferred        libcups.so.2
ELF     7d48c000-7d4be000       Deferred        uxtheme<elf>
  \-PE  7d490000-7d4be000       \               uxtheme
ELF     7d4c5000-7d4ca000       Deferred        libxfixes.so.3
ELF     7d4ca000-7d4d3000       Deferred        libxcursor.so.1
ELF     7d4d3000-7d4ef000       Deferred        imm32<elf>
  \-PE  7d4e0000-7d4ef000       \               imm32
ELF     7d4ef000-7d50d000       Deferred        ximcp.so.2
ELF     7d50d000-7d50f000       Deferred        xlcutf8load.so.2
ELF     7d50f000-7d512000       Deferred        libxrandr.so.2
ELF     7d512000-7d51a000       Deferred        libxrender.so.1
ELF     7d51a000-7d51d000       Deferred        libxinerama.so.1
ELF     7e11f000-7e34a000       Deferred        i915_dri.so
ELF     7e34a000-7e351000       Deferred        libdrm.so.2
ELF     7e351000-7e3c0000       Deferred        libgl.so.1
ELF     7e3c0000-7e489000       Deferred        libx11.so.6
ELF     7e489000-7e496000       Deferred        libxext.so.6
ELF     7e496000-7e4ae000       Deferred        libice.so.6
ELF     7e4ae000-7e53b000       Deferred        winex11<elf>
  \-PE  7e4c0000-7e53b000       \               winex11
ELF     7e53b000-7e559000       Deferred        libexpat.so.1
ELF     7e559000-7e588000       Deferred        libfontconfig.so.1
ELF     7e588000-7e59c000       Deferred        libz.so.1
ELF     7e59c000-7e606000       Deferred        libfreetype.so.6
ELF     7e606000-7e632000       Deferred        ws2_32<elf>
  \-PE  7e610000-7e632000       \               ws2_32
ELF     7e632000-7e64c000       Deferred        wsock32<elf>
  \-PE  7e640000-7e64c000       \               wsock32
ELF     7e64c000-7e6e3000       Deferred        oleaut32<elf>
  \-PE  7e660000-7e6e3000       \               oleaut32
ELF     7e6e3000-7e715000       Deferred        winspool<elf>
  \-PE  7e6f0000-7e715000       \               winspool
ELF     7e715000-7e7b4000       Deferred        comdlg32<elf>
  \-PE  7e720000-7e7b4000       \               comdlg32
ELF     7e7b4000-7e7c8000       Deferred        lz32<elf>
  \-PE  7e7c0000-7e7c8000       \               lz32
ELF     7e7c8000-7e7e1000       Deferred        version<elf>
  \-PE  7e7d0000-7e7e1000       \               version
ELF     7e7e1000-7e8a1000       Deferred        comctl32<elf>
  \-PE  7e7f0000-7e8a1000       \               comctl32
ELF     7e8a1000-7e8b4000       Deferred        libresolv.so.2
ELF     7e8b4000-7e8d2000       Deferred        iphlpapi<elf>
  \-PE  7e8c0000-7e8d2000       \               iphlpapi
ELF     7e8d2000-7e926000       Deferred        rpcrt4<elf>
  \-PE  7e8e0000-7e926000       \               rpcrt4
ELF     7e926000-7e9bb000       Deferred        ole32<elf>
  \-PE  7e930000-7e9bb000       \               ole32
ELF     7e9bb000-7ea13000       Deferred        shlwapi<elf>
  \-PE  7e9d0000-7ea13000       \               shlwapi
ELF     7ea13000-7eb05000       Deferred        shell32<elf>
  \-PE  7ea20000-7eb05000       \               shell32
ELF     7eb05000-7ec3d000       Deferred        user32<elf>
  \-PE  7eb20000-7ec3d000       \               user32
ELF     7ec3d000-7ec83000       Deferred        advapi32<elf>
  \-PE  7ec50000-7ec83000       \               advapi32
ELF     7ec83000-7ec8e000       Deferred        libgcc_s.so.1
ELF     7ec8f000-7ec94000       Deferred        libxdmcp.so.6
ELF     7ec94000-7ec9d000       Deferred        libsm.so.6
ELF     7ed7c000-7ee32000       Deferred        gdi32<elf>
  \-PE  7ed90000-7ee32000       \               gdi32
ELF     7ee32000-7ee96000       Deferred        msvcrt<elf>
  \-PE  7ee40000-7ee96000       \               msvcrt
ELF     7efa0000-7efab000       Deferred        libnss_files.so.2
ELF     7efab000-7efb5000       Deferred        libnss_nis.so.2
ELF     7efb5000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff1000       Deferred        libm.so.6
ELF     7eff2000-7eff7000       Deferred        libxxf86vm.so.1
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d01000-b7d04000       Deferred        libxau.so.6
ELF     b7d07000-b7d0b000       Deferred        libdl.so.2
ELF     b7d0b000-b7e3f000       Export          libc.so.6
ELF     b7e40000-b7e53000       Deferred        libpthread.so.0
ELF     b7e62000-b7f73000       Deferred        libwine.so.1
ELF     b7f75000-b7f90000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f 
        00000011    0
        00000010    0
0000000d (D) C:\Program Files\ACT\act.exe
        0000001b    0
        0000001a    0
        00000019  -15
        00000018   15
        00000017    0
        00000016  -15
        00000015    0
        00000014    0
        00000013    0
        00000012    0
        0000000e    0 <==

```

---

### Post by shane2peru on 2006-12-24
In case anyone else searches and stumbles across this thread I did get it working!!!  There was a wine update.  I'm using wine-0.9.28 (was updated this morning).  I set Act to run in Win 98, and in the Library I set the MSVCRT to Native, Bulletin.  It seems to work great!  

Shane

PS - I did find this group more helpful for wine problems:  [http://groups.google.com/group/comp.emulators.ms-windows.wine?hl=en]("http://groups.google.com/group/comp.emulators.ms-windows.wine?hl=en")
Seems to be the wine support group.

---

