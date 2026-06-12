---
title: "Problem getting zsnes to work."
date: 2009-01-04
forum: General Help
---

### Post by ulyanov on 2009-01-04
i use the latest version of linux mint. I know its not ubuntu, but i was directed here for support by some colleagues of mine. When i try and run zsnes i get the following:
 it.
ManyMouse: 3 mice detected.
Using ManyMouse for:
Mouse 0: AlpsPS/2 ALPS DualPoint TouchPad
Mouse 1: DualPoint Stick
File opened successfully !
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d9e558]
/lib/tls/i686/cmov/libc.so.6[0xb7d9c680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:01 98922      /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:01 98922      /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:01 98922      /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
08a0a000-08a54000 rw-p 08a0a000 00:00 0          [heap]
b6a06000-b7793000 rw-p b6a06000 00:00 0 
b7793000-b77b5000 r-xp 00000000 08:01 100270     /usr/lib/libaudiofile.so.0.0.2
b77b5000-b77b8000 rw-p 00021000 08:01 100270     /usr/lib/libaudiofile.so.0.0.2
b77c7000-b77ca000 r-xp 00000000 08:01 861882     /lib/libcap.so.1.10
b77ca000-b77cb000 rw-p 00002000 08:01 861882     /lib/libcap.so.1.10
b77cb000-b7819000 r-xp 00000000 08:01 98929      /usr/lib/libpulse.so.0.4.1
b7819000-b781a000 r--p 0004d000 08:01 98929      /usr/lib/libpulse.so.0.4.1
b781a000-b781b000 rw-p 0004e000 08:01 98929      /usr/lib/libpulse.so.0.4.1
b781b000-b7827000 r-xp 00000000 08:01 98930      /usr/lib/libpulse-simple.so.0.0.1
b7827000-b7828000 r--p 0000b000 08:01 98930      /usr/lib/libpulse-simple.so.0.0.1
b7828000-b7829000 rw-p 0000c000 08:01 98930      /usr/lib/libpulse-simple.so.0.0.1
b782a000-b7833000 r-xp 00000000 08:01 100446     /usr/lib/libesd.so.0.2.39
b7833000-b7834000 r--p 00008000 08:01 100446     /usr/lib/libesd.so.0.2.39
b7834000-b7835000 rw-p 00009000 08:01 100446     /usr/lib/libesd.so.0.2.39
b7835000-b7836000 r-xp 00000000 08:01 123610     /usr/lib/ao/plugins-2/libesd.so
b7836000-b7838000 rw-p 00000000 08:01 123610     /usr/lib/ao/plugins-2/libesd.so
b7838000-b7860000 r-xp 00000000 08:01 861953     /lib/libpcre.so.3.12.1
b7860000-b7861000 r--p 00027000 08:01 861953     /lib/libpcre.so.3.12.1
b7861000-b7862000 rw-p 00028000 08:01 861953     /lib/libpcre.so.3.12.1
b7862000-b7917000 r-xp 00000000 08:01 99318      /usr/lib/libglib-2.0.so.0.1800.2
b7917000-b7918000 r--p 000b4000 08:01 99318      /usr/lib/libglib-2.0.so.0.1800.2
b7918000-b7919000 rw-p 000b5000 08:01 99318      /usr/lib/libglib-2.0.so.0.1800.2
b7919000-b791d000 r-xp 00000000 08:01 99365      /usr/lib/libgthread-2.0.so.0.1800.2
b791d000-b791e000 r--p 00003000 08:01 99365      /usr/lib/libgthread-2.0.so.0.1800.2
b791e000-b791f000 rw-p 00004000 08:01 99365      /usr/lib/libgthread-2.0.so.0.1800.2
b791f000-b7922000 r-xp 00000000 08:01 99319      /usr/lib/libgmodule-2.0.so.0.1800.2
b7922000-b7923000 r--p 00002000 08:01 99319      /usr/lib/libgmodule-2.0.so.0.1800.2
b7923000-b7924000 rw-p 00003000 08:01 99319      /usr/lib/libgmodule-2.0.so.0.1800.2
b7924000-b7929000 r-xp 00000000 08:01 100256     /usr/lib/libartsc.so.0.0.0
b7929000-b792a000 r--p 00004000 08:01 100256     /usr/lib/libartsc.so.0.0.0
b792a000-b792b000 rw-p 00005000 08:01 100256     /usr/lib/libartsc.so.0.0.0
b792b000-b7940000 r-xp 00000000 08:01 100128     /usr/lib/libICE.so.6.3.0
b7940000-b7941000 rw-p 00014000 08:01 100128     /usr/lib/libICE.so.6.3.0
b7941000-b7943000 rw-p b7941000 00:00 0 
b7943000-b7990000 r-xp 00000000 08:01 100214     /usr/lib/libXt.so.6.0.0
b7990000-b7994000 rw-p 0004c000 08:01 100214     /usr/lib/libXt.so.6.0.0
b7994000-b79aa000 r-xp 00000000 08:01 100268     /usr/lib/libaudio.so.2.4
b79aa000-b79ab000 r--p 00015000 08:01 100268     /usr/lib/libaudio.so.2.4
b79ab000-b79ac000 rw-p 00016000 08:01 100268     /usr/lib/libaudio.so.2.4
b79ad000-b79ae000 rw-p b79ad000 00:00 0 
b79ae000-b79b0000 r-xp 00000000 08:01 123613     /usr/lib/ao/plugins-2/libpulse.so
b79b0000-b79b2000 rw-p 00001000 08:01 123613     /usr/lib/ao/plugins-2/libpulse.so
b79b2000-b79b4000 r-xp 00000000 08:01 123612     /usr/lib/ao/plugins-2/liboss.so
b79b4000-b79b6000 rw-p 00001000 08:01 123612     /usr/lib/ao/plugins-2/liboss.so
b79b6000-b79b9000 r-xp 00000000 08:01 123608     /usr/lib/ao/plugins-2/libalsa09.so
b79b9000-b79bb000 rw-p 00002000 08:01 123608     /usr/lib/ao/plugins-2/libalsa09.so
b79bb000-b79c5000 r-xp 00000000 08:01 887654     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b79c5000-b79c6000 r--p 00009000 08:01 887654     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b79c6000-b79c7000 rw-p 0000a000 08:01 887654     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b79c7000-b79d0000 r-xp 00000000 08:01 887658     /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b79d0000-b79d1000 r--p 00008000 08:01 887658     /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b79d1000-b79d2000 rw-p 00009000 08:01 887658     /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b79d2000-b79e7000 r-xp 00000000 08:01 887648     /lib/tls/i686/cmov/libnsl-2.8.90.so
b79e7000-b79e8000 r--p 00014000 08:01 887648     /lib/tls/i686/cmov/libnsl-2.8.90.so
b79e8000-b79e9000 rw-p 00015000 08:01 887648     /lib/tls/i686/cmov/libnsl-2.8.90.so
b79e9000-b79eb000 rw-p b79e9000 00:00 0 
b79eb000-b79f2000 r-xp 00000000 08:01 887650     /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b79f2000-b79f3000 r--p 00006000 08:01 887650     /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b79f3000-b79f4000 rw-p 00007000 08:01 887650     /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b79f4000-b79f6000 rw-p b79f4000 00:00 0 
b79f6000-b79fa000 r-xp 00000000 08:01 100184     /usr/lib/libXdmcp.so.6.0.0
b79fa000-b79fb000 rw-p 00003000 08:01 100184     /usr/lib/libXdmcp.so.6.0.0
b79fb000-b79fd000 r-xp 00000000 08:01 100173     /usr/lib/libXau.so.6.0.0
b79fd000-b79fe000 rw-p 00001000 08:01 100173     /usr/lib/libXau.so.6.0.0
b79fe000-b79ff000 rw-p b79fe000 00:00 0 
b79ff000-b7a16000 r-xp 00000000 08:01 101260     /usr/lib/libxcb.so.1.0.0
b7a16000-b7a17000 r--p 00016000 08:01 101260     /usr/lib/libxcb.so.1.0.0
b7a17000-b7a18000 rw-p 00017000 08:01 101260     /usr/lib/libxcb.so.1.0.0
b7a18000-b7a19000 r-xp 00000000 08:01 101256     /usr/lib/libxcb-xlib.so.0.0.0
b7a19000-b7a1a000 r--p 00000000 08:01 101256     /usr/lib/libxcb-xlib.so.0.0.0
b7a1a000-b7a1b000 rw-p 00001000 08:01 101256     /usr/lib/libxcb-xlib.so.0.0.0
b7a1b000-b7a22000 r-xp 00000000 08:01 887667     /lib/tls/i686/cmov/librt-2.8.90.so
b7a22000-b7a23000 r--p 00007000 08:01 887667     /lib/tls/i686/cmov/librt-2.8.90.so
b7a23000-b7a24000 rw-p 00008000 08:01 887667     /lib/tls/i686/cmov/librt-2.8.90.so
b7a24000-b7a2b000 r-xp 00000000 08:01 100406     /usr/lib/libdrm.so.2.3.1
b7a2b000-b7a2c000 r--p 00006000 08:01 100406     /usr/lib/libdrm.so.2.3.1
b7a2c000-b7a2d000 rw-p 00007000 08:01 100406     /usr/lib/libdrm.so.2.3.1
b7a2d000-b7a31000 r-xp 00000000 08:01 100190     /usr/lib/libXfixes.so.3.1.0
b7a31000-b7a32000 rw-p 00003000 08:01 100190     /usr/lib/libXfixes.so.3.1.0
b7a32000-b7a33000 rw-p b7a32000 00:00 0 
b7a33000-b7a35000 r-xp 00000000 08:01 100182     /usr/lib/libXdamage.so.1.1.0
b7a35000-b7a36000 rw-p 00001000 08:01 100182     /usr/lib/libXdamage.so.1.1.0
b7a36000-b7a3a000 r-xp 00000000 08:01 100228     /usr/lib/libXxf86vm.so.1.0.0
b7a3a000-b7a3b000 r--p 00003000 08:01 100228     /usr/lib/libXxf86vm.so.1.0.0
b7a3b000-b7a3c000 rw-p 00004000 08:01 100228     /usr/lib/libXxf86vm.so.1.0.0
b7a3c000-b7a49000 r-xp 00000000 08:01 100188     /usr/lib/libXext.so.6.4.0
b7a49000-b7a4b000 rw-p 0000c000 08:01 100188     /usr/lib/libXext.so.6.4.0
b7a4b000-b7b36000 r-xp 00000000 08:01 99311      /usr/lib/libX11.so.6.2.0
b7b36000-b7b37000 r--p 000ea000 08:01 99311      /usr/lib/libX11.so.6.2.0
b7b37000-b7b39000 rw-p 000eb000 08:01 99311      /usr/lib/libX11.so.6.2.0
b7b39000-b7b3a000 rw-p b7b39000 00:00 0 
b7b3a000-b7b4d000 r-xp 00000000 08:01 100392     /usr/lib/libdirect-1.0.so.0.1.0
b7b4d000-b7b4e000 r--p 00012000 08:01 100392     /usr/lib/libdirect-1.0.so.0.1.0
b7b4e000-b7b4f000 rw-p 00013000 08:01 100392     /usr/lib/libdirect-1.0.so.0.1.0
b7b4f000-b7b56000 r-xp 00000000 08:01 100496     /usr/lib/libfusion-1.0.so.0.1.0
b7b56000-b7b57000 r--p 00006000 08:01 100496     /usr/lib/libfusion-1.0.so.0.1.0
b7b57000-b7b58000 rw-p 00007000 08:01 100496     /usr/lib/libfusion-1.0.so.0.1.0
b7b58000-b7b59000 rw-p b7b58000 00:00 0 
b7b59000-b7bbd000 r-xp 00000000 08:01 100394     /usr/lib/libdirectfb-1.0.so.0.1.0
b7bbd000-b7bbe000 r--p 00063000 08:01 100394     /usr/lib/libdirectfb-1.0.so.0.1.0
b7bbe000-b7bbf000 rw-p 00064000 08:01 100394     /usr/lib/libdirectfb-1.0.so.0.1.0
b7bbf000-b7bc1000 r-xp 00000000 08:01 887643     /lib/tls/i686/cmov/libdl-2.8.90.so
b7bc1000-b7bc2000 r--p 00001000 08:01 887643     /lib/tls/i686/cmovAborted
sharar@sharar-laptop ~ $ 


could someone help me :confused:

---

### Post by northern lights on 2009-01-04
I have no idea why it'd give a buffer overflow, but have you tried going for an alternative, such as *snes9x*?

It's in the Ubuntu repositories as well as available as a .deb from [here]("http://ftp.debian.org/debian/pool/non-free/s/snes9x/").

---

### Post by ulyanov on 2009-01-04
thanks man that worked perfectly

---

### Post by ulyanov on 2009-01-04
okay snes9x is nice, but it is also very very buggy. IF someone could help getting zsnes work, it would be even better.

edit: i got an older package and it works now

---

