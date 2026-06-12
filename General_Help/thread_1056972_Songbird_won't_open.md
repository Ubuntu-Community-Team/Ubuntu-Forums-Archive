---
title: "Songbird won't open"
date: 2009-02-01
forum: General Help
---

### Post by jcphil on 2009-02-01
I tried both the tar ball and the .deb package for Songbird, but both give me the same results. It starts to reference all the libs it needs to run and then it just stops. My last attempt looked like this:

rebus@rebus-desktop:~/Desktop/Songbird$ ./songbird
*** glibc detected *** ././songbird-bin: munmap_chunk(): invalid pointer: 0xb37a80a0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d5c454]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb3484141]
/usr/lib/libvisual-0.4.so.0[0xb347b407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb347b5e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb348aec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb34c21f4]
/home/rebus/Desktop/Songbird/lib/libgstreamer-0.10.so[0xb41a52c2]
/home/rebus/Desktop/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb41a5b79]
/home/rebus/Desktop/Songbird/lib/libgstreamer-0.10.so[0xb41b07ee]
/home/rebus/Desktop/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb41b0993]
/home/rebus/Desktop/Songbird/lib/libgstreamer-0.10.so[0xb4160a44]
/home/rebus/Desktop/Songbird/lib/libgstreamer-0.10.so[0xb4160f30]
/home/rebus/Desktop/Songbird/lib/libgstreamer-0.10.so[0xb4161589]
/home/rebus/Desktop/Songbird/lib/libgstreamer-0.10.so[0xb4161b44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6b697e3]
/home/rebus/Desktop/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb415fd1b]
/home/rebus/Desktop/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb415fe25]
/home/rebus/Desktop/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb40cacf3]
/home/rebus/Desktop/Songbird/lib/sbGStreamerMediacore.so[0xb40d18e1]
/home/rebus/Desktop/Songbird/lib/sbGStreamerMediacore.so[0xb40d8252]
/home/rebus/Desktop/Songbird/xulrunner/libxul.so[0xb7610449]
/home/rebus/Desktop/Songbird/xulrunner/libxul.so[0xb760f90b]
/home/rebus/Desktop/Songbird/lib/sbGStreamerMediacore.so[0xb40d52ef]
/home/rebus/Desktop/Songbird/lib/sbGStreamerMediacore.so[0xb40d5319]
/home/rebus/Desktop/Songbird/lib/sbGStreamerMediacore.so[0xb40d4ac5]
/home/rebus/Desktop/Songbird/lib/sbGStreamerMediacore.so[0xb40d03a5]
/home/rebus/Desktop/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb40d0b5c]
/home/rebus/Desktop/Songbird/lib/sbGStreamerMediacore.so[0xb40d1841]
/home/rebus/Desktop/Songbird/lib/sbGStreamerMediacore.so[0xb40d8252]
/home/rebus/Desktop/Songbird/xulrunner/libxul.so[0xb7610449]
/home/rebus/Desktop/Songbird/components/sbMediacoreManager.so[0xb3a100f9]
/home/rebus/Desktop/Songbird/components/sbMediacoreManager.so[0xb3a10126]
/home/rebus/Desktop/Songbird/components/sbMediacoreManager.so[0xb3a0f9c1]
/home/rebus/Desktop/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb39fc8b5]
/home/rebus/Desktop/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb39fa1e7]
/home/rebus/Desktop/Songbird/components/sbMediacoreManager.so[0xb39fa564]
/home/rebus/Desktop/Songbird/xulrunner/libxul.so[0xb75ed21f]
/home/rebus/Desktop/Songbird/xulrunner/libxul.so[0xb75ed7c4]
/home/rebus/Desktop/Songbird/xulrunner/libxul.so[0xb6e82a98]
/home/rebus/Desktop/Songbird/xulrunner/libxul.so(XRE_main+0x1aba)[0xb6e807b2]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d03685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:03 360510     /home/rebus/Desktop/Songbird/songbird-bin
0804e000-0804f000 rw-p 00006000 08:03 360510     /home/rebus/Desktop/Songbird/songbird-bin
087c3000-087e4000 rw-p 087c3000 00:00 0          [heap]
b3462000-b346a000 rw-p b3462000 00:00 0 
b346a000-b34a6000 r-xp 00000000 08:03 2829839    /usr/lib/libvisual-0.4.so.0.0.0
b34a6000-b34a7000 r--p 0003b000 08:03 2829839    /usr/lib/libvisual-0.4.so.0.0.0
b34a7000-b34a8000 rw-p 0003c000 08:03 2829839    /usr/lib/libvisual-0.4.so.0.0.0
b34ab000-b34bb000 rw-p b34ab000 00:00 0 
b34c0000-b34c6000 r-xp 00000000 08:03 2842818    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b34c6000-b34c7000 r--p 00005000 08:03 2842818    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b34c7000-b34c8000 rw-p 00006000 08:03 2842818    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b34c8000-b34d4000 r-xp 00000000 08:03 2842924    /usr/lib/gstreamer-0.10/libgstpango.so
b34d4000-b34d5000 r--p 0000b000 08:03 2842924    /usr/lib/gstreamer-0.10/libgstpango.so
b34d5000-b34d6000 rw-p 0000c000 08:03 2842924    /usr/lib/gstreamer-0.10/libgstpango.so
b34d6000-b351f000 r-xp 00000000 08:03 2829814    /usr/lib/libtheora.so.0.3.3
b351f000-b3521000 rw-p 00049000 08:03 2829814    /usr/lib/libtheora.so.0.3.3
b3525000-b352c000 r-xp 00000000 08:03 2842868    /usr/lib/gstreamer-0.10/libgstgconfelements.so
b352c000-b352d000 r--p 00006000 08:03 2842868    /usr/lib/gstreamer-0.10/libgstgconfelements.so
b352d000-b352e000 rw-p 00007000 08:03 2842868    /usr/lib/gstreamer-0.10/libgstgconfelements.so
b352e000-b3537000 r-xp 00000000 08:03 2842923    /usr/lib/gstreamer-0.10/libgstximagesrc.so
b3537000-b3538000 r--p 00008000 08:03 2842923    /usr/lib/gstreamer-0.10/libgstximagesrc.so
b3538000-b3539000 rw-p 00009000 08:03 2842923    /usr/lib/gstreamer-0.10/libgstximagesrc.so
b3539000-b3548000 r-xp 00000000 08:03 2842824    /usr/lib/gstreamer-0.10/libgsttheora.so
b3548000-b3549000 r--p 0000e000 08:03 2842824    /usr/lib/gstreamer-0.10/libgsttheora.so
b3549000-b354a000 rw-p 0000f000 08:03 2842824    /usr/lib/gstreamer-0.10/libgsttheora.so
b354a000-b354e000 r-xp 00000000 08:03 2828769    /usr/lib/libXv.so.1.0.0
b354e000-b354f000 r--p 00003000 08:03 2828769    /usr/lib/libXv.so.1.0.0
b354f000-b3550000 rw-p 00004000 08:03 2828769    /usr/lib/libXv.so.1.0.0
b3551000-b355c000 r-xp 00000000 08:03 2842891    /usr/lib/gstreamer-0.10/libgstossaudio.so
b355c000-b355d000 r--p 0000a000 08:03 2842891    /usr/lib/gstreamer-0.10/libgstossaudio.so
b355d000-b355e000 rw-p 0000b000 08:03 2842891    /usr/lib/gstreamer-0.10/libgstossaudio.so
b355e000-b3566000 r-xp 00000000 08:03 2842892    /usr/lib/gstreamer-0.10/libgstpng.so
b3566000-b3567000 r--p 00007000 08:03 2842892    /usr/lib/gstreamer-0.10/libgstpng.so
b3567000-b3568000 rw-p 00008000 08:03 2842892    /usr/lib/gstreamer-0.10/libgstpng.so
b3568000-b358f000 r-xp 00000000 08:03 2827272    /usr/lib/libsidplay.so.1.0.3
b358f000-b359f000 rw-p 00026000 08:03 2827272    /usr/lib/libsidplay.so.1.0.3
b359f000-b35ab000 rw-p b359f000 00:00 0 
b35ab000-b3612000 r-xp 00000000 08:03 2829804    /usr/lib/libtag.so.1.5.0
b3612000-b3613000 r--p 00067000 08:03 2829804    /usr/lib/libtag.so.1.5.0
b3613000-b3614000 rw-p 00068000 08:03 2829804    /usr/lib/libtag.so.1.5.0
b3618000-b362a000 r-xp 00000000 08:03 2842826    /usr/lib/gstreamer-0.10/libgstvideo4linux.so
b362a000-b362b000 r--p 00012000 08:03 2842826    /usr/lib/gstreamer-0.10/libgstvideo4linux.so
b362b000-b362c000 rw-p 00013000 08:03 2842826    /usr/lib/gstreamer-0.10/libgstvideo4linux.so
b362c000-b363a000 r-xp 00000000 08:03 2830045    /usr/lib/libid3tag.so.0.3.0
b363a000-b363c000 rw-p 0000d000 08:03 2830045    /usr/lib/libid3tag.so.0.3.0
b363c000-b3652000 r-xp 00000000 08:03 2827981    /usr/lib/libmad.so.0.2.1
b3652000-b3653000 r--p 00015000 08:03 2827981    /usr/lib/libmad.so.0.2.1
b3653000-b3654000 rw-p 00016000 08:03 2827981    /usr/lib/libmad.so.0.2.1
b3654000-b365e000 r-xp 00000000 08:03 2842878    /usr/lib/gstreamer-0.10/libgstinterleave.so
b365e000-b365f000 r--p 00009000 08:03 2842878    /usr/lib/gstreamer-0.10/libgstinterleave.so
b365f000-b3660000 rw-p 0000a000 08:03 2842878    /usr/lib/gstreamer-0.10/libgstinterleave.so
b3660000-b366a000 r-xp 00000000 08:03 2842912    /usr/lib/gstreamer-0.10/libgsttaglib.so
b366a000-b366b000 r--p 00009000 08:03 2842912    /usr/lib/gstreamer-0.10/libgsttaglib.so
b366b000-b366c000 rw-p 0000a000 08:03 2842912    /usr/lib/gstreamer-0.10/libgsttaglib.so
b366c000-b368b000 r-xp 00000000 08:03 2829171    /usr/lib/libjpeg.so.62.0.0
b368b000-b368c000 rw-p 0001e000 08:03 2829171    /usr/lib/libjpeg.so.62.0.0
b368c000-b3692000 rw-p b368c000 00:00 0 
b3692000-b36a2000 r-xp 00000000 08:03 2842933    /usr/lib/gstreamer-0.10/libgstmad.so
b36a2000-b36a3000 r--p 0000f000 08:03 2842933    /usr/lib/gstreamer-0.10/libgstmad.so
b36a3000-b36a4000 rw-p 00010000 08:03 2842933    /usr/lib/gstreamer-0.10/libgstmad.so
b36a4000-b36b0000 r-xp 00000000 08:03 2859873    /usr/lib/i686/cmov/libpostproc.so.51.1.0
b36b0000-b36b1000 r--p 0000b000 08:03 2859873    /usr/lib/i686/cmov/l

---

### Post by jcphil on 2009-02-01
OK. I found some other posts on this, but no real solution. Seems to be the nVidia driver, combined with Cairo and Glitz

---

