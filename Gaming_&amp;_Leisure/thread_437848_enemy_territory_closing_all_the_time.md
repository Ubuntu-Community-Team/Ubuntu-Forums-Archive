---
title: "enemy territory closing all the time"
date: 2007-05-09
forum: Gaming &amp; Leisure
---

### Post by tomt610 on 2007-05-09
my enemy territory was quitting all the time so i run this from console and this is what i saw:

-------- UNRECOVERABLE ERROR --------
This may be due to a bug in etpro
Information to be used in a bug report is being generated:
------------- CUT HERE --------------
Version: etpro 3.2.6
Platform: Linux
Build: Sep 16 2006 18:02:39
Signal: Abort (6)
Signal code: -6
Load addresses:
0xb7f67000 /lib/tls/i686/cmov/libdl.so.2
0xb7e9e000 /usr/lib/libX11.so.6
0xb7e91000 /usr/lib/libXext.so.6
0xb7e6b000 /lib/tls/i686/cmov/libm.so.6
0xb7d37000 /lib/tls/i686/cmov/libc.so.6
0xb7f7c000 /lib/ld-linux.so.2
0xb7d34000 /usr/lib/libXau.so.6
0xb7d2e000 /usr/lib/libXdmcp.so.6
0xa2474000 /lib/tls/i686/cmov/libnss_compat.so.2
0xa245e000 /lib/tls/i686/cmov/libnsl.so.1
0xa2454000 /lib/tls/i686/cmov/libnss_nis.so.2
0xa2449000 /lib/tls/i686/cmov/libnss_files.so.2
0xa0bb4000 /usr/lib/libGL.so.1
0xa03f1000 /usr/lib/libGLcore.so.1
0xa2489000 /usr/lib/tls/libnvidia-tls.so.1
0x9fba5000 /usr/lib/X11/locale/common/xlibi18n.so.2
0x9fb9c000 /usr/lib/libXcursor.so.1
0x9fb94000 /usr/lib/libXrender.so.1
0xa247f000 /usr/lib/libXfixes.so.3
0x9c592000 /home/ferros/.etwolf/pb/pbcl.so
0x9f987000 /lib/tls/i686/cmov/libnss_dns.so.2
0x9f974000 /lib/tls/i686/cmov/libresolv.so.2
0x9c53f000 /home/ferros/.etwolf/pb/pbag.so
0x9c227000 /home/ferros/.etwolf/pb/pbsv.so
0x9c864000 /home/ferros/.etwolf/etpro/ui.mp.i386.so
0x95e7e000 /home/ferros/.etwolf/etpro/cgame.mp.i386.so
0x9cee1000 /lib/libgcc_s.so.1
EIP: ffffe410
edi:b7e66ff4 esi:bff51808 ebp:bff51768 esp:bff51750
eax:00000000 ebx:00002e90 ecx:00002e90 edx:00000006
stack:
bff51768 00000006 00002e90 b7d60770 b7e66ff4 b7d2d6b0 bff51894 b7d61ef3
00000006 bff51808 00000000 00000000 00000000 00000000 00000000 00000000
00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
00000000 00000000 bff517ec b7e396a9 b7f962e0 bff517ec 00000004 bff51820
code:
!! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !!
!! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !! !!
Stack trace:
1 entries
/home/ferros/.etwolf/etpro/cgame.mp.i386.so[0x95e9bf22]
------------- CUT HERE --------------
Trying to clean up...
Received signal 6, exiting...
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 135
  Minor opcode of failed request: 10
  Serial number of failed request: 34508
---------- RECURSIVE CRASH ----------
Exiting hard.
Aborted 


anyone can help me with this?

---

### Post by mbradlcu on 2007-05-18
a couple questions, did it ever work?, if so when did it start happening?
I would suggest taking out etpro and see if et will run for you without issue,, if so maybe a fresh install of the etpro package may help.

---

### Post by tomt610 on 2007-05-18
I have reinstalled all the et and it is happening again. i have played without etpro and it quit too. I have reinstalled system with same effect. This is only happening on my computer i think and from beginning.

---

