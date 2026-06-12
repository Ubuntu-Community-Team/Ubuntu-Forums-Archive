---
title: "yagiuda crashes on Intrepid"
date: 2009-01-01
forum: Education &amp; Science
---

### Post by mocha on 2009-01-01
I get the following everytime I run the "input" program after I start to enter the parameters for my antenna.  It makes it up to about the 2nd element and then bombs out.  Is this an issue with libc?


*** glibc detected *** input: munmap_chunk(): invalid pointer: 0x0804a7c3 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7df63f4]
input[0x8048e66]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d9d685]
input[0x80487d1]
======= Memory map: ========
08048000-0804c000 r-xp 00000000 08:02 1558124    /usr/bin/input
0804c000-0804e000 rw-p 00003000 08:02 1558124    /usr/bin/input
08a2b000-08a4c000 rw-p 08a2b000 00:00 0          [heap]
b7d86000-b7d87000 rw-p b7d86000 00:00 0 
b7d87000-b7edf000 r-xp 00000000 08:02 721575     /lib/tls/i686/cmov/libc-2.8.90.so
b7edf000-b7ee1000 r--p 00158000 08:02 721575     /lib/tls/i686/cmov/libc-2.8.90.so
b7ee1000-b7ee2000 rw-p 0015a000 08:02 721575     /lib/tls/i686/cmov/libc-2.8.90.so
b7ee2000-b7ee5000 rw-p b7ee2000 00:00 0 
b7ee5000-b7f09000 r-xp 00000000 08:02 721730     /lib/tls/i686/cmov/libm-2.8.90.so
b7f09000-b7f0a000 r--p 00023000 08:02 721730     /lib/tls/i686/cmov/libm-2.8.90.so
b7f0a000-b7f0b000 rw-p 00024000 08:02 721730     /lib/tls/i686/cmov/libm-2.8.90.so
b7f20000-b7f2d000 r-xp 00000000 08:02 720914     /lib/libgcc_s.so.1
b7f2d000-b7f2e000 r--p 0000c000 08:02 720914     /lib/libgcc_s.so.1
b7f2e000-b7f2f000 rw-p 0000d000 08:02 720914     /lib/libgcc_s.so.1
b7f2f000-b7f33000 rw-p b7f2f000 00:00 0 
b7f33000-b7f4d000 r-xp 00000000 08:02 721209     /lib/ld-2.8.90.so
b7f4d000-b7f4e000 r-xp b7f4d000 00:00 0          [vdso]
b7f4e000-b7f4f000 r--p 0001a000 08:02 721209     /lib/ld-2.8.90.so
b7f4f000-b7f50000 rw-p 0001b000 08:02 721209     /lib/ld-2.8.90.so
bfb3b000-bfb50000 rw-p bffeb000 00:00 0          [stack]
Aborted

---

