---
title: "RIFT on Ubuntu 12.04"
date: 2013-01-28
forum: Gaming &amp; Leisure
---

### Post by bman on 2013-01-28
I am trying to install and play RIFT on my Ubuntu 12.04.1 LTS install and have had no luck.

I am trying to install it through PlayonLinux which does not have an automated install, but I should be able to do it. I think I have installed all needed files, but I can't even get the installer to work.

When I run the .exe file to install the launcher/installing I just get an error.

```

Unhandled exception: page fault on read access to 0x00000030 in 32-bit code (0x7e7a3ae6).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e7a3ae6 ESP:0033f9d0 EBP:0033f9d0 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000018 EBX:7e7eeff4 ECX:00110064 EDX:008ad854
 ESI:00000018 EDI:00000002
Stack dump:
0x0033f9d0:  0033fa00 7e7a49e9 00000018 f7573e2d
0x0033f9e0:  7bca6ff4 7bc35d8d 7bcc2568 7bcc2599
0x0033f9f0:  7e6f5bab 7e7eeff4 7e7eeff4 0033fae8
0x0033fa00:  0033fad0 7e7997e6 00000018 0033fa2c
0x0033fa10:  7bca6ff4 7bca6ff4 7e7cf8a6 00000000
0x0033fa20:  0033fa60 7bc35e46 7e7cf8a6 0033fab8
000c: sel=0067 base=00000000 limit=00000000 16-bit --x
Backtrace:
=>0 0x7e7a3ae6 basic_string_char_const_ptr+0x6() in msvcp90 (0x0033f9d0)
  1 0x7e7a49e9 MSVCP_basic_string_char_c_str+0x58() in msvcp90 (0x0033fa00)
  2 0x7e7997e6 ctype_char__Getcat+0xd5() in msvcp90 (0x0033fad0)
  3 0x004468ac in riftinstall (+0x468ab) (0x0033faec)
  4 0x00446925 in riftinstall (+0x46924) (0x0033fafc)
  5 0x00446b9f in riftinstall (+0x46b9e) (0x0033fb24)
  6 0x00446c7e in riftinstall (+0x46c7d) (0x0033fb34)
  7 0x004080b8 in riftinstall (+0x80b7) (0x0033fc28)
  8 0x00405831 in riftinstall (+0x5830) (0x0033fc90)
  9 0x0040574e in riftinstall (+0x574d) (0x0033fca0)
  10 0x004052e0 in riftinstall (+0x52df) (0x0033fdbc)
  11 0x0053a8ec in riftinstall (+0x13a8eb) (0x0033fde0)
  12 0x00524d99 in riftinstall (+0x124d98) (0x0033fe70)
  13 0x7b859cdc call_process_entry+0xb() in kernel32 (0x0033fe88)
  14 0x7b85af4f in kernel32 (+0x4af4e) (0x0033fec8)
  15 0x7bc71db0 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  16 0x7bc7486d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  17 0x7bc71d8e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  18 0x7bc49f4e call_dll_entry_point+0x61d() in ntdll (0x0033ffe8)
0x7e7a3ae6 basic_string_char_const_ptr+0x6 in msvcp90: cmpl	$15,0x18(%eax)
Modules:
Module	Address			Debug info	Name (100 modules)
PE	  400000-  8f1000	Export          riftinstall
PE	65000000-6587d000	Deferred        qtgui4
PE	67000000-67271000	Deferred        qtcore4
ELF	7b800000-7ba15000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba15000	\               kernel32
ELF	7bc00000-7bcc3000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcc3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d715000-7d71e000	Deferred        librt.so.1
ELF	7d71e000-7d723000	Deferred        libgpg-error.so.0
ELF	7d723000-7d73b000	Deferred        libresolv.so.2
ELF	7d73b000-7d784000	Deferred        libdbus-1.so.3
ELF	7d784000-7d796000	Deferred        libp11-kit.so.0
ELF	7d796000-7d81b000	Deferred        libgcrypt.so.11
ELF	7d81b000-7d82d000	Deferred        libtasn1.so.3
ELF	7d82d000-7d836000	Deferred        libkrb5support.so.0
ELF	7d836000-7d85e000	Deferred        libk5crypto.so.3
ELF	7d961000-7d965000	Deferred        libkeyutils.so.1
ELF	7d965000-7da34000	Deferred        libkrb5.so.3
ELF	7da34000-7da46000	Deferred        libavahi-client.so.3
ELF	7da46000-7db0a000	Deferred        libgnutls.so.26
ELF	7db0a000-7db48000	Deferred        libgssapi_krb5.so.2
ELF	7db48000-7db9b000	Deferred        libcups.so.2
ELF	7dbe0000-7dc14000	Deferred        uxtheme<elf>
  \-PE	7dbf0000-7dc14000	\               uxtheme
ELF	7dc14000-7dc1a000	Deferred        libxfixes.so.3
ELF	7dc1a000-7dc25000	Deferred        libxcursor.so.1
ELF	7dc27000-7dc2c000	Deferred        libcom_err.so.2
ELF	7dc2c000-7dc3a000	Deferred        libavahi-common.so.3
ELF	7dc9b000-7dcc5000	Deferred        libexpat.so.1
ELF	7dcc5000-7dcf9000	Deferred        libfontconfig.so.1
ELF	7dcf9000-7dd09000	Deferred        libxi.so.6
ELF	7dd09000-7dd0d000	Deferred        libxcomposite.so.1
ELF	7dd0d000-7dd16000	Deferred        libxrandr.so.2
ELF	7dd16000-7dd20000	Deferred        libxrender.so.1
ELF	7dd20000-7dd26000	Deferred        libxxf86vm.so.1
ELF	7dd26000-7dd2a000	Deferred        libxinerama.so.1
ELF	7dd2a000-7dd4b000	Deferred        libxcb.so.1
ELF	7dd4b000-7dd65000	Deferred        libice.so.6
ELF	7dd65000-7de99000	Deferred        libx11.so.6
ELF	7de99000-7deab000	Deferred        libxext.so.6
ELF	7deab000-7df3e000	Deferred        winex11<elf>
  \-PE	7dec0000-7df3e000	\               winex11
ELF	7df3e000-7df54000	Deferred        libz.so.1
ELF	7df54000-7dfee000	Deferred        libfreetype.so.6
ELF	7dfee000-7e09b000	Deferred        winmm<elf>
  \-PE	7e000000-7e09b000	\               winmm
ELF	7e09b000-7e18d000	Deferred        oleaut32<elf>
  \-PE	7e0b0000-7e18d000	\               oleaut32
ELF	7e18d000-7e39e000	Deferred        shell32<elf>
  \-PE	7e1a0000-7e39e000	\               shell32
ELF	7e3bf000-7e3c6000	Deferred        libxdmcp.so.6
ELF	7e3c6000-7e3ee000	Deferred        msacm32<elf>
  \-PE	7e3d0000-7e3ee000	\               msacm32
ELF	7e3ee000-7e410000	Deferred        imm32<elf>
  \-PE	7e3f0000-7e410000	\               imm32
ELF	7e410000-7e44a000	Deferred        winspool<elf>
  \-PE	7e420000-7e44a000	\               winspool
ELF	7e44a000-7e542000	Deferred        comctl32<elf>
  \-PE	7e450000-7e542000	\               comctl32
ELF	7e542000-7e5ac000	Deferred        shlwapi<elf>
  \-PE	7e550000-7e5ac000	\               shlwapi
ELF	7e5ac000-7e68b000	Deferred        comdlg32<elf>
  \-PE	7e5b0000-7e68b000	\               comdlg32
ELF	7e68b000-7e6ba000	Deferred        msvcr90<elf>
  \-PE	7e690000-7e6ba000	\               msvcr90
ELF	7e6ba000-7e747000	Deferred        msvcrt<elf>
  \-PE	7e6d0000-7e747000	\               msvcrt
ELF	7e747000-7e82c000	Dwarf           msvcp90<elf>
  \-PE	7e770000-7e82c000	\               msvcp90
ELF	7e82c000-7e85e000	Deferred        ws2_32<elf>
  \-PE	7e830000-7e85e000	\               ws2_32
ELF	7e85e000-7e8d3000	Deferred        rpcrt4<elf>
  \-PE	7e870000-7e8d3000	\               rpcrt4
ELF	7e8d3000-7e9db000	Deferred        ole32<elf>
  \-PE	7e8f0000-7e9db000	\               ole32
ELF	7e9db000-7e9f4000	Deferred        version<elf>
  \-PE	7e9e0000-7e9f4000	\               version
ELF	7e9f4000-7ea54000	Deferred        advapi32<elf>
  \-PE	7ea00000-7ea54000	\               advapi32
ELF	7ea54000-7eb11000	Deferred        gdi32<elf>
  \-PE	7ea60000-7eb11000	\               gdi32
ELF	7eb11000-7ec51000	Deferred        user32<elf>
  \-PE	7eb20000-7ec51000	\               user32
ELF	7ec51000-7ec6b000	Deferred        libnsl.so.1
ELF	7ec6b000-7ec74000	Deferred        libnss_compat.so.2
ELF	7efbd000-7efe9000	Deferred        libm.so.6
ELF	7efea000-7eff3000	Deferred        libsm.so.6
ELF	7eff3000-7f000000	Deferred        libnss_files.so.2
ELF	f7412000-f7430000	Deferred        wintab32<elf>
  \-PE	f7420000-f7430000	\               wintab32
ELF	f7430000-f7436000	Deferred        libuuid.so.1
ELF	f7437000-f743c000	Deferred        libdl.so.2
ELF	f743c000-f75e6000	Deferred        libc.so.6
ELF	f75e7000-f7602000	Deferred        libpthread.so.0
ELF	f7602000-f7606000	Deferred        libxau.so.6
ELF	f760d000-f7619000	Deferred        libnss_nis.so.2
ELF	f7619000-f775b000	Dwarf           libwine.so.1
ELF	f775d000-f777f000	Deferred        ld-linux.so.2
ELF	f777f000-f7780000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001f    0
	0000001e    0
	0000001c    0
	00000017    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001b    0
	00000018    0
	00000014    0
	00000013    0
00000019 plugplay.exe
	00000020    0
	0000001d    0
	0000001a    0
00000021 explorer.exe
	00000022    0
00000023 RIFT-Install.exe
	00000024    0
00000029 (D) C:\users\bman\Temp\{091A0D18-3929-414F-9764-EF90458CB749}\riftinstall.exe
	0000002a    0 <==
System information:
    Wine build: wine-1.4
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.2.0-36-generic

```

I haven't even got to the part of playing the game yet and I am having issues.

Any ideas?

---

