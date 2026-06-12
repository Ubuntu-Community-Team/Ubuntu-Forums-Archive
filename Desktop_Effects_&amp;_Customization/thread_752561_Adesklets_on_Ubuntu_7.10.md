---
title: "Adesklets on Ubuntu 7.10"
date: 2008-04-11
forum: Desktop Effects &amp; Customization
---

### Post by ENigma885 on 2008-04-11
I'm a 6 month Ubuntu user...and actually i'm facing some problems installing and configuring my applications,but it's getting better everyday :)
One of these problems is installing Adesklets 0. 6.1 on Ubuntu 7.10  (GNOME desktop environment)
i installed it from Synaptic Package Manager , i launched adesklets_installer chose Calender,i launched Calendar.py from the .desklets folder in my Home Folder and i got this ```
melancholia@Melancholia:~$ '/home/melancholia/.desklets/Calendar-0.5.3/Calendar.py' --nautilus
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
*** glibc detected *** adesklets: double free or corruption (out): 0x08087de0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7c53d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7c57800]
/usr/lib/libfontconfig.so.1(FcStrFree+0x3d)[0xb7d4d5cd]
/usr/lib/libfontconfig.so.1[0xb7d4b783]
/usr/lib/libfontconfig.so.1(FcPatternDestroy+0x71)[0xb7d4b951]
/usr/lib/libfontconfig.so.1(FcFontSetDestroy+0x31)[0xb7d45201]
adesklets[0x80578c8]
adesklets[0x804e32d]
adesklets[0x804cb3f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7c00050]
adesklets(rl_filename_completion_function+0x5d9)[0x804ca91]
======= Memory map: ========
08048000-08064000 r-xp 00000000 08:07 857525     /usr/local/bin/adesklets
08064000-08065000 rw-p 0001b000 08:07 857525     /usr/local/bin/adesklets
08065000-080a7000 rw-p 08065000 00:00 0          [heap]
b7900000-b7921000 rw-p b7900000 00:00 0 
b7921000-b7a00000 ---p b7921000 00:00 0 
b7a05000-b7a0f000 r-xp 00000000 08:07 716739     /lib/libgcc_s.so.1
b7a0f000-b7a10000 rw-p 0000a000 08:07 716739     /lib/libgcc_s.so.1
b7a28000-b7a2a000 r--s 00000000 08:07 852352     /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86.cache-2
b7a2a000-b7a30000 r--s 00000000 08:07 852351     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b7a30000-b7a33000 r--s 00000000 08:07 852348     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b7a33000-b7a34000 r--s 00000000 08:07 852342     /var/cache/fontconfig/5bc99d13c41710fd4d04a3be3075ea0a-x86.cache-2
b7a34000-b7a38000 r--s 00000000 08:07 852341     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b7a38000-b7a39000 r--s 00000000 08:07 852340     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b7a39000-b7a3a000 r--s 00000000 08:07 852336     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b7a3a000-b7a3d000 r--s 00000000 08:07 852335     /var/cache/fontconfig/062808c12e6e608270f93bb230aed730-x86.cache-2
b7a3d000-b7a40000 r--s 00000000 08:07 852287     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b7a40000-b7a41000 r--s 00000000 08:07 852284     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b7a41000-b7a42000 r--s 00000000 08:07 852283     /var/cache/fontconfig/32fc3cbe01df6a30798854a2c93eb444-x86.cache-2
b7a42000-b7a48000 r--s 00000000 08:07 852280     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b7a48000-b7a4a000 r--s 00000000 08:07 852279     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b7a4a000-b7a52000 r--s 00000000 08:07 852278     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b7a52000-b7a58000 r--s 00000000 08:07 847187     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b7a58000-b7a59000 r--s 00000000 08:07 847185     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b7a59000-b7a70000 r--s 00000000 08:07 848977     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b7a70000-b7a72000 r--s 00000000 08:07 847184     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b7a72000-b7a78000 r--s 00000000 08:07 847186     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b7a78000-b7a7c000 r--s 00000000 08:07 852266     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b7a7c000-b7a83000 r--s 00000000 08:07 852374     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b7a83000-b7a84000 r--s 00000000 08:07 852371     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b7a84000-b7a85000 r--s 00000000 08:07 852269     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b7a85000-b7a86000 r--s 00000000 08:07 848986     /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b7a86000-b7a89000 r--s 00000000 08:07 852372     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b7a89000-b7a8c000 r--s 00000000 08:07 848988     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b7a8c000-b7a93000 r--s 00000000 08:07 856913     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b7a93000-b7a95000 r--s 00000000 08:07 848985     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b7a95000-b7a96000 r--s 00000000 08:07 852375     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b7a96000-b7a97000 r--s 00000000 08:07 848983     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b7a97000-b7a98000 r--s 00000000 08:07 852263     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b7a98000-b7a9d000 r--s 00000000 08:07 852376     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b7a9d000-b7aa2000 r--s 00000000 08:07 847241     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b7aa2000-b7aa4000 r--s 00000000 08:07 848989     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b7aa4000-b7aa8000 r--s 00000000 08:07 852262     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b7aa8000-b7aa9000 r--s 00000000 08:07 848981     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b7aa9000-b7aaa000 r--s 00000000 08:07 848982     /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b7aaa000-b7aab000 r--s 00000000 08:07 852275     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b7aab000-b7aaf000 r--s 00000000 08:07 852363     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b7aaf000-b7ab5000 r--s 00000000 08:07 852361     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b7ab5000-b7abe000 r-xp 00000000 08:07 716725     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7abe000-b7ac0000 rw-p 00008000 08:07 716725     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7ac0000-b7ac8000 r-xp 00000000 08:07 716732     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7ac8000-b7aca000 rw-p 00007000 08:07 716732     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7aca000-b7ade000 r-xp 00000000 08:07 716718     /lib/tls/i686/cmov/libnsl-2.6.1.so
b7ade000-b7ae0000 rw-p 00013000 08:07 716718     /lib/tls/i686/cmov/libnsl-2.6.1.so
b7ae0000-b7ae2000 rw-p b7ae0000 00:00 0 
b7ae2000-b7ae9000 r-xp 00000000 08:07 716719     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7ae9000-b7aeb000 rw-p 00006000 08:07 716719     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7aeb000-b7aec000 rw-p b7aeb000 00:00 0 
b7aec000-b7b00000 r-xp 00000000 08:07 716749     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7b00000-b7b02000 rw-p 00013000 08:07 716749     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7b02000-b7b04000 rw-p b7b02000 00:00 0 
b7b04000-b7b22000 r-xp 00000000 08:07 702195     /usr/lib/libexpat.so.1.0.0
b7b22000-b7b24000 rw-p 0001e000 08:07 702195     /usr/lib/libexpat.so.1.0.0
b7b24000-b7b25000 rw-p b7b24000 00:00 0 
b7b25000-b7b32000 r-xp 00000000 08:07 702008     /usr/lib/libXext.so.6.4.0
b7b32000-b7b33000 rw-p 0000d000 08:07 702008     /usr/lib/libXext.so.6.4.0
b7b33000-b7b47000 r-xp 00000000 08:07 702771     /usr/lib/libz.so.1.2.3.3
b7b47000-b7b48000 rw-p 00013000 08:07 702771     /usr/lib/libz.so.1.2.3.3
b7b48000-b7bb4000 r-xp 00000000 08:07 702209     /usr/lib/libfreetype.so.6.3.16
b7bb4000-b7bb8000 rw-p 0006b000 08:07 702209     /usr/lib/libfreetype.so.6.3.16
b7bb8000-b7bba000 r-xp 00000000 08:07 716700     /lib/tls/i686/cmov/libdl-2.6.1.so
b7bba000-b7bbc000 rw-p 00001000 08:07 716700     /lib/tls/i686/cmov/libdl-2.6.1.so
b7bbc000-b7bc0000 r-xp 00000000 08:07 702004     /usr/lib/libXdmcp.so.6.0.0
b7bc0000-b7bc1000 rw-p 00003000 08:07 702004     /usr/lib/libXdmcp.so.6.0.0
b7bc1000-b7bc2000 rw-p b7bc1000 00:00 0 
b7bc2000-b7bc4000 r-xp 00000000 08:07 701993     /usr/lib/libXau.so.6.0.0
b7bc4000-b7bc5000 rw-p 00001000 08:07 701993     /usr/lib/libXau.so.6.0.0
b7bc5000-b7be8000 r-xp 00000000 08:07 716712     /lib/tls/i686/cmov/libm-2.6.1.so
b7be8000-b7bea000 rw-p 00023000 08:07 716712     /lib/tls/i686/cmov/libm-2.6.1.so
b7bea000-b7d2e000 r-xp 00000000 08:07 716695     /lib/tls/i686/cmov/libc-2.6.1.so
b7d2e000-b7d2f000 r--p 00143000 08:07 716695     /lib/tls/i686/cmov/libc-2.6.1.so
b7d2f000-b7d31000 rw-p 00144000 08:07 716695     /lib/tls/i686/cmov/libc-2.6.1.so
b7d31000-b7d34000 rw-p b7d31000 00:00 0 
b7d34000-b7d57000 r-xp 00000000 08:07 702201     /usr/lib/libfontconfig.so.1.2.0
b7d57000-b7d5f000 rw-p 00023000 08:07 702201     /usr/lib/libfontconfig.so.1.2.0
b7d5f000-b7d66000 r-xp 00000000 08:07 716743     /lib/libhistory.so.5.2
b7d66000-b7d67000 rw-p 00006000 08:07 716743     /lib/libhistory.so.5.2
b7d67000-b7d93000 r-xp 00000000 08:07 716791     /lib/libreadline.so.5.2
b7d93000-b7d97000 rw-p 0002c000 08:07 716791     /lib/libreadline.so.5.2
b7d97000-b7d99000 rw-p b7d97000 00:00 0 
b7d99000-b7dd5000 r-xp 00000000 08:07 716751     /lib/libncurses.so.5.6
b7dd5000-b7ddd000 rw-p 0003b000 08:07 716751     /lib/libncurses.so.5.6
b7ddd000-b7e29000 r-xp 00000000 08:07 706892     /usr/lib/libImlib2.so.1.3.0
b7e29000-b7e2a000 rw-p 0004c000 08:07 706892     /usr/lib/libImlib2.so.1.3.0
b7e2a000-b7e3e000 rw-p b7e2a000 00:00 0 
b7e3e000-b7f2b000 r-xp 00000000 08:07 701987     /usr/lib/libX11.so.6.2.0
b7f2b000-b7f2f000 rw-p 000ed000 08:07 701987     /usr/lib/libX11.so.6.2.0
b7f2f000-b7f30000 r--s 00000000 08:07 848987     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7f30000-b7f38000 r--s 00000000 08:07 847248     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b7f38000-b7f3d000 r--s 00000000 08:07 847369     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b7f3d000-b7f41000 r--s 00000000 08:07 847367     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b7f41000-b7f46000 r--s 00000000 08:07 852356     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b7f46000-b7f47000 r--s 00000000 08:07 40055      /home/melancholia/.fontconfig/d7ef6eb20062954f4ab16387feac279d-x86.cache-2
b7f47000-b7f49000 rw-p b7f47000 00:00 0 
b7f49000-b7f63000 r-xp 00000000 08:07 716685     /lib/ld-2.6.1.so
b7f63000-b7f65000 rw-p 00019000 08:07 716685     /lib/ld-2.6.1.so
bfde4000-bfdfa000 rw-p bfde4000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Traceback (most recent call last):
  File "/home/melancholia/.desklets/Calendar-0.5.3/Calendar.py", line 14, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 43, in <module>
    raise e
adesklets.error_handler.ADESKLETSError: adesklets process exited - 
Exception exceptions.AttributeError: AttributeError("'NoneType' object has no attribute 'kill'",) in <bound method _Communicator.__del__ of <adesklets.communicator._Communicator instance at 0x825b2ec>> ignored  
```

i tried to google the problem ,some ppl say it's a Python 2.5 incompatibility issue with Adesklets (i'm using Python 2.5.1) and i got  dozens of codes and workarounds  , tried many of them and nothing worked ...
- I know there's gDesklets as an alternative but 
Do u have any suggestions ??

- I know there's gDesklets as an alternative-

---

