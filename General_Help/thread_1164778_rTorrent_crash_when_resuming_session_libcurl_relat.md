---
title: "rTorrent crash when resuming session: libcurl related"
date: 2009-05-20
forum: General Help
---

### Post by Hortinstein on 2009-05-20
Im running Ubuntu 9.04 with rtorrent install from the repos (.82 i think) and I have rtorrent configured to resume sessions since I seed for private ratio watched torrent sites.  

I get a crash when starting up most of the time that is (apologize for formatting): 

```
** glibc detected *** rtorrent: double free or corruption (fasttop): 0x0a99e240 ***
                                                                                   ======= Backtrace: =========
                                                                                                               /lib/tls/i686/cmov/libc.so.6[0xb7944604]
                                                                                                                                                       /lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb79465b6]
                                              /usr/lib/libcurl.so.4[0xb7f6b3d4]
                                                                               /usr/lib/libcurl.so.4[0xb7f62440]
                                                                                                                /usr/lib/libcurl.so.4[0xb7f6ed00]
                                                                                                                                                 /usr/lib/libcurl.so.4[0xb7f8162d]
                     /usr/lib/libcurl.so.4(curl_multi_perform+0x59)[0xb7f81979]
                                                                               rtorrent[0x80c0de1]
                                                                                                  rtorrent[0x80ba9b4]
                                                                                                                     rtorrent[0x807b035]
                                                                                                                                        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb78eb775]
                                           rtorrent(_ZNSt8ios_base4InitD1Ev+0x71)[0x80530a1]
                                                                                            ======= Memory map: ========
                                                                                                                        08048000-08111000 r-xp 00000000 08:01 8907650    /usr/bin/rtorrent
                             08111000-08113000 rw-p 000c8000 08:01 8907650    /usr/bin/rtorrent
                                                                                               08113000-08114000 rw-p 08113000 00:00 0 
                                                                                                                                       09a6c000-0ad09000 rw-p 09a6c000 00:00 0          [heap]
                                 b7300000-b7321000 rw-p b7300000 00:00 0 
                                                                         b7321000-b7400000 ---p b7321000 00:00 0 
                                                                                                                 b7482000-b7487000 r-xp 00000000 08:01 1360282    /lib/tls/i686/cmov/libnss_dns-2.9.so
                                         b7487000-b7488000 r--p 00004000 08:01 1360282    /lib/tls/i686/cmov/libnss_dns-2.9.so
                                                                                                                              b7488000-b7489000 rw-p 00005000 08:01 1360282    /lib/tls/i686/cmov/libnss_dns-2.9.so
                                                      b7489000-b748b000 r-xp 00000000 08:01 1335391    /lib/libnss_mdns4_minimal.so.2
                                                                                                                                     b748b000-b748c000 rw-p 00001000 08:01 1335391    /lib/libnss_mdns4_minimal.so.2
                                                       b748c000-b7496000 r-xp 00000000 08:01 1360284    /lib/tls/i686/cmov/libnss_files-2.9.so
                                                                                                                                              b7496000-b7497000 r--p 00009000 08:01 1360284    /lib/tls/i686/cmov/libnss_files-2.9.so
                                                                        b7497000-b7498000 rw-p 0000a000 08:01 1360284    /lib/tls/i686/cmov/libnss_files-2.9.so
  b74a9000-b761b000 rw-p b74a9000 00:00 0 
                                          b761b000-b765a000 r--p 00000000 08:01 8938333    /usr/lib/locale/en_CA.utf8/LC_CTYPE
                                                                                                                              b765a000-b7745000 r--p 00000000 08:01 8938332    /usr/lib/locale/en_CA.utf8/LC_COLLATE
                                                       b7745000-b7747000 rw-p b7745000 00:00 0 
                                                                                               b7747000-b774a000 r-xp 00000000 08:01 1335365    /lib/libgpg-error.so.0.3.0
             b774a000-b774b000 rw-p 00002000 08:01 1335365    /lib/libgpg-error.so.0.3.0
                                                                                        b774b000-b774c000 rw-p b774b000 00:00 0 
                                                                                                                                b774c000-b774e000 r-xp 00000000 08:01 1335370    /lib/libkeyutils-1.2.so
                                           b774e000-b774f000 r--p 00001000 08:01 1335370    /lib/libkeyutils-1.2.so
                                                                                                                   b774f000-b7750000 rw-p 00002000 08:01 1335370    /lib/libkeyutils-1.2.so
                              b7750000-b7757000 r-xp 00000000 08:01 8906889    /usr/lib/libkrb5support.so.0.1
                                                                                                             b7757000-b7758000 r--p 00006000 08:01 8906889    /usr/lib/libkrb5support.so.0.1
                               b7758000-b7759000 rw-p 00007000 08:01 8906889    /usr/lib/libkrb5support.so.0.1
                                                                                                              b7759000-b77bf000 r-xp 00000000 08:01 1335363    /lib/libgcrypt.so.11.4.4
                          b77bf000-b77c0000 r--p 00065000 08:01 1335363    /lib/libgcrypt.so.11.4.4
                                                                                                   b77c0000-b77c2000 rw-p 00066000 08:01 1335363    /lib/libgcrypt.so.11.4.4
               b77c2000-b77d2000 r-xp 00000000 08:01 8907180    /usr/lib/libtasn1.so.3.0.16
                                                                                           b77d2000-b77d3000 r--p 0000f000 08:01 8907180    /usr/lib/libtasn1.so.3.0.16
          b77d3000-b77d4000 rw-p 00010000 08:01 8907180    /usr/lib/libtasn1.so.3.0.16
                                                                                      b77d4000-b77d5000 rw-p b77d4000 00:00 0 
                                                                                                                              b77d5000-b786c000 r-xp 00000000 08:01 8906696    /usr/lib/libgnutls.so.26.4.6
                                              b786c000-b7871000 r--p 00097000 08:01 8906696    /usr/lib/libgnutls.so.26.4.6
                                                                                                                           b7871000-b7872000 rw-p 0009c000 08:01 8906696    /usr/lib/libgnutls.so.26.4.6
                                           b7872000-b7884000 r-xp 00000000 08:01 1360295    /lib/tls/i686/cmov/libresolv-2.9.so
                                                                                                                               b7884000-b7885000 r--p 00011000 08:01 1360295    /lib/tls/i686/cmov/libresolv-2.9.so
                                                      b7885000-b7886000 rw-p 00012000 08:01 1360295    /lib/tls/i686/cmov/libresolv-2.9.so
                                                                                                                                          b7886000-b7888000 rw-p b7886000 00:00 0 
                     b7888000-b789e000 r-xp 00000000 08:01 8907115    /usr/lib/libsasl2.so.2.0.22
                                                                                                 b789e000-b789f000 r--p 00015000 08:01 8907115    /usr/lib/libsasl2.so.2.0.22
                b789f000-b78a0000 rw-p 00016000 08:01 8907115    /usr/lib/libsasl2.so.2.0.22
                                                                                            b78a0000-b78a7000 r-xp 00000000 08:01 1360297    /lib/tls/i686/cmov/librt-2.9.so
               b78a7000-b78a8000 r--p 00006000 08:01 1360297    /lib/tls/i686/cmov/librt-2.9.so
                                                                                               b78a8000-b78a9000 rw-p 00007000 08:01 1360297    /lib/tls/i686/cmov/librt-2.9.so
                  b78a9000-b78b5000 r-xp 00000000 08:01 8906893    /usr/lib/liblber-2.4.so.2.4.1
                                                                                                b78b5000-b78b6000 r--p 0000b000 08:01 8906893    /usr/lib/liblber-2.4.so.2.4.1
                 b78b6000-b78b7000 rw-p 0000c000 08:01 8906893    /usr/lib/liblber-2.4.so.2.4.1
                                                                                               b78b7000-b78b9000 r-xp 00000000 08:01 1360273    /lib/tls/i686/cmov/libdl-2.9.so
                  b78b9000-b78ba000 r--p 00001000 08:01 1360273  Aborted

```


If you guys could help that would be awesome

---

### Post by stoof on 2009-06-14
I'm having the same problem. Running 0.8.2/0.12.2 with ~160 torrents, 80-800MB each.

Not sure it's related specifically to resuming session tho', it just randomly crashes. Sometimes I can have it running for days, sometimes it crashes just moments after starting it, and then again just after restarting it. Very annoying. I wonder if it has something to do with not being the latest version. I'm not sure about upgrading to newer version than what's in the repos, would that be a problem?

Any help is greatly appreciated!

---

### Post by FarmCretin on 2009-12-09
sorry to dig up an old post, but im also having this issue and i still cant find the solution.

---

