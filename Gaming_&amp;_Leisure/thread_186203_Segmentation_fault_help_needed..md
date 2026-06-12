---
title: "Segmentation fault help needed."
date: 2006-06-01
forum: Gaming &amp; Leisure
---

### Post by shane634 on 2006-06-01
Hello all. I have been playing Enemy Terrritory recently and have started getting a segmentation fault. Any help is appreciated. Here is the output in terminal after it exits in the middle of a game:

-------- UNRECOVERABLE ERROR --------
This may be due to a bug in etpro
Information to be used in a bug report is being generated:
------------- CUT HERE --------------
Version: etpro 3.2.5
Platform: Linux
Build: Jan 17 2006 20:27:35
Signal: Segmentation violation (11)
Signal code: 1
fault address: 0xcf89acac
Load addresses:
0xb7f76000 /lib/tls/i686/cmov/libdl.so.2
0xb7eb6000 /usr/lib/libX11.so.6
0xb7ea9000 /usr/lib/libXext.so.6
0xb7e86000 /lib/tls/i686/cmov/libm.so.6
0xb7d58000 /lib/tls/i686/cmov/libc.so.6
0xb7f88000 /lib/ld-linux.so.2
0xb7d54000 /usr/lib/libXau.so.6
0xb7d50000 /usr/lib/libXdmcp.so.6
0xb2c29000 /lib/tls/i686/cmov/libnss_compat.so.2
0xb2c13000 /lib/tls/i686/cmov/libnsl.so.1
0xb7f7c000 /lib/tls/i686/cmov/libnss_nis.so.2
0xb2c08000 /lib/tls/i686/cmov/libnss_files.so.2
0xb1383000 /usr/lib/libGL.so.1
0xb0c32000 /usr/lib/libGLcore.so.1
0xb7f7a000 /usr/lib/tls/libnvidia-tls.so.1
0xaf3b5000 /usr/lib/X11/locale/common/xlcDef.so.2
0xb2c34000 /usr/lib/libXcursor.so.1
0xaf3ad000 /usr/lib/libXrender.so.1
0xaf3a9000 /usr/lib/libXfixes.so.3
0xac050000 /home/shane634/.etwolf/pb/pbcl.so
0xaf362000 /lib/tls/i686/cmov/libnss_dns.so.2
0xaf34e000 /lib/tls/i686/cmov/libresolv.so.2
0xaf340000 /home/shane634/.etwolf/pb/pbag.so
0xabded000 /home/shane634/.etwolf/pb/pbsv.so
0xacdbf000 /home/shane634/.etwolf/etpro/ui.mp.i386.so
0xa5a9e000 /home/shane634/.etwolf/etpro/cgame.mp.i386.so
EIP: a5b0dda2
edi:a9fe9dc8 esi:00000c2b ebp:ab937960 esp:bf89ac10
eax:ab937960 ebx:a5b779cc ecx:00000062 edx:a9fe9dc8
stack:
bf89ac70 a9fe9e04 00000000 00000000 00000000 00000000 ab97ee3c 00000062
3d4ccccd 3f7e7845 80000000 bf7e7845 3ddf9686 00000000 a9fe9d70 00000062
2357c25e 00000000 00000000 ab937960 ab937960 00000000 00000000 3d4ccccd
c4471e4b c4965ae7 4276504b 00000000 3fc95534 00000000 a5b0d8d9 a5b779cc
code:
8b 8c 24 9c 00 00 00 8b 91 e8 02 00 00 8b 81 90 02 00 00 81 e2 ff fd ff ff 25
ff fd ff ff 39 c2 0f 85 73 ff ff ff 8b 44 24 4c 8b 50 58 85 d2 0f 84 64 ff ff
Stack trace:
1 entries
/home/shane634/.etwolf/etpro/cgame.mp.i386.so[0xa5abba52]
------------- CUT HERE --------------
  Any ideas???

---

