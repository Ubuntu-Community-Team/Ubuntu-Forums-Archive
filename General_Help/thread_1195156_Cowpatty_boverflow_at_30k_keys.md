---
title: "Cowpatty boverflow at 30k keys?"
date: 2009-06-23
forum: General Help
---

### Post by Glyph89 on 2009-06-23
I've even applied the patch for cowpatty which I found from these forums, but still seem to have this problem.
 
 I'm using 9.04 Jaunty. Anyone else have this problem before? Google isn't helping. :(
 
 I also noticed that cowpatty is using  "/lib/**i686**/cmov/libcrypto.so.0.9.8". I'm on i386. So, i'm not sure if this is a problem or not. Thanks for reading, anyway. Hope someone can help!

Here's what i'm seeing:

```
glyph@glyphtop:~/Desktop/cowpatty-4.2$ ./cowpatty -d home -r homes-01.cap -s home
cowpatty 4.2 - WPA-PSK dictionary attack. <jwright@hasborg.com>

Collected all necessary data to mount crack against WPA/PSK passphrase.
Starting dictionary attack.  Please be patient.
key no. 10000: 1Seaport
key no. 20000: 53dog162
key no. 30000: CHARLESW
*** buffer overflow detected ***: ./cowpatty terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7e8eda8]
/lib/tls/i686/cmov/libc.so.6[0xb7e8ceb0]
/lib/tls/i686/cmov/libc.so.6(__fread_chk+0x143)[0xb7e8d7a3]
./cowpatty[0x804904f]
./cowpatty[0x804a278]
./cowpatty[0x804a7e1]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7da7775]
./cowpatty[0x8048cb1]
======= Memory map: ========
08048000-0804d000 r-xp 00000000 08:01 4104354    /home/glyph/Desktop/cowpatty-4.2/cowpatty
0804d000-0804e000 r--p 00004000 08:01 4104354    /home/glyph/Desktop/cowpatty-4.2/cowpatty
0804e000-0804f000 rw-p 00005000 08:01 4104354    /home/glyph/Desktop/cowpatty-4.2/cowpatty
09db8000-09dd9000 rw-p 09db8000 00:00 0          [heap]
b7d76000-b7d77000 rw-p b7d76000 00:00 0 
b7d77000-b7d8b000 r-xp 00000000 08:01 3825825    /lib/libz.so.1.2.3.3
b7d8b000-b7d8c000 r--p 00013000 08:01 3825825    /lib/libz.so.1.2.3.3
b7d8c000-b7d8d000 rw-p 00014000 08:01 3825825    /lib/libz.so.1.2.3.3
b7d8d000-b7d8f000 r-xp 00000000 08:01 3843294    /lib/tls/i686/cmov/libdl-2.9.so
b7d8f000-b7d90000 r--p 00001000 08:01 3843294    /lib/tls/i686/cmov/libdl-2.9.so
b7d90000-b7d91000 rw-p 00002000 08:01 3843294    /lib/tls/i686/cmov/libdl-2.9.so
b7d91000-b7eed000 r-xp 00000000 08:01 3843288    /lib/tls/i686/cmov/libc-2.9.so
b7eed000-b7eee000 ---p 0015c000 08:01 3843288    /lib/tls/i686/cmov/libc-2.9.so
b7eee000-b7ef0000 r--p 0015c000 08:01 3843288    /lib/tls/i686/cmov/libc-2.9.so
b7ef0000-b7ef1000 rw-p 0015e000 08:01 3843288    /lib/tls/i686/cmov/libc-2.9.so
b7ef1000-b7ef5000 rw-p b7ef1000 00:00 0 
b7ef5000-b8028000 r-xp 00000000 08:01 3826074    /lib/i686/cmov/libcrypto.so.0.9.8
b8028000-b8030000 r--p 00132000 08:01 3826074    /lib/i686/cmov/libcrypto.so.0.9.8
b8030000-b803d000 rw-p 0013a000 08:01 3826074    /lib/i686/cmov/libcrypto.so.0.9.8
b803d000-b8041000 rw-p b803d000 00:00 0 
b8041000-b8070000 r-xp 00000000 08:01 3680527    /usr/lib/libpcap.so.1.0.0
b8070000-b8071000 r--p 0002e000 08:01 3680527    /usr/lib/libpcap.so.1.0.0
b8071000-b8072000 rw-p 0002f000 08:01 3680527    /usr/lib/libpcap.so.1.0.0
b8074000-b8081000 r-xp 00000000 08:01 3825729    /lib/libgcc_s.so.1
b8081000-b8082000 r--p 0000c000 08:01 3825729    /lib/libgcc_s.so.1
b8082000-b8083000 rw-p 0000d000 08:01 3825729    /lib/libgcc_s.so.1
b8083000-b8087000 rw-p b8083000 00:00 0 
b8087000-b8088000 r-xp b8087000 00:00 0          [vdso]
b8088000-b80a4000 r-xp 00000000 08:01 3825687    /lib/ld-2.9.so
b80a4000-b80a5000 r--p 0001b000 08:01 3825687    /lib/ld-2.9.so
b80a5000-b80a6000 rw-p 0001c000 08:01 3825687    /lib/ld-2.9.so
bf891000-bf8a6000 rw-p bffeb000 00:00 0          [stack]
Aborted
glyph@glyphtop:~/Desktop/cowpatty-4.2$ 
```

---

