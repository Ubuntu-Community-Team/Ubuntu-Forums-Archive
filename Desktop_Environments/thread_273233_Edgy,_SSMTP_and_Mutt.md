---
title: "Edgy, SSMTP and Mutt"
date: 2006-10-07
forum: Desktop Environments
---

### Post by greglaun on 2006-10-07
Hey, upgrading to edgy broke ssmtp on both of my machines. When I try to email something I get this:


```


*** glibc detected *** ssmtp: free(): invalid pointer: 0x080544b2 ***
======= Backtrace: =========
/lib/libc.so.6[0xb7e7f082]
/lib/libc.so.6(__libc_free+0x84)[0xb7e80704]
ssmtp[0x804aeae]
ssmtp[0x804b88f]
ssmtp[0x804c2f7]
/lib/libc.so.6(__libc_start_main+0xdc)[0xb7e318cc]
ssmtp[0x8049541]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:01 25252459   /usr/sbin/ssmtp
0804e000-0804f000 rw-p 00005000 08:01 25252459   /usr/sbin/ssmtp
0804f000-08074000 rw-p 0804f000 00:00 0          [heap]
b7b00000-b7b21000 rw-p b7b00000 00:00 0
b7b21000-b7c00000 ---p b7b21000 00:00 0
b7cac000-b7cb4000 r-xp 00000000 08:01 11944493   /lib/libnss_files-2.4.so
b7cb4000-b7cb6000 rw-p 00007000 08:01 11944493   /lib/libnss_files-2.4.so
b7cb6000-b7cbe000 r-xp 00000000 08:01 11944495   /lib/libnss_nis-2.4.so
b7cbe000-b7cc0000 rw-p 00007000 08:01 11944495   /lib/libnss_nis-2.4.so
b7cc0000-b7cc6000 r-xp 00000000 08:01 11944488   /lib/libnss_compat-2.4.so
b7cc6000-b7cc8000 rw-p 00005000 08:01 11944488   /lib/libnss_compat-2.4.so
b7cc8000-b7cca000 rw-p b7cc8000 00:00 0
b7cca000-b7cdd000 r-xp 00000000 08:01 25037246   /usr/lib/libz.so.1.2.3
b7cdd000-b7cde000 rw-p 00012000 08:01 25037246   /usr/lib/libz.so.1.2.3
b7cde000-b7ce0000 r-xp 00000000 08:01 11944479   /lib/libdl-2.4.so
b7ce0000-b7ce2000 rw-p 00001000 08:01 11944479   /lib/libdl-2.4.so
b7ce2000-b7e04000 r-xp 00000000 08:01 25036270   /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7e04000-b7e19000 rw-p 00121000 08:01 25036270   /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7e19000-b7e1c000 rw-p b7e19000 00:00 0
b7e1c000-b7f35000 r-xp 00000000 08:01 11944473   /lib/libc-2.4.so
b7f35000-b7f37000 r--p 00118000 08:01 11944473   /lib/libc-2.4.so
b7f37000-b7f39000 rw-p 0011a000 08:01 11944473   /lib/libc-2.4.so
b7f39000-b7f3c000 rw-p b7f39000 00:00 0
b7f3c000-b7f77000 r-xp 00000000 08:01 25036271   /usr/lib/i686/cmov/libssl.so.0.9.8
b7f77000-b7f7b000 rw-p 0003b000 08:01 25036271   /usr/lib/i686/cmov/libssl.so.0.9.8
b7f7b000-b7f8c000 r-xp 00000000 08:01 11944486   /lib/libnsl-2.4.so
b7f8c000-b7f8e000 rw-p 00010000 08:01 11944486   /lib/libnsl-2.4.so
b7f8e000-b7f91000 rw-p b7f8e000 00:00 0
b7f94000-b7f9e000 r-xp 00000000 08:01 11944174   /lib/libgcc_s.so.1
b7f9e000-b7f9f000 rw-p 00009000 08:01 11944174   /lib/libgcc_s.so.1
b7f9f000-b7fa1000 rw-p b7f9f000 00:00 0
b7fa1000-b7fba000 r-xp 00000000 08:01 11944466   /lib/ld-2.4.so
b7fba000-b7fbc000 rw-p 00018000 08:01 11944466   /lib/ld-2.4.so
bfaa5000-bfaba000 rw-p bfaa5000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]



```


I've searched the fora and I can't seem to find anything useful.  Does anybody have any idea what to do?  I tried reinstalling all the packages and libraries listed

---

### Post by b7j0c on 2006-10-13
sasl authentication is also broken with the edgy mutt and sasl packages.

the debian etch packages are *not* broken, perhaps those should be used.

this apparently was a known bug in the upstream codebases:

[http://archives.free.net.ph/message/20060908.135707.30e95afd.en.html](http://archives.free.net.ph/message/20060908.135707.30e95afd.en.html)

mutt does not use malone for bugtracking, impossible to figure out from launchpad where to file the bug

---

