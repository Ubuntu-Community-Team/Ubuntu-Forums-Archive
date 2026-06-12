---
title: "TLF (contest logger) crashes on startup"
date: 2009-01-20
forum: General Help
---

### Post by ryanferreri on 2009-01-20
Hi All,

I'm trying to get TLF running on a Ubuntu latop I use for amateur radio applications. Unfortunately I cannot get it to work. I have tried both the version in the repositories and compiling from source. I sent a message to the dev team and have been back and forth with them but they asked that I post here as well.

When I run tlf, it enters the DX cluster first. When I hit ':' to exit the cluster and go into the logger, I get this output:

** buffer overflow detected ***: tlf terminated
                              
                  ======= Backtrace: =========
                                                                            /lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7ec2558]
                                                         /lib/tls/i686/cmov/libc.so.6[0xb7ec0680]
                 /lib/tls/i686/cmov/libc.so.6[0xb7ebfaf5]
                                                         tlf[0x8056647]
                                                                       tlf[0x807a9da]
     tlf[0x80635b5]
                   /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7dde685]
   tlf[0x804a591]
                 ======= Memory map: ========
                                             08048000-08084000 r-xp 00000000 08:05 421882     /usr/local/bin/tlf
                                08084000-08085000 r--p 0003b000 08:05 421882     /usr/local/bin/tlf
                   08085000-08088000 rw-p 0003c000 08:05 421882     /usr/local/bin/tlf
      08088000-08358000 rw-p 08088000 00:00 0
                                              0a22b000-0a24c000 rw-p 0a22b000 00:00 0          [heap]
                     b7db4000-b7dc1000 r-xp 00000000 08:05 472414     /lib/libgcc_s.so.1
        b7dc1000-b7dc2000 r--p 0000c000 08:05 472414     /lib/libgcc_s.so.1
                                                                           b7dc2000-b7dc3000 rw-p 0000d000 08:05 472414     /lib/libgcc_s.so.1
                                                              b7dc3000-b7dc4000 rw-p b7dc3000 00:00 0
                      b7dc4000-b7dc6000 r-xp 00000000 08:05 490015     /lib/tls/i686/cmov/libdl-2.8.90.so
                         b7dc6000-b7dc7000 r--p 00001000 08:05 490015     /lib/tls/i686/cmov/libdl-2.8.90.so
                            b7dc7000-b7dc8000 rw-p 00002000 08:05 490015     /lib/tls/i686/cmov/libdl-2.8.90.so
                               b7dc8000-b7f20000 r-xp 00000000 08:05 490009     /lib/tls/i686/cmov/libc-2.8.90.so
                                 b7f20000-b7f22000 r--p 00158000 08:05 490009     /lib/tls/i686/cmov/libc-2.8.90.so
                                   b7f22000-b7f23000 rw-p 0015a000 08:05 490009     /lib/tls/i686/cmov/libc-2.8.90.so
                                     b7f23000-b7f26000 rw-p b7f23000 00:00 0
                                                                             b7f26000-b7f4a000 r-xp 00000000 08:05 490017     /lib/tls/i686/cmov/libm-2.8.90.so
                                                                               b7f4a000-b7f4b000 r--p 00023000 08:05 490017     /lib/tls/i686/cmov/libm-2.8.90.so
 b7f4b000-b7f4c000 rw-p 00024000 08:05 490017     /lib/tls/i686/cmov/libm-2.8.90.so
   b7f4c000-b7f4d000 rw-p b7f4c000 00:00 0
                                           b7f4d000-b7f62000 r-xp 00000000 08:05 490035     /lib/tls/i686/cmov/libpthread-2.8.90.so
                                                   b7f62000-b7f63000 r--p 00014000 08:05 490035     /lib/tls/i686/cmov/libpthread-2.8.90.so
                                                           b7f63000-b7f64000 rw-p 00015000 08:05 490035     /lib/tls/i686/cmov/libpthread-2.8.90.so
                                                                   b7f64000-b7f66000 rw-p b7f64000 00:00 0
                           b7f66000-b7f93000 r-xp 00000000 08:05 472429     /lib/libncurses.so.5.6
                  b7f93000-b7f96000 rw-p 0002c000 08:05 472429     /lib/libncurses.so.5.6
         b7fa6000-b7fa8000 rw-p b7fa6000 00:00 0
                                                 b7fa8000-b7fc2000 r-xp 00000000 08:05 472371     /lib/ld-2.8.90.so
                                   b7fc2000-b7fc3000 r-xp b7fc2000 00:00 0          [vdso]
          b7fc3000-b7fc4000 r--p 0001a000 08:05 472371     /lib/ld-2.8.90.so
                                                                            b7fc4000-b7fc5000 rw-p 0001b000 08:05 472371     /lib/ld-2.8.90.so
                                                              bfdb0000-bfdc5000 rw-p bffeb000 00:00 0          [stack]
                                      Aborted

---

### Post by ryanferreri on 2009-01-20
Sorry, forgot to mention this is Ubuntu 8.10. Thanks.

---

### Post by Blaze1024 on 2011-03-27
> **ryanferreri said:**
> Sorry, forgot to mention this is Ubuntu 8.10. Thanks.

Was this issue ever resolved?

---

