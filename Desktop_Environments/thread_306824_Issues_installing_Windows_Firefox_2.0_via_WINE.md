---
title: "Issues installing Windows Firefox 2.0 via WINE"
date: 2006-11-25
forum: Desktop Environments
---

### Post by Raavea on 2006-11-25
I'm trying to install shockwave using this guide;
[https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave)
 And I'm on the bit for installing windows firefox 2.0. After extracting, I click Next, and the thing just crashes. 

 Here's the terminal messages. I have no idea what's wrong, and need to go out in just a sec. If you know what's wrong, please help. :) ```
raavea@bernard:~/Desktop$ wine Firefox\ Setup\ 2.0.exe
fixme:win:SetWindowTextW setting text L"Extracting" of other process window 0x10022 should not use SendMessage
fixme:win:SetWindowTextA setting text "Mozilla Firefox Setup" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Mozilla Firefox Setup" of other process window (nil) should not use SendMessage
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub
wine: Unhandled page fault on read access to 0x0000000c at address 0x7f08a570 (thread 0013), starting debugger...
WineDbg starting on pid 0x12
Unhandled exception: page fault on read access to 0x0000000c in 32-bit code (0x7f08a570).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7f08a570 ESP:7fb87cbc EBP:7fb87da4 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7f0a9498 ECX:b7e246a4 EDX:00000001
 ESI:7fb87e38 EDI:7fb87e38
Stack dump:
0x7fb87cbc:  7fb87e38 00000001 7ef54998 00000010
0x7fb87ccc:  7fb87cf6 00000020 7fb87d34 7ff997d7
0x7fb87cdc:  00000074 40000000 00000000 00000000
0x7fb87cec:  7fc4e03a 00000000 00000001 00200053
0x7fb87cfc:  00680053 006c0065 0020006c 00690044
0x7fb87d0c:  006c0061 0067006f 00000000 7ffd51fc
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7f08a570 in riched20 (+0xa570) (0x7f08a570)
  2 0x7f0945c2 RTFGetToken+0x43 in riched20 (0x7f0945c2)
  3 0x7f094b99 RTFRead+0x28 in riched20 (0x7f094b99)
  4 0x7f08abbc in riched20 (+0xabbc) (0x7f08abbc)
  5 0x7f08e7c6 RichEditANSIWndProc+0x2595 in riched20 (0x7f08e7c6)
  6 0x7fa0ed3a WINPROC_wrapper+0x1a in user32 (0x7fa0ed3a)
  7 0x7fa0f842 in user32 (+0x9f842) (0x7fa0f842)
  8 0x7fa1313d CallWindowProcA+0x1b5 in user32 (0x7fa1313d)
  9 0x7f9dd7cd in user32 (+0x6d7cd) (0x7f9dd7cd)
  10 0x7f9e1473 SendMessageTimeoutA+0x226 in user32 (0x7f9e1473)
  11 0x7f9e152e SendMessageA+0x50 in user32 (0x7f9e152e)
  12 0x00404020 in setup (+0x4020) (0x00404020)
  13 0x7fa0ed3a WINPROC_wrapper+0x1a in user32 (0x7fa0ed3a)
  14 0x7fa0f842 in user32 (+0x9f842) (0x7fa0f842)
  15 0x7fa13001 CallWindowProcA+0x79 in user32 (0x7fa13001)
  16 0x7f9a7dae DefDlgProcA+0x91 in user32 (0x7f9a7dae)
  17 0x7fa0ed3a WINPROC_wrapper+0x1a in user32 (0x7fa0ed3a)
  18 0x7fa0f842 in user32 (+0x9f842) (0x7fa0f842)
  19 0x7fa1558e CallWindowProcW+0x122 in user32 (0x7fa1558e)
  20 0x7f9dd85c in user32 (+0x6d85c) (0x7f9dd85c)
  21 0x7f9e16c1 SendMessageTimeoutW+0x186 in user32 (0x7f9e16c1)
  22 0x7f9e171e SendMessageW+0x50 in user32 (0x7f9e171e)
  23 0x7f9ae170 in user32 (+0x3e170) (0x7f9ae170)
  24 0x7f9aedc9 CreateDialogIndirectParamAorW+0x3e in user32 (0x7f9aedc9)
  25 0x7f9aeede CreateDialogIndirectParamA+0x41 in user32 (0x7f9aeede)
  26 0x7f9aef5d CreateDialogParamA+0x75 in user32 (0x7f9aef5d)
  27 0x00403cd1 in setup (+0x3cd1) (0x00403cd1)
0x7f08a570: movl        0xc(%eax),%edx
Modules:
Module  Address                 Debug info      Name (71 modules)
PE      0x00400000-0043f000     Export          setup
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7ed49000-7ed95000     Deferred        libgcrypt.so.11
ELF     0x7ed95000-7eda5000     Deferred        libtasn1.so.2
ELF     0x7eda5000-7edd2000     Deferred        libcrypt.so.1
ELF     0x7edd2000-7ee3b000     Deferred        libgnutls.so.12
ELF     0x7ee3b000-7ee69000     Deferred        libcups.so.2
ELF     0x7f06a000-7f0b0000     Export          riched20<elf>
  \-PE  0x7f080000-7f0b0000     \               riched20
ELF     0x7f154000-7f185000     Deferred        uxtheme<elf>
  \-PE  0x7f160000-7f185000     \               uxtheme
ELF     0x7f1a3000-7f1ac000     Deferred        libxcursor.so.1
ELF     0x7f1ac000-7f1c8000     Deferred        imm32<elf>
  \-PE  0x7f1b0000-7f1c8000     \               imm32
ELF     0x7f1c8000-7f1d0000     Deferred        libxrender.so.1
ELF     0x7f1d0000-7f236000     Deferred        libgl.so.1
ELF     0x7f236000-7f31c000     Deferred        libx11.so.6
ELF     0x7f31c000-7f334000     Deferred        libice.so.6
ELF     0x7f334000-7f3b7000     Deferred        winex11<elf>
  \-PE  0x7f340000-7f3b7000     \               winex11
ELF     0x7f3b7000-7f3d6000     Deferred        libexpat.so.1
ELF     0x7f3d6000-7f404000     Deferred        libfontconfig.so.1
ELF     0x7f404000-7f418000     Deferred        libz.so.1
ELF     0x7f418000-7f481000     Deferred        libfreetype.so.6
ELF     0x7f481000-7f495000     Deferred        lz32<elf>
  \-PE  0x7f490000-7f495000     \               lz32
ELF     0x7f495000-7f4ae000     Deferred        version<elf>
  \-PE  0x7f4a0000-7f4ae000     \               version
ELF     0x7f4ae000-7f56e000     Deferred        comctl32<elf>
  \-PE  0x7f4c0000-7f56e000     \               comctl32
ELF     0x7f56e000-7f58d000     Deferred        iphlpapi<elf>
  \-PE  0x7f580000-7f58d000     \               iphlpapi
ELF     0x7f58d000-7f5d6000     Deferred        rpcrt4<elf>
  \-PE  0x7f5a0000-7f5d6000     \               rpcrt4
ELF     0x7f5d6000-7f667000     Deferred        ole32<elf>
  \-PE  0x7f5f0000-7f667000     \               ole32
ELF     0x7f667000-7f6c2000     Deferred        shlwapi<elf>
  \-PE  0x7f680000-7f6c2000     \               shlwapi
ELF     0x7f6c2000-7f78e000     Deferred        shell32<elf>
  \-PE  0x7f6e0000-7f78e000     \               shell32
ELF     0x7f78e000-7f7ce000     Deferred        advapi32<elf>
  \-PE  0x7f7a0000-7f7ce000     \               advapi32
ELF     0x7f8a3000-7f954000     Deferred        gdi32<elf>
  \-PE  0x7f8c0000-7f954000     \               gdi32
ELF     0x7f954000-7fa80000     Export          user32<elf>
  \-PE  0x7f970000-7fa80000     \               user32
ELF     0x7fb90000-7fb94000     Deferred        libgpg-error.so.0
ELF     0x7fb94000-7fb9b000     Deferred        libdrm.so.2
ELF     0x7fbce000-7fcd0000     Deferred        kernel32<elf>
  \-PE  0x7fbf0000-7fcd0000     \               kernel32
ELF     0x7fcd3000-7fce0000     Deferred        libxext.so.6
ELF     0x7fce2000-7fce6000     Deferred        libxfixes.so.3
ELF     0x7fce6000-7fceb000     Deferred        libxxf86vm.so.1
ELF     0x7fceb000-7fcf0000     Deferred        libxxf86dga.so.1
ELF     0x7fe00000-7fe03000     Deferred        libxrandr.so.2
ELF     0x7fe03000-7fe0d000     Deferred        libgcc_s.so.1
ELF     0x7fe0d000-7fe17000     Deferred        libnss_files.so.2
ELF     0x7fe17000-7fe20000     Deferred        libnss_nis.so.2
ELF     0x7fe20000-7fe35000     Deferred        libnsl.so.1
ELF     0x7fe35000-7fe3e000     Deferred        libnss_compat.so.2
ELF     0x7fe3f000-7fe42000     Deferred        libxau.so.6
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e25000-b7e28000     Deferred        libdl.so.2
ELF     0xb7e28000-b7f57000     Deferred        libc.so.6
ELF     0xb7f57000-b7f69000     Deferred        libpthread.so.0
ELF     0xb7f76000-b7f90000     Deferred        libwine.so.1
ELF     0xb7f93000-b7fa9000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000012 (D) C:\windows\temp\7zS3ed.tmp\setup.exe
        00000013    0 <==
00000008
        00000009    0
raavea@bernard:~/Desktop$

```

---

### Post by beefcurry on 2006-11-27
You do know that there is a Native LINUX version of Firefox 2.0 for Ubuntu. Not to mention that it comes with Edgy? so Why the need to use WINE with it?

---

### Post by Raavea on 2006-11-28
If you'd checked out the link *(or read my post)*, you'd see I am doing it to be able to view Shockwave media.

 I don't actually want 2.0 specifically, but I couldn't be bothered to go hunt down an earlier version since all I want it for is the Shockwave plugin.



 I'm still not able to install it. I've tried downloading the .exe from Mozilla several times *(in case I got a slightly corrupt download or something)* and the issue persists. ](*,) 

 I really want shockwave. I was going to do this a few weeks *(possibly longer, I'm not good with time)* back when I'd had enough of waiting for the damned linux flash update, but discovered the beta was out so decided to wait a while longer before sullying my lappy.

---

