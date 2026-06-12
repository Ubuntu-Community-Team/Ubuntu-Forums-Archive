---
title: "[SOLVED] Beryl and Emerald problems"
date: 2007-07-18
forum: Desktop Environments
---

### Post by tupesadilla on 2007-07-18
When attempting to run beryl from the terminal (because icon wont load it) i get this ```
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

[Warning ]: Relaunching beryl with __GL_YIELD="NOTHING"

**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

*** glibc detected *** beryl: corrupted double-linked list: 0x0825ca68 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7c40b2a]
/lib/tls/i686/cmov/libc.so.6[0xb7c42e38]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb7c4460e]
/usr/lib/beryl/libinputzoom.so[0xb6cf33f8]
beryl(initPluginForScreen+0x2b)[0x807166b]
beryl(initPluginForDisplay+0x59)[0x8071879]
beryl(updatePlugins+0x45b)[0x807140b]
beryl(eventLoop+0x8dc)[0x8059b8c]
beryl(main+0x3fa)[0x805295a]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7bf0ebc]
beryl[0x8052481]
======= Memory map: ========
08048000-08080000 r-xp 00000000 03:41 7096006    /usr/bin/beryl
08080000-08081000 rw-p 00038000 03:41 7096006    /usr/bin/beryl
08081000-0827c000 rw-p 08081000 00:00 0          [heap]
b4400000-b4421000 rw-p b4400000 00:00 0 
b4421000-b4500000 ---p b4421000 00:00 0 
b4589000-b4594000 r-xp 00000000 03:41 10715200   /lib/libgcc_s.so.1
b4594000-b4595000 rw-p 0000a000 03:41 10715200   /lib/libgcc_s.so.1
b45a7000-b45a8000 rw-s 00000000 00:08 4390953    /SYSV00000000 (deleted)
b45a8000-b45a9000 rw-s 00000000 00:08 4358184    /SYSV00000000 (deleted)
b45a9000-b45aa000 rw-s 00000000 00:08 4325415    /SYSV00000000 (deleted)
b45aa000-b45ab000 rw-s 00000000 00:08 4292646    /SYSV00000000 (deleted)
b45ab000-b45b5000 r-xp 00000000 03:41 7685866    /usr/lib/beryl/libswitcher.so
b45b5000-b45b6000 rw-p 00009000 03:41 7685866    /usr/lib/beryl/libswitcher.so
b45b6000-b45cc000 r-xp 00000000 03:41 7685847    /usr/lib/beryl/libgroup.so
b45cc000-b45d3000 rw-p 00016000 03:41 7685847    /usr/lib/beryl/libgroup.so
b45d3000-b45d8000 r-xp 00000000 03:41 7685858    /usr/lib/beryl/libresize.so
b45d8000-b45d9000 rw-p 00004000 03:41 7685858    /usr/lib/beryl/libresize.so
b45d9000-b45dc000 r-xp 00000000 03:41 7685852    /usr/lib/beryl/libneg.so
b45dc000-b45dd000 rw-p 00003000 03:41 7685852    /usr/lib/beryl/libneg.so
b45dd000-b45e5000 r-xp 00000000 03:41 7685872    /usr/lib/beryl/libwobbly.so
b45e5000-b45e6000 rw-p 00008000 03:41 7685872    /usr/lib/beryl/libwobbly.so
b45e6000-b45f5000 r-xp 00000000 03:41 10715174   /lib/libbz2.so.1.0.3
b45f5000-b45f6000 rw-p 0000f000 03:41 10715174   /lib/libbz2.so.1.0.3
b45f6000-b470d000 r-xp 00000000 03:41 7096578    /usr/lib/libxml2.so.2.6.27
b470d000-b4713000 rw-p 00116000 03:41 7096578    /usr/lib/libxml2.so.2.6.27
b4713000-b4743000 r-xp 00000000 03:41 7095907    /usr/lib/libcroco-0.6.so.3.0.1
b4743000-b4746000 rw-p 0002f000 03:41 7095907    /usr/lib/libcroco-0.6.so.3.0.1
b4746000-b4772000 r-xp 00000000 03:41 7096177    /usr/lib/libgsf-1.so.114.0.3
b4772000-b4775000 rw-p 0002b000 03:41 7096177    /usr/lib/libgsf-1.so.114.0.3
b4775000-b4776000 rw-p b4775000 00:00 0 
b4776000-b478c000 r-xp 00000000 03:41 7096056    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b478c000-b478d000 rw-p 00015000 03:41 7096056    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b478d000-b47bc000 r-xp 00000000 03:41 7096465    /usr/lib/librsvg-2.so.2.16.0
b47bc000-b47bd000 rw-p 0002f000 03:41 7096465    /usr/lib/librsvg-2.so.2.16.0
b47bd000-b47c4000 r-xp 00000000 03:41 7096251    /usr/lib/libberyldecoration.so.0.0.0
b47c4000-b47c5000 rw-p 00006000 03:41 7096251    /usr/lib/libberyldecoration.so.0.0.0
b47c5000-b47c7000 r-xp 00000000 03:41 7685845    /usr/lib/beryl/libfadedesktop.so
b47c7000-b47c8000 rw-p 00001000 03:41 7685845    /usr/lib/beryl/libfadedesktop.so
b47c8000-b47cb000 r-xp 00000000 03:41 7685851    /usr/lib/beryl/libmove.so
b47cb000-b47cc000 rw-p 00002000 03:41 7685851    /usr/lib/beryl/libmove.so
b47cc000-b47d6000 r-xp 00000000 03:41 7685841    /usr/lib/beryl/libcube.so
b47d6000-b47d7000 rw-p 00009000 03:41 7685841    /usr/lib/beryl/libcube.so
b47d7000-b47db000 r-xp 00000000 03:41 7685843    /usr/lib/beryl/libdecoration.so
b47db000-b47dc000 rw-p 00003000 03:41 7685843    /usr/lib/beryl/libdecoration.so
b47dc000-b47e5000 r-xp 00000000 03:41 7685859    /usr/lib/beryl/librotate.so
b47e5000-b47e6000 rw-p 00008000 03:41 7685859    /usr/lib/beryl/librotate.so
b47e6000-b4804000 r-xp 00000000 03:41 7095987    /usr/lib/libexpat.so.1.0.0
b4804000-b4806000 rw-p 0001d000 03:41 7095987    /usr/lib/libexpat.so.1.0.0
b4806000-b4870000 r-xp 00000000 03:41 7095228    /usr/lib/libfreetype.so.6.3.15
b4870000-b4874000 rw-p 00069000 03:41 7095228    /usr/lib/libfreetype.so.6.3.15
b4874000-b4897000 r-xp 00000000 03:41 7095996    /usr/lib/libfontconfig.so.1.2.0
b4897000-b489f000 rw-p 00023000 03:41 7095996    /usr/lib/libfontconfig.so.1.2.0
b489f000-b48c9000 r-xp 00000000 03:41 7096406    /usr/lib/libpangoft2-1.0.so.0.1600.2
b48c9000-b48ca000 rw-p 0002a000 03:41 7096406    /usr/lib/libpangoft2-1.0.so.0.1600.2
b48ca000-b493d000 r-xp 00000000 03:41 7096426    /usr/lib/libcairo.so.2.11.3
b493d000-b493f000 rw-p 00072000 03:41 7096426    /usr/lib/libcairo.so.2.11.3
b493f000-b4978000 r-xp 00000000 03:41 7096157    /usr/lib/libgobject-2.0.so.0.1200.11
b4978000-b4979000 rw-p 00039000 03:41 7096157    /usr/lib/libgobject-2.0.so.0.1200.11
b4979000-b49b5000 r-xp 00000000 03:41 7096402    /usr/lib/libpango-1.0.so.0.1600.2
b49b5000-b49b7000 rw-p 0003b000 03:41 7096402    /usr/lib/libpango-1.0.so.0.1600.2
b49b7000-b49be000 r-xp 00000000 03:41 7096404    /usr/lib/libpangocairo-1.0.so.0.1600.2
b49be000-b49bf000 rw-p 00007000 03:41 7096404    /usr/lib/libpangocairo-1.0.so.0.1600.2
b49bf000-b49d9000 r-xp 00000000 03:41 7685835    /usr/lib/beryl/libanimation.so
b49d9000-b49da000 rw-p 0001a000 03:41 7685835    /usr/lib/beryl/libanimation.so
b49da000-b4a0b000 r-xp 00000000 03:41 7095927    /usr/lib/libdbus-1.so.3.2.0
b4a0b000-b4a0c000 rw-p 00031000 03:41 7095927    /usr/lib/libdbus-1.so.3.2.0
b4a0c000-b4a0e000 r-xp 00000000 03:41 7685853    /usr/lib/beryl/libobs.so
b4a0e000-b4a0f000 rw-p 00001000 03:41 7685853    /usr/lib/beryl/libobs.so
b4a0f000-b4a11000 r-xp 00000000 03:41 7685844    /usr/lib/beryl/libfade.so
b4a11000-b4a12000 rw-p 00001000 03:41 7685844    /usr/lib/beryl/libfade.so
b4a12000-b4a17000 r-xp 00000000 03:41 7685868    /usr/lib/beryl/libthumbnail.so
b4a17000-b4a1a000 rw-p 00005000 03:41 7685868    /usr/lib/beryl/libthumbnail.so
b4a1a000-b4a1d000 r-xp 00000000 03:41 7685855    /usr/lib/beryl/libplace.so
b4a1d000-b4a1e000 rw-p 00002000 03:41 7685855    /usr/lib/beryl/libplace.so
b4a1e000-b4a20000 r-xp 00000000 03:41 7685848    /usr/lib/beryl/libimgjpeg.so
b4a20000-b4a21000 rw-p 00001000 03:41 7685848    /usr/lib/beryl/libimgjpeg.so
b4a21000-b6a21000 rw-s 00000000 00:08 4194339    /SYSV00000000 (deleted)
b6a21000-b6a22000 rw-s 00000000 00:08 4161553    /SYSV00000000 (deleted)
b6a22000-b6a23000 rw-s 00000000 00:08 4128784    /SYSV00000000 (deleted)
b6a23000-b6a63000 rw-s ef832000 00:0d 17386      /dev/nvidia0
b6a63000-b6b63000 rw-s 038be000 00:0d 17386      /dev/nvidia0
b6b63000-b6ca5000 rw-s 0a26a000 00:0d 17386      /dev/nvidia0
b6ca5000-b6cb8000 r-xp 00000000 03:41 10749212   /lib/tls/i686/cmov/libpthread-2.5.so
b6cb8000-b6cba000 rw-p 00013000 03:41 10749212   /lib/tls/i686/cmov/libpthread-2.5.so
b6cba000-b6cbc000 rw-p b6cba000 00:00 0 
b6cbc000-b6cbd000 rw-s 00000000 00:08 4259877    /SYSV00000000 (deleted)
b6cbd000-b6cbe000 rw-s 00000000 00:08 4227108    /SYSV00000000 (deleted)
b6cbe000-b6cc0000 r-xp 00000000 03:41 7096113    /usr/lib/libgmodule-2.0.so.0.1200.11
b6cc0000-b6cc1000 rw-p 00002000 03:41 7096113    /usr/lib/libgmodule-2.0.so.0.1200.11
b6cc1000-b6ccc000 r-xp 00000000 03:41 7685860    /usr/lib/beryl/libscale.so
b6ccc000-b6ccd000 rw-p 0000a000 03:41 7685860    /usr/lib/beryl/libscale.so
b6ccd000-b6ceb000 r-xp 00000000 03:41 7096285    /usr/lib/libjpeg.so.62.0.0
b6ceb000-b6cec000 rw-p 0001d000 03:41 7096285    /usr/lib/libjpeg.so.62.0.0
b6cec000-b6ced000 r-xp 00000000 03:41 7685865    /usr/lib/beryl/libsvg.so
b6ced000-b6cee000 rw-p 00001000 03:41 7685865    /usr/lib/beryl/libsvg.so
b6cee000-b6cf0000 r-xp 00000000 03:41 7685867    /usr/lib/beryl/libtext.so
b6cf0000-b6cf1000 rw-p 00001000 03:41 7685867    /usr/lib/beryl/libtext.so
b6cf1000-b6cf5000 r-xp 00000000 03:41 7685849    /usr/lib/beryl/libinputzoom.so
b6cf5000-b6cf6000 rw-p 00003000 03:41 7685849    /usr/lib/beryl/libinputzoom.so
b6cf6000-b6cf8000 r-xp 00000000 03:41 7685856    /usr/lib/beryl/libpng.so
b6cf8000-b6cf9000 rw-p 00002000 03:41 7685856    /usr/lib/beryl/libpng.so
b6cf9000-b6cfd000 r-xp 00000000 03:41 7685842    /usr/lib/beryl/libdbus.so
b6cfd000-b6cfe000 rw-p 00003000 03:41 7685842    /usr/lib/beryl/libdbus.so
b6cfe000-b6d02000 rw-s 038b9000 00:0d 17386      /dev/nvidia0
b6d02000-b6d03000 rw-s ef873000 00:0d 17386      /dev/nvidia0
b6d03000-b6d04000 rw-s 038b7000 00:0d 17386      /dev/nvidia0
b6d04000-b6d5f000 rw-p 00000000 00:0d 2685       /dev/zero
b6d5f000-b6d60000 rw-s 038b6000 00:0d 17386      /dev/nvidia0
b6d60000-b7060000 rw-s e0000000 00:0d 17386      /dev/nvidia0
b7060000-b707e000 rw-s 00000000 00:08 0          /SYSV00000000 (deleted)
b707e000-b7087000 r-xp 00000000 03:41 10749203   /lib/tls/i686/cmov/libnss_files-2.5.so
b7087000-b7089000 rw-p 00008000 03:41 10749203   /lib/tls/i686/cmov/libnss_files-2.5.so
b7089000-b709c000 r-xp 00000000 03:41 10749197   /lib/tls/i686/cmov/libnsl-2.5.so
b709c000-b709e000 rw-p 00012000 03:41 10749197   /lib/tls/i686/cmov/libnsl-2.5.so
b709e000-b70a0000 rw-p b709e000 00:00 0 
b70a0000-b70a7000 r-xp 00000000 03:41 10749199   /lib/tls/i686/cmov/libnss_compat-2.5.so
b70a7000-b70a9000 rw-p 00006000 03:41 10749199   /lib/tls/i686/cmov/libnss_compat-2.5.so
b70a9000-b70aa000 rw-s f7001000 00:0d 17386      /dev/nvidia0
b70aa000-b70ab000 rw-s f7c02000 00:0d 17386      /dev/nvidia0
b70ab000-b70b3000 r-xp 00000000 03:41 7095782    /usr/lib/libXcursor.so.1.0.2
b70b3000-b70b4000 rw-p 00007000 03:41 7095782    /usr/lib/libXcursor.so.1.0.2
b70b4000-b70bb000 r--s 00000000 03:41 12501227   /usr/lib/gconv/gconv-modules.cache
b70bb000-b7118000 rw-p b70bb000 00:00 0 
b7118000-b711c000 r-xp 00000000 03:41 7095786    /usr/lib/libXdmcp.so.6.0.0
b711c000-b711d000 rw-p 00003000 03:41 7095786    /usr/lib/libXdmcp.so.6.0.0
b711d000-b711f000 r-xp 00000000 03:41 7095775    /usr/lib/libXau.so.6.0.0
b711f000-b7120000 rw-p 00001000 03:41 7095775    /usr/lib/libXau.so.6.0.0
b7120000-b7121000 r-xp 00000000 03:41 8242678    /usr/lib/nvidia/libnvidia-tls.so.100.14.09
b7121000-b7122000 rw-p 00000000 03:41 8242678    /usr/lib/nvidia/libnvidia-tls.so.100.14.09
b7122000-b7a7e000 r-xp 00000000 03:41 7095894    /usr/lib/libGLcore.so.100.14.09
b7a7e000-b7ab6000 rwxp 0095c000 03:41 7095894    /usr/lib/libGLcore.so.100.14.09
b7ab6000-b7aba000 rwxp b7ab6000 00:00 0 
b7aba000-b7abb000 rw-p b7aba000 00:00 0 
b7abb000-b7ace000 r-xp 00000000 03:41 7096584    /usr/lib/libz.so.1.2.3
b7ace000-b7acf000 rw-p 00012000 03:41 7096584    /usr/lib/libz.so.1.2.3
b7acf000-b7ad1000 r-xp 00000000 03:41 10749192   /lib/tls/i686/cmov/libdl-2.5.so
b7ad1000-b7ad3000 rw-p 00001000 03:41 10749192   /lib/tls/i686/cmov/libdl-2.5.so
b7ad3000-b7ada000 r-xp 00000000 03:41 7095812    /usr/lib/libXrender.so.1.3.0
b7ada000-b7adb000 rw-p 00006000 03:41 7095812    /usr/lib/libXrender.so.1.3.0
b7adb000-b7ae8000 r-xp 00000000 03:41 7095790    /usr/lib/libXext.so.6.4.0
b7ae8000-b7ae9000 rw-p 0000d000 03:41 7095790    /usr/lib/libXext.so.6.4.0
b7ae9000-b7bd6000 r-xp 00000000 03:41 7095769    /usr/lib/libX11.so.6.2.0
b7bd6000-b7bda000 rw-p 000ed000 03:41 7095769    /usr/lib/libX11.so.6.2.0
b7bda000-b7bdb000 rw-p b7bda000 00:00 0 
b7bdb000-b7d16000 r-xp 00000000 03:41 10749186   /lib/tls/i686/cmov/libc-2.5.so
b7d16000-b7d17000 r--p 0013b000 03:41 10749186   /lib/tls/i686/cmov/libc-2.5.so
b7d17000-b7d19000 rw-p 0013c000 03:41 10749186   /lib/tls/i686/cmov/libc-2.5.so
b7d19000-b7d1c000 rw-p b7d19000 00:00 0 
b7d1c000-b7d2a000 r-xp 00000000 03:41 7095963    /usr/lib/libberylsettings.so.0.0.0
b7d2a000-b7d2b000 rw-p 0000d000 03:41 7095963    /usr/lib/libberylsettings.so.0.0.0
b7d2b000-b7d2c000 rw-p b7d2b000 00:00 0 
b7d2c000-b7d51000 r-xp 00000000 03:41 10749194   /lib/tls/i686/cmov/libm-2.5.so
b7d51000-b7d53000 rw-p 00024000 03:41 10749194   /lib/tls/i686/cmov/libm-2.5.so
b7d53000-b7dcc000 r-xp 00000000 03:41 7095955    /usr/lib/libGL.so.100.14.09
b7dcc000-b7de7000 rwxp 00079000 03:41 7095955    /usr/lib/libGL.so.100.14.09
b7de7000-b7de8000 rwxp b7de7000 00:00 0 
b7de8000-b7e7c000 r-xp 00000000 03:41 7096103    /usr/lib/libglib-2.0.so.0.1200.11
b7e7c000-b7e7d000 rw-p 00093000 03:41 7096103    /usr/lib/libglib-2.0.so.0.1200.11
b7e7d000-b7e85000 r-xp 00000000 03:41 7096513    /usr/lib/libstartup-notification-1.so.0.0.0
b7e85000-b7e86000 rw-p 00007000 03:41 7096513    /usr/lib/libstartup-notification-1.so.0.0.0
b7e86000-b7e87000 rw-p b7e86000 00:00 0 
b7e87000-b7e89000 r-xp 00000000 03:41 7095800    /usr/lib/libXinerama.so.1.0.0
b7e89000-b7e8a000 rw-p 00001000 03:41 7095800    /usr/lib/libXinerama.so.1.0.0
b7e8a000-b7e9f000 r-xp 00000000 03:41 7095747    /usr/lib/libICE.so.6.3.0
b7e9f000-b7ea1000 rw-p 00014000 03:41 7095747    /usr/lib/libICE.so.6.3.0
b7ea1000-b7ea2000 rw-p b7ea1000 00:00 0 
b7ea2000-b7eaa000 r-xp 00000000 03:41 7095765    /usr/lib/libSM.so.6.0.0
b7eaa000-b7eab000 rw-p 00007000 03:41 7095765    /usr/lib/libSM.so.6.0.0
b7eab000-b7eb0000 r-xp 00000000 03:41 7095810    /usr/lib/libXrandr.so.2.1.0
b7eb0000-b7eb1000 rw-p 00005000 03:41 7095810    /usr/lib/libXrandr.so.2.1.0
b7eb1000-b7eb5000 r-xp 00000000 03:41 7095792    /usr/lib/libXfixes.so.3.1.0
b7eb5000-b7eb6000 rw-p 00003000 03:41 7095792    /usr/lib/libXfixes.so.3.1.0
b7eb6000-b7eb8000 r-xp 00000000 03:41 7095784    /usr/lib/libXdamage.so.1.0.0
b7eb8000-b7eb9000 rw-p 00001000 03:41 7095784    /usr/lib/libXdamage.so.1.0.0
b7eb9000-b7eba000 rw-p b7eb9000 00:00 0 
b7eba000-b7ebc000 r-xp 00000000 03:41 7095780    /usr/lib/libXcomposite.so.1.0.0
b7ebc000-b7ebd000 rw-p 00001000 03:41 7095780    /usr/lib/libXcomposite.so.1.0.0
b7ebd000-b7edf000 r-xp 00000000 03:41 7095120    /usr/lib/libpng12.so.0.15.0
b7edf000-b7ee0000 rw-p 00021000 03:41 7095120    /usr/lib/libpng12.so.0.15.0
b7ee0000-b7ee4000 r-xp 00000000 03:41 7684238    /usr/lib/beryl/backends/libini.so
b7ee4000-b7ee5000 rw-p 00004000 03:41 7684238    /usr/lib/beryl/backends/libini.so
b7ee5000-b7eed000 r-xp 00000000 03:41 10749207   /lib/tls/i686/cmov/libnss_nis-2.5.so
b7eed000-b7eef000 rw-p 00007000 03:41 10749207   /lib/tls/i686/cmov/libnss_nis-2.5.so
b7eef000-b7ef0000 rw-p b7eef000 00:00 0 
b7ef0000-b7ef2000 rwxp 00000000 00:0d 2685       /dev/zero
b7ef2000-b7ef4000 rw-p b7ef2000 00:00 0 
b7ef4000-b7f0d000 r-xp 00000000 03:41 10715157   /lib/ld-2.5.so
b7f0d000-b7f0f000 rw-p 00019000 03:41 10715157   /lib/ld-2.5.so
bfec9000-bfee7000 rwxp bfec9000 00:00 0          [stack]
bfee7000-bfeea000 rw-p bfee7000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```


so beryl wont start..... it used to work... and now all of the sudden it stopped working... also... i can't install emerald... it says i cannot install emerald because it has unmet dependencies (libemeraldengine0) so it wont be installed... but when i go to install that.. it says i have emerald as an unmet dependency and it wont install... (this is using synaptic but apt-get does the same thing) on Feisty Fawn... well... ubuntu ultimate 1.4 (which is feisty fawn) was wonderin if anyone could help!! thanks!!!

---

