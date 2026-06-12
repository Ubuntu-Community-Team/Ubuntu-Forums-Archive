---
title: "error installing ie6 with winetools"
date: 2006-08-12
forum: Desktop Environments
---

### Post by computergroove on 2006-08-12
Started installing wine and wine tools. Everything was working fine. Rebuilt the fake windows directory with WT and installed the entire base system except IE6. When I tried to install IE6 I got the following after it said that it failed. Can anyone help me with this? 

```
using english setup...
sytempath=/home/user/.wine/dosdevices/c:/windows/system32
Microsoft Internet Explorer.* to check
software installation verified by /home/user/.wine/winetools.log
downloading http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/ie6setup.exe to ie6setup.exe with 491768 bytes...
WINEDEBUG="fixme-all" WINEDLLOVERRIDES="" wine ./ie6setup.exe
waiting for wineservers to exit...
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 000c), starting debugger...
WineDbg starting on pid 0xa
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:119f GS:0033
 EIP:00000000 ESP:7ecfdc54 EBP:7ecfdcf0 EFLAGS:00010202(   - 00      - -RI1)
 EAX:7ebe0000 EBX:7ebf8678 ECX:00000000 EDX:7ebf3fe7
 ESI:00000001 EDI:7ebfeddc
Stack dump:
0x7ecfdc54:  7ebe9551 7ebe0000 7ebf3fe7 7ecfdcdc
0x7ecfdc64:  0000baf9 000011ce 0000008c 00000082
0x7ecfdc74:  00000000 000000aa 00000000 0000004b
0x7ecfdc84:  000000a9 0000000b 00000000 7ebf4158
0x7ecfdc94:  7ecfdca4 00000001 00000000 00000007
0x7ecfdca4:  7ebf3f57 7fd904d8 7ebf3f69 7fd90508
0233: sel=119f base=7f302000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x00000000 (0x00000000)
  2 0x7ebe9d89 DllRegisterServer+0x614 in urlmon (0x7ebe9d89)
fixme:dbghelp:sffip_cb NIY on 'advpack.pdb'
  3 0x715f4c3b in advpack (+0x4c3b) (0x715f4c3b)
  4 0x715f880b in advpack (+0x880b) (0x715f880b)
  5 0x715f98a3 in advpack (+0x98a3) (0x715f98a3)
  6 0x715f9e9b in advpack (+0x9e9b) (0x715f9e9b)
fixme:dbghelp:sffip_cb NIY on 'ie6wzdex.pdb'
  7 0x010167a3 in ie6wzd (+0x167a3) (0x010167a3)
  8 0x0100b966 in ie6wzd (+0xb966) (0x0100b966)
  9 0x7fc56478 in kernel32 (+0x66478) (0x7fc56478)
  10 0x7ffbc543 in ntdll (+0x3c543) (0x7ffbc543)
  11 0xb7f4e341 start_thread+0x81 in libpthread.so.0 (0xb7f4e341)
  12 0xb7ee34ee __clone+0x5e in libc.so.6 (0xb7ee34ee)
0x00000000: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (73 modules)
PE      0x01000000-01034000     Export          ie6wzd
PE      0x65f00000-65fc2000     Deferred        ole32
PE      0x70100000-70153000     Deferred        rpcrt4
PE      0x715f0000-71617000     Export          advpack
PE      0x716a0000-716a7000     Deferred        w95inf32
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7eb62000-7eba9000     Deferred        wininet<elf>
  \-PE  0x7eb70000-7eba9000     \               wininet
ELF     0x7eba9000-7ebca000     Deferred        cabinet<elf>
  \-PE  0x7ebb0000-7ebca000     \               cabinet
ELF     0x7ebca000-7ebff000     Export          urlmon<elf>
  \-PE  0x7ebe0000-7ebff000     \               urlmon
ELF     0x7eeab000-7ef00000     Deferred        setupapi<elf>
  \-PE  0x7eec0000-7ef00000     \               setupapi
ELF     0x7f096000-7f0dc000     Deferred        riched20<elf>
  \-PE  0x7f0b0000-7f0dc000     \               riched20
ELF     0x7f0dc000-7f0f0000     Deferred        riched32<elf>
  \-PE  0x7f0e0000-7f0f0000     \               riched32
ELF     0x7f1d9000-7f234000     Deferred        shlwapi<elf>
  \-PE  0x7f1f0000-7f234000     \               shlwapi
ELF     0x7f234000-7f300000     Deferred        shell32<elf>
  \-PE  0x7f250000-7f300000     \               shell32
ELF     0x7f30d000-7f33e000     Deferred        uxtheme<elf>
  \-PE  0x7f310000-7f33e000     \               uxtheme
ELF     0x7f382000-7f38b000     Deferred        libxcursor.so.1
ELF     0x7f38b000-7f3a7000     Deferred        imm32<elf>
  \-PE  0x7f390000-7f3a7000     \               imm32
ELF     0x7f3a7000-7f447000     Deferred        libgl.so.1
ELF     0x7f447000-7f52d000     Deferred        libx11.so.6
ELF     0x7f52d000-7f545000     Deferred        libice.so.6
ELF     0x7f545000-7f5c8000     Deferred        winex11<elf>
  \-PE  0x7f550000-7f5c8000     \               winex11
ELF     0x7f5c8000-7f5e7000     Deferred        libexpat.so.1
ELF     0x7f5e7000-7f615000     Deferred        libfontconfig.so.1
ELF     0x7f615000-7f629000     Deferred        libz.so.1
ELF     0x7f629000-7f692000     Deferred        libfreetype.so.6
ELF     0x7f692000-7f6a6000     Deferred        lz32<elf>
  \-PE  0x7f6a0000-7f6a6000     \               lz32
ELF     0x7f6a6000-7f6bf000     Deferred        version<elf>
  \-PE  0x7f6b0000-7f6bf000     \               version
ELF     0x7f6bf000-7f77f000     Deferred        comctl32<elf>
  \-PE  0x7f6d0000-7f77f000     \               comctl32
ELF     0x7f77f000-7f79e000     Deferred        mpr<elf>
  \-PE  0x7f790000-7f79e000     \               mpr
ELF     0x7f79e000-7f8ca000     Deferred        user32<elf>
  \-PE  0x7f7c0000-7f8ca000     \               user32
ELF     0x7f99f000-7fa50000     Deferred        gdi32<elf>
  \-PE  0x7f9b0000-7fa50000     \               gdi32
ELF     0x7fa50000-7fa90000     Deferred        advapi32<elf>
  \-PE  0x7fa60000-7fa90000     \               advapi32
ELF     0x7fb93000-7fb9b000     Deferred        libxrender.so.1
ELF     0x7fbce000-7fcd0000     Export          kernel32<elf>
  \-PE  0x7fbf0000-7fcd0000     \               kernel32
ELF     0x7fcd3000-7fce0000     Deferred        libxext.so.6
ELF     0x7fce4000-7fce8000     Deferred        libxfixes.so.3
ELF     0x7fce8000-7fceb000     Deferred        libxau.so.6
ELF     0x7fceb000-7fcf0000     Deferred        libxxf86vm.so.1
ELF     0x7fe02000-7fe0c000     Deferred        libgcc_s.so.1
ELF     0x7fe0c000-7fe16000     Deferred        libnss_files.so.2
ELF     0x7fe16000-7fe1f000     Deferred        libnss_nis.so.2
ELF     0x7fe1f000-7fe34000     Deferred        libnsl.so.1
ELF     0x7fe34000-7fe3d000     Deferred        libnss_compat.so.2
ELF     0x7fe3d000-7fe42000     Deferred        libxxf86dga.so.1
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Export          ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e17000-b7e1a000     Deferred        libdl.so.2
ELF     0xb7e1a000-b7f49000     Export          libc.so.6
ELF     0xb7f49000-b7f5b000     Export          libpthread.so.0
ELF     0xb7f68000-b7f82000     Deferred        libwine.so.1
ELF     0xb7f85000-b7f9b000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) C:\windows\temp\IXP001.TMP\ie6wzd.exe
        0000000c    0 <==
        0000000b    0
00000008
        00000009    0
all wineservers endet after 4 seconds...
Failed: 0
check installation by path or registry value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Microsoft Internet Explorer.* to check
software installation verified by /home/user/.wine/winetools.log
Failed: 1
Failed: 1
mv: cannot stat `/home/user/.wine/dosdevices/c:/windows/system32/regsvr32.exe': No such file or directory
du: cannot access `/home/user/winetools/sys/Windows Update Setup Files': No such file or directory
du: cannot access `/home/user/.wine/c/windows/Windows Update Setup Files': No such file or directory
Downloaded IE6-Files=0
Winetools  IE6-Files=0

```

I posted a question on how to browse to the fake drive c folder in a browser window but am still waiting on a reply. I am guessing that I need to copy regsvr32.exe into windows/system32. Ill try to install the windows installer part if wt and see if it helps.

---

### Post by Jagot on 2006-08-12
I can't answer the question directly, but I can say that the following link gives you the best way of install IE on Linux - works flawlessly every time for me:

[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

---

### Post by computergroove on 2006-08-12
This looks like an IE 4 environment testing spftware. I dont need to test an ie6 environment I need to install ie6 within my wine installation because I need to install other things that depend on ie. Would this really help for wine?

---

### Post by Jagot on 2006-08-12
It is not IE4 - the 4 is as in for.  As it says on the site:

> Run IE 6, 5.5 and 5 on Linux with Wine

---

### Post by quiv on 2006-12-27
I get the same error when trying to install IE6 from WineTools on wine 0.9.9. 

```
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0014), starting debugger...
WineDbg starting on pid 0x12
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:119f GS:0033
 EIP:00000000 ESP:7e61dc54 EBP:7e61dcf0 EFLAGS:00010202(   - 00      - -RI1)
 EAX:7e4e0000 EBX:7e4fa678 ECX:00000000 EDX:7e4f5fe7
 ESI:00000001 EDI:7e500ddc
Stack dump:
0x7e61dc54:  7e4eb551 7e4e0000 7e4f5fe7 7e61dcdc
0x7e61dc64:  0000baf9 000011ce 0000008c 00000082
0x7e61dc74:  00000000 000000aa 00000000 0000004b
0x7e61dc84:  000000a9 0000000b 00000000 7e4f6158
0x7e61dc94:  7e61dca4 00000001 00000000 00000007
0x7e61dca4:  7e4f5f57 7fd70540 7e4f5f69 7fd70570
0233: sel=119f base=7fce2000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x00000000 (0x00000000)
  2 0x7e4ebd89 DllRegisterServer+0x614 in urlmon (0x7e4ebd89)
fixme:dbghelp:sffip_cb NIY on 'advpack.pdb'
  3 0x715f4c3b in advpack (+0x4c3b) (0x715f4c3b)
  4 0x715f880b in advpack (+0x880b) (0x715f880b)
  5 0x715f98a3 in advpack (+0x98a3) (0x715f98a3)
  6 0x715f9e9b in advpack (+0x9e9b) (0x715f9e9b)
fixme:dbghelp:sffip_cb NIY on 'ie6wzdex.pdb'
  7 0x010167a3 in ie6wzd (+0x167a3) (0x010167a3)
  8 0x0100b966 in ie6wzd (+0xb966) (0x0100b966)
  9 0x7fc56478 in kernel32 (+0x66478) (0x7fc56478)
  10 0x7ffbc543 in ntdll (+0x3c543) (0x7ffbc543)
  11 0xb7eef341 start_thread+0x81 in libpthread.so.0 (0xb7eef341)
  12 0xb7e844ee __clone+0x5e in libc.so.6 (0xb7e844ee)
0x00000000: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (75 modules)
PE      0x01000000-01034000     Export          ie6wzd
PE      0x65f00000-65fc2000     Deferred        ole32
PE      0x70100000-70153000     Deferred        rpcrt4
PE      0x715f0000-71617000     Export          advpack
PE      0x716a0000-716a7000     Deferred        w95inf32
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e464000-7e4ab000     Deferred        wininet<elf>
  \-PE  0x7e470000-7e4ab000     \               wininet
ELF     0x7e4ab000-7e4cc000     Deferred        cabinet<elf>
  \-PE  0x7e4b0000-7e4cc000     \               cabinet
ELF     0x7e4cc000-7e501000     Export          urlmon<elf>
  \-PE  0x7e4e0000-7e501000     \               urlmon
ELF     0x7e77b000-7e7d0000     Deferred        setupapi<elf>
  \-PE  0x7e790000-7e7d0000     \               setupapi
ELF     0x7e966000-7e9ac000     Deferred        riched20<elf>
  \-PE  0x7e980000-7e9ac000     \               riched20
ELF     0x7e9ac000-7e9c0000     Deferred        riched32<elf>
  \-PE  0x7e9b0000-7e9c0000     \               riched32
ELF     0x7ea59000-7eab4000     Deferred        shlwapi<elf>
  \-PE  0x7ea70000-7eab4000     \               shlwapi
ELF     0x7eab4000-7eb80000     Deferred        shell32<elf>
  \-PE  0x7ead0000-7eb80000     \               shell32
ELF     0x7eb8b000-7ebbc000     Deferred        uxtheme<elf>
  \-PE  0x7eb90000-7ebbc000     \               uxtheme
ELF     0x7ebda000-7ebe3000     Deferred        libxcursor.so.1
ELF     0x7ebe3000-7ebff000     Deferred        imm32<elf>
  \-PE  0x7ebf0000-7ebff000     \               imm32
ELF     0x7ebff000-7f3c2000     Deferred        libglcore.so.1
ELF     0x7f3c2000-7f447000     Deferred        libgl.so.1
ELF     0x7f447000-7f52d000     Deferred        libx11.so.6
ELF     0x7f52d000-7f545000     Deferred        libice.so.6
ELF     0x7f545000-7f5c8000     Deferred        winex11<elf>
  \-PE  0x7f550000-7f5c8000     \               winex11
ELF     0x7f5c8000-7f5e7000     Deferred        libexpat.so.1
ELF     0x7f5e7000-7f615000     Deferred        libfontconfig.so.1
ELF     0x7f615000-7f629000     Deferred        libz.so.1
ELF     0x7f629000-7f692000     Deferred        libfreetype.so.6
ELF     0x7f692000-7f6a6000     Deferred        lz32<elf>
  \-PE  0x7f6a0000-7f6a6000     \               lz32
ELF     0x7f6a6000-7f6bf000     Deferred        version<elf>
  \-PE  0x7f6b0000-7f6bf000     \               version
ELF     0x7f6bf000-7f77f000     Deferred        comctl32<elf>
  \-PE  0x7f6d0000-7f77f000     \               comctl32
ELF     0x7f77f000-7f79e000     Deferred        mpr<elf>
  \-PE  0x7f790000-7f79e000     \               mpr
ELF     0x7f79e000-7f8ca000     Deferred        user32<elf>
  \-PE  0x7f7c0000-7f8ca000     \               user32
ELF     0x7f99f000-7fa50000     Deferred        gdi32<elf>
  \-PE  0x7f9b0000-7fa50000     \               gdi32
ELF     0x7fa50000-7fa90000     Deferred        advapi32<elf>
  \-PE  0x7fa60000-7fa90000     \               advapi32
ELF     0x7fb93000-7fb9b000     Deferred        libxrender.so.1
ELF     0x7fbce000-7fcd0000     Export          kernel32<elf>
  \-PE  0x7fbf0000-7fcd0000     \               kernel32
ELF     0x7fcd3000-7fce0000     Deferred        libxext.so.6
ELF     0x7fce6000-7fcf0000     Deferred        libgcc_s.so.1
ELF     0x7fe00000-7fe04000     Deferred        libxfixes.so.3
ELF     0x7fe04000-7fe09000     Deferred        libxxf86vm.so.1
ELF     0x7fe09000-7fe13000     Deferred        libnss_files.so.2
ELF     0x7fe13000-7fe1c000     Deferred        libnss_nis.so.2
ELF     0x7fe1c000-7fe31000     Deferred        libnsl.so.1
ELF     0x7fe31000-7fe3a000     Deferred        libnss_compat.so.2
ELF     0x7fe3a000-7fe3d000     Deferred        libxau.so.6
ELF     0x7fe3d000-7fe42000     Deferred        libxxf86dga.so.1
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Export          ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7db0000-b7db2000     Deferred        libnvidia-tls.so.1
ELF     0xb7db8000-b7dbb000     Deferred        libdl.so.2
ELF     0xb7dbb000-b7eea000     Export          libc.so.6
ELF     0xb7eea000-b7efc000     Export          libpthread.so.0
ELF     0xb7f0c000-b7f26000     Deferred        libwine.so.1
ELF     0xb7f29000-b7f3f000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000012 (D) C:\windows\temp\IXP002.TMP\ie6wzd.exe
        00000014    0 <==
        00000013    0
00000010
        00000011    0
```


I installed IE6 from the IEs 4 Linux link above. This installed fine, but WineTools doesn't see/recognize this installation. How can I get WineTools to recognize this install, or how can I get past this error when installing IE6 via WineTools?

---

### Post by uncleclinto on 2007-07-08
I'm with you.  I get the same error, and everyone and their grandmother wants to direct me to the IEs 4 Linux.  I have it.  It works fine.  Yippy.  That does not a darn thing for my wine environment.  I need it there to get full functionality out of my Macromedia Studio Suite.  Then I can kiss windows good bye.

Does anyone have a solution to our actual problem?

---

