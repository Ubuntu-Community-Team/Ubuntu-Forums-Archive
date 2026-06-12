---
title: "error after installing adesklet"
date: 2008-01-07
forum: Desktop Effects &amp; Customization
---

### Post by olymp on 2008-01-07
hi,
i'm try to run adesklet on my ubuntu Gusty. I follow the instructions and installed core without any errors, but when I run any desklet return an error :

[HTML]python cpu_meter.py
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
*** glibc detected *** adesklets: double free or corruption (out): 0x08084288 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7c17d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7c1b800]
/usr/lib/libfontconfig.so.1(FcStrFree+0x3d)[0xb7d115cd]
/usr/lib/libfontconfig.so.1[0xb7d0f783]
/usr/lib/libfontconfig.so.1(FcPatternDestroy+0x71)[0xb7d0f951]
/usr/lib/libfontconfig.so.1(FcFontSetDestroy+0x31)[0xb7d09201]
adesklets[0x80578c8]
adesklets[0x804e32d]
adesklets[0x804cb3f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7bc4050]
adesklets(rl_filename_completion_function+0x5d9)[0x804ca91]
======= Memory map: ========
08048000-08064000 r-xp 00000000 08:01 2412667    /usr/local/bin/adesklets
08064000-08065000 rw-p 0001b000 08:01 2412667    /usr/local/bin/adesklets
08065000-080a1000 rw-p 08065000 00:00 0          [heap]
b7900000-b7921000 rw-p b7900000 00:00 0 
b7921000-b7a00000 ---p b7921000 00:00 0 
b7a00000-b7a0a000 r-xp 00000000 08:01 2555971    /lib/libgcc_s.so.1
b7a0a000-b7a0b000 rw-p 0000a000 08:01 2555971    /lib/libgcc_s.so.1
b7a1c000-b7a22000 r--s 00000000 08:01 3948619    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b7a22000-b7a25000 r--s 00000000 08:01 3948633    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b7a25000-b7a29000 r--s 00000000 08:01 3948616    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b7a29000-b7a2a000 r--s 00000000 08:01 3948626    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b7a2a000-b7a2b000 r--s 00000000 08:01 3948606    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b7a2b000-b7a2e000 r--s 00000000 08:01 3948621    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b7a2e000-b7a2f000 r--s 00000000 08:01 3948612    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b7a2f000-b7a32000 r--s 00000000 08:01 3948610    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b7a32000-b7a34000 r--s 00000000 08:01 3948630    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b7a34000-b7a3c000 r--s 00000000 08:01 3948634    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b7a3c000-b7a42000 r--s 00000000 08:01 3948598    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b7a42000-b7a43000 r--s 00000000 08:01 3948604    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b7a43000-b7a45000 r--s 00000000 08:01 3948631    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b7a45000-b7a4b000 r--s 00000000 08:01 3948628    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b7a4b000-b7a4f000 r--s 00000000 08:01 3948596    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b7a4f000-b7a51000 r--s 00000000 08:01 3950675    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b7a51000-b7a52000 r--s 00000000 08:01 3948638    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b7a52000-b7a53000 r--s 00000000 08:01 3948635    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b7a53000-b7a54000 r--s 00000000 08:01 3948625    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b7a54000-b7a57000 r--s 00000000 08:01 3948623    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b7a57000-b7a5a000 r--s 00000000 08:01 3948639    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b7a5a000-b7a5c000 r--s 00000000 08:01 3948595    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b7a5c000-b7a5d000 r--s 00000000 08:01 3948636    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b7a5d000-b7a5e000 r--s 00000000 08:01 3948600    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b7a5e000-b7a5f000 r--s 00000000 08:01 3948620    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b7a5f000-b7a64000 r--s 00000000 08:01 3948615    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b7a64000-b7a69000 r--s 00000000 08:01 3948597    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b7a69000-b7a6b000 r--s 00000000 08:01 3948613    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b7a6b000-b7a6e000 r--s 00000000 08:01 3948607    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b7a6e000-b7a6f000 r--s 00000000 08:01 3948632    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b7a6f000-b7a70000 r--s 00000000 08:01 3948603    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b7a70000-b7a73000 r--s 00000000 08:01 3948601    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b7a73000-b7a79000 r--s 00000000 08:01 3948599    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b7a79000-b7a82000 r-xp 00000000 08:01 2589980    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7a82000-b7a84000 rw-p 00008000 08:01 2589980    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7a84000-b7a8c000 r-xp 00000000 08:01 2589984    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7a8c000-b7a8e000 rw-p 00007000 08:01 2589984    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7a8e000-b7aa2000 r-xp 00000000 08:01 2589974    /lib/tls/i686/cmov/libnsl-2.6.1.so
b7aa2000-b7aa4000 rw-p 00013000 08:01 2589974    /lib/tls/i686/cmov/libnsl-2.6.1.so
b7aa4000-b7aa6000 rw-p b7aa4000 00:00 0 
b7aa6000-b7aad000 r-xp 00000000 08:01 2589976    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7aad000-b7aaf000 rw-p 00006000 08:01 2589976    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7aaf000-b7ab0000 rw-p b7aaf000 00:00 0 
b7ab0000-b7ac4000 r-xp 00000000 08:01 2589989    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7ac4000-b7ac6000 rw-p 00013000 08:01 2589989    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7ac6000-b7ac8000 rw-p b7ac6000 00:00 0 
b7ac8000-b7ae6000 r-xp 00000000 08:01 2229746    /usr/lib/libexpat.so.1.0.0
b7ae6000-b7ae8000 rw-p 0001e000 08:01 2229746    /usr/lib/libexpat.so.1.0.0
b7ae8000-b7ae9000 rw-p b7ae8000 00:00 0 
b7ae9000-b7af6000 r-xp 00000000 08:01 2229559    /usr/lib/libXext.so.6.4.0
b7af6000-b7af7000 rw-p 0000d000 08:01 2229559    /usr/lib/libXext.so.6.4.0
b7af7000-b7b0b000 r-xp 00000000 08:01 2230322    /usr/lib/libz.so.1.2.3.3
b7b0b000-b7b0c000 rw-p 00013000 08:01 2230322    /usr/lib/libz.so.1.2.3.3
b7b0c000-b7b78000 r-xp 00000000 08:01 2229760    /usr/lib/libfreetype.so.6.3.16
b7b78000-b7b7c000 rw-p 0006b000 08:01 2229760    /usr/lib/libfreetype.so.6.3.16
b7b7c000-b7b7e000 r-xp 00000000 08:01 2589969    /lib/tls/i686/cmov/libdl-2.6.1.so
b7b7e000-b7b80000 rw-p 00001000 08:01 2589969    /lib/tls/i686/cmov/libdl-2.6.1.so
b7b80000-b7b84000 r-xp 00000000 08:01 2229555    /usr/lib/libXdmcp.so.6.0.0
b7b84000-b7b85000 rw-p 00003000 08:01 2229555    /usr/lib/libXdmcp.so.6.0.0
b7b85000-b7b86000 rw-p b7b85000 00:00 0 
b7b86000-b7b88000 r-xp 00000000 08:01 2229544    /usr/lib/libXau.so.6.0.0
b7b88000-b7b89000 rw-p 00001000 08:01 2229544    /usr/lib/libXau.so.6.0.0
b7b89000-b7bac000 r-xp 00000000 08:01 2589971    /lib/tls/i686/cmov/libm-2.6.1.so
b7bac000-b7bae000 rw-p 00023000 08:01 2589971    /lib/tls/i686/cmov/libm-2.6.1.so
b7bae000-b7cf2000 r-xp 00000000 08:01 2589963    /lib/tls/i686/cmov/libc-2.6.1.so
b7cf2000-b7cf3000 r--p 00143000 08:01 2589963    /lib/tls/i686/cmov/libc-2.6.1.so
b7cf3000-b7cf5000 rw-p 00144000 08:01 2589963    /lib/tls/i686/cmov/libc-2.6.1.so
b7cf5000-b7cf8000 rw-p b7cf5000 00:00 0 
b7cf8000-b7d1b000 r-xp 00000000 08:01 2229752    /usr/lib/libfontconfig.so.1.2.0
b7d1b000-b7d23000 rw-p 00023000 08:01 2229752    /usr/lib/libfontconfig.so.1.2.0
b7d23000-b7d2a000 r-xp 00000000 08:01 2555975    /lib/libhistory.so.5.2
b7d2a000-b7d2b000 rw-p 00006000 08:01 2555975    /lib/libhistory.so.5.2
b7d2b000-b7d57000 r-xp 00000000 08:01 2556023    /lib/libreadline.so.5.2
b7d57000-b7d5b000 rw-p 0002c000 08:01 2556023    /lib/libreadline.so.5.2
b7d5b000-b7d5d000 rw-p b7d5b000 00:00 0 
b7d5d000-b7d99000 r-xp 00000000 08:01 2555983    /lib/libncurses.so.5.6
b7d99000-b7da1000 rw-p 0003b000 08:01 2555983    /lib/libncurses.so.5.6
b7da1000-b7ded000 r-xp 00000000 08:01 2231652    /usr/lib/libImlib2.so.1.3.0
b7ded000-b7dee000 rw-p 0004c000 08:01 2231652    /usr/lib/libImlib2.so.1.3.0
b7dee000-b7e02000 rw-p b7dee000 00:00 0 
b7e02000-b7eef000 r-xp 00000000 08:01 2229538    /usr/lib/libX11.so.6.2.0
b7eef000-b7ef3000 rw-p 000ed000 08:01 2229538    /usr/lib/libX11.so.6.2.0
b7ef6000-b7ef7000 r--s 00000000 08:01 3948617    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7ef7000-b7efb000 r--s 00000000 08:01 3948622    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b7efb000-b7efd000 r--s 00000000 08:01 3948618    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b7efd000-b7f01000 r--s 00000000 08:01 3948624    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b7f01000-b7f04000 r--s 00000000 08:01 3948608    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b7f04000-b7f06000 rw-p b7f04000 00:00 0 
b7f06000-b7f20000 r-xp 00000000 08:01 2555924    /lib/ld-2.6.1.so
b7f20000-b7f22000 rw-p 00019000 08:01 2555924    /lib/ld-2.6.1.so
bfb22000-bfb37000 rw-p bfb22000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Traceback (most recent call last):
  File "cpu_meter.py", line 1, in <module>
    from circlemeter import *
  File "/home/penev/Desktop/desklets/CircleMeter/circlemeter.py", line 2, in <module>
    from adesklets.commands import *
  File "usr/lib/python2.5/site-packages/adesklets/__init__.py", line 43, in <module>
adesklets.error_handler.ADESKLETSError: adesklets process exited - 
Exception exceptions.AttributeError: AttributeError("'NoneType' object has no attribute 'kill'",) in <bound method _Communicator.__del__ of <adesklets.communicator._Communicator instance at 0xb7c87b8c>> ignored
penev@penev:~/Desktop/desklets/CircleMeter$ [/HTML]

Any ideas how to solve the problem?

---

