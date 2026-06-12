---
title: "PlayOnLinux! Can't install Skyrim!"
date: 2014-04-26
forum: Gaming &amp; Leisure
---

### Post by wolflint on 2014-04-26
I bought Skyrim because I thought I will be able to play it with PlayOnLinux because it was on the list and there was an option to install the Steam version.
Installation goes fine I've changed the file thing from 1 to 0 when the installer told me to.
When it gets to opening steam after I press Login button I get an error. How do I fix this? I don't have Windows and Steam doesn't do refunds :(

---

### Post by dannyboy79 on 2014-04-27
we can't help you without knowing what the error is.

---

### Post by wolflint on 2014-04-27
This is the error.

Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x7c530aea).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7c530aea ESP:05c0c070 EBP:05c0c088 EFLAGS:00210202(  R- --  I   - - - )
 EAX:00000000 EBX:7c53eabc ECX:05c0b7f0 EDX:05c0bfc0
 ESI:00000000 EDI:06806f00
Stack dump:
0x05c0c070:  05c0c098 00000000 00110000 00000010
0x05c0c080:  05c0c0a0 068074ec 05c0c0b8 7c53172b
0x05c0c090:  00000000 06806f18 068074ec 0000004d
0x05c0c0a0:  00000003 80041017 06806f04 06806f08
0x05c0c0b0:  068074ec 06806f00 05c0c108 7c531843
0x05c0c0c0:  06806f00 06806f04 06806f08 f75dddcb
Backtrace:
=>0 0x7c530aea in wbemprox (+0x10aea) (0x05c0c088)
  1 0x7c53172b in wbemprox (+0x1172a) (0x05c0c0b8)
  2 0x7c531843 in wbemprox (+0x11842) (0x05c0c108)
  3 0x7c534938 in wbemprox (+0x14937) (0x05c0c168)
  4 0x3847a843 in steamclient (+0x47a842) (0x05c0c1f4)
  5 0x3847ac0a in steamclient (+0x47ac09) (0x05c0c8b8)
  6 0x380f8f8f in steamclient (+0xf8f8e) (0x05c0cb38)
  7 0x380f9bd7 in steamclient (+0xf9bd6) (0x05c0cb4c)
  8 0x380fb32f in steamclient (+0xfb32e) (0x05c0d080)
  9 0x380f2591 in steamclient (+0xf2590) (0x05c0d088)
  10 0x38490b48 in steamclient (+0x490b47) (0x05c0d6a0)
  11 0x38491ba0 in steamclient (+0x491b9f) (0x05c0d6f8)
  12 0x38475ced in steamclient (+0x475cec) (0x05c0db18)
  13 0x38478f26 in steamclient (+0x478f25) (0x05c0db3c)
  14 0x38477651 in steamclient (+0x477650) (0x05c0db6c)
  15 0x3847e5c7 in steamclient (+0x47e5c6) (0x05c0e3b8)
  16 0x38475972 in steamclient (+0x475971) (0x05c0e3d8)
  17 0x3847e16c in steamclient (+0x47e16b) (0x05c0e3e4)
  18 0x3847de23 in steamclient (+0x47de22) (0x05c0e470)
  19 0x381a87b1 in steamclient (+0x1a87b0) (0x05c0e4ac)
  20 0x381da985 in steamclient (+0x1da984) (0x05c0e4f8)
  21 0x381aa611 in steamclient (+0x1aa610) (0x05c0e564)
  22 0x381aa900 in steamclient (+0x1aa8ff) (0x05c0e578)
  23 0x3f00c7af in tier0_s (+0xc7ae) (0x05c0e5a8)
  24 0x3f00d85c in tier0_s (+0xd85b) (0x05c0e5cc)
  25 0x3f0118c0 in tier0_s (+0x118bf) (0x05c0ea08)
  26 0x7bc75690 call_thread_func_wrapper+0xb() in ntdll (0x05c0ea18)
  27 0x7bc758ed call_thread_func+0x7c() in ntdll (0x05c0eae8)
  28 0x7bc7566e RtlRaiseException+0x21() in ntdll (0x05c0eb08)
  29 0x7bc7fbc9 in ntdll (+0x6fbc8) (0x05c0f358)
  30 0xf75a3f70 start_thread+0xcf() in libpthread.so.0 (0x05c0f428)
  31 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  32 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  33 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  34 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  35 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  36 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  37 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  38 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  39 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  40 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  41 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  42 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  43 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  44 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  45 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  46 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  47 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  48 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  49 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  50 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  51 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  52 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  53 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  54 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  55 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  56 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  57 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  58 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  59 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  60 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  61 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  62 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  63 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  64 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  65 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  66 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  67 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  68 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  69 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  70 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  71 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  72 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  73 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  74 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  75 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  76 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  77 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  78 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  79 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  80 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  81 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  82 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  83 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  84 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  85 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  86 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  87 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  88 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  89 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  90 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  91 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  92 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  93 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  94 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  95 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  96 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  97 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  98 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  99 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  100 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  101 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  102 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  103 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  104 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  105 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  106 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  107 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  108 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  109 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  110 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  111 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  112 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  113 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  114 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  115 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  116 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  117 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  118 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  119 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  120 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  121 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  122 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  123 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  124 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  125 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  126 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  127 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  128 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  129 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  130 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  131 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  132 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  133 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  134 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  135 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  136 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  137 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  138 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  139 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  140 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  141 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  142 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  143 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  144 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  145 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  146 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  147 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  148 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  149 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  150 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  151 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  152 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  153 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  154 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  155 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  156 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  157 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  158 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  159 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  160 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  161 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  162 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  163 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  164 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  165 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  166 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  167 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  168 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  169 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  170 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  171 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  172 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  173 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  174 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  175 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  176 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  177 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  178 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  179 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  180 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  181 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  182 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  183 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  184 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  185 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  186 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  187 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  188 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  189 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  190 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  191 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  192 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  193 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  194 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  195 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  196 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  197 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  198 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  199 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
  200 0xf74da70e __clone+0x5d() in libc.so.6 (0x00000000)
0x7c530aea: movl	0x4(%esi),%eax
Modules:
Module	Address			Debug info	Name (172 modules)
PE	  400000-  63e000	Deferred        steam
PE	  e30000-  e88000	Deferred        libavresample-1
PE	  e90000-  f0d000	Deferred        libavutil-53
PE	  f10000-  fcf000	Deferred        sdl2
PE	 31f0000- 3301000	Deferred        chromehtml
PE	 3310000- 46eb000	Deferred        libcef
PE	 5e10000- 6119000	Deferred        steamservice
PE	10000000-100b4000	Deferred        crashhandler
PE	38000000-388a5000	Export          steamclient
PE	3a000000-3ab66000	Deferred        steamui
PE	3f000000-3f0ac000	Export          tier0_s
PE	3f200000-3f2af000	Deferred        vgui2_s
PE	3f600000-3f64b000	Deferred        vstdlib_s
PE	3f800000-3f82a000	Deferred        filesystem_stdio
PE	4ad00000-4b67f000	Deferred        icudt
PE	65ec0000-66072000	Deferred        avcodec-53
PE	68b80000-68ba7000	Deferred        avutil-51
PE	6ab00000-6ab33000	Deferred        avformat-53
ELF	7b800000-7b904000	Deferred        kernel32<elf>
  \-PE	7b810000-7b904000	\               kernel32
ELF	7bc00000-7bcc6000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcc6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c226000-7c35b000	Deferred        wined3d<elf>
  \-PE	7c230000-7c35b000	\               wined3d
ELF	7c4f5000-7c518000	Deferred        dxgi<elf>
  \-PE	7c500000-7c518000	\               dxgi
ELF	7c518000-7c540000	Dwarf           wbemprox<elf>
  \-PE	7c520000-7c540000	\               wbemprox
ELF	7c540000-7c554000	Deferred        hid<elf>
  \-PE	7c550000-7c554000	\               hid
ELF	7c76a000-7c773000	Deferred        libogg.so.0
ELF	7c773000-7c8eb000	Deferred        libvorbisenc.so.2
ELF	7c8eb000-7c91f000	Deferred        libflac.so.8
ELF	7c91f000-7c991000	Deferred        libsndfile.so.1
ELF	7c991000-7ca00000	Deferred        libpulsecommon-4.0.so
ELF	7cb07000-7cb33000	Deferred        libvorbis.so.0
ELF	7cc52000-7cc59000	Deferred        libasyncns.so.0
ELF	7cc59000-7cc63000	Deferred        libwrap.so.0
ELF	7cc63000-7cc6e000	Deferred        libjson-c.so.2
ELF	7cc6e000-7ccbd000	Deferred        libpulse.so.0
ELF	7ccbd000-7cdb3000	Deferred        libasound.so.2
ELF	7cdb3000-7cde0000	Deferred        winealsa<elf>
  \-PE	7cdc0000-7cde0000	\               winealsa
ELF	7cde0000-7ce00000	Deferred        mmdevapi<elf>
  \-PE	7cdf0000-7ce00000	\               mmdevapi
ELF	7d205000-7d24a000	Deferred        dsound<elf>
  \-PE	7d210000-7d24a000	\               dsound
ELF	7d24a000-7d267000	Deferred        libgcc_s.so.1
ELF	7d273000-7d27a000	Deferred        libnss_dns.so.2
ELF	7d281000-7d2a1000	Deferred        hnetcfg<elf>
  \-PE	7d290000-7d2a1000	\               hnetcfg
ELF	7d2a1000-7d2ba000	Deferred        imagehlp<elf>
  \-PE	7d2b0000-7d2ba000	\               imagehlp
ELF	7d445000-7d4db000	Deferred        msvcrt<elf>
  \-PE	7d460000-7d4db000	\               msvcrt
ELF	7d4db000-7d4f0000	Deferred        dwmapi<elf>
  \-PE	7d4e0000-7d4f0000	\               dwmapi
ELF	7d4f0000-7d52e000	Deferred        usp10<elf>
  \-PE	7d500000-7d52e000	\               usp10
ELF	7d52e000-7d542000	Deferred        dhcpcsvc<elf>
  \-PE	7d530000-7d542000	\               dhcpcsvc
ELF	7d542000-7d56c000	Deferred        netapi32<elf>
  \-PE	7d550000-7d56c000	\               netapi32
ELF	7d56c000-7d59a000	Deferred        secur32<elf>
  \-PE	7d570000-7d59a000	\               secur32
ELF	7d59a000-7d629000	Deferred        urlmon<elf>
  \-PE	7d5b0000-7d629000	\               urlmon
ELF	7d629000-7d64c000	Deferred        iphlpapi<elf>
  \-PE	7d630000-7d64c000	\               iphlpapi
ELF	7d64c000-7d6b5000	Deferred        setupapi<elf>
  \-PE	7d660000-7d6b5000	\               setupapi
ELF	7d6b5000-7d6cc000	Deferred        userenv<elf>
  \-PE	7d6c0000-7d6cc000	\               userenv
ELF	7d6cc000-7d704000	Deferred        winhttp<elf>
  \-PE	7d6d0000-7d704000	\               winhttp
ELF	7d704000-7d7da000	Deferred        opengl32<elf>
  \-PE	7d720000-7d7da000	\               opengl32
ELF	7d7da000-7d7e3000	Deferred        librt.so.1
ELF	7d7e3000-7d7e7000	Deferred        libgpg-error.so.0
ELF	7d7e7000-7d7ff000	Deferred        libresolv.so.2
ELF	7d7ff000-7d803000	Deferred        libkeyutils.so.1
ELF	7d803000-7d84e000	Deferred        libdbus-1.so.3
ELF	7d84e000-7d8c2000	Deferred        libgcrypt.so.11
ELF	7d8c2000-7d8f2000	Deferred        libk5crypto.so.3
ELF	7d8f2000-7d9b0000	Deferred        libkrb5.so.3
ELF	7d9b0000-7da48000	Deferred        libgnutls.so.26
ELF	7da48000-7dab5000	Deferred        libcups.so.2
ELF	7dab5000-7db95000	Deferred        comdlg32<elf>
  \-PE	7dac0000-7db95000	\               comdlg32
ELF	7db95000-7dc52000	Deferred        crypt32<elf>
  \-PE	7dba0000-7dc52000	\               crypt32
ELF	7dc52000-7dd00000	Deferred        winmm<elf>
  \-PE	7dc60000-7dd00000	\               winmm
ELF	7de01000-7de11000	Deferred        libtasn1.so.3
ELF	7de11000-7de1d000	Deferred        libkrb5support.so.0
ELF	7de1d000-7de62000	Deferred        libgssapi_krb5.so.2
ELF	7debc000-7dece000	Deferred        libavahi-client.so.3
ELF	7dece000-7dedc000	Deferred        libavahi-common.so.3
ELF	7dedc000-7dee3000	Deferred        libasound_module_pcm_pulse.so
ELF	7dee3000-7def6000	Deferred        msimg32<elf>
  \-PE	7def0000-7def6000	\               msimg32
ELF	7def6000-7df33000	Deferred        winspool<elf>
  \-PE	7df00000-7df33000	\               winspool
ELF	7df33000-7df5b000	Deferred        msacm32<elf>
  \-PE	7df40000-7df5b000	\               msacm32
ELF	7df5b000-7df7d000	Deferred        imm32<elf>
  \-PE	7df60000-7df7d000	\               imm32
ELF	7dfad000-7e00a000	Deferred        dbghelp<elf>
  \-PE	7dfb0000-7e00a000	\               dbghelp
ELF	7e00a000-7e02f000	Deferred        mpr<elf>
  \-PE	7e010000-7e02f000	\               mpr
ELF	7e02f000-7e0a1000	Deferred        wininet<elf>
  \-PE	7e040000-7e0a1000	\               wininet
ELF	7e0a1000-7e0d4000	Deferred        uxtheme<elf>
  \-PE	7e0b0000-7e0d4000	\               uxtheme
ELF	7e0d4000-7e0da000	Deferred        libxfixes.so.3
ELF	7e0da000-7e0e5000	Deferred        libxcursor.so.1
ELF	7e0e5000-7e0f6000	Deferred        libxi.so.6
ELF	7e0f6000-7e0fa000	Deferred        libxcomposite.so.1
ELF	7e0fa000-7e105000	Deferred        libxrandr.so.2
ELF	7e105000-7e110000	Deferred        libxrender.so.1
ELF	7e110000-7e116000	Deferred        libxxf86vm.so.1
ELF	7e116000-7e13b000	Deferred        libxcb.so.1
ELF	7e13b000-7e26f000	Deferred        libx11.so.6
ELF	7e26f000-7e282000	Deferred        libxext.so.6
ELF	7e282000-7e29c000	Deferred        libice.so.6
ELF	7e29c000-7e2a5000	Deferred        libsm.so.6
ELF	7e2a5000-7e32f000	Deferred        winex11<elf>
  \-PE	7e2b0000-7e32f000	\               winex11
ELF	7e32f000-7e357000	Deferred        libpng12.so.0
ELF	7e357000-7e36b000	Deferred        libz.so.1
ELF	7e36b000-7e40a000	Deferred        libfreetype.so.6
ELF	7e40c000-7e411000	Deferred        libcom_err.so.2
ELF	7e411000-7e424000	Deferred        psapi<elf>
  \-PE	7e420000-7e424000	\               psapi
ELF	7e424000-7e49c000	Deferred        rpcrt4<elf>
  \-PE	7e430000-7e49c000	\               rpcrt4
ELF	7e49c000-7e5b0000	Deferred        ole32<elf>
  \-PE	7e4b0000-7e5b0000	\               ole32
ELF	7e5b0000-7e6cb000	Deferred        oleaut32<elf>
  \-PE	7e5d0000-7e6cb000	\               oleaut32
ELF	7e6cb000-7e73a000	Deferred        shlwapi<elf>
  \-PE	7e6e0000-7e73a000	\               shlwapi
ELF	7e73a000-7e951000	Deferred        shell32<elf>
  \-PE	7e750000-7e951000	\               shell32
ELF	7e951000-7e9b6000	Deferred        advapi32<elf>
  \-PE	7e960000-7e9b6000	\               advapi32
ELF	7e9b6000-7eabb000	Deferred        gdi32<elf>
  \-PE	7e9c0000-7eabb000	\               gdi32
ELF	7eabb000-7ec00000	Deferred        user32<elf>
  \-PE	7ead0000-7ec00000	\               user32
ELF	7ec00000-7ecf6000	Deferred        comctl32<elf>
  \-PE	7ec10000-7ecf6000	\               comctl32
ELF	7ecf6000-7ed26000	Deferred        ws2_32<elf>
  \-PE	7ed00000-7ed26000	\               ws2_32
ELF	7ed26000-7ed33000	Deferred        libnss_files.so.2
ELF	7ed33000-7ed3f000	Deferred        libnss_nis.so.2
ELF	7ed3f000-7ed58000	Deferred        libnsl.so.1
ELF	7ed58000-7ed61000	Deferred        libnss_compat.so.2
ELF	7efa0000-7efe6000	Deferred        libm.so.6
ELF	7efe8000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f73e0000-f73e4000	Deferred        libxinerama.so.1
ELF	f73e4000-f73e8000	Deferred        libxau.so.6
ELF	f73e9000-f73ee000	Deferred        libdl.so.2
ELF	f73ee000-f759d000	Dwarf           libc.so.6
ELF	f759d000-f75b9000	Dwarf           libpthread.so.0
ELF	f75ba000-f75c0000	Deferred        libuuid.so.1
ELF	f75d4000-f7715000	Dwarf           libwine.so.1
ELF	f7717000-f7739000	Deferred        ld-linux.so.2
ELF	f7739000-f773a000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	00000028    0
	00000027    0
	00000020    0
	00000017    0
	00000010    0
	0000000f    0
00000012 mscorsvw.exe
	0000001c    0
	0000001b    0
	00000016    0
	00000013    0
00000014 explorer.exe
	00000015    0
0000001d winedevice.exe
	00000025    0
	00000022    0
	0000001f    0
	0000001e    0
00000023 plugplay.exe
	00000029    0
	00000026    0
	00000024    0
00000041 (D) C:\Program Files\Steam\Steam.exe
	0000004a    0
	00000048    0
	00000039    0
	00000040    0
	0000003e    0
	0000003d    0
	0000003f    0
	0000003a    0
	0000003b    0
	0000003c    0
	00000037    0
	00000033    0 <==
	00000036    0
	00000035    0
	00000019    0
	0000001a    0
	0000002f    0
	00000030    0
	0000002d    0
	0000002b    0
	0000002c    0
	0000000d    0
	00000009    0
	0000000b    0
	00000047    0
	00000046    0
	00000042    0
System information:
    Wine build: wine-1.5.20
    Platform: i386
    Host system: Linux
    Host version: 3.13.0-24-generic

---

