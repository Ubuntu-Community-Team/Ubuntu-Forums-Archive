---
title: "Enemy Territory - Random Crashes..."
date: 2007-06-13
forum: Gaming &amp; Leisure
---

### Post by creativ3rst on 2007-06-13
This is a very random crash... i can play for hours and nothing... or i can play for 10 mins an it will crash every 10 minutes from then... Tried updating pb, reinstall et, reinstall etpro.
Occurs on etmain servers, etpro servers and wierd mod servers...

I have googles this, and found some other people with the same problem, but no solution.

```
-------- UNRECOVERABLE ERROR --------
This may be due to a bug in etpro
Information to be used in a bug report is being generated:
------------- CUT HERE --------------
Version: etpro 3.2.6 
Platform: Linux
Build: Sep 16 2006 18:02:39
Signal: Segmentation violation (11)
Signal code: 1
fault address: 0x32e42b6c
Load addresses:
0xb7f34000 /lib/tls/i686/cmov/libdl.so.2
0xb7e43000 /usr/lib/libX11.so.6
0xb7e35000 /usr/lib/libXext.so.6
0xb7e0e000 /lib/tls/i686/cmov/libm.so.6
0xb7ccd000 /lib/tls/i686/cmov/libc.so.6
0xb7f45000 /lib/ld-linux.so.2
0xb7cca000 /usr/lib/libXau.so.6
0xb7cc4000 /usr/lib/libXdmcp.so.6
0xb2c2c000 /lib/tls/i686/cmov/libnss_compat.so.2
0xb2c15000 /lib/tls/i686/cmov/libnsl.so.1
0xb2c0b000 /lib/tls/i686/cmov/libnss_nis.so.2
0xb2c00000 /lib/tls/i686/cmov/libnss_files.so.2
0xb0097000 /usr/lib/libXcursor.so.1
0xb008f000 /usr/lib/libXrender.so.1
0xb008a000 /usr/lib/libXfixes.so.3
0xad550000 /root/.etwolf/pb/pbcl.so
0xb00a7000 /lib/libnss_mdns4_minimal.so.2
0xaffb7000 /lib/tls/i686/cmov/libnss_dns.so.2
0xaffa4000 /lib/tls/i686/cmov/libresolv.so.2
0xaff51000 /root/.etwolf/pb/pbag.so
0xad209000 /root/.etwolf/pb/pbsv.so
0xb136a000 /usr/lib/libGL.so.1
0xb09d2000 /usr/lib/libGLcore.so.1
0xb7f3b000 /usr/lib/tls/libnvidia-tls.so.1
0xadc3e000 /root/.etwolf/etpro/ui.mp.i386.so
0xa6e60000 /root/.etwolf/etpro/cgame.mp.i386.so
EIP: 08113f46
edi:00000009 esi:b2e42a54 ebp:00000000 esp:bfefa7c0
eax:000000ff ebx:b2e42b90 ecx:000000b4 edx:00000000
stack:
437e8fd3 bd31c249 bdbf4fbe 44953c3f 43792924 4357d070 449a752c 4313df34 
43c2f22a 435aeb92 4339b190 44887aaa 438e8fd2 3eeeeeef 43c8803c 4498397e 
4309b8d8 41e440fa 401aa67b 42afae76 43860057 44719a77 43389258 421e910f 
447c0c52 43b7c098 4355b828 00000000 bfefa8a4 b48f342c b48f342c 0811ae61 
code:
d8 8e 18 01 00 00 d9 c9 d8 86 04 01 00 00 d9 c9 d8 86 08 01 00 00 d9 ca d9 54 
24 30 d8 86 0c 01 00 00 d9 5c 24 30 d9 05 a8 da 1a 08 db f1 0f 83 5d 01 00 00 
Stack trace:
1 entries
/root/.etwolf/etpro/cgame.mp.i386.so[0xa6e7df22]
```

Is what the console says.

Any help would be awesome, thanks. And yes, i know - i shouldnt run et as root....

---

### Post by hikaricore on 2007-06-13
Current Hardware / Video drivers?

---

### Post by asipi on 2007-06-14
etpro 3.2.6 needs et 2.60b patch. 
have you installed it?

---

### Post by creativ3rst on 2007-06-20
Hardware / Software:

Clean install of Feisty 7.04

nvidia linux x86 100 14.06 pkg1 run - installed... but not configured correctly.
X crashes alot, and there is no splash screen - but et works to an extent, so i dont wanna play around with it.

this is not the problem either, because i recently encoutered the same problem too when running SuSe 10.2 with the 9577 drivers.

I think its pb... 

etpro 3.2.6 and et 2.60b patch installed

---

