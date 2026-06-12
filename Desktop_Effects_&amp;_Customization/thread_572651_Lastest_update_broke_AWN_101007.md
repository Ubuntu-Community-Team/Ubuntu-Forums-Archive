---
title: "Lastest update broke AWN 10/10/07"
date: 2007-10-10
forum: Desktop Effects &amp; Customization
---

### Post by tcpip4lyfe on 2007-10-10
Anyone having problems with avant-window-navigator after the upgrade this morning?

After rebooting I get this dump when I try to start AWN. 

```
josh@josh-desktop:~$ avant-window-navigator

** (avant-window-navigator:10096): WARNING **: Failed to make connection to session bus: Failed to connect to socket /tmp/dbus-cEQTGVPQRk: Connection refused

** (avant-window-navigator:10096): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (avant-window-navigator:10096): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (avant-window-navigator:10096): WARNING **: There was an error requesting the name: \xe0\u0016\u001d\u0008_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
*** glibc detected *** avant-window-navigator: double free or corruption (!prev): 0x081d1e90 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7276d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb727a800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb74c2961]
/usr/lib/libglib-2.0.so.0(g_error_free+0x29)[0xb74ac469]
avant-window-navigator[0x804f4ce]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7223050]
avant-window-navigator[0x804e7f1]
======= Memory map: ========
08048000-08066000 r-xp 00000000 08:02 4784338    /usr/bin/avant-window-navigator
08066000-08067000 rw-p 0001d000 08:02 4784338    /usr/bin/avant-window-navigator
08067000-081ef000 rw-p 08067000 00:00 0          [heap]
b6a00000-b6a21000 rw-p b6a00000 00:00 0 
b6a21000-b6b00000 ---p b6a21000 00:00 0 
b6be4000-b6bee000 r-xp 00000000 08:02 2244615    /lib/libgcc_s.so.1
b6bee000-b6bef000 rw-p 0000a000 08:02 2244615    /lib/libgcc_s.so.1
b6c02000-b6c8e000 r--p 00000000 08:02 5213443    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6c8e000-b6c90000 r-xp 00000000 08:02 4852137    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6c90000-b6c91000 rw-p 00001000 08:02 4852137    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6c91000-b6c93000 r--s 00000000 08:02 1327263    /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86.cache-2
b6c93000-b6c99000 r--s 00000000 08:02 1327207    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6c99000-b6c9c000 r--s 00000000 08:02 1327260    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b6c9c000-b6c9d000 r--s 00000000 08:02 1327259    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b6c9d000-b6c9f000 r--s 00000000 08:02 1327258    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b6c9f000-b6ca0000 r--s 00000000 08:02 1327256    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b6ca0000-b6ca1000 r--s 00000000 08:02 1327255    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b6ca1000-b6ca5000 r--s 00000000 08:02 1327254    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6ca5000-b6ca6000 r--s 00000000 08:02 1327251    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b6ca6000-b6ca7000 r--s 00000000 08:02 1327250    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6ca7000-b6ca9000 r--s 00000000 08:02 1327248    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b6ca9000-b6cac000 r--s 00000000 08:02 1327247    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b6cac000-b6cae000 r--s 00000000 08:02 1327246    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b6cae000-b6caf000 r--s 00000000 08:02 1327245    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b6caf000-b6cb1000 r--s 00000000 08:02 1327244    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b6cb1000-b6cb7000 r--s 00000000 08:02 1327243    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6cb7000-b6cb9000 r--s 00000000 08:02 1327242    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6cb9000-b6cbb000 r--s 00000000 08:02 1327241    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b6cbb000-b6cc3000 r--s 00000000 08:02 1327240    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6cc3000-b6cc9000 r--s 00000000 08:02 1327239    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6cc9000-b6cca000 r--s 00000000 08:02 1327238    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6cca000-b6ccc000 r--s 00000000 08:02 1327237    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6ccc000-b6cd2000 r--s 00000000 08:02 1327236    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6cd2000-b6cd5000 r--s 00000000 08:02 1327235    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b6cd5000-b6cd9000 r--s 00000000 08:02 1327173    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6cd9000-b6ce0000 r--s 00000000 08:02 1327167    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6ce0000-b6ce1000 r--s 00000000 08:02 1327230    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b6ce1000-b6ce2000 r--s 00000000 08:02 1327229    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b6ce2000-b6ce5000 r--s 00000000 08:02 1327224    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b6ce5000-b6cea000 r--s 00000000 08:02 1327223    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b6cea000-b6ced000 r--s 00000000 08:02 1327221    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b6ced000-b6cee000 r--s 00000000 08:02 1327218    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b6cee000-b6cf0000 r--s 00000000 08:02 1327217    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b6cf0000-b6cf1000 r--s 00000000 08:02 1327216    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b6cf1000-b6cf6000 r--s 00000000 08:02 1327211    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b6cf6000-b6cfa000 r--s 00000000 08:02 1327199    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b6cfa000-b6cfc000 r--s 00000000 08:02 1327191    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b6cfc000-b6cff000 r--s 00000000 08:02 1327190    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b6cff000-b6d00000 r--s 00000000 08:02 1327189    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b6d00000-b6d02000 r--s 00000000 08:02 1327186    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b6d02000-b6d06000 r--s 00000000 08:02 1327162    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b6d06000-b6d0e000 r--s 00000000 08:02 1327159    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b6d0e000-b6d17000 r-xp 00000000 08:02 2245063    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b6d17000-b6d19000 rw-p 00008000 08:02 2245063    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b6d19000-b6d21000 r-xp 00000000 08:02 2245071    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b6d21000-b6d23000 rw-p 00007000 08:02 2245071    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b6d23000-b6d2a000 r-xp 00000000 08:02 2245030    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b6d2a000-b6d2c000 rw-p 00006000 08:02 2245030    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b6d2d000-b6d33000 r--s 00000000 08:02 1327161    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b6d33000-b6d35000 r--s 00000000 08:02 1327158    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6d35000-b6d39000 r--s 00000000 08:02 1327157    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6d39000-b6d3c000 r--s 00000000 08:02 1327155    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6d3c000-b6d3d000 r-xp 00000000 08:02 4790772    /usr/lib/gconv/ISO8859-1.so
b6d3d000-b6d3f000 rw-p 00000000 08:02 4790772    /usr/lib/gconv/ISO8859-1.so
b6d3f000-b6d7e000 r--p 00000000 08:02 4849978    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6d7e000-b6e5e000 r--p 00000000 08:02 4849983    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6e5e000-b6e62000 rw-p b6e5e000 00:00 0 
b6e62000-b6e98000 r-xp 00000000 08:02 2244667    /lib/libsepol.so.1
b6e98000-b6e99000 rw-p 00035000 08:02 2244667    /lib/libsepol.so.1
b6e99000-b6ea3000 rw-p b6e99000 00:00 0 
b6ea3000-b6ef2000 r-xp 00000000 08:02 4784898    /usr/lib/libgcrypt.so.11.2.3
b6ef2000-b6ef4000 rw-p 0004e000 08:02 4784898    /usr/lib/libgcrypt.so.11.2.3
b6ef4000-b6ef7000 r-xp 00000000 08:02 4784831    /usr/lib/libgpg-error.so.0.3.0
b6ef7000-b6ef8000 rw-p 00002000 08:02 4784831    /usr/lib/libgpg-error.so.0.3.0
b6ef8000-b6f07000 r-xp 00000000 08:02 4784922    /usr/lib/libtasn1.so.3.0.9
b6f07000-b6f08000 rw-p 0000e000 08:02 4784922    /usr/lib/libtasn1.so.3.0.9
b6f08000-b6fc9000 r-xp 00000000 08:02 4786274    /usr/lib/libasound.so.2.0.0
b6fc9000-b6fce000 rw-p 000c0000 08:02 4786274    /usr/lib/libasound.so.2.0.0
b6fce000-b6fcf000 rw-p b6fce000 00:00 0 
b6fcf000-b6fd3000 r-xp 00000000 08:02 4784515    /usr/lib/libXdmcp.so.6.0.0
b6fd3000-b6fd4000 rw-p 00003000 08:02 4784515    /usr/lib/libXdmcp.so.6.0.0
b6fd4000-b6ff6000 r-xp 00000000 08:02 4787717    /usr/lib/libpng12.so.0.15.0
b6ff6000-b6ff7000 rw-p 00021000 08:02 4787717    /usr/lib/libpng12.so.0.15.0
b6ff7000-b6ff9000 r-xp 00000000 08:02 4784413    /usr/lib/libXau.so.6.0.0
b6ff9000-b6ffa000 rw-p 00001000 08:02 4784413    /usr/lib/libXau.so.6.0.0
b6ffa000-b6ffb000 rw-p b6ffa000 00:00 0 
b6ffb000-b7019000 r-xp 00000000 08:02 3490208    /usr/lib/libexpat.so.1.0.0
b7019000-b701b000 rw-p 0001e000 08:02 3490208    /usr/lib/libexpat.so.1.0.0
b701b000-b7087000 r-xp 00000000 08:02 3490211    /usr/lib/libfreetype.so.6.3.16
b7087000-b708b000 rw-p 0006b000 08:02 3490211    /usr/lib/libfreetype.so.6.3.16
b708b000-b709f000 r-xp 00000000 08:02 3490050    /usr/lib/libz.so.1.2.3.3
b709f000-b70a0000 rw-p 00013000 08:02 3490050    /usr/lib/libz.so.1.2.3.3
b70a0000-b70b4000 r-xp 00000000 08:02 2245029    /lib/tls/i686/cmov/libnsl-2.6.1.so
b70b4000-b70b6000 rw-p 00013000 08:02 2245029    /lib/tls/i686/cmov/libnsl-2.6.1.so
b70b6000-b70b9000 rw-p b70b6000 00:00 0 
b70b9000-b70bb000 r-xp 00000000 08:02 2245080    /lib/tls/i686/cmov/libutil-2.6.1.so
b70bb000-b70bd000 rw-p 00001000 08:02 2245080    /lib/tls/i686/cmov/libutil-2.6.1.so
b70bd000-b70d1000 r-xp 00000000 08:02 2244668    /lib/libselinux.so.1
b70d1000-b70d3000 rw-p 00013000 08:02 2244668    /lib/libselinux.so.1
b70d3000-b70e2000 r-xp 00000000 08:02 2245076    /lib/tls/i686/cmov/libresolv-2.6.1.so
b70e2000-b70e4000 rw-p 0000f000 08:02 2245076    /lib/tls/i686/cmov/libresolv-2.6.1.so
b70e4000-b70e6000 rw-p b70e4000 00:00 0 
b70e6000-b70f4000 r-xp 00000000 08:02 4786612    /usr/lib/libavahi-client.so.3.2.2
b70f4000-b70f5000 rw-p 0000e000 08:02 4786612    /usr/lib/libavahi-client.so.3.2.2
b70f5000-b70ff000 r-xp 00000000 08:02 4784458    /usr/lib/libavahi-common.so.3.4.4
b70ff000-b7100000 rw-p 00009000 08:02 4784458    /usr/lib/libavahi-common.so.3.4.4
b7100000-b7101000 rw-p b7100000 00:00 0 
b7101000-b7103000 r-xp 00000000 08:02 4785200    /usr/lib/libavahi-glib.so.1.0.1
b7103000-b7104000 rw-p 00001000 08:02 4785200    /usr/lib/libavahi-glib.so.1.0.1
b7104000-b716e000 r-xp 00000000 08:02 4786382    /usr/lib/libgnutls.so.13.3.0
b716e000-b7174000 rw-p 0006a000 08:02 4786382    /usr/lib/libgnutls.so.13.3.0
b7174000-b7178000 r-xp 00000000 08:02 3490048    /usr/lib/libORBitCosNaming-2.so.0.1.0
b7178000-b7179000 rw-p 00003000 08:02 3490048    /usr/lib/libORBitCosNaming-2.so.0.1.0
b7179000-b7199000 r-xp 00000000 08:02 4785860    /usr/lib/libaudiofile.so.0.0.2
b7199000-b719b000 rw-p 00020000 08:02 4785860    /usr/lib/libaudiofile.so.0.0.2
b719b000-b71a4000 r-xp 00000000 08:02 4784636    /usr/lib/libesd.so.0.2.38
b71a4000-b71a5000 rw-p 00009000 08:02 4784636    /usr/lib/libesd.so.0.2.38
b71a5000-b71a6000 rw-p b71a5000 00:00 0 
b71a6000-b71d3000 r-xp 00000000 08:02 4784941    /usr/lib/libpangoft2-1.0.so.0.1800.2
b71d3000-b71d4000 rw-p 0002c000 08:02 4784941    /usr/lib/libpangoft2-1.0.so.0.1800.2
b71d4000-b71db000 r-xp 00000000 08:02 4785914    /usr/lib/libgailutil.so.18.0.1
b71db000-b71dc000 rw-p 00006000 08:02 4785914    /usr/lib/libgailutil.so.18.0.1
b71dc000-b71fb000 r-xp 00000000 08:02 4785385    /usr/lib/libjpeg.so.62.0.0
b71fb000-b71fc000 rw-p 0001e000 08:02 4785385    /usr/lib/libjpeg.so.62.0.0
b71fc000-b7209000 r-xp 00000000 08:02 4786104    /usr/lib/libgnome-keyring.so.0.1.1
b7209000-b720a000 rw-p 0000d000 08:02 4786104    /usr/lib/libgnome-keyring.so.0.1.1
b720a000-b720b000 rw-p b720a000 00:00 0 
b720b000-b720c000 r-xp 00000000 08:02 4785288    /usr/lib/libXRes.so.1.0.0
b720c000-b720d000 rw-p 00001000 08:02 4785288    /usr/lib/libXRes.so.1.0.0
b720d000-b7351000 r-xp 00000000 08:02 2244906    /lib/tls/i686/cmov/libc-2.6.1.so
b7351000-b7352000 r--p 00143000 08:02 2244906    /lib/tls/i686/cmov/libc-2.6.1.so
b7352000-b7354000 rw-p 00144000 08:02 2244906    /lib/tls/i686/cmov/libc-2.6.1.so
b7354000-b7357000 rw-p b7354000 00:00 0 
b7357000-b736b000 r-xp 00000000 08:02 2245075    /lib/tls/i686/cmov/libpthread-2.6.1.so
b736b000-b736d000 rw-p 00013000 08:02 2245075    /lib/tls/i686/cmov/libpthread-2.6.1.so
b736d000-b736f000 rw-p b736d000 00:00 0 
b736f000-b7386000 r-xp 00000000 08:02 4785771    /usr/lib/libawn.so.0.0.1
b7386000-b7387000 rw-p 00016000 08:02 4785771    /usr/lib/libawn.so.0.0.1
b7387000-b7474000 r-xp 00000000 08:02 4784354    /usr/lib/libX11.so.6.2.0
b7474000-b7478000 rw-p 000ed000 08:02 4784354    /usr/lib/libX11.so.6.2.0
b7478000-b7479000 rw-p b7478000 00:00 0 
b7479000-b7480000 r-xp 00000000 08:02 4784337    /usr/lib/libXrender.so.1.3.0
b7480000-b7481000 rw-p 00006000 08:02 4784337    /usr/lib/libXrender.so.1.3.0
b7481000-b7485000 r-xp 00000000 08:02 4785088    /usr/lib/libXfixes.so.3.1.0
b7485000-b7486000 rw-p 00003000 08:02 4785088    /usr/lib/libXfixes.so.3.1.0
b7486000-b7488000 r-xp 00000000 08:02 4785106    /usr/lib/libXcomposite.so.1.0.0
b7488000-b7489000 rw-p 00001000 08:02 4785106    /usr/lib/libXcomposite.so.1.0.0
b7489000-b748b000 r-xp 00000000 08:02 4784278    /usr/lib/libXdamage.so.1.1.0
b748b000-b748c000 rw-p 00001000 08:02 4784278    /usr/lib/libXdamage.so.1.1.0
b748c000-b7548000 r-xp 00000000 08:02 4784549    /usr/lib/libglib-2.0.so.0.1400.1
b7548000-b7549000 rw-p 000bc000 08:02 4784549    /usr/lib/libglib-2.0.so.0.1400.1
b7549000-b754b000 r-xp 00000000 08:02 2244909    /lib/tls/i686/cmov/libdl-2.6.1.so
b754b000-b754d000 rw-p 00001000 08:02 2244909    /lib/tls/i686/cmov/libdl-2.6.1.so
b754d000-b754e000 rw-p b754d000 00:00 0 
b754e000-b7551000 r-xp 00000000 08:02 4784814    /usr/lib/libgmodule-2.0.so.0.1400.1
b7551000-b7552000 rw-p 00002000 08:02 4784814    /usr/lib/libgmodule-2.0.so.0.1400.1
b7552000-b758c000 r-xp 00000000 08:02 4784870    /usr/lib/libgobject-2.0.so.0.1400.1
b758c000-b758d000 rw-p 0003a000 08:02 4784870    /usr/lib/libgobject-2.0.so.0.1400.1
b758d000-b7602000 r-xp 00000000 08:02 4784235    /usr/lib/libcairo.so.2.11.5
b7602000-b7604000 rw-p 00074000 08:02 4784235    /usr/lib/libcairo.so.2.11.5
b7604000-b763f000 r-xp 00000000 08:02 4784878    /usr/lib/libpango-1.0.so.0.1800.2
b763f000-b7641000 rw-p 0003b000 08:02 4784878    /usr/lib/libpango-1.0.so.0.1800.2
b7641000-b7649000 r-xp 00000000 08:02 4784647    /usr/lib/libXcursor.so.1.0.2
b7649000-b764a000 rw-p 00007000 08:02 4784647    /usr/lib/libXcursor.so.1.0.2
b764a000-b764f000 r-xp 00000000 08:02 4785648    /usr/lib/libXrandr.so.2.1.0
b764f000-b7650000 rw-p 00005000 08:02 4785648    /usr/lib/libXrandr.so.2.1.0
b7650000-b7657000 r-xp 00000000 08:02 4785083    /usr/lib/libXi.so.6.0.0
b7657000-b7658000 rw-p 00006000 08:02 4785083    /usr/lib/libXi.so.6.0.0
b7658000-b7659000 rw-p b7658000 00:00 0 
b7659000-b765b000 r-xp 00000000 08:02 4785112    /usr/lib/libXinerama.so.1.0.0
b765b000-b765c000 rw-p 00001000 08:02 4785112    /usr/lib/libXinerama.so.1.0.0
b765c000-b7669000 r-xp 00000000 08:02 4784488    /usr/lib/libXext.so.6.4.0
b7669000-b766a000 rw-p 0000d000 08:02 4784488    /usr/lib/libXext.so.6.4.0
b766a000-b768d000 r-xp 00000000 08:02 4784426    /usr/lib/libfontconfig.so.1.2.0
b768d000-b7695000 rw-p 00023000 08:02 4784426    /usr/lib/libfontconfig.so.1.2.0
b7695000-b769d000 r-xp 00000000 08:02 4784907    /usr/lib/libpangocairo-1.0.so.0.1800.2
b769d000-b769e000 rw-p 00007000 08:02 4784907    /usr/lib/libpangocairo-1.0.so.0.1800.2
b769e000-b76c1000 r-xp 00000000 08:02 2244910    /lib/tls/i686/cmov/libm-2.6.1.so
b76c1000-b76c3000 rw-p 00023000 08:02 2244910    /lib/tls/i686/cmov/libm-2.6.1.so
b76c3000-b76da000 r-xp 00000000 08:02 4787653    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b76da000-b76db000 rw-p 00016000 08:02 4787653    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b76db000-b76dc000 rw-p b76db000 00:00 0 
b76dc000-b76f5000 r-xp 00000000 08:02 4784960    /usr/lib/libatk-1.0.so.0.2009.1
b76f5000-b76f7000 rw-p 00018000 08:02 4784960    /usr/lib/libatk-1.0.so.0.2009.1
b76f7000-b777b000 r-xp 00000000 08:02 4787652    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b777b000-b777e000 rw-p 00084000 08:02 4787652    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b777e000-b7896000 r-xp 00000000 08:02 4784327    /usr/lib/libxml2.so.2.6.30
b7896000-b789b000 rw-p 00118000 08:02 4784327    /usr/lib/libxml2.so.2.6.30
b789b000-b789c000 rw-p b789b000 00:00 0 
b789c000-b7c19000 r-xp 00000000 08:02 4787655    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7c19000-b7c20000 rw-p 0037c000 08:02 4787655    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7c20000-b7c21000 rw-p b7c20000 00:00 0 
b7c21000-b7c38000 r-xp 00000000 08:02 4785625    /usr/lib/libglade-2.0.so.0.0.7
b7c38000-b7c39000 rw-p 00016000 08:02 4785625    /usr/lib/libglade-2.0.so.0.0.7
b7c39000-b7c6d000 r-xp 00000000 08:02 4786610    /usr/lib/libdbus-1.so.3.3.0
b7c6d000-b7c6e000 rw-p 00033000 08:02 4786610    /usr/lib/libdbus-1.so.3.3.0
b7c6e000-b7c6f000 rw-p b7c6e000 00:00 0 
b7c6f000-b7c89000 r-xp 00000000 08:02 4786615    /usr/lib/libdbus-glib-1.so.2.1.0
b7c89000-b7c8a000 rw-p 0001a000 08:02 4786615    /usr/lib/libdbus-glib-1.so.2.1.0
b7c8a000-b7c91000 r-xp 00000000 08:02 2245077    /lib/tls/i686/cmov/librt-2.6.1.so
b7c91000-b7c93000 rw-p 00006000 08:02 2245077    /lib/tls/i686/cmov/librt-2.6.1.so
b7c93000-b7c97000 r-xp 00000000 08:02 4784915    /usr/lib/libgthread-2.0.so.0.1400.1
b7c97000-b7c98000 rw-p 00003000 08:02 4784915    /usr/lib/libgthread-2.0.so.0.1400.1
b7c98000-b7ce1000 r-xp 00000000 08:02 4784673    /usr/lib/libORBit-2.so.0.1.0
b7ce1000-b7cea000 rw-p 00049000 08:02 4784673    /usr/lib/libORBit-2.so.0.1.0
b7cea000-b7ceb000 rw-p b7cea000 00:00 0 
b7ceb000-b7d1a000 r-xp 00000000 08:02 4784465    /usr/lib/libgconf-2.so.4.1.2
b7d1a000-b7d1d000 rw-p 0002e000 08:02 4784465    /usr/lib/libgconf-2.so.4.1.2
b7d1d000-b7d73000 r-xp 00000000 08:02 4785040    /usr/lib/libgnomevfs-2.so.0.2000.0
b7d73000-b7d76000 rw-p 00055000 08:02 4785040    /usr/lib/libgnomevfs-2.so.0.2000.0
b7d76000-b7d77000 rw-p b7d76000 00:00 0 
b7d77000-b7d8a000 r-xp 00000000 08:02 3490206    /usr/lib/libbonobo-activation.so.4.0.0
b7d8a000-b7d8c000 rw-p 00013000 08:02 3490206    /usr/lib/libbonobo-activation.so.4.0.0
b7d8c000-b7dde000 r-xp 00000000 08:02 3490205    /usr/lib/libbonobo-2.so.0.0.0
b7dde000-b7de8000 rw-p 00051000 08:02 3490205    /usr/lib/libbonobo-2.so.0.0.0
b7de8000-b7def000 r-xp 00000000 08:02 2244658    /lib/libpopt.so.0.0.0
b7def000-b7df0000 rw-p 00006000 08:02 2244658    /lib/libpopt.so.0.0.0
b7df0000-b7e04000 r-xp 00000000 08:02 4784466    /usr/lib/libgnome-2.so.0.2000.0
b7e04000-b7e05000 rw-p 00014000 08:02 4784466    /usr/lib/libgnome-2.so.0.2000.0
b7e05000-b7e1a000 r-xp 00000000 08:02 4784309    /usr/lib/libart_lgpl_2.so.2.3.19
b7e1a000-b7e1b000 rw-p 00014000 08:02 4784309    /usr/lib/libart_lgpl_2.so.2.3.19
b7e1b000-b7e1c000 rw-p b7e1b000 00:00 0 
b7e1c000-b7e4b000 r-xp 00000000 08:02 4785845    /usr/lib/libgnomecanvas-2.so.0.2000.0
b7e4b000-b7e4c000 rw-p 0002f000 08:02 4785845    /usr/lib/libgnomecanvas-2.so.0.2000.0
b7e4c000-b7ea7000 r-xp 00000000 08:02 4784548    /usr/lib/libbonoboui-2.so.0.0.0
b7ea7000-b7eaa000 rw-p 0005a000 08:02 4784548    /usr/lib/libbonoboui-2.so.0.0.0
b7eaa000-b7eb2000 r-xp 00000000 08:02 4786178    /usr/lib/libstartup-notification-1.so.0.0.0
b7eb2000-b7eb3000 rw-p 00007000 08:02 4786178    /usr/lib/libstartup-notification-1.so.0.0.0
b7eb3000-b7ec8000 r-xp 00000000 08:02 4785976    /usr/lib/libICE.so.6.3.0
b7ec8000-b7eca000 rw-p 00014000 08:02 4785976    /usr/lib/libICE.so.6.3.0
b7eca000-b7ecb000 rw-p b7eca000 00:00 0 
b7ecb000-b7ed2000 r-xp 00000000 08:02 4786196    /usr/lib/libSM.so.6.0.0
b7ed2000-b7ed3000 rw-p 00006000 08:02 4786196    /usr/lib/libSM.so.6.0.0
b7ed3000-b7f5b000 r-xp 00000000 08:02 4786011    /usr/lib/libgnomeui-2.so.0.2000.0
b7f5b000-b7f5f000 rw-p 00087000 08:02 4786011    /usr/lib/libgnomeui-2.so.0.2000.0
b7f5f000-b7f60000 rw-p b7f5f000 00:00 0 
b7f60000-b7f74000 r-xp 00000000 08:02 4784496    /usr/lib/libgnome-desktop-2.so.2.3.13
b7f74000-b7f75000 rw-p 00014000 08:02 4784496    /usr/lib/libgnome-desktop-2.so.2.3.13
b7f75000-b7faa000 r-xp 00000000 08:02 4784643    /usr/lib/libwnck-1.so.22.2.3
b7faa000-b7fac000 rw-p 00034000 08:02 4784643    /usr/lib/libwnck-1.so.22.2.3
b7fad000-b7fae000 r--s 00000000 08:02 1327160    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7fae000-b7faf000 r--p 00000000 08:02 4852841    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7faf000-b7fb0000 r--p 00000000 08:02 4851706    /usr/lib/locale/en_US.utf8/LC_TIME
b7fb0000-b7fb1000 r--p 00000000 08:02 4851722    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7fb1000-b7fb2000 r--p 00000000 08:02 4852884    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fb2000-b7fb3000 r--p 00000000 08:02 4852972    /usr/lib/locale/en_US.utf8/LC_PAPER
b7fb3000-b7fb4000 r--p 00000000 08:02 4852876    /usr/lib/locale/en_US.utf8/LC_NAME
b7fb4000-b7fb5000 r--p 00000000 08:02 4851723    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7fb5000-b7fb6000 r--p 00000000 08:02 4851724    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7fb6000-b7fb7000 r--p 00000000 08:02 4851725    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7fb7000-b7fbe000 r--s 00000000 08:02 4784576    /usr/lib/gconv/gconv-modules.cache
b7fbe000-b7fbf000 r--p 00000000 08:02 4851726    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7fbf000-b7fc1000 rw-p b7fbf000 00:00 0 
b7fc1000-b7fdb000 r-xp 00000000 08:02 2244748    /lib/ld-2.6.1.so
b7fdb000-b7fdd000 rw-p 00019000 08:02 2244748    /lib/ld-2.6.1.so
bfac5000-bfadb000 rw-p bfac5000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

No idea what any of this stuff means.

---

### Post by travislepp on 2007-11-03
I have a similar issue:
** (avant-window-navigator:6212): WARNING **: Failed to make connection to session bus: Failed to connect to socket /tmp/dbus-udrT1KGZH0: Connection refused

** (avant-window-navigator:6212): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (avant-window-navigator:6212): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (avant-window-navigator:6212): WARNING **: There was an error requesting the name: 
Segmentation fault (core dumped)

could it be gnome related?

---

### Post by gadgetgirl02 on 2007-11-03
/

---

### Post by allstar1971 on 2007-11-05
My AWN works, but the trash icon has a thin white line show up where the trash was located. The date also looks the same.

Jeff P

AMD 3700+ 64-bit
1GB memory
Nvidia GeForce4

---

