---
title: "Can't get Songbird to start"
date: 2009-04-05
forum: General Help
---

### Post by villainy on 2009-04-05
Hi,

I downloaded Songbird 1.1.1 and I can't get it to start. I installed it via package from getdeb.net and it installed fine, but it won't start. I'll go into Applications > Sound & Video > Songbird and it'll load, but won't show up. I'll do it again and a popup comes up with a notification that Songbird is already running.

I went ahead and looked at what programs are running and there are two songbird files running and two songbird-bin files running. Even after I kill them and try it again, still the same problem.

Any ideas? It worked fine an older install of Intrepid (installed another distro and came back to Intrepid). I even tried downloading and installing another .deb from another site other than getdeb.net and still the same problem.

Thanks

---

### Post by 67GTA on 2009-04-05
I remember reading somewhere about a conflict with libvisual. Try removing it. You might also try starting it from a terminal to see if it spits out any errors.

```
sudo apt-get remove libvisual-0.4-plugins

```

---

### Post by |Porsche on 2009-04-05
start from command line and post output.

---

### Post by villainy on 2009-04-05
Here is what I get in the terminal:

```
*** glibc detected *** ././songbird-bin: munmap_chunk(): invalid pointer: 0xb3181b00 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7cf1454]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb2f36141]
/usr/lib/libvisual-0.4.so.0[0xb2f2d407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb2f2d5e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb2f3cec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb2f6e1f4]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3b592f6]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb3b59bad]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3b64822]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb3b649c7]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3b14a44]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3b14f30]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3b15589]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3b15b44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6ae0803]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb3b13d1b]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb3b13e25]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb3a0e6a3]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a16a05]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a1fdb6]
/usr/share/Songbird/xulrunner/libxul.so[0xb75a0a85]
/usr/share/Songbird/xulrunner/libxul.so[0xb759ff47]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a1ce83]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a1cead]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a1c659]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a15413]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb3a15be0]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a16965]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a1fdb6]
/usr/share/Songbird/xulrunner/libxul.so[0xb75a0a85]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb40d5e29]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb40d5e56]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb40d56f1]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb40be705]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb40bc2d7]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb40bc654]
/usr/share/Songbird/xulrunner/libxul.so[0xb757d773]
/usr/share/Songbird/xulrunner/libxul.so[0xb757dd18]
/usr/share/Songbird/xulrunner/libxul.so[0xb6e11be0]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x19af)[0xb6e0f8c1]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7c98685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:07 279295     /usr/share/Songbird/songbird-bin
0804e000-0804f000 rw-p 00006000 08:07 279295     /usr/share/Songbird/songbird-bin
093c8000-093e9000 rw-p 093c8000 00:00 0          [heap]
b2f1c000-b2f58000 r-xp 00000000 08:07 1878461    /usr/lib/libvisual-0.4.so.0.0.0
b2f58000-b2f59000 r--p 0003b000 08:07 1878461    /usr/lib/libvisual-0.4.so.0.0.0
b2f59000-b2f5a000 rw-p 0003c000 08:07 1878461    /usr/lib/libvisual-0.4.so.0.0.0
b2f5f000-b2f67000 rw-p b2f5f000 00:00 0 
b2f6c000-b2f72000 r-xp 00000000 08:07 540783     /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2f72000-b2f73000 r--p 00005000 08:07 540783     /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2f73000-b2f74000 rw-p 00006000 08:07 540783     /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2f74000-b2f9d000 r-xp 00000000 08:07 279172     /usr/share/Songbird/gst-plugins/libgstmatroska.so
b2f9d000-b2f9e000 rw-p 00028000 08:07 279172     /usr/share/Songbird/gst-plugins/libgstmatroska.so
b2f9e000-b2fa7000 r-xp 00000000 08:07 279161     /usr/share/Songbird/gst-plugins/libgsteffectv.so
b2fa7000-b2fa8000 rw-p 00008000 08:07 279161     /usr/share/Songbird/gst-plugins/libgsteffectv.so
b2fa8000-b2fb6000 r-xp 00000000 08:07 279197     /usr/share/Songbird/gst-plugins/libgstaudioconvert.so
b2fb6000-b2fb7000 rw-p 0000d000 08:07 279197     /usr/share/Songbird/gst-plugins/libgstaudioconvert.so
b2fb7000-b2fba000 r-xp 00000000 08:07 876586     /lib/libcap.so.1.10
b2fba000-b2fbb000 rw-p 00002000 08:07 876586     /lib/libcap.so.1.10
b2fbb000-b3009000 r-xp 00000000 08:07 1877371    /usr/lib/libpulse.so.0.4.1
b3009000-b300a000 r--p 0004d000 08:07 1877371    /usr/lib/libpulse.so.0.4.1
b300a000-b300b000 rw-p 0004e000 08:07 1877371    /usr/lib/libpulse.so.0.4.1
b300b000-b3012000 r-xp 00000000 08:07 279145     /usr/share/Songbird/gst-plugins/libgstsdpelem.so
b3012000-b3013000 rw-p 00006000 08:07 279145     /usr/share/Songbird/gst-plugins/libgstsdpelem.so
b3013000-b301c000 r-xp 00000000 08:07 279130     /usr/share/Songbird/gst-plugins/libgstselector.so
b301c000-b301d000 rw-p 00008000 08:07 279130     /usr/share/Songbird/gst-plugins/libgstselector.so
b301d000-b302b000 r-xp 00000000 08:07 279176     /usr/share/Songbird/gst-plugins/libgstpulse.so
b302b000-b302c000 rw-p 0000d000 08:07 279176     /usr/share/Songbird/gst-plugins/libgstpulse.so
b302c000-b3036000 r-xp 00000000 08:07 279163     /usr/share/Songbird/gst-plugins/libgstdecodebin.so
b3036000-b3037000 rw-p 00009000 08:07 279163     /usr/share/Songbird/gst-plugins/libgstdecodebin.so
b3037000-b3057000 r-xp 00000000 08:07 279140     /usr/share/Songbird/gst-plugins/libgstogg.so
b3057000-b3058000 rw-p 00020000 08:07 279140     /usr/share/Songbird/gst-plugins/libgstogg.so
b3058000-b3063000 r-xp 00000000 08:07 279181     /usr/share/Songbird/gst-plugins/libgstvideoscale.so
b3063000-b3064000 rw-p 0000b000 08:07 279181     /usr/share/Songbird/gst-plugins/libgstvideoscale.so
b3064000-b3068000 r-xp 00000000 08:07 279164     /usr/share/Songbird/gst-plugins/libgstalaw.so
b3068000-b3069000 rw-p 00003000 08:07 279164     /usr/share/Songbird/gst-plugins/libgstalaw.so
b3069000-b309d000 r-xp 00000000 08:07 279193     /usr/share/Songbird/gst-plugins/libgstffmpegcolorspace.so
b309d000-b309e000 rw-p 00033000 08:07 279193     /usr/share/Songbird/gst-plugins/libgstffmpegcolorspace.so
b309e000-b309f000 rw-p b309e000 00:00 0 
b309f000-b30a2000 r-xp 00000000 08:07 279135     /usr/share/Songbird/gst-plugins/libgstmulaw.so
b30a2000-b30a3000 rw-p 00002000 08:07 279135     /usr/share/Songbird/gst-plugins/libgstmulaw.so
b30a3000-b30ac000 r-xp 00000000 08:07 279162     /usr/share/Songbird/gst-plugins/libgstreplaygain.so
b30ac000-b30ad000 rw-p 00009000 08:07 279162     /usr/share/Songbird/gst-plugins/libgstreplaygain.so
b30ad000-b30b2000 r-xp 00000000 08:07 279171     /usr/share/Songbird/gst-plugins/libgstalpha.so
b30b2000-b30b3000 rw-p 00004000 08:07 279171     /usr/share/Songbird/gst-plugins/libgstalpha.so
b30b3000-b30e8000 r-xp 00000000 08:07 279174     /usr/share/Songbird/gst-plugins/libgstrtp.so
b30e8000-b30eb000 rw-p 00034000 08:07 279174     /usr/share/Songbird/gst-plugins/libgstrtp.so
b30eb000-b30fc000 r-xp 00000000 08:07 279195     /usr/share/Songbird/gst-plugins/libgstflac.so
b30fc000-b30fd000 rw-p 00010000 08:07 279195     /usr/share/Songbird/gst-plugins/libgstflac.so
b30fd000-b30ff000 r-xp 00000000 08:07 279192     /usr/share/Songbird/gst-plugins/libgstgamma.so
b30ff000-b3100000 rw-p 00001000 08:07 279192     /usr/share/Songbird/gst-plugins/libgstgamma.so
b3100000-b3200000 rw-p b3100000 00:00 0 
b3201000-b3211000 r-xp 00000000 08:07 279194     /usr/share/Songbird/gst-plugins/libgstmpegaudioparse.so
b3211000-b3212000 rw-p 00010000 08:07 279194     /usr/share/Songbird/gst-plugins/libgstmpegaudioparse.so
b3212000-b323b000 r-xp 00000000 08:07 279173     /usr/share/Songbird/gst-plugins/libgstplaybin.so
b323b000-b323c000 rw-p 00028000 08:07 279173     /usr/share/Songbird/gst-plugins/libgstplaybin.so
b323c000-b324c000 r-xp 00000000 08:07 279198     /usr/share/Songbird/gst-plugins/libgsttheora.so
b324c000-b324d000 rw-p 0000f000 08:07 279198     /usr/share/Songbird/gst-plugins/libgsttheora.so
b324d000-b324f000 r-xp 00000000 08:07 279178     /usr/share/Songbird/gst-plugins/libgstcoreindexers.so
b324f000-b3250000 rw-p 00001000 08:07 279178     /usr/share/Songbird/gst-plugins/libgstcoreindexers.so
b3250000-b326c000 r-xp 00000000 08:07 279187     /usr/share/Songbird/gst-plugins/libgstasf.so
b326c000-b326d000 rw-p 0001b000 08:07 279187     /usr/share/Songbird/gst-plugins/libgstasf.so
b326d000-b3299000 r-xp 00000000 08:07 279158     /usr/share/Songbird/gst-plugins/libgstcoreelements.so
b3299000-b329a000 rw-p 0002c000 08:07 279158     /usr/share/Songbird/gst-plugins/libgstcoreelements.so
b329a000-b329f000 r-xp 00000000 08:07 279149     /usr/share/Songbird/gst-plugins/libgstvideobox.so
b329f000-b32a0000 rw-p 00005000 08:07 279149     /usr/share/Songbird/gst-plugins/libgstvideobox.so
b32a0000-b32ac000 r-xp 00000000 08:07 279144     /usr/share/Songbird/gst-plugins/libgstudp.so
b32ac000-b32ad000 rw-p 0000b000 08:07 279144 *** glibc detected *** ././songbird-bin: double free or corruption (out): 0xb4597df0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7cf1454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7cf34b6]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7ece0b1]
/usr/lib/libstdc++.so.6(_ZNSbIwSt11char_traitsIwESaIwEE4_Rep10_M_destroyERKS1_+0x1d)[0xb7ec503d]
/usr/lib/libstdc++.so.6(_ZNSbIwSt11char_traitsIwESaIwEED1Ev+0x51)[0xb7ec5cd1]
/usr/share/Songbird/components/sbMetadataHandlerTaglib.so(_ZN6TagLib6String13StringPrivateD1Ev+0x38)[0xb3f7db8e]
/usr/share/Songbird/components/sbMetadataHandlerTaglib.so(_ZN6TagLib6StringD1Ev+0x4c)[0xb3f79fce]
/usr/share/Songbird/components/sbMetadataHandlerTaglib.so[0xb3f54a2d]
/lib/tls/i686/cmov/libc.so.6(exit+0x89)[0xb7cb0d89]
/usr/share/Songbird/xulrunner/libxul.so[0xb6e1aaa6]
/usr/share/Songbird/xulrunner/libxul.so[0xb6e162ce]
[0xb7f58400]
/lib/tls/i686/cmov/libc.so.6(abort+0x188)[0xb7caf268]
/lib/tls/i686/cmov/libc.so.6[0xb7ceb16d]
/lib/tls/i686/cmov/libc.so.6[0xb7cf1454]
/usr/share/Songbird/xulrunner/libxul.so[0xb6e158af]
/usr/share/Songbird/xulrunner/libxul.so[0xb6e16291]
[0xb7f58400]
/lib/tls/i686/cmov/libc.so.6(abort+0x188)[0xb7caf268]
/lib/tls/i686/cmov/libc.so.6[0xb7ceb16d]
/lib/tls/i686/cmov/libc.so.6[0xb7cf1454]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb2f36141]
/usr/lib/libvisual-0.4.so.0[0xb2f2d407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb2f2d5e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb2f3cec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb2f6e1f4]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3b592f6]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb3b59bad]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3b64822]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb3b649c7]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3b14a44]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3b14f30]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3b15589]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3b15b44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6ae0803]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb3b13d1b]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb3b13e25]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb3a0e6a3]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a16a05]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a1fdb6]
/usr/share/Songbird/xulrunner/libxul.so[0xb75a0a85]
/usr/share/Songbird/xulrunner/libxul.so[0xb759ff47]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a1ce83]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a1cead]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a1c659]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a15413]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb3a15be0]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a16965]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3a1fdb6]
/usr/share/Songbird/xulrunner/libxul.so[0xb75a0a85]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb40d5e29]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb40d5e56]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb40d56f1]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb40be705]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb40bc2d7]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb40bc654]
/usr/share/Songbird/xulrunner/libxul.so[0xb757d773]
/usr/share/Songbird/xulrunner/libxul.so[0xb757dd18]
/usr/share/Songbird/xulrunner/libxul.so[0xb6e11be0]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x19af)[0xb6e0f8c1]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7c98685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:07 279295     /usr/share/Songbird/songbird-bin
0804e000-0804f000 rw-p 00006000 08:07 279295     /usr/share/Songbird/songbird-bin
093c8000-093e9000 rw-p 093c8000 00:00 0          [heap]
b2f1c000-b2f58000 r-xp 00000000 08:07 1878461    /usr/lib/libvisual-0.4.so.0.0.0
b2f58000-b2f59000 r--p 0003b000 08:07 1878461    /usr/lib/libvisual-0.4.so.0.0.0
b2f59000-b2f5a000 rw-p 0003c000 08:07 1878461    /usr/lib/libvisual-0.4.so.0.0.0
b2f5f000-b2f67000 rw-p b2f5f000 00:00 0 
b2f6c000-b2f72000 r-xp 00000000 08:07 540783     /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2f72000-b2f73000 r--p 00005000 08:07 540783     /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2f73000-b2f74000 rw-p 00006000 08:07 540783     /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2f74000-b2f9d000 r-xp 00000000 08:07 279172     /usr/share/Songbird/gst-plugins/libgstmatroska.so
b2f9d000-b2f9e000 rw-p 00028000 08:07 279172     /usr/share/Songbird/gst-plugins/libgstmatroska.so
b2f9e000-b2fa7000 r-xp 00000000 08:07 279161     /usr/share/Songbird/gst-plugins/libgsteffectv.so
b2fa7000-b2fa8000 rw-p 00008000 08:07 279161     /usr/share/Songbird/gst-plugins/libgsteffectv.so
b2fa8000-b2fb6000 r-xp 00000000 08:07 279197     /usr/share/Songbird/gst-plugins/libgstaudioconvert.so
b2fb6000-b2fb7000 rw-p 0000d000 08:07 279197     /usr/share/Songbird/gst-plugins/libgstaudioconvert.so
b2fb7000-b2fba000 r-xp 00000000 08:07 876586     /lib/libcap.so.1.10
b2fba000-b2fbb000 rw-p 00002000 08:07 876586     /lib/libcap.so.1.10
b2fbb000-b3009000 r-xp 00000000 08:07 1877371    /usr/lib/libpulse.so.0.4.1
b3009000-b300a000 r--p 0004d000 08:07 1877371    /usr/lib/libpulse.so.0.4.1
b300a000-b300b000 rw-p 0004e000 08:07 1877371    /usr/lib/libpulse.so.0.4.1
b300b000-b3012000 r-xp 00000000 08:07 279145     /usr/share/Songbird/gst-plugins/libgstsdpelem.so
b3012000-b3013000 rw-p 00006000 08:07 279145     /usr/share/Songbird/gst-plugins/libgstsdpelem.so
b3013000-b301c000 r-xp 00000000 08:07 279130     /usr/share/Songbird/gst-plugins/libgstselector.so
b301c000-b301d000 rw-p 00008000 08:07 279130     /usr/share/Songbird/gst-plugins/libgstselector.so
b301d000-b302b000 r-xp 00000000 08:07 279176     /usr/share/Songbird/gst-plugins/libgstpulse.so
b302b000-b302c000 rw-p 0000d000 08:07 279176     /usr/share/Songbird/gst-plugins/libgstpulse.so
b302c000-b3036000 r-xp 00000000 08:07 279163     /usr/share/Songbird/gst-plugins/libgstdecodebin.so
b3036000-b3037000 rw-p 00009000 08:07 279163     /usr/share/Songbird/gst-plugins/libgstdecodebin.so
b3037000-b3057000 r-xp 00000000 08:07 279140     /usr/share/Songbird/gst-plugins/libgstogg.so
b3057000-b3058000 rw-p 00020000 08:07 279140     /usr/share/Songbird/gst-plugins/libgstogg.so
b3058000-b3063000 r-xp 00000000 08:07 279181     /usr/share/Songbird/gst-plugins/libgstvideoscale.so
b3063000-b3064000 rw-p 0000b000 08:07 279181     /usr/share/Songbird/gst-plugins/libgstvideoscale.so
b3064000-b3068000 r-xp 00000000 08:07 279164     /usr/share/Songbird/gst-plugins/libgstalaw.so
b3068000-b3069000 rw-p 00003000 08:07 279164     /usr/share/Songbird/gst-plugins/libgstalaw.so
b3069000-b309d000 r-xp 00000000 08:07 279193     /usr/share/Songbird/gst-plugins/libgstffmpegcolorspace.so
b309d000-b309e000 rw-p 00033000 08:07 279193     /usr/share/Songbird/gst-plugins/libgstffmpegcolorspace.so
b309e000-b309f000 rw-p b309e000 00:00 0 
b309f000-b30a2000 r-xp 00000000 08:07 279135     /usr/share/Songbird/gst-plugins/libgstmulaw.so
b30a2000-b30a3000 rw-p 00002000 08:07 279135     /usr/share/Songbird/gst-plugins/libgstmulaw.so
b30a3000-b30ac000 r-xp 00000000 08:07 279162     /usr/share/Songbird/gst-plugins/libgstreplaygain.so
b30ac000-b30ad000 rw-p 00009000 08:07 279162     /usr/share/Songbird/gst-plugins/libgstreplaygain.so
b30ad000-b30b2000 r-xp 00000000 08:07 279171     /usr/share/Songbird/gst-plugins/libgstalpha.so
b30b2000-b30b3000 rw-p 00004000 08:07 279171     /usr/share/Songbird/gst-plugins/libgstalpha.so
b30b3000-b30e8000 r-xp 00000000 08:07 279174     /usr/share/Songbird/gst-plugins/libgstrtp.so
b30e8000-b30eb000 rw-p 00034000 08:07 279174     /usr/share/Songbird/gst-plugins/libgstrtp.so
b30eb000-b30fc000 r-xp 00000000 08:07 279195     /usr/share/Songbird/gst-plugins/libgstflac.so
b30fc000-b30fd000 rw-p 00010000 08:07 279195     /usr/share/Songbird/gst-plugins/libgstflac.so
b30fd000-b30ff000 r-xp 00000000 08:07 279192     /usr/share/Songbird/gst-plugins/libgstgamma.so
b30ff000-b3100000 rw-p 00001000 08:07 279192     /usr/share/Songbird/gst-plugins/libgstgamma.so
b3100000-b3200000 rw-p b3100000 00:00 0 
b3201000-b3211000 r-xp 00000000 08:07 279194     /usr/share/Songbird/gst-plugins/libgstmpegaudioparse.so
b3211000-b3212000 rw-p 00010000 08:07 279194     /usr/share/Songbird/gst-plugins/libgstmpegaudioparse.so
b3212000-b323b000 r-xp 00000000 08:07 279173     /usr/share/Songbird/gst-plugins/libgstplaybin.so
b323b000-b323c000 rw-p 00028000 08:07 279173     /usr/share/Songbird/gst-plugins/libgstplaybin.so
b323c000-b324c000 r-xp 00000000 08:07 279198     /usr/share/Songbird/gst-plugins/libgsttheora.so
b324c000-b324d000 rw-p 0000f000 08:07 279198     /usr/share/Songbird/gst-plugins/libgsttheora.so
b324d000-b324f000 r-xp 00000000 08:07 279178     /usr/share/Songbird/gst-plugins/libgstcoreindexers.so
b324f000-b3250000 rw-p 00001000 08:07 279178     /usr/share/Songbird/gst-plugins/libgstcoreindexers.so
b3250000-b326c000 r-xp 00000000 08:07 279187     /usr/share/Songbird/gst-plugins/libgstasf.so
b326c000-b326d000 rw-p 0001b000 08:07 279187     /usr/share/Songbird/gst-plugins/libgstasf.so
b326d000-b3299000 r-xp 00000000 08:07 279158     /usr/share/Songbird/gst-plugins/libgstcoreelements.so
b3299000-b329a000 rw-p 0002c000 08:07 279158     /usr/share/Songbird/gst-plugins/libgstcoreelements.so
b329a000-b329f000 r-xp 00000000 08:07 279149     /usr/share/Songbird/gst-plugins/libgstvideobox.so
b329f000-b32a0000 rw-p 00005000 08:07 279149     /usr/share/Songbird/gst-plugins/libgstvideobox.so
b32a0000-b32ac000 r-xp 00000000 08:07 279144     /usr/share/Songbird/gst-plugins/libgstudp.so
b32ac000-b32ad000 rw-p 0000b000 08:07 279144     /usr/share/Songbird/gst-plugins/libgstudp.so
b32ad000-b32b3000 r-xp 00000000 08:07 279160     /usr/share/Songbird/gst-plugins/libgstequalizer.so
b32b3000-b32b4000 rw-p 00005000 08:07 279160     /usr/share/Songbird/gst-plugins/libgstequalizer.so
b32b4000-b32b8000 r-xp 00000000 08:07 279185     /usr/share/Songbird/gst-plugins/libgstcutter.so
b32b8000-b32b9000 rw-p 00003000 08:07 279185     /usr/share/Songbird/gst-plugins/libgstcutter.so
b32b9000-b32d9000 r-xp 00000000 08:07 279154     /usr/share/Songbird/gst-plugins/libgstavi.so
b32d9000-b32da000 rw-p 0001f000 08:07 279154     /usr/share/Songbird/gst-plugins/libgstavi.so
b32da000-b32de000 r-xp 00000000 08:07 279177     /usr/share/Songbird/gst-plugins/libgstvideoflip.so
b32de000-b32df000 rw-p 00004000 08:07 279177     /usr/share/Songbird/gst-plugins/libgstvideoflip.so
b32df000-b32e4000 r-xp 00000000 08:07 279159     /usr/share/Songbird/gst-plugins/libgstlevel.so
b32e4000-b32e5000 rw-p 00004000 08:07 279159     /usr/share/Songbird/gst-plugins/libgstlevel.so

(crashreporter:7533): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

---

### Post by 67GTA on 2009-04-05
Remove libvisual plugins with the command I posted earlier and try it again.

---

### Post by villainy on 2009-04-05
> **67GTA said:**
> I remember reading somewhere about a conflict with libvisual. Try removing it. You might also try starting it from a terminal to see if it spits out any errors.

```
sudo apt-get remove libvisual-0.4-plugins

```

This was it. It works now. Thank you!

What exactly are those plugins?

---

### Post by 67GTA on 2009-04-05
They are just extra visuals for multimedia players. The libvisuals package contains the visual effects such as the bars that bounce up and down while a song is playing. The plugins package just adds more visuals. There is some kind of conflict in the code. I just found several bug reports on the songbird forums. Hopefully it will get fixed soon.

---

### Post by Chudilo on 2009-04-07
I had the same error. Uninstalling lib visuals took care of the problem.

---

### Post by James78 on 2009-05-08
Songbird alpha wouldn't work with me. Removing that package also fixed the problem for me. :)

---

