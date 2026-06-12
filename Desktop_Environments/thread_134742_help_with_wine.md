---
title: "help with wine"
date: 2006-02-22
forum: Desktop Environments
---

### Post by tlaloczint on 2006-02-22
I tried to run winectg and it just closes on me 
I tried several times I already search the forum but no anwser 

this is the log I have 

tlaloczint@aztlan:~$ winecfg
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\tlaloczint\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\tlaloczint\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\tlaloczint\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\tlaloczint\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\tlaloczint\\Desktop"'.
err:commdlg:IShellBrowserImpl_BrowseObject could not browse to folder
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\tlaloczint\\Desktop"'.
err:commdlg:IShellBrowserImpl_BrowseObject could not browse to folder
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\tlaloczint\\Desktop"'.
err:commdlg:IShellBrowserImpl_BrowseObject could not browse to folder
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\tlaloczint\\Desktop"'.
err:commdlg:IShellBrowserImpl_BrowseObject could not browse to folder
wine: Unhandled page fault on read access to 0x00000000 at address 0x7f93a5dc (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7f93a5dc).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7f93a5dc ESP:7fabc640 EBP:7fabc688 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:7fabc678 EBX:7f9573b8 ECX:7f6a33d1 EDX:00000000
 ESI:00010042 EDI:7fabe26c
Stack dump:
0x00000000:  00000000 00000000 00000000 00000000
0x00000010:  00000000 00000000 00000000 00000000
0x00000020:  00000000 00000000 00000000 00000000
0x00000030:  00000000 00000000 00000000 00000000
0x00000040:  00000000 00000000 00000000 00000000
0x00000050:  00000000 00000000 00000000 00000000
0200: sel=1007 base=7ffdc000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7f93a5dc in comdlg32 (+0xa5dc) (0x7f93a5dc)
  2 0x7f93fcee in comdlg32 (+0xfcee) (0x7f93fcee)
  3 0x7f9408ce FileOpenDlgProc95+0x9fe in comdlg32 (0x7f9408ce)
  4 0x7f6c1aca WINPROC_wrapper+0x1a in user32 (0x7f6c1aca)
  5 0x7f6c2716 in user32 (+0x92716) (0x7f6c2716)
  6 0x7f6c5bca CallWindowProcA+0x7a in user32 (0x7f6c5bca)
  7 0x7f66348d DefDlgProcA+0x5d in user32 (0x7f66348d)
  8 0x7f6c1aca WINPROC_wrapper+0x1a in user32 (0x7f6c1aca)
  9 0x7f6c2716 in user32 (+0x92716) (0x7f6c2716)
  10 0x7f6c7ac1 CallWindowProcW+0x121 in user32 (0x7f6c7ac1)
  11 0x7f694487 in user32 (+0x64487) (0x7f694487)
  12 0x7f697e1c SendMessageTimeoutW+0x16c in user32 (0x7f697e1c)
  13 0x7f697e67 SendMessageW+0x37 in user32 (0x7f697e67)
  14 0x7eb7b5f2 in comctl32 (+0x6b5f2) (0x7eb7b5f2)
  15 0x7eb7de6d in comctl32 (+0x6de6d) (0x7eb7de6d)
  16 0x7f6c1aca WINPROC_wrapper+0x1a in user32 (0x7f6c1aca)
  17 0x7f6c2716 in user32 (+0x92716) (0x7f6c2716)
  18 0x7f6c7b51 CallWindowProcW+0x1b1 in user32 (0x7f6c7b51)
  19 0x7f694cc2 DispatchMessageW+0x172 in user32 (0x7f694cc2)
  20 0x7f6673e9 IsDialogMessageW+0xf9 in user32 (0x7f6673e9)
  21 0x7f667b6d DIALOG_DoDialogBox+0x10d in user32 (0x7f667b6d)
  22 0x7f66931b DialogBoxIndirectParamAorW+0x4b in user32 (0x7f66931b)
  23 0x7f6693ae DialogBoxIndirectParamA+0x2e in user32 (0x7f6693ae)
  24 0x7f93a221 in comdlg32 (+0xa221) (0x7f93a221)
  25 0x7f93c152 GetFileDialog95A+0x342 in comdlg32 (0x7f93c152)
  26 0x7f93c324 GetOpenFileNameA+0x44 in comdlg32 (0x7f93c324)
  27 0x7fadbc9a AppDlgProc+0x58a in winecfg (0x7fadbc9a)
  28 0x7f6c1aca WINPROC_wrapper+0x1a in user32 (0x7f6c1aca)
  29 0x7f6c2716 in user32 (+0x92716) (0x7f6c2716)
  30 0x7f6c7b51 CallWindowProcW+0x1b1 in user32 (0x7f6c7b51)
  31 0x7f6632cd DefDlgProcW+0x5d in user32 (0x7f6632cd)
  32 0x7f6c1aca WINPROC_wrapper+0x1a in user32 (0x7f6c1aca)
  33 0x7f6c2716 in user32 (+0x92716) (0x7f6c2716)
  34 0x7f6c7ddb CallWindowProcW+0x43b in user32 (0x7f6c7ddb)
  35 0x7f694487 in user32 (+0x64487) (0x7f694487)
  36 0x7f697e1c SendMessageTimeoutW+0x16c in user32 (0x7f697e1c)
  37 0x7f697e67 SendMessageW+0x37 in user32 (0x7f697e67)
  38 0x7f64c85a in user32 (+0x1c85a) (0x7f64c85a)
  39 0x7f64d13a in user32 (+0x1d13a) (0x7f64d13a)
  40 0x7f6c1aca WINPROC_wrapper+0x1a in user32 (0x7f6c1aca)
  41 0x7f6c2716 in user32 (+0x92716) (0x7f6c2716)
  42 0x7f6c7b51 CallWindowProcW+0x1b1 in user32 (0x7f6c7b51)
  43 0x7f694cc2 DispatchMessageW+0x172 in user32 (0x7f694cc2)
  44 0x7f6673e9 IsDialogMessageW+0xf9 in user32 (0x7f6673e9)
  45 0x7eb52604 in comctl32 (+0x42604) (0x7eb52604)
  46 0x7eb543e6 PropertySheetW+0x246 in comctl32 (0x7eb543e6)
  47 0x7fae2c7d WinMain+0x33d in winecfg (0x7fae2c7d)
  48 0x7fae6e0a main+0xaa in winecfg (0x7fae6e0a)
  49 0x7fae6d3e in winecfg (+0x16d3e) (0x7fae6d3e)
  50 0x7fccce0f in kernel32 (+0x4ce0f) (0x7fccce0f)
  51 0xb7ec7237 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7ec7237)
0x7f93a5dc: movl        0x0(%edx),%ecx
Modules:
Module  Address                 Debug info      Name (83 modules)
ELF     0x7be87000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7dbcb000-7dbe0000     Deferred        midimap<elf>
  \-PE  0x7dbd0000-7dbe0000     \               midimap
ELF     0x7dcf6000-7dd1a000     Deferred        msacm32<elf>
  \-PE  0x7dd00000-7dd1a000     \               msacm32
ELF     0x7dd1a000-7dd5d000     Deferred        wineoss<elf>
  \-PE  0x7dd30000-7dd5d000     \               wineoss
ELF     0x7dd5d000-7dda9000     Deferred        libgcrypt.so.11
ELF     0x7dda9000-7de0b000     Deferred        libgnutls.so.11
ELF     0x7de0b000-7de28000     Deferred        libcups.so.2
ELF     0x7de29000-7de40000     Deferred        msacm<elf>
  \-PE  0x7de30000-7de40000     \               msacm
ELF     0x7de8c000-7de90000     Deferred        libgpg-error.so.0
ELF     0x7df67000-7df70000     Deferred        libxcursor.so.1
ELF     0x7df70000-7df8c000     Deferred        imm32<elf>
  \-PE  0x7df80000-7df8c000     \               imm32
ELF     0x7df8c000-7dfa8000     Deferred        ximcp.so.2
ELF     0x7dfa8000-7dfb0000     Deferred        libxrender.so.1
ELF     0x7dfb0000-7e76e000     Deferred        libglcore.so.1
ELF     0x7e76e000-7e7f1000     Deferred        libgl.so.1
ELF     0x7e7f1000-7e8b1000     Deferred        libx11.so.6
ELF     0x7e8b1000-7e8be000     Deferred        libxext.so.6
ELF     0x7e8be000-7e8d7000     Deferred        libice.so.6
ELF     0x7e8d7000-7e956000     Deferred        winex11<elf>
  \-PE  0x7e8f0000-7e956000     \               winex11
ELF     0x7e956000-7e975000     Deferred        libexpat.so.1
ELF     0x7e975000-7e9a3000     Deferred        libfontconfig.so.1
ELF     0x7e9a3000-7e9b7000     Deferred        libz.so.1
ELF     0x7e9b7000-7ea21000     Deferred        libfreetype.so.6
ELF     0x7ea21000-7ea52000     Deferred        uxtheme<elf>
  \-PE  0x7ea30000-7ea52000     \               uxtheme
ELF     0x7ea52000-7ead9000     Deferred        winmm<elf>
  \-PE  0x7ea60000-7ead9000     \               winmm
ELF     0x7ead9000-7eb03000     Deferred        winspool<elf>
  \-PE  0x7eae0000-7eb03000     \               winspool
ELF     0x7eb03000-7ebb7000     Export          comctl32<elf>
  \-PE  0x7eb10000-7ebb7000     \               comctl32
ELF     0x7ebb7000-7ebd5000     Deferred        iphlpapi<elf>
  \-PE  0x7ebc0000-7ebd5000     \               iphlpapi
ELF     0x7ebd5000-7ec1d000     Deferred        rpcrt4<elf>
  \-PE  0x7ebf0000-7ec1d000     \               rpcrt4
ELF     0x7ec1d000-7ec28000     Deferred        libgcc_s.so.1
ELF     0x7ed0e000-7f611000     Deferred        gdi32<elf>
  \-PE  0x7ed50000-7f611000     \               gdi32
ELF     0x7f611000-7f733000     Export          user32<elf>
  \-PE  0x7f630000-7f733000     \               user32
ELF     0x7f733000-7f770000     Deferred        advapi32<elf>
  \-PE  0x7f740000-7f770000     \               advapi32
ELF     0x7f770000-7f7fb000     Deferred        ole32<elf>
  \-PE  0x7f790000-7f7fb000     \               ole32
ELF     0x7f7fb000-7f853000     Deferred        shlwapi<elf>
  \-PE  0x7f810000-7f853000     \               shlwapi
ELF     0x7f853000-7f918000     Deferred        shell32<elf>
  \-PE  0x7f870000-7f918000     \               shell32
ELF     0x7f918000-7f9b0000     Export          comdlg32<elf>
  \-PE  0x7f930000-7f9b0000     \               comdlg32
ELF     0x7fac2000-7fb10000     Export          winecfg<elf>
  \-PE  0x7fad0000-7fb10000     \               winecfg
ELF     0x7fb14000-7fb19000     Deferred        libxxf86vm.so.1
ELF     0x7fc61000-7fd60000     Export          kernel32<elf>
  \-PE  0x7fc80000-7fd60000     \               kernel32
ELF     0x7fe70000-7fe74000     Deferred        libxfixes.so.3
ELF     0x7fe74000-7fe79000     Deferred        libxxf86dga.so.1
ELF     0x7fe79000-7fe8e000     Deferred        libnsl.so.1
ELF     0x7fe8e000-7fe97000     Deferred        libnss_compat.so.2
ELF     0x7fe97000-7fea7000     Deferred        libtasn1.so.2
ELF     0x7feaf000-7fed1000     Deferred        libm.so.6
ELF     0x7fed1000-7ffc8000     Deferred        libwine_unicode.so.1
ELF     0x7ffc8000-7ffcb000     Deferred        libxrandr.so.2
ELF     0x7ffcb000-7ffd2000     Deferred        libsm.so.6
ELF     0x7ffd2000-7ffdc000     Deferred        libnss_files.so.2
ELF     0x7ffde000-7ffe0000     Deferred        xlcutf8load.so.2
ELF     0xb7d72000-b7d74000     Deferred        libnvidia-tls.so.1
ELF     0xb7d74000-b7d7d000     Deferred        libnss_nis.so.2
ELF     0xb7d7e000-b7d81000     Deferred        libdl.so.2
ELF     0xb7d81000-b7eaf000     Deferred        libc.so.6
ELF     0xb7eb0000-b7ec2000     Deferred        libpthread.so.0
ELF     0xb7ec2000-b7edc000     Export          libwine.so.1
ELF     0xb7edc000-b7ee0000     Deferred        libxdmcp.so.6
ELF     0xb7ef1000-b7ef4000     Deferred        libxau.so.6
ELF     0xb7ef7000-b7f0d000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\winecfg.exe
        00000009    0 <==
WineDbg terminated on pid 0x8
tlaloczint@aztlan:~$ wineserver: could not save registry branch to /home/tlaloczint/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/tlaloczint/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/tlaloczint/.wine/user.reg : Permission denied

any thoughts? 
thanks in avance

---

### Post by dcstar on 2006-02-23
[QUOTE=tlaloczint]I tried to run winectg and it just closes on me 
I tried several times I already search the forum but no anwser 
.....[/QUOTE]
Try renaming your hidden .wine directory, and run winecfg again.

---

### Post by tlaloczint on 2006-02-24
[QUOTE=dcstar]Try renaming your hidden .wine directory, and run winecfg again.[/QUOTE]



I am afraid I do not know how to do it would you gimme a example?
and to what should I rename it?

---

