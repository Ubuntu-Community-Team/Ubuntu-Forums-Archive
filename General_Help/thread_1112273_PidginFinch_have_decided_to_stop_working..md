---
title: "Pidgin/Finch have decided to stop working."
date: 2009-03-31
forum: General Help
---

### Post by Unicow on 2009-03-31
I have both installed but prefer to use finch when I can. Just recently, though (the last hour or so) neither have been working and I'll be damned if I know why. Any insight would be appreciated.

Output of terminal using 'pidgin':

```
*** glibc detected *** pidgin: double free or corruption (fasttop): 0x085f3ec8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7623a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb76274f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7784b81]
/usr/lib/libpurple.so.0[0xb789e75b]
/usr/lib/libpurple.so.0(purple_proxy_get_setup+0x92)[0xb78a2251]
/usr/lib/libpurple.so.0(purple_proxy_connect+0x10f)[0xb78a259f]
/usr/lib/purple-2/libmsn.so(msn_servconn_connect+0x18c)[0xb6442589]
/usr/lib/purple-2/libmsn.so(msn_notification_connect+0x78)[0xb643dcdb]
/usr/lib/purple-2/libmsn.so(msn_session_connect+0x10e)[0xb6443031]
/usr/lib/purple-2/libmsn.so[0xb6438da7]
/usr/lib/libpurple.so.0(purple_connection_new+0x308)[0xb787abc9]
/usr/lib/libpurple.so.0(purple_account_connect+0x1ae)[0xb785faea]
/usr/lib/libpurple.so.0(purple_accounts_restore_current_statuses+0x7c)[0xb78634f8]
pidgin(main+0xb89)[0x80c709a]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb75ce450]
pidgin[0x806c821]
======= Memory map: ========
08048000-08115000 r-xp 00000000 08:01 105334     /usr/bin/pidgin
08115000-08118000 rw-p 000cc000 08:01 105334     /usr/bin/pidgin
08118000-08611000 rw-p 08118000 00:00 0          [heap]
b5000000-b5021000 rw-p b5000000 00:00 0
b5021000-b5100000 ---p b5021000 00:00 0
b514f000-b51af000 rw-s 00000000 00:09 1310741    /SYSV00000000 (deleted)
b51af000-b52b3000 rw-p b51af000 00:00 0
b52b3000-b5330000 r--p 00000000 08:01 397325     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansCondensed-Bold.ttf
b5330000-b533f000 r--p 00000000 08:01 396841     /usr/share/fonts/truetype/ttf-bitstream-vera/VeraBd.ttf
b533f000-b5356000 r--s 00000000 08:01 50507      /var/lib/aspell/en_GB-ise-wo_accents-only.rws
b5356000-b536d000 r--s 00000000 08:01 50511      /var/lib/aspell/en_US-wo_accents-only.rws
b536d000-b55f5000 r--s 00000000 08:01 50499      /var/lib/aspell/en-common.rws
b55f5000-b55f7000 r-xp 00000000 08:01 309389     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b55f7000-b55f8000 rw-p 00001000 08:01 309389     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b55f8000-b5609000 r--p 00000000 08:01 396839     /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf
b5609000-b560f000 r--s 00000000 08:01 48685      /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b560f000-b5612000 r--s 00000000 08:01 48681      /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b5612000-b5613000 r--s 00000000 08:01 48680      /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b5613000-b5614000 r--s 00000000 08:01 48679      /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b5614000-b5617000 r--s 00000000 08:01 48678      /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b5617000-b561e000 r--s 00000000 08:01 52177      /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b561e000-b5621000 r--s 00000000 08:01 48676      /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b5621000-b5629000 r--s 00000000 08:01 48675      /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b5629000-b5631000 r--s 00000000 08:01 48674      /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b5631000-b5632000 r--s 00000000 08:01 48673      /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b5632000-b5654000 r--s 00000000 08:01 51010      /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b5654000-b566b000 r-xp 00000000 08:01 291580     /lib/libselinux.so.1
b566b000-b566d000 rw-p 00016000 08:01 291580     /lib/libselinux.so.1
b566d000-b567c000 r-xp 00000000 08:01 291493     /lib/libbz2.so.1.0.4
b567c000-b567d000 rw-p 0000f000 08:01 291493     /lib/libbz2.so.1.0.4
b567d000-b56dc000 r-xp 00000000 08:01 293241     /usr/lib/libgio-2.0.so.0.0.0
b56dc000-b56de000 rw-p 0005f000 08:01 293241     /usr/lib/libgio-2.0.so.0.0.0
b56de000-b5710000 r-xp 00000000 08:01 284844     /usr/lib/libcroco-0.6.so.3.0.1
b5710000-b5713000 rw-p 00031000 08:01 284844     /usr/lib/libcroco-0.6.so.3.0.1
b5713000-b5743000 r-xp 00000000 08:01 285104     /usr/lib/libgsf-1.so.114.0.7
b5743000-b5746000 rw-p 0002f000 08:01 285104     /usr/lib/libgsf-1.so.114.0.7
b5746000-b5747000 rw-p b5746000 00:00 0
b5747000-b5777000 r-xp 00000000 08:01 285432     /usr/lib/librsvg-2.so.2.22.2
b5777000-b5778000 rw-p 00030000 08:01 285432     /usr/lib/librsvg-2.so.2.22.2
b577e000-b5781000 r--s 00000000 08:01 48672      /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b5781000-b5788000 r--s 00000000 08:01 48671      /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b5788000-b5797000 r-xp 00000000 08:01 287070     /usr/lib/libgnomenu.so.0.0.0
b5797000-b5798000 rw-p 0000e000 08:01 287070     /usr/lib/libgnomenu.so.0.0.0
b5799000-b579f000 r--s 00000000 08:01 48670      /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b579f000-b57a1000 r--s 00000000 08:01 48664      /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b57a1000-b57a6000 r--s 00000000 08:01 48773Aborted
cow@professor:~$  
```

Finch returns:

```
                                                            b7270000-b7274000 r-xp 00000000 08:01 129546     /usr/lib/sasl2/libcrammd5.so.2.0.22
                                                                b7274000-b7275000 rw-p 00003000 08:01 129546     /usr/lib/sasl2/libcrammd5.so.2.0.22
                                                                    b7275000-b72ad000 r-xp 00000000 08:01 61709      /usr/lib/purple-2/libjabber.so.0.0.0
                                                                         b72ad000-b72ae000 rw-p 00038000 08:01 61709      /usr/lib/purple-2/libjabber.so.0.0.0
                                                                              b72ae000-b72b1000 rw-p b72ae000 00:00 0
                                      b72b1000-b72de000 r-xp 00000000 08:01 61711      /usr/lib/purple-2/libmsn.so
                                  b72de000-b72df000 rw-p 0002d000 08:01 61711      /usr/lib/purple-2/libmsn.so
                              b72df000-b72e2000 rw-p b72df000 00:00 0
                                                                      b72e2000-b72e4000 r-xp 00000000 08:01 291503     /lib/libcom_err.so.2.1
                                                             b72e4000-b72e5000 rw-p 00001000 08:01 291503     /lib/libcom_err.so.2.1
                                                    b72e5000-b7312000 r-xp 00000000 08:01 291535     /lib/libncurses.so.5.6
                                           b7312000-b7315000 rw-p 0002c000 08:01 291535     /lib/libncurses.soAborted
cow@professor:~$ 
```

---

