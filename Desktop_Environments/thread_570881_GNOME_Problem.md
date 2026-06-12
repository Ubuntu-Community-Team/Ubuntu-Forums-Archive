---
title: "GNOME Problem"
date: 2007-10-08
forum: Desktop Environments
---

### Post by damir_1105 on 2007-10-08
when i login to gnome.
i got this in new window:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "damir"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/linux:/tmp/.ICE-unix/21899
Initializing gnome-mount extension
** Message: failed to load session from /home/damir/.nautilus/saved-session-06AIVT
*** glibc detected *** /usr/bin/gnome-session: corrupted double-linked list: 0x082048e8 ***
======= Backtrace: =========
/lib/libc.so.6[0xb7604107]
/lib/libc.so.6[0xb76063fa]
/lib/libc.so.6(__libc_malloc+0x97)[0xb7607997]
/usr/lib/libICE.so.6(IceAcceptConnection+0x56)[0xb7e72c66]
/usr/bin/gnome-session[0x80556fc]
/usr/lib/libglib-2.0.so.0[0xb773240d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7708df2]
/usr/lib/libglib-2.0.so.0[0xb770bdcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb770c179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c40044]
/usr/bin/gnome-session(main+0x5de)[0x805638e]
/lib/libc.so.6(__libc_start_main+0xe0)[0xb75b4050]
/usr/bin/gnome-session[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 03:06 661584     /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 03:06 661584     /usr/bin/gnome-session
08069000-0823d000 rw-p 08069000 00:00 0          [heap]
b3a00000-b3a21000 rw-p b3a00000 00:00 0 
b3a21000-b3b00000 ---p b3a21000 00:00 0 
b3b23000-b3b2e000 r-xp 00000000 03:06 709696     /lib/libgcc_s.so.1
b3b2e000-b3b2f000 rw-p 0000a000 03:06 709696     /lib/libgcc_s.so.1
b3b44000-b3ba4000 rw-s 00000000 00:09 10027011   /SYSV00000000 (deleted)
b3ba4000-b3ba5000 ---p b3ba4000 00:00 0 
b3ba5000-b43a4000 rw-p b3ba5000 00:00 0 
b43a4000-b4421000 r--p 00000000 03:06 148239     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4421000-b4423000 r-xp 00000000 03:06 66981      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4423000-b4424000 rw-p 00001000 03:06 66981      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4424000-b442a000 r--s 00000000 03:06 345846     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b442a000-b442b000 r--s 00000000 03:06 348033     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b442b000-b442e000 r--s 00000000 03:06 348031     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b442e000-b442f000 r--s 00000000 03:06 348030     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b442f000-b4430000 r--s 00000000 03:06 348029     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b4430000-b4434000 r--s 00000000 03:06 345841     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b4434000-b4435000 r--s 00000000 03:06 348027     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b4435000-b4437000 r--s 00000000 03:06 348023     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b4437000-b4439000 r--s 00000000 03:06 348022     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b4439000-b443a000 r--s 00000000 03:06 348020     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b443a000-b443c000 r--s 00000000 03:06 347663     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b443c000-b4442000 r--s 00000000 03:06 347632     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b4442000-b4444000 r--s 00000000 03:06 346900     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b4444000-b4446000 r--s 00000000 03:06 346574     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b4446000-b444e000 r--s 00000000 03:06 345912     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b444e000-b4454000 r--s 00000000 03:06 345911     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b4454000-b4455000 r--s 00000000 03:06 345898     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b4455000-b446c000 r--s 00000000 03:06 344781     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b446c000-b446e000 r--s 00000000 03:06 345896     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b446e000-b4474000 r--s 00000000 03:06 345895     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b4474000-b4477000 r--s 00000000 03:06 345756     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b4477000-b447b000 r--s 00000000 03:06 341542     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b447b000-b447d000 r--s 00000000 03:06 343679     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b447d000-b447e000 r--s 00000000 03:06 348109     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b447e000-b447f000 r--s 00000000 03:06 348106     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b447f000-b4480000 r--s 00000000 03:06 348105     /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b4480000-b4481000 r--s 00000000 03:06 348104     /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b4481000-b4482000 r--s 00000000 03:06 500517     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b4482000-b4485000 r--s 00000000 03:06 348101     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b4485000-b448a000 r--s 00000000 03:06 500516     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b448a000-b448c000 r--s 00000000 03:06 348083     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b448c000-b448d000 r--s 00000000 03:06 348082     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b448d000-b448f000 r--s 00000000 03:06 348079     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b448f000-b4490000 r--s 00000000 03:06 348078     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b4490000-b4495000 r--s 00000000 03:06 348076     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b4495000-b4499000 r--s 00000000 03:06 348073     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b4499000-b449b000 r--s 00000000 03:06 348072     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b449b000-b449e000 r--s 00000000 03:06 348071     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b449e000-b449f000 r--s 00000000 03:06 348070     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b449f000-b44a1000 r--s 00000000 03:06 348064     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b44a1000-b44a5000 r--s 00000000 03:06 309646     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b44a5000-b44ab000 r--s 00000000 03:06 348062     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b44ab000-b44ac000 r--s 00000000 03:06 348058     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b44ac000-b44b4000 r--s 00000000 03:06 348053     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b44b4000-b44b6000 r--s 00000000 03:06 309645     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b44b6000-b4b5f000 r--p 00000000 03:06 693792     /usr/share/icons/gnome/icon-theme.cache
b4b5f000-b53d1000 r--p 00000000 03:06 178620     /usr/share/icons/hicolor/icon-theme.cache
b53d1000-b6ccb000 r--p 00000000 03:06 306438     /usr/share/icons/crystalsvg/icon-theme.cache
b6ccb000-b6d2b000 rw-s 00000000 00:09 9994240    /SYSV00000000 (deleted)
b6d2b000-b6d88000 rw-p b6d2b000 00:00 0 
b6d88000-b6d8f000 r-xp 00000000 03:06 662967     /usr/lib/libfam.so.0.0.0
b6d8f000-b6d90000 rw-p 00006000 03:06 662967     /usr/lib/libfam.so.0.0.0
b6d90000-b6d96000 r-xp 00000000 03:06 709659     /lib/libacl.so.1.1.0
b6d96000-b6d97000 rw-p 00005000 03:06 709659     /lib/libacl.so.1.1.0
b6d97000-b6d9a000 r--s 00000000 03:06 348049     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6d9a000-b6d9c000 r--s 00000000 03:06 309643     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6d9c000-b6d9e000 r--s 00000000 03:06 343675     /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6d9e000-b6da5000 r-xp 00000000 03:06 665442     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b6da5000-b6da6000 rw-p 00007000 03:06 665442     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b6da6000-b6daa000 r-xp 00000000 03:06 665468     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6daa000-b6dab000 rw-p 00003000 03:06 665468     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6dac000-b6db8000 r-xp 00000000 03:06 665305     /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6db8000-b6db9000 rw-p 0000b000 03:06 665305     /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6db9000-b6dba000 r-xp 00000000 03:06 669746     /usr/lib/gconv/ISO8859-1.so
b6dba000-b6dbc000 rw-p 00000000 03:06 669746     /usr/lib/gconv/ISO8859-1.so
b6dbc000-b6df7000 r--p 00000000 03:06 961        /usr/lib/locale/en_US.utf8/LC_CTYPE
b6df7000-b6ece000 r--p 00000000 03:06 960        /usr/lib/locale/en_US.utf8/LC_COLLATE
b6ece000-b6ed6000 r-xp 00000000 03:06 712616     /lib/libnss_files-2.6.1.so
b6ed6000-b6ed8000 rw-p 00007000 03:06 712616     /lib/libnss_files-2.6.1.so
b6ed8000-b6ee0000 r-xp 00000000 03:06 712668     /lib/libnss_nis-2.6.1.so
b6ee0000-b6ee2000 rw-p 00007000 03:06 712668     /lib/libnss_nis-2.6.1.so
b6ee2000-b6ee8000 r-xp 00000000 03:06 712599     /lib/libnss_compat-2.6.1.so
b6ee8000-b6eea000 rw-p 00005000 03:06 712599     /lib/libnss_compat-2.6.1.so
b6eea000-b6eee000 rw-p b6eea000 00:00 0 
b6eee000-b6f24000 r-xp 00000000 03:06 709750     /lib/libsepol.so.1
b6f24000-b6f25000 rw-p 00035000 03:06 709750     /lib/libsepol.so.1
b6f25000-b6f2f000 rw-p b6f25000 00:00 0 
b6f2f000-b6f32000 r-xp 00000000 03:06 663120     /usr/lib/libgpg-error.so.0.3.0
b6f32000-b6f33000 rw-p 00002000 03:06 663120     /usr/lib/libgpg-error.so.0.3.0
b6f33000-b6f82000 r-xp 00000000 03:06 663008     /usr/lib/libgcrypt.so.11.2.2
b6f82000-b6f84000 rw-p 0004e000 03:06 663008     /usr/lib/libgcrypt.so.11.2.2
b6f84000-b6f98000 r-xp 00000000 03:06 663464     /usr/lib/libtasn1.so.3.0.6
b6f98000-b6f99000 rw-p 00013000 03:06 663464     /usr/lib/libtasn1.so.3.0.6
b6f99000-b6f9a000 rw-p b6f99000 00:00 0 
b6f9a000-b6f9c000 r-xp 00000000 03:06 712708     /lib/libutil-2.6.1.so
b6f9c000-b6f9e000 rw-p 00001000 03:06 712708     /lib/libutil-2.6.1.so
b6f9e000-b6fb2000 r-xp 00000000 03:06 709749     /lib/libselinux.so.1
b6fb2000-b6fb4000 rw-p 00013000 03:06 709749     /lib/libselinux.so.1
b6fb4000-b6fc2000 r-xp 00000000 03:06 712687     /lib/libresolv-2.6.1.so
b6fc2000-b6fc4000 rw-p 0000d000 03:06 712687     /lib/libresolv-2.6.1.so
b6fc4000-b6fc6000 rw-p b6fc4000 00:00 0 
b6fc6000-b6fd4000 r-xp 00000000 03:06 662846     /usr/lib/libavahi-client.so.3.2.2
b6fd4000-b6fd5000 rw-p 0000e000 03:06 662846     /usr/lib/libavahi-client.so.3.2.2
b6fd5000-b6fdf000 r-xp 00000000 03:06 662848     /usr/lib/libavahi-common.so.3.4.3
b6fdf000-b6fe0000 rw-p 00009000 03:06 662848     /usr/lib/libavahi-common.so.3.4.3
b6fe0000-b6fe1000 rw-p b6fe0000 00:00 0 
b6fe1000-b6fe3000 r-xp 00000000 03:06 662852     /usr/lib/libavahi-glib.so.1.0.1
b6fe3000-b6fe4000 rw-p 00001000 03:06 662852     /usr/lib/libavahi-glib.so.1.0.1
b6fe4000-b704e000 r-xp 00000000 03:06 663116     /usr/lib/libgnutls.so.13.0.9
b704e000-b7054000 rw-p 0006a000 03:06 663116     /usr/lib/libgnutls.so.13.0.9
b7054000-b7076000 r-xp 00000000 03:06 294517     /usr/lib/libpng12.so.0.15.0
b7076000-b7077000 rw-p 00021000 03:06 294517     /usr/lib/libpng12.so.0.15.0
b7077000-b7095000 r-xp 00000000 03:06 662963     /usr/lib/libexpat.so.1.0.0
b7095000-b7097000 rw-p 0001d000 03:06 662963     /usr/lib/libexpat.so.1.0.0
b7097000-b70ff000 r-xp 00000000 03:06 664421     /usr/lib/libfreetype.so.6.3.10
b70ff000-b7102000 rw-p 00068000 03:06 664421     /usr/lib/libfreetype.so.6.3.10
b7102000-b7103000 rw-p b7102000 00:00 0 
b7103000-b7116000 r-xp 00000000 03:06 663522     /usr/lib/libz.so.1.2.3
b7116000-b7117000 rw-p 00012000 03:06 663522     /usr/lib/libz.so.1.2.3
b7117000-b712a000 r-xp 00000000 03:06 712569     /lib/libnsl-2.6.1.so
b712a000-b712c000 rw-p 00012000 03:06 712569     /lib/libnsl-2.6.1.so
b712c000-b712e000 rw-p b712c000 00:00 0 
b712e000-b7132000 r-xp 00000000 03:06 662753     /usr/lib/libORBitCosNaming-2.so.0.1.0
b7132000-b7133000 rw-p 00003000 03:06 662753     /usr/lib/libORBitCosNaming-2.so.0.1.0
b7133000-b7134000 rw-p b7133000 00:00 0 
b7134000-b7138000 r-xp 00000000 03:06 662778     /usr/lib/libXdmcp.so.6.0.0
b7138000-b7139000 rw-p 00003000 03:06 662778     /usr/lib/libXdmcp.so.6.0.0
b7139000-b7157000 r-xp 00000000 03:06 663245     /usr/lib/libjpeg.so.62.0.0
b7157000-b7158000 rw-p 0001d000 03:06 663245     /usr/lib/libjpeg.so.62.0.0
b7158000-b7160000 r-xp 00000000 03:06 663454     /usr/lib/libstartup-notification-1.so.0.0.0
b7160000-b7161000 rw-p 00007000 03:06 663454     /usr/lib/libstartup-notification-1.so.0.0.0
b7161000-b7168000 r-xp 00000000 03:06 712698     /lib/librt-2.6.1.so
b7168000-b716a000 rw-p 00006000 03:06 712698     /lib/librt-2.6.1.so
b716a000-b716b000 rw-p b716a000 00:00 0 
b716b000-b716f000 r-xp 00000000 03:06 663172     /usr/lib/libgthread-2.0.so.0.1200.11
b716f000-b7170000 rw-p 00003000 03:06 663172     /usr/lib/libgthread-2.0.so.0.1200.11
b7170000-b7172000 r-xp 00000000 03:06 709966     /lib/libdl-2.6.1.so
b7172000-b7174000 rw-p 00001000 03:06 709966     /lib/libdl-2.6.1.so
b7174000-b7176000 r-xp 00000000 03:06 663074     /usr/lib/libgmodule-2.0.so.0.1200.11
b7176000-b7177000 rw-p 00002000 03:06 663074     /usr/lib/libgmodule-2.0.so.0.1200.11
b7177000-b71cd000 r-xp 00000000 03:06 663108     /usr/lib/libgnomevfs-2.so.0.1800.1
b71cd000-b71d0000 rw-p 00055000 03:06 663108     /usr/lib/libgnomevfs-2.so.0.1800.1
b71d0000-b723e000 r-xp 00000000 03:06 662871     /usr/lib/libcairo.so.2.11.1
b723e000-b7240000 rw-p 0006d000 03:06 662871     /usr/lib/libcairo.so.2.11.1
b7240000-b7244000 r-xp 00000000 03:06 662784     /usr/lib/libXfixes.so.3.1.0
b7244000-b7245000 rw-p 00003000 03:06 662784     /usr/lib/libXfixes.so.3.1.0
b7245000-b7246000 rw-p b7245000 00:00 0 
b7246000-b724e000 r-xp 00000000 03:06 662774     /usr/lib/libXcursor.so.1.0.2
b724e000-b724f000 rw-p 00007000 03:06 662774     /usr/lib/libXcursor.so.1.0.2
b724f000-b7256000 r-xp 00000000 03:06 662790     /usr/lib/libXi.so.6.0.0
b7256000-b7257000 rw-p 00006000 03:06 662790     /usr/lib/libXi.so.6.0.0
b7257000-b7259000 r-xp 00000000 03:06 662792     /usr/lib/libXinerama.so.1.0.0
b7259000-b725a000 rw-p 00001000 03:06 662792     /usr/lib/libXinerama.so.1.0.0
b725a000-b7261000 r-xp 00000000 03:06 662804     /usr/lib/libXrender.so.1.3.0
b7261000-b7262000 rw-p 00006000 03:06 662804     /usr/lib/libXrender.so.1.3.0
b7262000-b726f000 r-xp 00000000 03:06 662782     /usr/lib/libXext.so.6.4.0
b726f000-b7270000 rw-p 0000d000 03:06 662782     /usr/lib/libXext.so.6.4.0
b7270000-b7293000 r-xp 00000000 03:06 662969     /usr/lib/libfontconfig.so.1.2.0
b7293000-b729b000 rw-p 00023000 03:06 662969     /usr/lib/libfontconfig.so.1.2.0
b729b000-b729c000 rw-p b729b000 00:00 0 
b729c000-b72a3000 r-xp 00000000 03:06 663353     /usr/lib/libpangocairo-1.0.so.0.1600.2
b72a3000-b72a4000 rw-p 00007000 03:06 663353     /usr/lib/libpangocairo-1.0.so.0.1600.2
b72a4000-b72ce000 r-xp 00000000 03:06 663355     /usr/lib/libpangoft2-1.0.so.0.1600.2
b72ce000-b72cf000 rw-p 0002a000 03:06 663355     /usr/lib/libpangoft2-1.0.so.0.1600.2
b72cf000-b72e3000 r-xp 00000000 03:06 662830     /usr/lib/libart_lgpl_2.so.2.3.17
b72e3000-b72e4000 rw-p 00013000 03:06 662830     /usr/lib/libart_lgpl_2.so.2.3.17
b72e4000-b72eb000 r-xp 00000000 03:06 709739     /lib/libpopt.so.0.0.0
b72eb000-b72ec000 rw-p 00006000 03:06 709739     /lib/libpopt.so.0.0.0
b72ec000-b7315000 r-xp 00000000 03:06 663090     /usr/lib/libgnomecanvas-2.so.0.1400.0
b7315000-b7316000 rw-p 00029000 03:06 663090     /usr/lib/libgnomecanvas-2.so.0.1400.0
b7316000-b7371000 r-xp 00000000 03:06 662867     /usr/lib/libbonoboui-2.so.0.0.0
b7371000-b7374000 rw-p 0005a000 03:06 662867     /usr/lib/libbonoboui-2.so.0.0.0
b7374000-b7375000 rw-p b7374000 00:00 0 
b7375000-b748c000 r-xp 00000000 03:06 663516     /usr/lib/libxml2.so.2.6.27
b748c000-b7492000 rw-p 00116000 03:06 663516     /usr/lib/libxml2.so.2.6.27
b7492000-b7552000 r-xp 00000000 03:06 662832     /usr/lib/libasound.so.2.0.0
b7552000-b7557000 rw-p 000bf000 03:06 662832     /usr/lib/libasound.so.2.0.0
b7557000-b757a000 r-xp 00000000 03:06 709967     /lib/libm-2.6.1.so
b757a000-b757c000 rw-p 00022000 03:06 709967     /lib/libm-2.6.1.so
b757c000-b759c000 r-xp 00000000 03:06 662844     /usr/lib/libaudiofile.so.0.0.2
b759c000-b759e000 rw-p 00020000 03:06 662844     /usr/lib/libaudiofile.so.0.0.2
b759e000-b76cc000 r-xp 00000000 03:06 709963     /lib/libc-2.6.1.so
b76cc000-b76cd000 r--p 0012d000 03:06 709963     /lib/libc-2.6.1.so
b76cd000-b76cf000 rw-p 0012e000 03:06 709963     /lib/libc-2.6.1.so
b76cf000-b76d2000 rw-p b76cf000 00:00 0 
b76d2000-b76d9000 r-xp 00000000 03:06 712560     /lib/libwrap.so.0.7.6
b76d9000-b76da000 rw-p 00007000 03:06 712560     /lib/libwrap.so.0.7.6
b76da000-b76db000 rw-p b76da000 00:00 0 
b76db000-b776f000 r-xp 00000000 03:06 663064     /usr/lib/libglib-2.0.so.0.1200.11
b776f000-b7770000 rw-p 00093000 03:06 663064     /usr/lib/libglib-2.0.so.0.1200.11
b7770000-b777c000 r-xp 00000000 03:06 663080     /usr/lib/libgnome-keyring.so.0.0.1
b777c000-b777d000 rw-p 0000b000 03:06 663080     /usr/lib/libgnome-keyring.so.0.0.1
b777d000-b77b6000 r-xp 00000000 03:06 663118     /usr/lib/libgobject-2.0.so.0.1200.11
b77b6000-b77b7000 rw-p 00039000 03:06 663118     /usr/lib/libgobject-2.0.so.0.1200.11
b77b7000-b77e9000 r-xp 00000000 03:06 661872     /usr/lib/libdbus-1.so.3.2.0
b77e9000-b77ea000 rw-p 00031000 03:06 661872     /usr/lib/libdbus-1.so.3.2.0
b77ea000-b7804000 r-xp 00000000 03:06 662907     /usr/lib/libdbus-glib-1.so.2.1.0
b7804000-b7805000 rw-p 0001a000 03:06 662907     /usr/lib/libdbus-glib-1.so.2.1.0
b7805000-b7818000 r-xp 00000000 03:06 712686     /lib/libpthread-2.6.1.so
b7818000-b781a000 rw-p 00012000 03:06 712686     /lib/libpthread-2.6.1.so
b781a000-b781d000 rw-p b781a000 00:00 0 
b781d000-b7866000 r-xp 00000000 03:06 662749     /usr/lib/libORBit-2.so.0.1.0
b7866000-b7870000 rw-p 00048000 03:06 662749     /usr/lib/libORBit-2.so.0.1.0
b7870000-b789f000 r-xp 00000000 03:06 663006     /usr/lib/libgconf-2.so.4.1.2
b789f000-b78a2000 rw-p 0002e000 03:06 663006     /usr/lib/libgconf-2.so.4.1.2
b78a2000-b78b5000 r-xp 00000000 03:06 662865     /usr/lib/libbonobo-activation.so.4.0.0
b78b5000-b78b7000 rw-p 00013000 03:06 662865     /usr/lib/libbonobo-activation.so.4.0.0
b78b7000-b7909000 r-xp 00000000 03:06 662863     /usr/lib/libbonobo-2.so.0.0.0
b7909000-b7913000 rw-p 00051000 03:06 662863     /usr/lib/libbonobo-2.so.0.0.0
b7913000-b7a00000 r-xp 00000000 03:06 662761     /usr/lib/libX11.so.6.2.0
b7a00000-b7a04000 rw-p 000ed000 03:06 662761     /usr/lib/libX11.so.6.2.0
b7a04000-b7a40000 r-xp 00000000 03:06 663351     /usr/lib/libpango-1.0.so.0.1600.2
b7a40000-b7a42000 rw-p 0003b000 03:06 663351     /usr/lib/libpango-1.0.so.0.1600.2
b7a42000-b7a43000 rw-p b7a42000 00:00 0 
b7a43000-b7a48000 r-xp 00000000 03:06 662802     /usr/lib/libXrandr.so.2.1.0
b7a48000-b7a49000 rw-p 00005000 03:06 662802     /usr/lib/libXrandr.so.2.1.0
b7a49000-b7a5f000 r-xp 00000000 03:06 663028     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a5f000-b7a60000 rw-p 00015000 03:06 663028     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a60000-b7a79000 r-xp 00000000 03:06 662838     /usr/lib/libatk-1.0.so.0.1809.1
b7a79000-b7a7b000 rw-p 00018000 03:06 662838     /usr/lib/libatk-1.0.so.0.1809.1
b7a7b000-b7afe000 r-xp 00000000 03:06 663026     /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7afe000-b7b01000 rw-p 00083000 03:06 663026     /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b01000-b7e52000 r-xp 00000000 03:06 663175     /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e52000-b7e58000 rw-p 00351000 03:06 663175     /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e58000-b7e59000 rw-p b7e58000 00:00 0 
b7e59000-b7e6d000 r-xp 00000000 03:06 663076     /usr/lib/libgnome-2.so.0.1800.0
b7e6d000-b7e6e000 rw-p 00014000 03:06 663076     /usr/lib/libgnome-2.so.0.1800.0
b7e6e000-b7e6f000 rw-p b7e6e000 00:00 0 
b7e6f000-b7e84000 r-xp 00000000 03:06 662739     /usr/lib/libICE.so.6.3.0
b7e84000-b7e86000 rw-p 00014000 03:06 662739     /usr/lib/libICE.so.6.3.0
b7e86000-b7e87000 rw-p b7e86000 00:00 0 
b7e87000-b7e8f000 r-xp 00000000 03:06 662757     /usr/lib/libSM.so.6.0.0
b7e8f000-b7e90000 rw-p 00007000 03:06 662757     /usr/lib/libSM.so.6.0.0
b7e90000-b7f1a000 r-xp 00000000 03:06 663106     /usr/lib/libgnomeui-2.so.0.1788.4
b7f1a000-b7f1e000 rw-p 00089000 03:06 663106     /usr/lib/libgnomeui-2.so.0.1788.4
b7f1e000-b7f32000 r-xp 00000000 03:06 663078     /usr/lib/libgnome-desktop-2.so.2.3.5
b7f32000-b7f33000 rw-p 00014000 03:06 663078     /usr/lib/libgnome-desktop-2.so.2.3.5
b7f33000-b7f3c000 r-xp 00000000 03:06 662954     /usr/lib/libesd.so.0.2.36
b7f3c000-b7f3d000 rw-p 00009000 03:06 662954     /usr/lib/libesd.so.0.2.36
b7f3d000-b7f3f000 r-xp 00000000 03:06 662767     /usr/lib/libXau.so.6.0.0
b7f3f000-b7f40000 rw-p 00001000 03:06 662767     /usr/lib/libXau.so.6.0.0
b7f40000-b7f41000 rw-p b7f40000 00:00 0 
b7f41000-b7f44000 r-xp 00000000 03:06 709663     /lib/libattr.so.1.1.0
b7f44000-b7f45000 rw-p 00002000 03:06 709663     /lib/libattr.so.1.1.0
b7f45000-b7f46000 r--p 00000000 03:06 966        /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7f46000-b7f47000 r--p 00000000 03:06 969        /usr/lib/locale/en_US.utf8/LC_TIME
b7f47000-b7f48000 r--p 00000000 03:06 964        /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f48000-b7f49000 r--p 00000000 03:06 970        /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f49000-b7f4a000 r--p 00000000 03:06 967        /usr/lib/locale/en_US.utf8/LC_PAPER
b7f4a000-b7f4b000 r--p 00000000 03:06 965        /usr/lib/locale/en_US.utf8/LC_NAME
b7f4b000-b7f4c000 r--p 00000000 03:06 959        /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f4c000-b7f4d000 r--p 00000000 03:06 968        /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f4d000-b7f4e000 r--p 00000000 03:06 963        /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f4e000-b7f55000 r--s 00000000 03:06 661700     /usr/lib/gconv/gconv-modules.cache
b7f55000-b7f56000 r--p 00000000 03:06 962        /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f56000-b7f57000 rw-p b7f56000 00:00 0 
b7f57000-b7f71000 r-xp 00000000 03:06 709956     /lib/ld-2.6.1.so
b7f71000-b7f73000 rw-p 00019000 03:06 709956     /lib/ld-2.6.1.so
bfecf000-bfee5000 rw-p bfecf000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

(evolution-alarm-notify:21968): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:21969): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
evolution-alarm-notify-Message: Setting timeout for 110 1191880800 1191880690
evolution-alarm-notify-Message:  Tue Oct  9 00:00:00 2007

evolution-alarm-notify-Message:  Mon Oct  8 23:58:10 2007


(gnome-power-manager:21967): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

---

