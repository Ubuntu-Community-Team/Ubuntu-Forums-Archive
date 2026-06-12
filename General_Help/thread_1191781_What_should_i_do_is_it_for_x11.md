---
title: "What should i do? is it for x11?"
date: 2009-06-19
forum: General Help
---

### Post by the_godz on 2009-06-19
hi

when i run a team on robocup soccer simulation server in my ubuntu Jaunty, this error showed : 

```

*** buffer overflow detected ***: src/trilearn_player terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d81558]
/lib/tls/i686/cmov/libc.so.6[0xb7d7f680]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0xb7d7e944]
src/trilearn_player[0x804eb05]
src/trilearn_player[0x808f191]
src/trilearn_player[0x80944d7]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7c9d685]
src/trilearn_player[0x804a9e1]
======= Memory map: ========
08048000-080a0000 r-xp 00000000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a0000-080a1000 r--p 00058000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a1000-080a2000 rw-p 00059000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a2000-080a6000 rw-p 080a2000 00:00 0 
08b80000-08ba1000 rw-p 08b80000 00:00 0          [heap]
b7479000-b747a000 ---p b7479000 00:00 0 
b747a000-b7c7a000 rw-p b747a000 00:00 0 
b7c7a000-b7c84000 r-xp 00000000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7c84000-b7c85000 r--p 00009000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7c85000-b7c86000 rw-p 0000a000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7c86000-b7c87000 rw-p b7c86000 00:00 0 
b7c87000-b7ddf000 r-xp 00000000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7ddf000-b7de1000 r--p 00158000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7de1000-b7de2000 rw-p 0015a000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7de2000-b7de5000 rw-p b7de2000 00:00 0 
b7de5000-b7df2000 r-xp 00000000 08:05 767102     /lib/libgcc_s.so.1
b7df2000-b7df3000 r--p 0000c000 08:05 767102     /lib/libgcc_s.so.1
b7df3000-b7df4000 rw-p 0000d000 08:05 767102     /lib/libgcc_s.so.1
b7df4000-b7e18000 r-xp 00000000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7e18000-b7e19000 r--p 00023000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7e19000-b7e1a000 rw-p 00024000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7e1a000-b7e1b000 rw-p b7e1a000 00:00 0 
b7e1b000-b7efe000 r-xp 00000000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7efe000-b7eff000 ---p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7eff000-b7f03000 r--p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7f03000-b7f04000 rw-p 000e7000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7f04000-b7f0a000 rw-p b7f04000 00:00 0 
b7f0a000-b7f1f000 r-xp 00000000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7f1f000-b7f20000 r--p 00014000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7f20000-b7f21000 rw-p 00015000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7f21000-b7f23000 rw-p b7f21000 00:00 0 
b7f37000-b7f3a000 rw-p b7f37000 00:00 0 
b7f3a000-b7f54000 r-xp 00000000 08:05 767059     /lib/ld-2.8.90.so
b7f54000-b7f55000 r-xp b7f54000 00:00 0          [vdso]
b7f55000-b7f56000 r--p 0001a000 08:05 767059     /lib/ld-2.8.90.so
b7f56000-b7f57000 rw-p 0001b000 08:05 767059     /lib/ld-2.8.90.so
bf841000-bf856000 rw-p bffeb000 00:00 0          [stack]
*** buffer overflow detected ***: src/trilearn_player terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7e9f558]
/lib/tls/i686/cmov/libc.so.6[0xb7e9d680]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0xb7e9c944]
src/trilearn_player[0x804eb05]
src/trilearn_player[0x808f191]
src/trilearn_player[0x80944d7]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7dbb685]
src/trilearn_player[0x804a9e1]
======= Memory map: ========
08048000-080a0000 r-xp 00000000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a0000-080a1000 r--p 00058000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a1000-080a2000 rw-p 00059000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a2000-080a6000 rw-p 080a2000 00:00 0 
09f04000-09f25000 rw-p 09f04000 00:00 0          [heap]
b7597000-b7598000 ---p b7597000 00:00 0 
b7598000-b7d98000 rw-p b7598000 00:00 0 
b7d98000-b7da2000 r-xp 00000000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7da2000-b7da3000 r--p 00009000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7da3000-b7da4000 rw-p 0000a000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7da4000-b7da5000 rw-p b7da4000 00:00 0 
b7da5000-b7efd000 r-xp 00000000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7efd000-b7eff000 r--p 00158000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7eff000-b7f00000 rw-p 0015a000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7f00000-b7f03000 rw-p b7f00000 00:00 0 
b7f03000-b7f10000 r-xp 00000000 08:05 767102     /lib/libgcc_s.so.1
b7f10000-b7f11000 r--p 0000c000 08:05 767102     /lib/libgcc_s.so.1
b7f11000-b7f12000 rw-p 0000d000 08:05 767102     /lib/libgcc_s.so.1
b7f12000-b7f36000 r-xp 00000000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7f36000-b7f37000 r--p 00023000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7f37000-b7f38000 rw-p 00024000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7f38000-b7f39000 rw-p b7f38000 00:00 0 
b7f39000-b801c000 r-xp 00000000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b801c000-b801d000 ---p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b801d000-b8021000 r--p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b8021000-b8022000 rw-p 000e7000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b8022000-b8028000 rw-p b8022000 00:00 0 
b8028000-b803d000 r-xp 00000000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b803d000-b803e000 r--p 00014000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b803e000-b803f000 rw-p 00015000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b803f000-b8041000 rw-p b803f000 00:00 0 
b8056000-b8058000 rw-p b8056000 00:00 0 
b8058000-b8072000 r-xp 00000000 08:05 767059     /lib/ld-2.8.90.so
b8072000-b8073000 r-xp b8072000 00:00 0          [vdso]
b8073000-b8074000 r--p 0001a000 08:05 767059     /lib/ld-2.8.90.so
b8074000-b8075000 rw-p 0001b000 08:05 767059     /lib/ld-2.8.90.so
bfd5f000-bfd74000 rw-p bffeb000 00:00 0          [stack]
*** buffer overflow detected ***: src/trilearn_player terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7e99558]
/lib/tls/i686/cmov/libc.so.6[0xb7e97680]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0xb7e96944]
src/trilearn_player[0x804eb05]
src/trilearn_player[0x808f191]
src/trilearn_player[0x80944d7]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7db5685]
src/trilearn_player[0x804a9e1]
======= Memory map: ========
08048000-080a0000 r-xp 00000000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a0000-080a1000 r--p 00058000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a1000-080a2000 rw-p 00059000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a2000-080a6000 rw-p 080a2000 00:00 0 
08520000-08541000 rw-p 08520000 00:00 0          [heap]
b7591000-b7592000 ---p b7591000 00:00 0 
b7592000-b7d92000 rw-p b7592000 00:00 0 
b7d92000-b7d9c000 r-xp 00000000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7d9c000-b7d9d000 r--p 00009000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7d9d000-b7d9e000 rw-p 0000a000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7d9e000-b7d9f000 rw-p b7d9e000 00:00 0 
b7d9f000-b7ef7000 r-xp 00000000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7ef7000-b7ef9000 r--p 00158000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7ef9000-b7efa000 rw-p 0015a000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7efa000-b7efd000 rw-p b7efa000 00:00 0 
b7efd000-b7f0a000 r-xp 00000000 08:05 767102     /lib/libgcc_s.so.1
b7f0a000-b7f0b000 r--p 0000c000 08:05 767102     /lib/libgcc_s.so.1
b7f0b000-b7f0c000 rw-p 0000d000 08:05 767102     /lib/libgcc_s.so.1
b7f0c000-b7f30000 r-xp 00000000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7f30000-b7f31000 r--p 00023000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7f31000-b7f32000 rw-p 00024000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7f32000-b7f33000 rw-p b7f32000 00:00 0 
b7f33000-b8016000 r-xp 00000000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b8016000-b8017000 ---p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b8017000-b801b000 r--p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b801b000-b801c000 rw-p 000e7000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b801c000-b8022000 rw-p b801c000 00:00 0 
b8022000-b8037000 r-xp 00000000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b8037000-b8038000 r--p 00014000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b8038000-b8039000 rw-p 00015000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b8039000-b803b000 rw-p b8039000 00:00 0 
b8050000-b8052000 rw-p b8050000 00:00 0 
b8052000-b806c000 r-xp 00000000 08:05 767059     /lib/ld-2.8.90.so
b806c000-b806d000 r-xp b806c000 00:00 0          [vdso]
b806d000-b806e000 r--p 0001a000 08:05 767059     /lib/ld-2.8.90.so
b806e000-b806f000 rw-p 0001b000 08:05 767059     /lib/ld-2.8.90.so
bff59000-bff6e000 rw-p bffeb000 00:00 0          [stack]
*** buffer overflow detected ***: src/trilearn_player terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7dd7558]
/lib/tls/i686/cmov/libc.so.6[0xb7dd5680]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0xb7dd4944]
src/trilearn_player[0x804eb05]
src/trilearn_player[0x808f191]
src/trilearn_player[0x80944d7]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7cf3685]
src/trilearn_player[0x804a9e1]
======= Memory map: ========
08048000-080a0000 r-xp 00000000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a0000-080a1000 r--p 00058000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a1000-080a2000 rw-p 00059000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a2000-080a6000 rw-p 080a2000 00:00 0 
08d10000-08d31000 rw-p 08d10000 00:00 0          [heap]
b74cf000-b74d0000 ---p b74cf000 00:00 0 
b74d0000-b7cd0000 rw-p b74d0000 00:00 0 
b7cd0000-b7cda000 r-xp 00000000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7cda000-b7cdb000 r--p 00009000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7cdb000-b7cdc000 rw-p 0000a000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7cdc000-b7cdd000 rw-p b7cdc000 00:00 0 
b7cdd000-b7e35000 r-xp 00000000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7e35000-b7e37000 r--p 00158000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7e37000-b7e38000 rw-p 0015a000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7e38000-b7e3b000 rw-p b7e38000 00:00 0 
b7e3b000-b7e48000 r-xp 00000000 08:05 767102     /lib/libgcc_s.so.1
b7e48000-b7e49000 r--p 0000c000 08:05 767102     /lib/libgcc_s.so.1
b7e49000-b7e4a000 rw-p 0000d000 08:05 767102     /lib/libgcc_s.so.1
b7e4a000-b7e6e000 r-xp 00000000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7e6e000-b7e6f000 r--p 00023000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7e6f000-b7e70000 rw-p 00024000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7e70000-b7e71000 rw-p b7e70000 00:00 0 
b7e71000-b7f54000 r-xp 00000000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7f54000-b7f55000 ---p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7f55000-b7f59000 r--p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7f59000-b7f5a000 rw-p 000e7000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7f5a000-b7f60000 rw-p b7f5a000 00:00 0 
b7f60000-b7f75000 r-xp 00000000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7f75000-b7f76000 r--p 00014000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7f76000-b7f77000 rw-p 00015000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7f77000-b7f79000 rw-p b7f77000 00:00 0 
b7f8e000-b7f90000 rw-p b7f8e000 00:00 0 
b7f90000-b7faa000 r-xp 00000000 08:05 767059     /lib/ld-2.8.90.so
b7faa000-b7fab000 r-xp b7faa000 00:00 0          [vdso]
b7fab000-b7fac000 r--p 0001a000 08:05 767059     /lib/ld-2.8.90.so
b7fac000-b7fad000 rw-p 0001b000 08:05 767059     /lib/ld-2.8.90.so
bf897000-bf8ac000 rw-p bffeb000 00:00 0          [stack]
*** buffer overflow detected ***: src/trilearn_player terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d4c558]
/lib/tls/i686/cmov/libc.so.6[0xb7d4a680]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0xb7d49944]
src/trilearn_player[0x804eb05]
src/trilearn_player[0x808f191]
src/trilearn_player[0x80944d7]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7c68685]
src/trilearn_player[0x804a9e1]
======= Memory map: ========
08048000-080a0000 r-xp 00000000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a0000-080a1000 r--p 00058000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a1000-080a2000 rw-p 00059000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a2000-080a6000 rw-p 080a2000 00:00 0 
097c5000-097e6000 rw-p 097c5000 00:00 0          [heap]
b7444000-b7445000 ---p b7444000 00:00 0 
b7445000-b7c45000 rw-p b7445000 00:00 0 
b7c45000-b7c4f000 r-xp 00000000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7c4f000-b7c50000 r--p 00009000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7c50000-b7c51000 rw-p 0000a000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7c51000-b7c52000 rw-p b7c51000 00:00 0 
b7c52000-b7daa000 r-xp 00000000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7daa000-b7dac000 r--p 00158000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7dac000-b7dad000 rw-p 0015a000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7dad000-b7db0000 rw-p b7dad000 00:00 0 
b7db0000-b7dbd000 r-xp 00000000 08:05 767102     /lib/libgcc_s.so.1
b7dbd000-b7dbe000 r--p 0000c000 08:05 767102     /lib/libgcc_s.so.1
b7dbe000-b7dbf000 rw-p 0000d000 08:05 767102     /lib/libgcc_s.so.1
b7dbf000-b7de3000 r-xp 00000000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7de3000-b7de4000 r--p 00023000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7de4000-b7de5000 rw-p 00024000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7de5000-b7de6000 rw-p b7de5000 00:00 0 
b7de6000-b7ec9000 r-xp 00000000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7ec9000-b7eca000 ---p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7eca000-b7ece000 r--p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7ece000-b7ecf000 rw-p 000e7000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7ecf000-b7ed5000 rw-p b7ecf000 00:00 0 
b7ed5000-b7eea000 r-xp 00000000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7eea000-b7eeb000 r--p 00014000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7eeb000-b7eec000 rw-p 00015000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7eec000-b7eee000 rw-p b7eec000 00:00 0 
b7f03000-b7f05000 rw-p b7f03000 00:00 0 
b7f05000-b7f1f000 r-xp 00000000 08:05 767059     /lib/ld-2.8.90.so
b7f1f000-b7f20000 r-xp b7f1f000 00:00 0          [vdso]
b7f20000-b7f21000 r--p 0001a000 08:05 767059     /lib/ld-2.8.90.so
b7f21000-b7f22000 rw-p 0001b000 08:05 767059     /lib/ld-2.8.90.so
bff0d000-bff22000 rw-p bffeb000 00:00 0          [stack]
 93: direction old: 119.978042, new: -23.470628
*** buffer overflow detected ***: src/trilearn_player terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7ee5558]
/lib/tls/i686/cmov/libc.so.6[0xb7ee3680]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0xb7ee2944]
src/trilearn_player[0x804eb05]
src/trilearn_player[0x808f191]
src/trilearn_player[0x80944d7]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7e01685]
src/trilearn_player[0x804a9e1]
======= Memory map: ========
08048000-080a0000 r-xp 00000000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a0000-080a1000 r--p 00058000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a1000-080a2000 rw-p 00059000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a2000-080a6000 rw-p 080a2000 00:00 0 
08b48000-08b69000 rw-p 08b48000 00:00 0          [heap]
b75dd000-b75de000 ---p b75dd000 00:00 0 
b75de000-b7dde000 rw-p b75de000 00:00 0 
b7dde000-b7de8000 r-xp 00000000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7de8000-b7de9000 r--p 00009000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7de9000-b7dea000 rw-p 0000a000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7dea000-b7deb000 rw-p b7dea000 00:00 0 
b7deb000-b7f43000 r-xp 00000000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7f43000-b7f45000 r--p 00158000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7f45000-b7f46000 rw-p 0015a000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7f46000-b7f49000 rw-p b7f46000 00:00 0 
b7f49000-b7f56000 r-xp 00000000 08:05 767102     /lib/libgcc_s.so.1
b7f56000-b7f57000 r--p 0000c000 08:05 767102     /lib/libgcc_s.so.1
b7f57000-b7f58000 rw-p 0000d000 08:05 767102     /lib/libgcc_s.so.1
b7f58000-b7f7c000 r-xp 00000000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7f7c000-b7f7d000 r--p 00023000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7f7d000-b7f7e000 rw-p 00024000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7f7e000-b7f7f000 rw-p b7f7e000 00:00 0 
b7f7f000-b8062000 r-xp 00000000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b8062000-b8063000 ---p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b8063000-b8067000 r--p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b8067000-b8068000 rw-p 000e7000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b8068000-b806e000 rw-p b8068000 00:00 0 
b806e000-b8083000 r-xp 00000000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b8083000-b8084000 r--p 00014000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b8084000-b8085000 rw-p 00015000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b8085000-b8087000 rw-p b8085000 00:00 0 
b809b000-b809e000 rw-p b809b000 00:00 0 
b809e000-b80b8000 r-xp 00000000 08:05 767059     /lib/ld-2.8.90.so
b80b8000-b80b9000 r-xp b80b8000 00:00 0          [vdso]
b80b9000-b80ba000 r--p 0001a000 08:05 767059     /lib/ld-2.8.90.so
b80ba000-b80bb000 rw-p 0001b000 08:05 767059     /lib/ld-2.8.90.so
bf8a5000-bf8ba000 rw-p bffeb000 00:00 0          [stack]
*** buffer overflow detected ***: src/trilearn_player terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7e2f558]
/lib/tls/i686/cmov/libc.so.6[0xb7e2d680]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0xb7e2c944]
src/trilearn_player[0x804eb05]
src/trilearn_player[0x808f191]
src/trilearn_player[0x80944d7]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d4b685]
src/trilearn_player[0x804a9e1]
======= Memory map: ========
08048000-080a0000 r-xp 00000000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a0000-080a1000 r--p 00058000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a1000-080a2000 rw-p 00059000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a2000-080a6000 rw-p 080a2000 00:00 0 
09884000-098a5000 rw-p 09884000 00:00 0          [heap]
b7527000-b7528000 ---p b7527000 00:00 0 
b7528000-b7d28000 rw-p b7528000 00:00 0 
b7d28000-b7d32000 r-xp 00000000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7d32000-b7d33000 r--p 00009000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7d33000-b7d34000 rw-p 0000a000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7d34000-b7d35000 rw-p b7d34000 00:00 0 
b7d35000-b7e8d000 r-xp 00000000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7e8d000-b7e8f000 r--p 00158000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7e8f000-b7e90000 rw-p 0015a000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7e90000-b7e93000 rw-p b7e90000 00:00 0 
b7e93000-b7ea0000 r-xp 00000000 08:05 767102     /lib/libgcc_s.so.1
b7ea0000-b7ea1000 r--p 0000c000 08:05 767102     /lib/libgcc_s.so.1
b7ea1000-b7ea2000 rw-p 0000d000 08:05 767102     /lib/libgcc_s.so.1
b7ea2000-b7ec6000 r-xp 00000000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7ec6000-b7ec7000 r--p 00023000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7ec7000-b7ec8000 rw-p 00024000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7ec8000-b7ec9000 rw-p b7ec8000 00:00 0 
b7ec9000-b7fac000 r-xp 00000000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7fac000-b7fad000 ---p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7fad000-b7fb1000 r--p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7fb1000-b7fb2000 rw-p 000e7000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b7fb2000-b7fb8000 rw-p b7fb2000 00:00 0 
b7fb8000-b7fcd000 r-xp 00000000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7fcd000-b7fce000 r--p 00014000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7fce000-b7fcf000 rw-p 00015000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7fcf000-b7fd1000 rw-p b7fcf000 00:00 0 
b7fe6000-b7fe8000 rw-p b7fe6000 00:00 0 
b7fe8000-b8002000 r-xp 00000000 08:05 767059     /lib/ld-2.8.90.so
b8002000-b8003000 r-xp b8002000 00:00 0          [vdso]
b8003000-b8004000 r--p 0001a000 08:05 767059     /lib/ld-2.8.90.so
b8004000-b8005000 rw-p 0001b000 08:05 767059     /lib/ld-2.8.90.so
bf9ef000-bfa04000 rw-p bffeb000 00:00 0          [stack]
*** buffer overflow detected ***: src/trilearn_player terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7eb3558]
/lib/tls/i686/cmov/libc.so.6[0xb7eb1680]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0xb7eb0944]
src/trilearn_player[0x804eb05]
src/trilearn_player[0x808f191]
src/trilearn_player[0x80944d7]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7dcf685]
src/trilearn_player[0x804a9e1]
======= Memory map: ========
08048000-080a0000 r-xp 00000000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a0000-080a1000 r--p 00058000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a1000-080a2000 rw-p 00059000 08:05 220626     /home/sadegh/Desktop/trilearn_base_sources-3.4/src/trilearn_player
080a2000-080a6000 rw-p 080a2000 00:00 0 
08983000-089a4000 rw-p 08983000 00:00 0          [heap]
b75ab000-b75ac000 ---p b75ab000 00:00 0 
b75ac000-b7dac000 rw-p b75ac000 00:00 0 
b7dac000-b7db6000 r-xp 00000000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7db6000-b7db7000 r--p 00009000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7db7000-b7db8000 rw-p 0000a000 08:05 784393     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7db8000-b7db9000 rw-p b7db8000 00:00 0 
b7db9000-b7f11000 r-xp 00000000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7f11000-b7f13000 r--p 00158000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7f13000-b7f14000 rw-p 0015a000 08:05 784376     /lib/tls/i686/cmov/libc-2.8.90.so
b7f14000-b7f17000 rw-p b7f14000 00:00 0 
b7f17000-b7f24000 r-xp 00000000 08:05 767102     /lib/libgcc_s.so.1
b7f24000-b7f25000 r--p 0000c000 08:05 767102     /lib/libgcc_s.so.1
b7f25000-b7f26000 rw-p 0000d000 08:05 767102     /lib/libgcc_s.so.1
b7f26000-b7f4a000 r-xp 00000000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7f4a000-b7f4b000 r--p 00023000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7f4b000-b7f4c000 rw-p 00024000 08:05 784384     /lib/tls/i686/cmov/libm-2.8.90.so
b7f4c000-b7f4d000 rw-p b7f4c000 00:00 0 
b7f4d000-b8030000 r-xp 00000000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b8030000-b8031000 ---p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b8031000-b8035000 r--p 000e3000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b8035000-b8036000 rw-p 000e7000 08:05 710667     /usr/lib/libstdc++.so.6.0.10
b8036000-b803c000 rw-p b8036000 00:00 0 
b803c000-b8051000 r-xp 00000000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b8051000-b8052000 r--p 00014000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b8052000-b8053000 rw-p 00015000 08:05 784402     /lib/tls/i686/cmov/libpthread-2.8.90.so
b8053000-b8055000 rw-p b8053000 00:00 0 
b806a000-b806c000 rw-p b806a000 00:00 0 
b806c000-b8086000 r-xp 00000000 08:05 767059     /lib/ld-2.8.90.so
b8086000-b8087000 r-xp b8086000 00:00 0          [vdso]
b8087000-b8088000 r--p 0001a000 08:05 767059     /lib/ld-2.8.90.so
b8088000-b8089000 rw-p 0001b000 08:05 767059     /lib/ld-2.8.90.so
bfc74000-bfc89000 rw-p bffeb000 00:00 0          [stack]
```what should i do!? please help?
[ i think it is for x11 libraries but when i searchesd in x11 package of 9.04 in package.ubuntu.com i found that we have a lot of X11 library!! ]

---

### Post by the_godz on 2009-06-19
Hello?!

---

### Post by lgxwqq on 2010-04-16
hello i'm chiese ,i feel sorry for my poor english...
 
i got the same question with yours.it really puzzle me .
 
 
have u fix it ?my msn:lgxwqq@126.com
 
best regards

---

### Post by ddani on 2010-11-26
hi!!! 
did you figure out the solution for this problem?? It would really help if you could share it.

---

